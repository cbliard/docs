page_main_title: replicas
main_section: Platform
sub_section: Configuration
sub_sub_section: Resources
page_title: replicas resource reference
page_description: replicas resource reference

# replicas
`replicas` is a resource that holds the number of instances of the container to deploy. It is used specifically to deploy Docker containers

You can create a `replicas` resource by [adding](/platform/tutorial/workflow/crud-resource#adding) it to **shippable.yml**.

- [Latest Syntax (Shippable v6.1.1 and above)](#latestSyntax)
- [Old Syntax (forward compatible)](#oldSyntax)

<a name="latestSyntax"></a>
### Latest Syntax (Shippable v6.1.1 and above)


```
resources:
  - name:             <string>
    type:             replicas
    versionTemplate:  <object>
```

* **`name`** -- should be an easy to remember text string

* **`type`** -- is set to `replicas`

* **`versionTemplate`** -- is an object that contains specific properties that apply to this resource. Any time this is changed in the YML, a new version of the resource will be created.

	        versionTemplate:
	          count: 1          #integer value > 0

  * For [AWS Application Auto Scaling](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/service-auto-scaling.html#service-auto-scaling-api),

          versionTemplate:
            count:               <number>
            minReplicas:         <number>
            maxReplicas:         <number>
            autoScalingRole:     <string>
            autoScalingPolicies: <array>
            metricAlarms:        <array>


      **`count`** -- Required. The number of containers to run.

      **`minReplicas`** -- Optional. The minimum number of replicas in the scalable target.  If this is defined, `maxReplicas` is required.

      **`maxReplicas`** -- Optional. The maximum number of replicas in the scalable target.  If this is defined, `minReplicas` is required.

      **`autoScalingRole`** -- Optional. This will be used in the scalable target and should be a valid ARN of an IAM role.

      **`autoScalingPolicies`** -- Optional. An array consisting of scaling policies with the fields described [here](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/ApplicationAutoScaling.html#putScalingPolicy-property). `ResourceId`, `ScalableDimension`, and `ServiceNamespace` will be filled in for the current manifest if not specified in the YML.

      **`metricAlarms`** -- Optional. An array consisting of alarms with the fields described [here](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/AWS/CloudWatch.html#putMetricAlarm-property). A `PolicyName` for a scaling policy in the same deploy job can be listed in `AlarmActions` and will be replaced with the corresponding ARN when the alarm is created or updated.

<a name="oldSyntax"></a>
### Old Syntax (forward compatible)


```
resources:
  - name:           <string>
    type:           replicas
    version:        <object>
```

* **`name`** -- should be an easy to remember text string

* **`type`** -- is set to `replicas`

* **`version`** -- is an object that contains specific properties that apply to this resource. Any time this is changed in the YML, a new version of the resource will be created.

	        version:
	          count: 1          #integer value > 0


## Used in Jobs
This resource is used as an `IN` for the following jobs:

* [deploy jobs](/platform/workflow/job/deploy/)
* [manifest jobs](/platform/workflow/job/manifest/)

## Default Environment Variables
Whenever `replicas` is used as an `IN` or `OUT` for a `runSh` or `runCI` job, a set of environment variables is automatically made available that you can use in your scripts.

`<NAME>` is the the friendly name of the resource with all letters capitalized and all characters that are not letters, numbers or underscores removed. Any numbers at the beginning of the name are also removed to create a valid variable. For example, `my-key-1` will be converted to `MYKEY1`, and `my_key_1` will be converted to `MY_KEY_1`.

| Environment variable						| Description                         |
| ------------- 								|------------------------------------ |
| `<NAME>`\_NAME 							| The name of the resource. |
| `<NAME>`\_ID 								| The ID of the resource. |
| `<NAME>`\_TYPE 							| The type of the resource. In this case `replicas`. |
| `<NAME>`\_OPERATION 						| The operation of the resource; either `IN` or `OUT`. |
| `<NAME>`\_PATH 							| The directory containing files for the resource. |
| `<NAME>`\_SOURCENAME    					| SourceName defined in the pointer. |
| `<NAME>`\_VERSION\_COUNT 				| The count defined in the version. |
| `<NAME>`\_VERSIONID    					| The ID of the version of the resource being used. |
| `<NAME>`\_VERSIONNUMBER 					| The number of the version of the resource being used. |

## Shippable Utility Functions
To make it easy to use these environment variables, the platform provides a command line utility that can be used to work with these values.

How to use these utility functions is [documented here](/platform/tutorial/workflow/using-shipctl).

## Further Reading
* [Jobs](/platform/workflow/job/overview)
* [Resource](/platform/workflow/resource/overview)
