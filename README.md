# ubuntu-ssh-enabled

NOTE: THIS IMAGE IS TO BE USED FOR TEST AND LEARNIGN PURPOSES ONLY! NOT TO BE USED IN A PRODUCTION ENVIRONMENT!

SSH Enabled Ubuntu Image for Test and Dev purposes ONLY!

## Use:

Run the container:

```docker run -d mmumshad/ubuntu-ssh-enabled```

Identify the Internal IP

```docker inspect <container-id-name>```

SSH

```ssh <container-ip>```

**Username:** root

**Password:** Passw0rd

Based on : https://docs.docker.com/engine/examples/running_ssh_service/

## Docker Desktop for Mac

Because of a [limitation](https://github.com/docker/for-mac/issues/2670) in Docker Desktop for Mac, you will not be able to connect to the IP addresses of the Docker containers from the Mac.  

One workaround is to publish the sshd port to the host and connect via localhost and that port.  See the instructions in [Run a test sshd container](https://docs.docker.com/engine/examples/running_ssh_service/#run-a-test_sshd-container) for how to publish the sshd port as a random port and connect to it.  For example:
```
$ docker run -d -P --name test_sshd eg_sshd
$ docker port test_sshd 22

0.0.0.0:49154

$ ssh root@localhost -p 49154
Password: *****
root@f38c87f2a42d:/#
```

In this case you will need to use `ansible_host=localhost` and `ansible_port=49154` for that container in your inventory file.

Another workaround is to run Docker inside of a VM such as [multipass](https://github.com/CanonicalLtd/multipass) or Virtualbox.
