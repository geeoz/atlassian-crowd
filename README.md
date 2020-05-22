![Atlassian Crowd](https://wac-cdn.atlassian.com/dam/jcr:d2a1da52-ae52-4b06-9ab1-da8647a89653/crowd-icon-gradient-blue.svg?cdnVersion=696)

Crowd provices single sign-on and user identity that's easy to use.

Learn more about Crowd: [https://www.atlassian.com/software/crowd][1]

# Overview

This Docker container makes it easy to get an instance of Crowd up and running.

# Quick Start

For the `CROWD_HOME` directory that is used to store application data (amongst other things) we recommend mounting a host directory as a [data volume](https://docs.docker.com/engine/tutorials/dockervolumes/#/data-volumes), or via a named volume if using a docker version >= 1.9.

To get started you can use a data volume, or named volumes. In this example we'll use named volumes.

    docker volume create --name crowdVolume
    docker run -v c/data/your-crowd-home:/var/atlassian/application-data/crowd --name="crowd" -d -p 8095:8095 geeoz/atlassian-crowd


**Success**. Crowd is now available on [http://localhost:8095](http://localhost:8095)*

Please ensure your container has the necessary resources allocated to it. See [Supported Platforms][2] for further information.

_* Note: If you are using `docker-machine` on Mac OS X, please use `open http://$(docker-machine ip default):8095` instead._

# Configuring Confluence

This Docker image is intended to be configured from its environment; the
provided information is used to generate the application configuration files
from templates. Most aspects of the deployment can be configured in this manner; 
the necessary environment variables are documented below.

You can configure a small set of things by supplying the following environment variables

| Environment Variable              | Description |
| --------------------------------- | ----------- |
| CATALINA_CONNECTOR_PROXYNAME      | The reverse proxy's fully qualified hostname. |
| CATALINA_CONNECTOR_PROXYPORT      | The reverse proxy's port number via which Confluence is accessed. |
| CATALINA_CONNECTOR_SCHEME         | The protocol via which Confluence is accessed. |
| CATALINA_CONNECTOR_SECURE         | Set 'true' if CATALINA_CONNECTOR_SCHEME is 'https'. |
| CATALINA_CONTEXT_PATH             | The context path the application is served over. |
| JAVA_OPTS                         | The standard environment variable that some servers and other java apps append to the call that executes the java command. |

[1]: https://www.atlassian.com/software/crowd
[2]: https://confluence.atlassian.com/crowd/supported-platforms-191851.html
