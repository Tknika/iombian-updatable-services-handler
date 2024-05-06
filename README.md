# IoMBian Updatable Services Handler

This services is in charge of updating the updatable services field of the firestore device.

`updatable_services` is a field on each device that determines if a service can be updated.
If there is a new version available of an installed service, it is represented like this:
```
{
    ...,
    updatable_services: {
        iombian-button-handler: "0.1.1"
    }
}
```

Whenever a new service version is added or the installed service version is updated, the updatable services changes.

## Docker
To build the docker image, from the cloned repository, execute the docker build command in the same level as the Dockerfile:

```
docker build -t ${IMAGE_NAME}:${IMAGE_VERSION} .
```

For example `docker build -t iombian-updatable-services-hanlder:latest .`

After building the image, execute it with docker run:

```
docker run --name ${CONTAINER_NAME} --rm -d -e CONFIG_PORT=5555 iombian-installed-services-hanlder:latest
```

- **--name** is used to define the name of the created container.
- **--rm** can be used to delete the container when it stops. This parameter is optional.
- **-d** is used to run the container detached. This way the container will run in the background. This parameter is optional.
- **-e** can be used to define the environment variables:
    - CONFIG_HOST: the host of the IoMBian Config File Handler.
    Default value is "127.0.0.1".
    - CONFIG_PORT: the port of the IoMBian Config File Handler.
    Default value is 5555.
    - LOG_LEVEL: define the log level for the python logger.
    This can be DEBUG, INFO, WARN or ERROR.
    Default value is INFO.

## Author
(c) 2024 IoMBian team ([Aitor Iturrioz Rodríguez](https://github.com/bodiroga), [Aitor Castaño Mesa](https://github.com/aitorcas23)).

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
