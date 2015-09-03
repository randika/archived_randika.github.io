---
layout: post
title: AWS-Ruby SDK and Elastic Transcoder Example

date: 2015-09-02 18:36:50 +00:00
---

AWS Elastic Transcoder is a very handy service if you looking for a cost effective, scalable solution to Transcode your  audio or video files.
AWS Elastic Transcoder takes input from a S3 bucket, transcodes it, and writes the resulting file to another S3 bucket - well you could also use the same bucket if you prefer.

Here is a very quick code extracted from one of a project I'm currenly working on. Here the uploaded .m4a audio files will be transcoded to HLS (HTTP Live Streaming) - m4a files will be first uploaded to a S3 bucket let’s call it “s3.audio.input”. Files will be saved on the root of the input s3 bucket **s3.audio.input/{UUID}.m4a** and transcoded HLS audio will be saved on **s3.audio.output/hlsv4/{UUID}/index.m3u8**


```ruby
#### transcoder.rb ####
class Transcoder < Message

  STATUS_SUBMITTED =  "Submitted"
  STATUS_PROGRESSING =  "Progressing"
  STATUS_COMPLETE =  "Complete"
  STATUS_CANCELED =  "Canceled"
  STATUS_ERROR =  "Error"

  def initialize(message)
    @message = message
  end

  def create
    uuid = UUID.new
    transcode_job_uuid = uuid.generate

    transcoder = Aws::ElasticTranscoder::Client.new(
      :access_key_id => "YOUR_AWS_ACCESS_KEY_ID",
      :secret_access_key => "YOUR_AWS_SECRET_ACCESS_KEY",
      :region => "us-east-1")

    #HLSV4

    options = {
      pipeline_id: "1432361831290-XXXXX",
      input: {
        key: "ACB685E9-8C3C-4E5D-A49A-8F3BB5298DDC-201509021233.m4a"
        },
      outputs: [
        {
          key: "hls_64k",
          preset_id: '1351620000001-200071',
          segment_duration: "10"
        }
      ],
      playlists: [
        {
          name: "index",
          format: "HLSv4",
          output_keys: ["hls_64k"]
        }
      ],
      output_key_prefix: "hlsv4/#{@message.id}-#{transcode_job_uuid}/"
    }
    job = transcoder.create_job(options)

    @message.update_attributes(
      transcode_job_uuid: transcode_job_uuid,
      transcode_job_id: job.data[:job][:id],
      transcode_job_status: job.data[:job][:status],
      state: Message::STATE_PUBLISHED)

  end

end
```

As you have already noticed, I'm using an UUID to keep track of the data submiited to S3, Trancoder pipeline with active record - (MySQL database).


The example above writes the resulting job data to active record object immediately after submit the job to transcoder service. `job.data[:job][:id]` is the uniqe identification (Usually looks like `1441177406727-xxxxx`) returned from AWS which you can use for further querying the transcoder API and get the details of the submited job.

```ruby
@message.update_attributes(
      transcode_job_uuid: transcode_job_uuid,
      transcode_job_id: job.data[:job][:id],
      transcode_job_status: job.data[:job][:status],
      state: Message::STATE_PUBLISHED)
```


You can also configure Elastic transcoder to work with SNS. AWS transcoder service will trigger SNS notifications to a predefined topic based on these events.

* On Progressing Event
* On Warning Event
* On Completion Event
* On Error Event


For example once the transcode job is finished SNS will notify the status of the job to an endpoint you have configured on your SNS topic.

Hope this helps - Happy coding :)

--RR









