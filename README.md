# polymc-freebsd-guide
A guide for FreeBSD users to get PolyMC up and running.

## Building
As PolyMC does not provide native FreeBSD binaries anymore, you will need to compile PolyMC for yourself. Thankfully, PolyMC provides build instructions for OpenBSD, which is close enough to FreeBSD that it compiles successfully. There are however some differences between package names. You will need to install the below packages in order to compile PolyMC.
* [java/openjdk8](https://www.freshports.org/java/openjdk8)
* [devel/qt5](https://www.freshports.org/devel/qt5)
* [devel/cmake](https://www.freshports.org/devel/cmake)

### Getting the source
Getting PolyMC's source code is very easy, run this command to get the source for PolyMC.
```sh
git clone --recursive https://github.com/PolyMC/PolyMC.git
```

### Compiling
The instructions for compiling PolyMC on FreeBSD are the exact same as OpenBSD.
```sh
mkdir install
# configure the project
cmake -S . -B build \
   -DCMAKE_INSTALL_PREFIX=./install -DCMAKE_PREFIX_PATH=/usr/local/lib/qt5/cmake -DENABLE_LTO=ON 
# build
cd build
# replace with how many cores you have on your system
make -j8
cmake --install install --component portable
```
After you have executed these commands, your binary can be found in /install/bin/

## Running Minecraft
### Dependencies
In order to run Minecraft, you will need more dependencies.
* [graphics/glfw](https://www.freshports.org/graphics/glfw)
* [java/openjdk17](https://www.freshports.org/java/openjdk17)
* [java/openjdk8](https://www.freshports.org/java/openjdk8)
* [converters/base64](https://www.freshports.org/converters/base64)

### Working around LWJGL
A script has been included in this repository called java-lwjgl3. This was taken from the original developers repository, before they were taken down. There is also java-lwjgl2, for older versions of Minecraft.

In the instance you want to run, go to settings, there will be an option to override the Java installation. Point the executable to the java-lwjgl3 or java-lwjgl2 script depending on what version of Minecraft you intend on running.

### Playing
Now, everything should be properly setup and functional. All that's left to do is hit the launch button, and enjoy Minecraft on FreeBSD!
