# deepazure
Repository for the NISHAVA 1227361 Course.

This repository only contains files and homework assignments that are required as part of the course listed above.

It also contains a docker container I created for the course, adding tools I felt helped throughout.

The docker container contains:
*  ssh utilities
*  sshd
*  Azure CLI
*  Powershell
*  Azure Powershell

The container may still be in the process of being developed.

# If you already have an RSA key to use, specify the containing directory when running the container:
docker run -dt --name deepazure -v /path/to/keydirectory:/root/.ssh -p 2222:22 jbonds/deepazure

# If you need an RSA key, generate it after deploying the container:
docker run -dt --name deepazure -p 2222:22 jbonds/deepazure

# Enter the Container, Create the RSA keypair and exit:
docker exec -it deepazure /bin/bash
ssh-keygen -q -N "" -t rsa -f /root/.ssh/deepazure_rsa_key
exit

# Copy the keypair / .ssh directory for safekeeping:
docker cp deepazure:/root/.ssh/ .

# Mount this again if needed in another container:
docker run -dt --name deepazure -v /path/to/keydirectory:/root/.ssh -p 2222:22 jbonds/deepazure

# Additionally Mount a volume to save files:
docker run -dt --name deepazure -v /home/jbonds/deepazure/.ssh:/root/.ssh -v /home/jbonds/deepazure/DeepAzure:/root/DeepAzure -p 555:22 jbonds/deepazure
