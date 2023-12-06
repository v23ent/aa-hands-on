# Setup

1. Clone this repository or download a .zip file and unzip to your local folder. Then navigate to a project's folder.

```
git clone https://github.com/v23ent/aa-hands-on.git && \
cd aa-hands-on
```

:information_source: In case you have Jupyter already installed on your host and would like to avoid fiddling with Docker networking options, you can also just run `jupyter notebook` from the project folder and skip to step 4

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

4. Navigate with your to a dummy notebook and execute the first block of code.
[http://localhost:8888/notebooks/aa-demo-exercise.ipynb](http://localhost:8888/notebooks/aa-demo-exercise.ipynb)

It will install 'atscale' package with dependencies. If all goes well then you're ready go with AI-Link for Adaptive Analytics hands-on!
We will be adding other blocks of code during hands-on session.


That's it!

# Cleanup
1. Stop your containers
```
docker compose down
```

2. Delete added docker daemon config lines:
```
  "default-address-pools" : [
    {
      "base" : "198.0.0.0/16",
      "size" : 24
    }
  ]
```
3. Restart docker service on your machine in the same way as in Setup.

