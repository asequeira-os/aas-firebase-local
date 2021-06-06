# aas-firebase-local
Dockerized Firebase emulator setup.

Currently configured for `auth` emulation only.  
Uses a local project (because of the `demo-` prefix in
[.firebaserc](data/.firebaserc) )


To start  
`<repo dir>/scripts/run`

To stop  
`<repo dir>/scripts/stop`

Auth UI will be available at http://localhost:4000/auth

Auth API is available at `localhost:9099`

## Planned use

### Option A
For project(s) that plan to use this, have their startup script
to run this project's start script first.  
Call the stop script after the dependent project stop script.

### Option B
For now run `start` and `stop` once so that the system has the necessary docker image for `fblocal`  
Above step would not be necessary if the image is published to a docker images registry.

Add `fblocal` as a service in the docker compose file of the dependent project.
```
    fblocal:
        image: fblocal
        ports: 
            - 9099:9099 # Authentication
            - 4000:4000 # Emulator UI

```

## Development
Change [Dockerfile](docker/Dockerfile) `CMD` to use `bash`
