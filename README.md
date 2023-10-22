# SE Summit 2023 - Adaptive Analytics hands-on
This is a repository to perform quick pre-setup for Adaptive Analytics session on SE Summit 2023.

# Setup
1. Clone this repository or download a .zip file and unzip to your local folder. Then navigate to a project's folder.
2. Change you docker default network IP subnets by amending docker config file and restarting docker service:
Open your docker daemon configuration file for editing. It should be located here:
- For Windows: C:\ProgramData\docker\config\daemon.json
- For Mac: ~/.docker/daemon.json
- Otherwise: /etc/docker/daemon.json

Add the following config lines:
```
  "default-address-pools" : [
    {
      "base" : "198.0.0.0/16",
      "size" : 24
    }
  ]
```

"base" could be different if you have the one mentioned above not available. The most important, it can't be 172.17.x.x :)

Save the file and restart your docker daemon:
- For Windows and Mac: restart your Docker Desktop service
- Otherwise: 
```
sudo systemctl restart docker
```

3. Launch container with docker compose. Container would expose port 8888. If it is in use on your system, just use the other one amending docker-compose.yml with appropriate port. 
```
docker compose up -d
```

4. Navigate with your to a dummy notebook and execute the first block of code. It will install 'atscale' package with dependencies. We will be adding other blocks during hands-on.

That's it!

