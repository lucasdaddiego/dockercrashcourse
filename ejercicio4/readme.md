https://hub.docker.com/r/lucasndaddiego/ejercicio4

docker build -f Dockerfile -t ejercicio4 .

docker run -p 8080:8080 -it --rm ejercicio4
