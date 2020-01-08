# test_swtc_lib_proxy

说明：此文档用于帮助审计 swtc_lib swtc_lib依赖的底层关系库 和 swtc_proxy 等相关的依赖库的代码。

此文档只做参考使用

## 目录

<!-- TOC -->

- [test_swtc_lib_proxy](#test_swtc_lib_proxy)
  - [目录](#目录)
  - [进度说明](#进度说明)
  - [依赖图系（进行中）](#依赖图系进行中)
  - [swtc-chains](#swtc-chains)
    - [主要依赖](#主要依赖)
    - [测试情况](#测试情况)
    - [问题以及建议](#问题以及建议)
  - [swtc-address-codec](#swtc-address-codec)
    - [主要依赖](#主要依赖-1)
    - [测试情况](#测试情况-1)
    - [问题以及建议](#问题以及建议-1)
  - [swtc-keypairs](#swtc-keypairs)
    - [主要依赖](#主要依赖-2)
    - [测试情况](#测试情况-2)
    - [问题以及建议](#问题以及建议-2)
  - [swtc-factory](#swtc-factory)
    - [主要依赖](#主要依赖-3)
    - [测试情况](#测试情况-3)
    - [问题以及建议](#问题以及建议-3)
  - [swtc-Wallet](#swtc-wallet)
    - [主要依赖](#主要依赖-4)
    - [测试情况](#测试情况-4)
    - [问题以及建议](#问题以及建议-4)
  - [swtc-utils](#swtc-utils)
    - [主要依赖](#主要依赖-5)
    - [测试情况](#测试情况-5)
    - [问题以及建议](#问题以及建议-5)
  - [swtc-serializer](#swtc-serializer)
    - [主要依赖](#主要依赖-6)
    - [测试情况](#测试情况-6)
    - [问题以及建议](#问题以及建议-6)
  - [swtc-transaction](#swtc-transaction)
    - [主要依赖](#主要依赖-7)
    - [测试情况](#测试情况-7)
    - [问题以及建议](#问题以及建议-7)
  - [swtc-api（进行中）](#swtc-api进行中)
    - [主要依赖](#主要依赖-8)
    - [测试情况](#测试情况-8)
    - [问题以及建议](#问题以及建议-8)

<!-- /TOC -->

## 进度说明

> 描述：此文档还在持续更新中，暂时还没有测试完毕。结果以更新完毕的文档为准。

* [X] ~~*swtc-chains*~~ [2020-01-08]
* [X] ~~*swtc-address-codec*~~ [2020-01-08]
* [X] ~~*swtc-keypairs*~~ [2020-01-08]
* [X] ~~*swtc-factory*~~ [2020-01-08]
* [X] ~~*swtc-Wallet*~~ [2020-01-08]
* [X] ~~*swtc-utils*~~ [2020-01-08]
* [X] ~~*swtc-serializer*~~ [2020-01-08]
* [X] ~~*swtc-transaction*~~ [2020-01-08]
* [ ] swtc-api 80%
* [ ] swtc-lib
* [ ] swtc-x-lib
* [ ] swtc-proxy
* [ ] swtc-nativescript

## 依赖图系（进行中）

> 说明：在测试和审计过程中，整理了一下依赖关系图。有助于理解相互之间的关系，此图还在继续完善中。

![SWTCLIB-依赖关系](src/images/SWTCLIB-依赖关系.png)

## swtc-chains

> 描述： 基础信息：包含各个平台的各种币种 基础信息

### 主要依赖

1. 无
 
### 测试情况

1. test passing 100%

### 问题以及建议

1. 无

## swtc-address-codec

> 描述： 主要作用是验证地址是否有效，加密base58和hex的互相转换的完整性和正确性

### 主要依赖

1. swtc-chains
2. x-address-codec -> create-hash

### 测试情况

1. test passing 100%

### 问题以及建议

1. 主要依赖 x-address-codec 已经不再维护，已经迁移到 ripple-address-codec 需要考虑是否迁移。[x-address-codec](https://github.com/ripple/x-address-codec) [ripple-address-codec](https://github.com/ripple/ripple-address-codec)


## swtc-keypairs

> 描述： 主要是生成各个不同规范的账号，进行不同规范的账号的测试。公私钥，16进账，签名等等。算法为 Elliptic 椭圆曲线加密

### 主要依赖

1. swtc-address-codec
2. swtc-factory
3. Elliptic

### 测试情况

1. test passing 100%

### 问题以及建议

1. 无

## swtc-factory

> 描述：提供生成公钥私钥，公钥验证，私钥验证，私钥导出公钥，用私钥给一段信息加密的相关功能

### 主要依赖

1. swtc-keypairs

### 测试情况

1. test passing 100%

### 问题以及建议

1. 无

## swtc-Wallet

> 描述： 提供生成公钥私钥，公钥验证，私钥验证，私钥导出公钥，用私钥给一段信息加密的相关功能,和swtc-factory实现的功能类似，这个比较新，lib库中的功能基本上用的这个。

### 主要依赖

1. swtc-keypairs

### 测试情况

1. test passing 100%

### 问题以及建议

1. 无


## swtc-utils

> 描述： 井通公链 utility 库，基于钱包。各种工具类库。

### 主要依赖

1. swtc-wallet

### 测试情况

1. test passing 100%
   * [X] ~~*hexToString*~~ [2020-01-06]
   * [X] ~~*stringToHex*~~ [2020-01-06]
   * [X] ~~*isValidAmount*~~ [2020-01-06]
   * [X] ~~*isValidAmount0*~~ [2020-01-06]
   * [X] ~~*...*~~ [2020-01-06]

### 问题以及建议

1. 无

## swtc-serializer

> 描述： 井通公链交易序列化库, 基于钱包。里面包含了各种工具和一些验证函数。

### 主要依赖

1. swtc-wallet

### 测试情况

1. test passing 100%
   
* datacheck.spec 36 passing 100%
   * [X] ~~*allNumeric*~~ [2020-01-06]
   * [X] ~~*isCurrency*~~ [2020-01-06]
   * [X] ~~*isRelation*~~ [2020-01-06]
   * [X] ~~*isTumCode*~~ [2020-01-06]
   * [X] ~~*isAmount*~~ [2020-01-06]
   * [X] ~~*...*~~ [2020-01-06]

* serializer.spec 47 passing 100%
   * [X] ~~*inst.buffer*~~ [2020-01-06]
   * [X] ~~*inst.pointer*~~ [2020-01-06]
   * [X] ~~*lookup_type_le*~~ [2020-01-06]
   * [X] ~~*lookup_type_tx*~~ [2020-01-06]
   * [X] ~~*sort_typedef*~~ [2020-01-06]
   * [X] ~~*...*~~ [2020-01-06]

* signature.spec 16 passing 100%
   * [X] ~~*signature*~~ [2020-01-06]
   * [X] ~~*inst.buffer*~~ [2020-01-06]

* tumAmount.spec 28 passing 100%
   * [X] ~~*parse_issuer*~~ [2020-01-06]
   * [X] ~~*parse_swt_value*~~ [2020-01-06]
   * [X] ~~*tum_to_bytes*~~ [2020-01-06]
   * [X] ~~*parse_tum_value*~~ [2020-01-06]
   * [X] ~~*to_json*~~ [2020-01-06]
   * [X] ~~*...*~~ [2020-01-06]

* types.utils.spec 25 passing 100%
   * [X] ~~*methods*~~ [2020-01-06]
   * [X] ~~*STArray*~~ [2020-01-06]
   * [X] ~~*STObject*~~ [2020-01-06]
   * [X] ~~*...*~~ [2020-01-06]
   
* utils.spec 87 passing 100%
   * [X] ~~*get_transaction_type*~~ [2020-01-06]
   * [X] ~~*get_transaction_result*~~ [2020-01-06]
   * [X] ~~*get_ledger_entry_type*~~ [2020-01-06]
   * [X] ~~*get_dec_from_hexchar*~~ [2020-01-06]
   * [X] ~~*hex_str_to_byte_array*~~ [2020-01-06]
   * [X] ~~*get_char_from_num*~~ [2020-01-06]
   

### 问题以及建议

1. 无

## swtc-transaction

> 描述： 提井通公链交易库, 支付/挂单/关系/合约。交易挂单方面的各种验证之类的。

### 主要依赖

1. swtc-serializer
2. swtc-utils
3. swtc-wallet

### 测试情况

1. test passing 75%

* test_multisign 2 passing 100% (测试多重签名)
  * [X] ~~*multiSigning*~~ [2020-01-06]
  * [X] ~~*buildMultisignedTx*~~ [2020-01-06]

* test_transaction_additional 30 passing 100% (本地签名，挂单，取消挂单相关)
  * [X] ~~*setSequence*~~ [2020-01-06]
  * [X] ~~*signPromise*~~ [2020-01-06]
  * [X] ~~*sign with sequence set*~~ [2020-01-06]
  * [X] ~~*build offer create*~~ [2020-01-06]
  * [X] ~~*build offer cancel*~~ [2020-01-06]
  * [X] ~~*...*~~ [2020-01-06]

* test_transaction 43 passing 100% (交易过程中的相关函数，包含了挂单和签名)
  * [X] ~~*constructor*~~ [2020-01-06]
  * [X] ~~*parseJson*~~ [2020-01-06]
  * [X] ~~*getAccount*~~ [2020-01-06]
  * [X] ~~*getTransactionType*~~ [2020-01-06]
  * [X] ~~*...*~~ [2020-01-06]

* api_test_transaction false 0% 
   * 404错误，请求的服务器404，这个是调用的井通api应该问题不大。不清楚这里的测试用例是否失效了。

### 问题以及建议

1. 编译问题，直接执行 tsc 命令报错，推断是跨平台的兼容性没有处理。需要手动执行 tsc 并把 local_sign.js 复制到 src目录下。建议在tssrc下面的文件都是ts，并且修改下package.json里面相关的命令。
2. 疑问：test/test_transaction_additional.js 文件78行、109行、等，交易和挂单方面的接口是否使用了 https://tapi.jingtum.com 的接口
3. 【属于 SWTC-LIB】在lib库的文档里面，本地签名的步骤如下：（可否不连接服务器，在本地直接进行签名，因为有些需求是需要断网进行签名。若有，建议在文档里面写出具体文档，本地签名单独的lib调用示例也建议在文档内标识出来。）
   1. remote = new Remote({server, issuer})
   2. remote.connectPromise
   3. remote.buildPaymentTx.signPromise
4. tssrc/transaction.ts 第1101行，链上的memo的最大长度等于1019个字节，需要先转换为buffer计算长度，中文算3个字节，这里是大于2048才会超出。请检查是否有误。相关的测试用例 test_transaction 第124行，也需要进行相应的修改。
5. api_test_transaction.js 这个文件下面使用的是井通API，测试不通过，不知道还有没有在用。



## swtc-api（进行中）

> 描述： 对jingtum-api 作出包装， 消除不安全操作 并且提供类似swtc-lib的接口支持jingtum-api缺失的操作

### 主要依赖

1. swtc-transaction
2. axios

### 测试情况

1. test passing 50%

* test_remote 0% (接口相关的测试)
  * [X] ~~*constructor*~~ [2020-01-06]
  * [ ] local sign 语法错误，逻辑正确。看情况是否修改,如需修改建议代码为:
    ```
      expect(error.response.data.message).to.equal("Transaction length invalid")
    ```
  * [ ] getLedger data.success 无此属性。
  * [ ] 下面不继续测试此脚本，使用接口测试的方案进行测试，
  
1. service test passing 100%
   * [X] ~~*创建钱包*~~ [2020-01-07]
   * [X] ~~*根据私钥创建钱包*~~ [2020-01-07]
   * [X] ~~*获取余额*~~ [2020-01-07]
   * [X] ~~*获得账号支付信息*~~ [2020-01-07]
   * [X] ~~*...*~~ [2020-01-07]

### 问题以及建议

1. 测试用例里面，有些语法错误，不能捕获该有的错误。
2. 分页的说明文档不是太详细，用法没有实例，在获取账号的支付记录按照文档说明传入值的时候，只想查询一条记录，却反悔了全部的13条记录，这个待考证。
3. 设置挂单佣金可以成功，但是具体的帮助文档可以写的详细一点，在井畅SWTC公链浏览器上差不到具体的交易hash，在井通浏览器上可以查到。