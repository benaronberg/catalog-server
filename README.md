# catalog-server
README file for connecting to the catalog server

## Login Instructions
Store the provided SSH private key locally and execute
```
ssh -i <private-key-file> -p 2200 grader@3.214.197.214
```
in a terminal to login. 

## IP Address and SSH Port
* IP Address: 3.214.197.214
* SSH Port: 2200 

## Complete URL to Web Application
The web app can be found [here](http://3.214.197.214.xip.io/catalog): http://3.214.197.214.xip.io/catalog

## Software and Configuration
The steps used to configure the server are summarized as follows:
1. Create an Amazon Lightsail instance.  An Ubuntu 16.04 image was used.
2. Configure Lightsail firewall.
* Allow incoming TCP connections on port 2200 (for SSH)
3. Configure UFW (Uncomplicated Firewall) on Lightsail image
* Allow TCP traffic on port 2200
* Allow TCP traffic on port 80
* Default to deny incoming traffic (except on allowed ports)
* Default to allow outgoing traffic
4. Modify sshd_config file to prohibit root login set default SSH port to 2200
5. Update packages using `apt-get update` and `apt-get upgrade`
6. Configure local timezone on Lightsail image to UTC
7. Create grader account and give sudo permissions
8. Generate an SSH key pair with `ssh-keygen` and place pub-key in the grader ~/.ssh directory
9. Install postgresql and create the database for use with the server.  A database user was also created with limited permissions to support this.
10. Pull server code using git (already installed on Lightsail's Ubuntu image)
11. Configure Apache .conf and .wsgi files to serve the code from step 9


## Third Party Resources
* Google OAuth was used in the creation of the [original catalog project](https://github.com/benaronberg/cool-catalog)
* Amazon's Lightsail was used to host the server
* [xip.io](http://xip.io/) was used to provide an authorized domain
* Udacity provided guidance on creating the code and configuring a linux distro to serve a Flask app using Apache and mod_wsgi
