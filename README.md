# TS7250V3-toolchain
Cross-compilation environment for TS7250-V3 SBPC from Embedded TS: https://www.embeddedts.com/products/TS-7250-V3

# Clone this repository to host.
git@github.com:adallolio/TS7250V3-toolchain.git

# Clone DUNE repository to host in folder TS7250V3-toolchain/.
git clone -b AutoNaut-update git@github.com:adallolio/dune.git

# In the folder with the Dockerfile, build the image:
docker build --tag armhf-bullseye-toolchain .

# Then run a container:
docker run --rm -it armhf-bullseye-toolchain bash

# In /home/build, run:
cmake ../dune
make -j8
make package
# The generated dune-20* can be sent to target.
