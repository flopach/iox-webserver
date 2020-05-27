# IOx App: Filehosting

With this application you can easily deploy the **NGINX web-server** on your IOx network device.

## Running the App

### Download deploy-ready Package File

1. Download your package from the `package_files` folder.

### Installation & Configuration

1. Install the application on your IOx device.
2. Go to `http://<IP to Container>:8000` and you will see the output of the `index.html`-file.

### Tested Hardware

* Cisco IR1101 / IOS XE 17.1
* Cisco IC3000 / 1.2.1

## Building the App

### 1. Select IOx Platform

Check the CPU architecture on your hardware (for example: ARM for IR1101, x86 for IC3000 and IR829/IR809) and edit the configuration files. With the character `#` we are commenting the other architecture out.

> Check out the [IOx Platform Support Matrix](https://developer.cisco.com/docs/iox/#!platform-support-matrix) for more information!

####ARM-based IOx devices

Dockerfile:

```
# ARM or x86
#FROM alpine:latest
FROM arm64v8/alpine:latest
```

package.yaml:

```
app:
  #cpuarch: "x86_64"
  cpuarch: "aarch64"
```

####x86-based IOx devices

Dockerfile:

```
# ARM or x86
FROM alpine:latest
#FROM arm64v8/alpine:latest
```

package.yaml:

```
app:
  cpuarch: "x86_64"
  #cpuarch: "aarch64"
```

#### 2. Edit Configuration files

You may edit the configuration files:

* **Dockerfile**: Add more files to the webserver
* **nginx.conf**: Configure your nginx server
* **index.html**: Change the website running on the server
* **entrypoint.sh**: Configure other applications which should run when the container starts

#### 3. Build .tar package and deploy

Please follow this guide here: https://developer.cisco.com/docs/iox/#!overview


## Versioning

**1.0** - Added basic functionality with Nginx and working configuration file

## Authors

* **Florian Pachinger** - *Initial work* - [flopach](https://github.com/flopach)

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE.md](LICENSE.md) file for details