# swiftformat-docker

Docker images for recent [SwiftFormat](https://github.com/nicklockwood/SwiftFormat) versions.

## Versions

- Swift 5.1.2
- Supported SwiftFormat versions can be found [here](https://github.com/slashmo/swiftformat-docker/releases)

## Usage

##### Pull the Docker image from Docker Hub:

```bash
docker pull slashmo/swiftformat
```

##### Create a container from the image and attach the code to be formated as a volume:

```bash
docker run --rm -v "$(pwd):/app" slashmo/swiftformat
```
