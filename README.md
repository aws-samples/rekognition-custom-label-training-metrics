**Rekognition Custom Label Training Metrics**

**Introduction**

Amazon Rekognition is a computer vision offering that helps customers analyze and derive insights from images and videos with little to no machine learning experience. However, customers have use cases where they need to custom train models for their specific image patterns for higher accuracy. For this reason, Amazon Rekognition offers Custom Labels feature where customers can upload their training and optionally test datasets to train models for specific use cases.

This sample project is intended to show case a mechanism to derive ML metrics of interest for custom trained models in Rekognition. These metrics will help data scientists and ML engineers to make better informed decisions. The project can be extended easily to generate additional ML metrics as needed

**Getting Started**

Please follow the documentation to create a custom label project and train a custom model
https://docs.aws.amazon.com/rekognition/latest/customlabels-dg/what-is.html

You can use the real estate images zip file in the repository to create a custom model as part of this exercise to get started.

**Metrics of interest**

1.Confusion Matrix
2.Heat map
3.Classification report
4.Micro / Macro / Weighted precision
5.Micro / Macro / Weighted recall
6.Micro / Macro / Weighted F1 score
7.Raw accuracy
8.Balanced accuracy
9.Hamming loss
10.Jaccard score
11.Matthew's correlation coefficient

**S3 Summary datasets**

Rekognition generates a number of evaluations, training and test summary datasets as part of custom training. In this sample project, we will be generating important ML metrics from these summary datasets. The notebook demonstrates the process to get the location of these datasets. The datasets mainly accessed as part of the notebook are

1. GroundTruthManifest
2. EvaluationResult

**Getting the Project ARN and version name**

The notebooks needs the project ARN and version name to get the S3 summary dataset location. You can find the version name under the project in the Rekognition console but project ARN might not be visible in the console. If you created the project via CLI, you would have got ARN as a json response. If you missed storing the ARN or if you used the console to create the project, you can still run a describe CLI command to list Custom Label projects in your AWS account and grab your corresponding project ARN with the below command

aws rekognition describe-projects

And this would return a JSON in the below format.

{
    "ProjectDescriptions": [
        {
            "ProjectArn": "arn:aws:rekognition:region:accountid:project/project_name/random_number",
            "CreationTimestamp": "YYYY-MM-DDTHH:MM:SS.MMMMMM-05:00",
            "Status": "CREATED"
        }
    ]
}

Now that you have all the needed info, you can go ahead and run the notebook to generate and visualize model metrics.

**Conclusion**

Based on your use case, if you find your important metric to be high or low, it would be appropriate to review and add appropriate data points or augment the existing datasets with more features, labels etc. Hope you found the sample project to provide better insights of your custom model.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
