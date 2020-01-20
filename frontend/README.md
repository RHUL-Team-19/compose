# frontend
Compose file for deploying all frontend services

### How to deploy
Assuming your terminal's working directory is this directory, simply run the following. Note: the -a arg will launch the service(s) in detached mode, and thus no logs will be pronted to your terminal.
```
docker-compose up -d
```

### How to view logs
To see log output, run the following. Note: the -f argument will 'follow' the output - to exit, you will need to hit ctrl+c.
```
docker-compose logs -f
```

:)
