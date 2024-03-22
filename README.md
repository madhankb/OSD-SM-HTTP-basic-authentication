# Guide to setup self-managed dashboards in ECS & in EC2 hosted container

## Prerequisite
A managed service OpenSearch domain must incorporate Fine-Grained Access Control (FGAC) with HTTP basic authentication, ensuring that a master user is created in the internal user database.
[Reference here](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/fgac-http-auth.html)

## Steps to spin up a self-managed dashboards in ECS
1. Create a task within ECS Fargate using the dashboards docker image.
> [!IMPORTANT]
> It is crucial to select the same major version of dashboards as the OpenSearch cluster you intend to connect the dashboards to. [Docker images repo link](https://hub.docker.com/r/opensearchproject/opensearch-dashboards/tags)
2. When creating a task, under "container definition" in "port mapping" make sure the container ports `5601` and `9200` are added.
3. Under environment variables, add the mandatory keys and values mentioned in this [doc](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/dashboards.html#dashboards-local) to seamlessly connect with managed service domain.

> [!NOTE]
> I have added `task.json` file from the ECS task defenition to help understand the environment variables that has to be set while creating tasks

4. Create a service using the previously created task within the identical VPC and subnet where the managed service OpenSearch domain is operating.
5. Access the self-managed dashboards by hitting the public endpoint of the running task in ECS Fargate. By doing so, you can conveniently view and interact with all the saved objects in accordance with the Fine-Grained Access Control settings.

## Steps to spin up a self-managed dashboards in EC2 hosted container
1. Deploy an EC2 instance in the same VPC and subnet as the managed OpenSearch service domain.
2. Set up Docker/Kubernetes and its dependencies on the instance.
3. Utilize the attached `docker-compose.yml` file to launch a self-managed dashboards container. After the container is running, you can easily access and interact with all the saved objects.
4. To enable TLS, add the attributes mentioned in this [link](https://opensearch.org/docs/latest/install-and-configure/install-dashboards/tls/) as environment variables.

> [!TIP]
> One notable advantage of setting up a standalone OpenSearch Dashboards is that when it is deployed on AWS ECS Fargate, it generates a public IP. This allows the standalone dashboards to be accessed over the internet without the need for setting up a reverse proxy. As a result, the OpenSearch domains will be within the VPC and standalone dashboards will be available in public, enabling seamless connectivity and eliminating the complexity of configuring additional infrastructure components. This simplifies the setup process and provides convenient access to the dashboards from anywhere on the internet without compromising security or requiring additional network configurations.
