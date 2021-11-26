## Video metadata extraction and knowledge graph

This repository contains a series of 4 jupyter notebooks demonstrating how AWS AI Services like Amazon Rekognition, Amazon Transcribe and Amazon Comprehend can help you extract valuable metadata from your video assets and store that information in a Graph database like Amazon Neptune for maximum query performance and flexibility.
At the end of the workshop you'll typically be able to search for a specific label or entity and return a list of 1min video segments related to your search across your videos.

To extract metadata from a video, we'll use a set of AI services:
- Amazon Rekognition to cut the video in scenes and detect label from the video itself
- Amazon Transcribe to convert audio into text
- Amazon Comprehend to extract entities and topics from the transcribed text via Topic Modelling and Named Entity recognition.

The metadata related to the video, segments, scenes, entities, labels will be stored in Amazon Neptune.
Amazon Neptune is a fully managed low latency graph database service that will allow us to store metadata as nodes (aka vertices) and branches (aka edges) to represent relationships between the nodes.
https://aws.amazon.com/neptune/

The diagram below summarises the workflow:
![Alt text](./static/overview.png?raw=true "workflow overview")

Topics addressed within the different parts:

Part 0:
Create the environment (S3 bucket, IAM roles/polices, SNS topic, Neptune, etc) and upload the sample video

Part 1:
Rekognition Scenes and Labels Detection

Part 2:
Amazon Transcribe and Amazon Comprehend to respectively transcibe audio to text and extract metadata (topics, Named Entities) from transcripts.

Part 3:
Amazon Neptune graph creation and query</br>

Part 4:
Resources clean-up


## Getting started

To run those notebooks you'll need to have a jupyter notebook instance and you'll need to create an Amazon Neptune database if you want to build the graph in part 3 of the workshop (otherwise ignore).

You need to make sure that you create the notebook instance and the Neptune database within the same VPC and that your security group allows them to communicate.

Please follow the below instructions to create your Amazon Neptune cluster. 
You can either follow the console instructions or automatically deploy your cluster with a cloudformation template. https://docs.aws.amazon.com/neptune/latest/userguide/get-started-create-cluster.html

You'll be asked in part0 of the workshop to retrieve the endpoint url and port of your newly created instance.


To create a notebook I recommend to use sagemaker studio and the datascience kernel. This is what I used for developing/testing this workshop.

if you haven't initialised your sagemaker studio environment, follow the instructions here:
https://docs.aws.amazon.com/sagemaker/latest/dg/onboard-iam.html

Do the standard setup and make sure you configure the same VPC as the one you used to create your Amazon Neptune DB.

Once your studio environment is up and running, you can use the git integration functionality to retrieve the workshop's notebooks as described here:
https://docs.aws.amazon.com/sagemaker/latest/dg/studio-tasks-git.html

Finally don't forget to use the datascience kernel to run your notebook as it comes packaged with all the default libraries required to run this notebooks.
https://docs.aws.amazon.com/sagemaker/latest/dg/notebooks-available-kernels.html

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.





