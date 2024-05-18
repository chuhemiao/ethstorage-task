# 完成 ethstorage 的二期任务指南

本指南需要 4 个步骤完成部署，如果有任何问题请通过 discord（kkdemian）联系我，也在 ethstorage 的群组。注意，使用的私钥是上次填表的地址进行部署的！

1. 安装 npm 的基础命令, 安装 ethfs-cli， 主要用来操作文件，`npm install -g ethfs-cli`

2.下载当前的文件到你的本地电脑，通过 vscode 或 terminal 打开文件，然后通过 ethfs-cli 创建一个 FlatDirectory 合约 `ethfs-cli create -p 私钥地址 -c 11155111`
运行后会出现一个这样的内容

```
chainId = 11155111 //链的id
providerUrl = `http://88.99.30.186:8545` //rpc服务地址
FlatDirectory Address: 0x4bDA24261CEa8A756D7151c875f00401De575607 // 创建后的合约地址，后面要用到
```

3.第三步，使用 ethfs-cli 部署 dapp，`ethfs-cli upload -f dist -a 上一步拿到的地址 -c 11155111 -p 私钥地址 -t 1` ， 此步骤大概需要 0.6-1.5 ETH 不等，根据网络 gas 情况而定，最好账户不要低于 1.5E 的测试代币。

部署成功后会看到文件分片的情况、消耗的 eth、文件大小等信息，然后访问 <https://0x4bda24261cea8a756d7151c875f00401de575607.sep.w3link.io/index.html>

**提示：图片的问题可以忽略，我忘记改名字了，不重新传了，太费测试币了。**

其实前面三个貌似不做也问题不大！！！万一官方也会检查，最好还是搞一下。

4.第四步，使用 blob 的模式，ETH+EthStorage 进行部署

还是通过，`ethfs-cli create -p 私钥地址 -c 11155111` 创建一个新的 FlatDirectory 合约地址，执行完大是：

```
chainId = 11155111
providerUrl = http://88.99.30.186:8545/
FlatDirectory Address: 0x3bfF11966bF854AF732e4Dc4bBe03eBb90F19b7f
```

然后通过拿到的 FlatDirectory 地址执行， `ethfs-cli upload -f dist -a 0x3bfF11966bF854AF732e4Dc4bBe03eBb90F19b7f  -c 11155111 -p 私钥地址 -t 2`

执行完会看到消耗的 gas，以及文件变化的情况。大概是下面这样：

```
Start Send...
Tx hash: 0xf9af8c11572d7531ba1d307bf7a864521f14983fe95a7a615976c6c40c6e57c2
Blob index: 0 uploaded!
Total number of blobs: 1
Number of blobs uploaded this time: 1
```

官方预计消耗 0.024 ETH 左右的测试币，刚刚部署消耗的比这少很多，基本可以忽略不计。

最后通过 FlatDirectory 的地址进行访问：<https://0x3bff11966bf854af732e4dc4bbe03ebb90f19b7f.3333.w3link.io/index.html> 此处要加上 3333，是通过 ethstorage 的 blob 存储的。

访问表单并提交内容，表单地址：<https://dawme4mo.forms.app/ethstorage-2nd-campaign-submission?ref=kkdemian>

第一步填写（记得替换为自己的地址）：web3://0x3bff11966bf854af732e4dc4bbe03ebb90f19b7f.3333.w3link.io/index.html
