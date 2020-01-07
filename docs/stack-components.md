# Parameters

The MySQL deployment package contains a sequence software (referred to as "components") required for MySQL to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

> MySQL-Server, MySQL-Agent, MySQL-Web have included for this deployment solution

## Path

### MySQL

MySQL root directory: */var/lib/docker*  
MySQL image directory: */var/lib/docker/image*   
MySQL daemon.json: please create it when you need and save to to the directory */etc/docker*   

### Portainer

Portainer Volume: */var/lib/docker/volumes/portainer_data/_data*    

## Ports

You can control(open or shut down) ports by **[Security Group Setting](https://support.websoft9.com/docs/faq/tech-instance.html)** of your Cloud Server whether the port can be accessed from Internet.

These ports should be opened for this application:

| Name | Number | Use |  Necessity |
| --- | --- | --- | --- |
| Portainer | 9000 | Remote connect Portainer | Optional |

## Version

You can see the version from product page of Marketplace. However, after being deployed to your server, the components will be automatically updated, resulting in a certain change in the version number. Therefore, the exact version number should be viewed by running the command on the server:

```shell
# Linux Version
lsb_release -a

# MySQL Version
docker -v
```