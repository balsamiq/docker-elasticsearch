docker-elasticsearch
====================

Elasticsearch master node with optional ec2 discovery.  Elasticsearch indices are rotated every two weeks and logs every week.

The following environment variables can be used to configure the container:

    ES_CLUSTER_NAME     The name of the elasticsearch cluster, default is "elasticsearch".
    ES_DISCOVERY        The type of discovery to use with elasticsearch, if not set will use multicast. Setting to "ec2"
    					will enable ec2 discovery using ES_CLUSTER_NAME in ES_AWS_REGION.
    ES_AWS_REGION       The aws region to be used for discovery, default is "us-east-1".
    ES_AWS_GROUP        The name or the id of the security group that is used for discovery. Optional.
    ES_AWS_ACCESS_KEY   The aws access key to be used for discovery.  Not required if
                        the instance profile has ec2 DescribeInstance permissions.
    ES_AWS_SECRET_KEY   The aws secret key to be used for discovery.  Not required if
                        the instance profile has ec2 DescribeInstance permissions.

To build:

    docker build -t balsamiq/docker-elasticsearch .

To run locally:

	docker balsamiq/docker-elasticsearch

To run on ec2:

	docker -e ES_DISCOVERY=ec2 balsamiq/docker-elasticsearch
