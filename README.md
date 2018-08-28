
![Alt text](https://github.com/LEAD-Anoy74/ZeroClassic/blob/master/art/zero_icon.png?raw=true "ZeroClassic")

[ZERC](https://github.com/zerocurrencycoin/zero) is a fork of Zcash.
Zcash is a fork of Bitcoin that adds shielded transaction via zk-SNARKs.

This software is the ZERO Classic node. It downloads and stores the entire history of ZERO Classic transactions, about 1GB at this point.
Depending on the speed of your computer and network connection, the synchronization process could take several hours.

Announcements
-----------------


Security Warnings
-----------------
See important security warnings on the
[Security Information page](https://z.cash/support/security/).

**ZERO Classic is unfinished and highly experimental.** Use at your own risk.

Deprecation Policy
------------------
This release is considered deprecated 26 weeks after the release day. There
is an automatic deprecation shutdown feature which will halt the node some
time after this 26 week time period. The automatic feature is based on block
height and can be explicitly disabled.

Building
--------
Currently only Linux build is officially supported.  8GB RAM is recommended.

### Install packages (needs to be done only once)
```
sudo apt-get install \
      build-essential pkg-config libc6-dev m4 g++-multilib \
      autoconf libtool ncurses-dev unzip git python python-zmq \
      zlib1g-dev wget bsdmainutils automake cmake
```

### Download cryptographic keys (needs to be done only once)
```
./zcutil/fetch-params.sh
```

### Obtain the ZERO Classic software from GitHub
```
git clone https://github.com/LEAD-Anoy74/ZeroClassic/
cd ZeroClassic
git checkout master
```

### Build the source code to produce binary executables:
```
./zcutil/build.sh --disable-rust -j$(nproc)
```
On a typical laptop -j3 works fine, while retaining some UI interactivity
```
./zcutil/build.sh --disable-rust -j3
```

### Create a ZERO Classic configuration file
```
mkdir -p ~/.zero
echo "rpcuser=YOUR_USER" > ~/.zero/zero.conf
echo "rpcpassword=`head -c 32 /dev/urandom | base64`" >> ~/.zero/zero.conf
echo "rpcport=23800" >> ~/.zero/zero.conf
```

### Seeder Nodes
As of 05/12/2018 the following seeder nodes are up and run a recent Linux version:
```
addnode=
addnode=
addnode=
```

### Enable CPU mining (optional)
```
echo 'gen=1' >> ~/.zero/zero.conf
echo "genproclimit=1" >> ~/.zero/zero.conf
echo 'equihashsolver=tromp' >> ~/.zero/zero.conf
```

A sample of the current zero.conf
```
./contrib/zero.conf
```
A sample demonstrating a large number of command line options
```
./contrib/debian/examples/zero.conf
```

Running & Using ZERO Classic
--------------------
After a successful build ZERO Classic binaries are in `./src`. The two important binaries are `zcashd` and `zcash-cli`.

Your wallet will be created (on first zcashd run) in: ~/.zero/wallet.zero
Please backup your wallet often and keep it safe.

The usage is currently the same ZCash. For more information see the [ZCash User Guide](https://github.com/zcash/zcash/wiki/1.0-User-Guide#running-zcash).
