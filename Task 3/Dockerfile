# Use Ubuntu as the base image
FROM ubuntu:22.04

# Install necessary dependencies for BoringSSL and building C++ programs
RUN apt-get update && apt-get install -y \
    cmake \
    ninja-build \
    golang \
    g++ \
    python3\
    python3-pip\
    git\
    && rm -rf /var/lib/apt/lists/*

# Set the working directory to /boringssl
RUN git clone https://github.com/dsayan99/boringssl
WORKDIR /boringssl

# Copy the contents of the current directory to /boringssl in the container
COPY . /boringssl

# Build BoringSSL
RUN cmake -GNinja -B build && \
    ninja -C build

RUN pip3 install requests

#RUN python3 QKDFetch.py

# Expose port 8080
EXPOSE 8080

# Run the compiled server by default
CMD ["bash"]