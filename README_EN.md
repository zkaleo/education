## 1. Prepare Mining Equipment

Operating System: It is recommended to use the following systems, desktop versions of Ubuntu are temporarily not compatible.

 HiveOS [Click here to view HiveOS configuration tutorial～～～](https://github.com/zkaleo/education/tree/main/hiveOS/README_EN.md)

 Ubuntu 18.04 server

 Ubuntu 20.04 server

Download Ubuntu system at: [Ubuntu 20.04.6 live server amd64](https://releases.ubuntu.com/focal/ubuntu-20.04.6-live-server-amd64.iso)

GPU: It is recommended to have a GPU with 6GB or more of VRAM, NVIDIA graphics card, driver version 515 or higher.

Driver download: [NVIDIA official driver download](https://www.nvidia.com/Download/index.aspx?lang=en-us)

## Nvidia Graphics Card Driver Installation Tutorial

```bash
apt update

apt install gcc make -y

echo -e "blacklist nouveau\noptions nouveau modeset=0" > /etc/modprobe.d/blacklist-nouveau.conf

update-initramfs -u

reboot

After rebooting, execute the following commands (the download link can also be replaced with the latest version driver from the official website):

wget https://us.download.nvidia.com/XFree86/Linux-x86_64/535.129.03/NVIDIA-Linux-x86_64-535.129.03.run

chmod +x NVIDIA-Linux-x86_64-535.129.03.run

./NVIDIA-Linux-x86_64-535.129.03.run --no-opengl-files --no-x-check -s
```

## 2. Register zkaleo Pool Account

Pool Address: https://zkaleo.cn

The mining method for zkaleo ALEO is mining by username. After registering a pool account, create a mining user according to the guide.

Visit the zkaleo official website, complete the registration according to the instructions to obtain the username. After logging into the account, click on the user avatar account settings to create a mining user for configuring mining parameters.

After starting mining, mining income will be automatically accumulated in the respective accounts.

## 3. Download Mining Programs

[Click here to enter the mining program download address～～～](https://github.com/zkaleo/education/releases)
```shell
zkaleo-pool-prover           //Mining program for Ubuntu system pool

zkaleo-solo-prover.tar.gz   //Solo mining program for Ubuntu system

zkaleoMiner.tar.gz       //Mining program for HiveOS system pool
```

## 4. Explanation of Program Parameters

```shell
#Pool mining program
./zkaleo-pool-prover --help
ZKLION-pool-prover 0.1.0 (7b503b8 2023-11-08)

USAGE:
    aleo-pool-prover [OPTIONS] --pool <POOL> --account <ACCOUNT> --worker-name <WORKER_NAME>

OPTIONS:
        --account <ACCOUNT>            //Mining username generated in the pool
    -h, --help                         //Print help information
        --pool <POOL>                  //Pool connection address, wss://client.zkaleo.cn:3888
        --rest <REST>                  //Local listening port, default 0.0.0.0:9988
    -v, --version                      //Program version
        --worker-name <WORKER_NAME>    //Enter your miner name

```

```shell
#Solo mining program
./zkaleo-solo-prover --help
-solo-prover 0.1.0 (ca566ce 2024-01-11)

USAGE:
    aleo-solo-prover [OPTIONS] --proxy <PROXY> --address <ADDRESS>

OPTIONS:
        --address <ADDRESS>            //Your aleo wallet address
    -h, --help                         //Print help information
        --proxy <PROXY>                //Pool connection address, wss://client.zkaleo.cn:3999
        --rest <REST>                  //Local listening port, default 0.0.0.0:9988
    -v, --version                      //Program version
        --worker-name <WORKER_NAME>    //Enter your miner name
```

## 5. Example

```shell
#Add executable permissions after download
chmod +x zkaleo-pool-prover
#Example of pool program startup
./zkaleo-pool-prover --account test --pool wss://client.zkaleo.cn:3888 --worker-name 192-158-22-101


#Example of solo program startup
1. Unzip
tar -zxvf zkaleo-solo-prover.tar.gz
2. Enter the extracted directory
cd zkaleo-solo-prover/
3. Add executable permissions
chmod +x zkaleo-solo-prover
4. Start
./zkaleo-solo-prover --address aleo1308gq2pfn0y3hgm722wysx4ks8szxs*** --proxy wss://client.zkaleo.cn:3999 --worker-name x66-01
```

## 6. Running Mining Programs in the Background
The following examples are for demonstration purposes. Replace the parameters with your own when running them actually.

Run the pool program in the background:
```shell
nohup ./zkaleo-pool-prover --account test01 --pool wss://client.zkaleo.cn:3888 --worker-name 192-168-90-100 &> /root/zkaleo-pool-prover.log &
```

Run the solo program in the background:
```shell
nohup ./zkaleo-solo-prover --address aleo1308gq2pfn0y3xxxx --proxy wss://client.zkaleo.cn:3999 --worker-name 192-168-90-101 &> /root/zkaleo-solo-prover.log &
```

## Check zkaleo-pool-prover.log Log

If the zkaleo-pool-prover.log log displays the following information, it indicates that the program is running normally:

<img width="845" alt="image" src="https://github.com/chihua2023/zkaleo/assets/137146992/cfaa57cc-f719-4d50-b214-9177db560bb0">
