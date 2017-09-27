page_main_title: Upgrade deployment strategy
main_section: Deploy
sub_section: Deploy with deployment strategies

# Upgrade deployment strategy

In this strategy, a new service is created on the orchestration platform on the very first deployment. However every subsequent deployment will just update the existing service. Shippable makes a best effort guarantee for zero downtime in the upgrade method.

## Assumptions

We will use the [Single container application](/deploy/cd_of_single_container_applications_to_orchestration_platforms) as a starting point.

## Steps

The upgrade strategy is specified by setting the `deployMethod` attribute on the [deploy](/platform/workflow/job/deploy) to `upgrade`.

To set this strategy on the [Single container application](/deploy/cd_of_single_container_applications_to_orchestration_platforms), we update the `app_deploy_job` yml block in your [shippable.jobs.yml](/platform/tutorial/workflow/shippable-jobs-yml/) file.

```
  jobs:

    - name: app_deploy_job
      type: deploy
      steps:
        - IN: app_service_def
        - IN: op_cluster
        - IN: app_replicas
        - TASK: managed
        deployMethod: upgrade
```

## Sample project
**Source code:**  [devops-recipes/deploy-ecs-strategy](https://github.com/devops-recipes/deploy-ecs-strategy)

## Ask questions on Chat

Feel free to engage us on Chat if you have any questions about this document. Simply click on the Chat icon on the bottom right corner of this page and someone from our customer success team will get in touch with you.

## Improve this page

We really appreciate your help in improving our documentation. If you find any problems with this page, please do not hesitate to reach out at [support@shippable.com](mailto:support@shippable.com) or [open a support issue](https://www.github.com/Shippable/support/issues). You can also send us a pull request to the [docs repository](https://www.github.com/Shippable/docs).