# Subflows Sample


This sample is modeled on sample BookStore application and invoke a REST API  at the backend that delivers sample JSON data. This backend REST API is hosted at - hosted at https://my-json-server.typicode.com/tibcosoftware/tci-flogo/Book

First you will need to upload Throw Error Extention from [github.com/TIBCOSoftware/flogo-contrib/activity/error](https://github.com/TIBCOSoftware/flogo-contrib/tree/master/activity/error)

If you run any of these samples locally using TIBCO Flogo® Enterprise -

1. To Get all Books - You will need to hit the url - http://localhost:9999/books/ 
2. To Get Book By ISBN - you will need to hit the url - http://localhost:9999/books/1451648537
3. If you want to test Error Handler, you can hit the above url with Invalid ISBN number like http://localhost:9999/books/999
4. You can check the sample JSON data for correct ISBN to be used while testing the samples - https://my-json-server.typicode.com/tibcosoftware/tci-flogo/Book

## Copy App 

1. Copy the flogo.sample.rest_with_subflows.flogo and flogo.sample.subflows_detachedInvocation.flogo apps into your workflow.
![Subflow Configuration](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.rest_with_subflows/CopyApps.png)

2. Click on flogo.sample.rest_with_subflows.flogo app. On the app-details page of flogo.sample.rest_with_subflows.flogo, you can see the getBooks, getBooksByISBN, and SubFlowLogging flows. Click the getBooks flow. You’ll see the REST trigger connected to an InvokeRestActivity; the InvokeRestActivity is connected to a StartSubFlowActivity; and the StartSubFlowActivity is connected to a Return Activity. Then click the StartSubFlowActivity — you will see a Configuration tab. Inside the Configuration tab, you will see Settings, Input, Output, Loop, and Retry on Error options displayed.
![App Details Page](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.rest_with_subflows/GetBooks.png)
![Trigger & Activity](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.rest_with_subflows/Trigger&Activity.png)
![Subflow Activity Configuration](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.rest_with_subflows/SubFlowActivityConfiguration.png)

3. Subflow configuration. On opening the StartASubFlow activity, in the Settings tab, you can see the list of available subflows, the Open Subflow button, and an option to set detached invocation to true/false.
![Subflow Configuration](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.rest_with_subflows/SubFlowConfiguration.png)

4. Opening a subflow. After selecting a subflow and saving it, clicking on the Open Subflow button appends the selected subflow to the right of the current flow.
![Open Subflow 1](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.rest_with_subflows/OpenSubFlow1.png)
![Open Subflow 2](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.rest_with_subflows/OpenSubFlow2.png)

5. Set Detached Invocation. Refer to app "flogo.sample.subflows_detachedInvocation.flogo"
Setting detached invocation to True, the subflow is invoked in fire-and-forget mode; in such a case, the main flow will not wait for the subflow to complete. Since the main flow is independent of the subflow output, the Output tab is hidden upon setting detached invocation. Detached invocation is set to False by default.
![Detached Invocation](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.subflows_detachedInvocation/Detached.png)

In this case, subflow1 is invoked in detached invocation True mode from the main flow. So, the main flow will not wait for completion of subflow1 and will execute the activities ahead. Since subflow1 is invoked in detached True mode, we will have 'Starting SubFlow 'res://flow:subflow1' in detached mode' printed in logs.

Upon encountering subflow1 in detached mode, the execution moves to completion of the main flow, and 'main flow execution' is printed followed by 'subflow2 execution' and 'subflow1 execution'.
The same can be understood by the timestamp difference in logs.
![Detached Mode Logs](../../VSCode_Extension/images/flow-design-concepts/flogo.sample.subflows_detachedInvocation/DetachedLogs.png)


## Help

Please visit our [TIBCO Flogo<sup>&trade;</sup> Extension for Visual Studio Code documentation](https://docs.tibco.com/products/tibco-flogo-extension-for-visual-studio-code-latest) for additional information.

