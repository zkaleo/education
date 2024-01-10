
## 1、準備挖礦設備

操作系統：推薦使用ubuntu 20.04 server版、暫不兼容桌面版ubuntu系統

系統下載地址：https://releases.ubuntu.com/focal/ubuntu-20.04.6-live-server-amd64.iso

GPU：推薦擁有6GB以上顯存，NVIDIA顯卡，驅動版本515或更高。

驅動下載：[NVIDIA官方驅動下載](https://www.nvidia.com/Download/index.aspx?lang=en-us)



## 2、註冊zkaleo礦池帳戶
礦池地址：https://zkaleo.cn

zkaleo ALEO挖礦方式為用戶名挖礦，需註冊礦池帳戶後根據引導創建挖礦用戶。

訪問zkaleo官網，根據指引完成註冊即可獲取用戶名，登錄帳戶後，點擊用戶頭像賬戶設置創建挖礦用戶，用於配置挖礦參數。

開始挖礦後，挖礦收益會自動累計在各自帳戶中



## 3、下載挖礦程序

[下載地址](https://github.com/zkaleo/education/releases)
```shell
zkaleo-pool-prover 	          //Ubuntu系統礦池挖礦程序

zkaleo-solo-prover.tar.gz 	   //Ubuntu系統solo挖礦程序

zkaleominer 		         //HiveOS系統礦池挖礦程序
```



## 4、程序參數解釋

```shell
#礦池挖礦程序
./zkaleo-pool-prover --help
zkaleo-pool-prover 0.1.0 (7b503b8 2023-11-08)

USAGE:
    zkaleo-pool-prover [OPTIONS] --pool <POOL> --account <ACCOUNT> --worker-name <WORKER_NAME>

OPTIONS:
        --account <ACCOUNT>            //礦池中生成的挖礦用戶名
    -h, --help                         //打印幫助信息
        --pool <POOL>                  //礦池連接地址、wss://client.zkaleo.cn:3888
        --rest <REST>                  //本地監聽端口、默認0.0.0.0:9988
    -v, --version                      //程序版本
        --worker-name <WORKER_NAME>    //輸入你的礦機名稱

```

```shell
#solo挖礦程序
./zkaleo-solo-prover --help
zkaleo-solo-prover 0.1.0 (7b503b8 2023-11-08)

USAGE:
    zkaleo-solo-prover [OPTIONS] --proxy <PROXY> --address <ADDRESS>

OPTIONS:
        --address <ADDRESS>            //你的aleo錢包地址
    -h, --help                         //打印幫助信息
        --proxy <PROXY>                //礦池連接地址、wss://client.zkaleo.cn:3999
        --rest <REST>                  //本地監聽端口、默認0.0.0.0:9988
    -v, --version                      //程序版本
        --worker-name <WORKER_NAME>    //輸入你的礦機名稱
```

## 5、示例 

```shell
#下載後首先添加可執行權限
chmod +x zkaleo-pool-prover
#礦池程序啟動示例
./zkaleo-pool-prover --account test01 --pool wss://client.zkaleo.cn:3888 --worker-name 192-168-100-101

#solo程序啟動示例
./zkaleo-solo-prover --address aleo1308gq2pfn0y3hgm722wysx4ks8szxsxaxsdnjnabdy --proxy wss://client.zkaleo.cn:3999 --worker-name x99-01
```

## 6、後臺運行挖礦程序
```shell
nohup ./zkaleo-pool-prover --account test01 --pool wss://client.zkaleo.cn:3888 --worker-name 192-168-100-101 &> /root/zkaleo-pool-prover.log &
```

檢查zkaleo-pool-prover.log日誌、顯示如下信息，則說明程序運行正常
<img width="847" alt="image" src="https://github.com/chihua2023/zkaleo/assets/137146992/cfaa57cc-f719-4d50-b214-9177db560bb0">

