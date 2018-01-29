### MkDocs in a docker.

MkDocs is a fast, simple and downright gorgeous static site generator that's geared towards building project documentation. Documentation source files are written in Markdown, and configured with a single YAML configuration file.

Purpose of this image was to simplify the process of deploying MkDocs. This image is based on Alpine Linux to minimize the size of the image.

Workdir is set to `/mkdocs`

### Usage

    docker run \
      -ti \
      --name mkdocs \
      cyberelfo/mkdocs

Mount Volume into working directory and make it available on port `80` on `localhost`.

    docker run \
      -ti \
      --name mkdocs \
      -p 80:8000 \
      -v /my_docs_dir:/mkdocs \
      cyberelfo/mkdocs

Docker Compose file contains default settings for deploying in local directory and it's set to bind port `8000` to localhost.


### Build

    docker build -t cyberelfo/mkdocs .

Docker troubleshooting
======================

Use docker command to see if all required containers are up and running:
```
$ docker ps
```

Check logs of mkdocs server container:
```
$ docker logs mkdocs
```

Sometimes you might just want to review how things are deployed inside a running
 container, you can do this by executing a _bash shell_ through _docker's
 exec_ command:
```
docker exec -ti mkdocs /bin/bash
```

History of an image and size of layers:
```
docker history --no-trunc=true polinux/mkdocs | tr -s ' ' | tail -n+2 | awk -F " ago " '{print $2}'
```

## Author

Przemyslaw Ozgo (<linux@ozgo.info>)
Franklin Amorim (@cyberelfo)
