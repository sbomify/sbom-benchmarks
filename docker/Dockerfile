FROM nginx:latest

# Install something unexpected, in this case vim as a litmus test
RUN apt-get update && \
    apt-get install -y vim && \
    rm -rf /var/lib/apt/lists/*
