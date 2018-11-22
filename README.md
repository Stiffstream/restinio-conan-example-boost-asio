This repository contains a simple example that use [RESTinio](https://stiffstream.com/en/products/restinio.html) via the corresponding Conan package.

RESTinio uses Boost.Asio. To see the same example but with usage of standalone version of Asio look at [that repo](https://github.com/Stiffstream/restinio-conan-example).

# How To Try

## Docker
The simplest way is to use Docker and Dockerfile from the repository. For example:
```bash
git clone https://github.com/Stiffstream/restinio-conan-example-boost-asio
cd restinio-conan-example-boost-asio
docker build -t restinio-conan-example-boost .
docker run -p 8080:8080 restinio-conan-example-boost &
curl http://localhost:8080/
```
All necessary steps like installing Python, PIP, conan, CMake and so on are performed in Dockerfile. You can inspect Dockerfile content to see how conan can be configured and used.

## Manual Build
To perform manual build it is necessary to have conan and CMake installed. Then you can do the following steps:
```bash
# Add remote for conan to find RESTinio package.
conan remote add stiffstream https://api.bintray.com/conan/stiffstream/public
# Add remote for conan to find RESTinio's dependencies.
conan remote add public-conan https://api.bintray.com/conan/bincrafters/public-conan  
# Clone the demo repository.
git clone https://github.com/Stiffstream/restinio-conan-example-boost-asio
cd restinio-conan-example-asio
# Build the example.
mkdir build && cd build
conan install .. --build=missing
cmake ..
cmake --build . --config Release
# Check the example.
./bin/hello_world_minimal &
curl http://localhost:8080/
```

