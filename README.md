# Kotlin Native - Docker Container
This Project is an Ubuntu based container to compile kotlin native applications.

### Information about the latest stable version
![](https://images.microbadger.com/badges/version/hemeroc/kotlin-native:v0.2.0.svg)  
![](https://images.microbadger.com/badges/image/hemeroc/kotlin-native:v0.2.0.svg)  

## Currently supported versions
Following branches and tags are supported.
* v0.2.0
each other tag/branch might or might not work.

## HowTo
1. Checkout the kotlin native samples  
Use following command to checkout the kotlin native samples from the JetBrains/kotlin-native git repository.  
```bash
mkdir kotlin-native-samples && \
cd kotlin-native-samples && \
git init && \
git config core.sparseCheckout true && \
git remote add -f origin https://github.com/JetBrains/kotlin-native.git && \
echo "samples/*" > .git/info/sparse-checkout && \
git checkout v0.2.0 # use other branch/tag if needed
```
2. Compile your first sample  
Run the following command to install the needed dependency inside the docker container and then run the build of the kotlin native curl sample.  
```bash
docker run --rm -ti --workdir /sample -u root \
-v "$(pwd)/samples/libcurl:/sample" \
hemeroc/kotlin-native:v0.2.0 \
/bin/bash -c \
"apt-get install libcurl4-openssl-dev; ./build.sh"
```

3. Enjoy the result
The result is located in ```./samples/libcurl/``` and is called ```Curl.kexe```.  
Just try it out:
```bash
./samples/libcourl/Curl.kexe
```
As your newly built version of curl requires libcurl-openssl it obviously has to be installed on the system where you are trying to run the binary.
