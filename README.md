## Video metadata extraction and knowledge graph

This repository contains a series of 4 jupyter notebooks demonstrating how AWS AI Services like Amazon Rekognition, Amazon Transcribe and Amazon Comprehend can help you extract valuable metadata from your video assets and store that information in a Graph database like Amazon Neptune for maximum query performance and flexibility.
At the end of the workshop you'll typically be able to search for a specific label or entity and return a list of 1min video segments related to your search across your videos.

To extract metadata from a video, we'll use a the following AWS AI services:
- Amazon Rekognition to cut the video in scenes and detect label from the video itself
- Amazon Transcribe to convert audio into text
- Amazon Comprehend to extract entities and topics from the transcribed text via Topic Modelling and Named Entity recognition.

The metadata related to the video, segments, scenes, entities, labels will be stored in Amazon Neptune.
Amazon Neptune is a fully managed low latency graph database service that will allow us to store metadata as nodes (aka vertices) and branches (aka edges) to represent relationships between the nodes.
https://aws.amazon.com/neptune/

The diagram below summarises the workflow:
![Alt text](./static/overview.png?raw=true "workflow overview")

Topics addressed within the different notebooks:

Part 0:
Create the environment (S3 bucket, IAM roles/polices, SNS topic, etc) and upload your sample video

Part 1:
Use Amazon Rekognition to detect scenes and labels from your video

Part 2:
Use Amazon Transcribe and Amazon Comprehend to respectively transcibe audio to text and extract metadata (topics, Named Entities) from transcripts.

Part 3:
Store all the previously extracted metadata in Amazon Neptune and query the graph.

Part 4:
Resources clean-up


## Getting started

To run those notebooks you'll need to create a jupyter notebook instance in sagemaker.

In the AWS console, first make sure you're in the right region and search for Sagemaker. Write down the region as you'll later need to create your Amazon Neptune database in the same region.

![Alt text](./static/notebook-creation-part01.png?raw=true "notebook-creation-part01")

In Amazon Sagemaker, click on "Notebook instances".

![Alt text](./static/notebook-creation-part02.png?raw=true "notebook-creation-part02")

In the "Create notebook instance wizard", enter the following:

![Alt text](./static/notebook-creation-part1.png?raw=true "notebook-creation-part1")

For Permissions, click on "create a new role". 

![Alt text](./static/notebook-creation-part2.png?raw=true "notebook-creation-part2")

Then specify an existing S3 bucket where you will later upload the .mp4 video sample to be used in the notebooks.

![Alt text](./static/notebook-creation-part3.png?raw=true "notebook-creation-part3")

In Network, specify a VPC, subnet and a security group. I used the default ones on my end. Write down the VPC name as you'll need to deploy your Amazon Neptune DB in the same VPC later in notebook part0 and make sure your security group allows traffic between the two.

![Alt text](./static/notebook-creation-part4.png?raw=true "notebook-creation-part4")

You can specify the git repo in the Git repositories section or do that later within the notebook.
Then hit the "Create notebook instance" button.

![Alt text](./static/notebook-creation-part5.png?raw=true "notebook-creation-part5")

Once your instance's status is "InService", click on "Open JupyterLab".

![Alt text](./static/notebook-creation-part6.png?raw=true "notebook-creation-part6")

Navigate in the aws-video-metadata-knowledge-graph-workshop folder, double click on the part0-setup.ipynb notebook and when prompted to select a kernel, choose "conda_python3". You'll need to repeat this operation when opening the other notebooks.

![Alt text](./static/notebook-creation-part7.png?raw=true "notebook-creation-part7")


## Costs

Please note that you might incur costs by running those notebooks. Most of those AI services have free tier but depending on how much you've already used or depending on the size of the video assets you're using, it might go over the limit.

Finally, if you're not planning to use those resources anymore at the end of the workshop, don't forget to shutdown/delete your Amazon Neptune instance, your Sagemaker studio notebook instances and run the part4-cleanup notebook to delete all the other resources created throughout the notebooks (S3 buckets, IAM roles, SNS topics, etc).

Before proceeding, please check the related services pricing pages:

https://aws.amazon.com/transcribe/pricing/

https://aws.amazon.com/comprehend/pricing/

https://aws.amazon.com/rekognition/pricing/

https://aws.amazon.com/neptune/pricing/


## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.





