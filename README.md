# 互联网计算机（IC）技术文档

Internet Computer (IC) Technical Doc

By [Paul Liu](https://github.com/ninegua), [Andrew Tang](https://twitter.com/andrew_lee_tang), [Vincent Zhang](https://github.com/zhangwei983), [Qi Jia](https://github.com/Qijia2Dfinity), [Herbert Yang](https://twitter.com/herbertyang) of [DFINITY Foundation](https://dfinity.org/)

[网页版](https://zire.github.io/ic-tech-doc/)， [源代码](https://github.com/zire/ic-tech-doc)

# 核心词汇表 Glossary

[(original wiki glossary in English)](https://wiki.internetcomputer.org/wiki/Glossary)

## ## 翻译问题汇总 -by Qi

1. 多次出现 token ，不知道如何翻译叫好，参考：代币/虚拟币/令牌
  
2. ```ledger account``` 全部被翻译为 ：```账本账户```，是否合适
  
3. ``` Internet Computer ``` 全部翻译为： IC 是否合适
  
4. 在`Dissolved State` `Dissolving State``Non-dissolving State` `Neuron Age` 中都出现了`Age`这个单词，目前翻译为`年龄` 建议翻译为：生命周期，是否合适
  
5. 在`Dissolved State` `Neuron` 中出现 stake 这个词，不知道如何翻译较好
  
6. 无能力翻译的词汇：
  
  - 1. Canister Account
    
  - 2. Node Operators
    
  - 3. P2P
    
  - 4. State Manager
    
  - 5. WebAssembly: WebAssembly
    

## A

```
Account: 账号
```

- 帐号是分类账本容器（Ledger Canister）中的账号字段，它是一种智能合约，模仿了常规银行帐户的伪装和行为，其度量单位是ICP (Internet Computer Protocol)token。账户由所有者主体（principals）拥有，其所有权不会随时间而改变。账本账号的每个账户都有一个正余额，在ICP中数字精度为小数点后8位。
- A ledger account is a set of entries in the ledger canister, which is a smart contract that mimics the guise and behavior of a regular banking account, whose unit of measure is ICP (Internet Computer Protocol) utility tokens. Ledger accounts are owned by principals, and their ownerships do not change over time. Every account on the ledger has a positive balance measured in ICP with a precision of eight decimals.

```
Address: 地址
```

- 在谈论`账本`的时候，`地址` 跟`账号`是同一个意思。
- In the context of transactions on the ledger, address is synonymous with account.

```
Actor Model: 参与者模式
```

- Actor是参与者模式```Actor Model```中的原语。它是一个封装了的进程，通过顺序接收异步消息，并与其他必发运行的参与者（Actor）进行通信。参与者模式（Actor Model）与IC相关。因为IC中的容器（Canister）遵循参与者模式（Actor Model）进行并发与异步计算。
- An actor is a primitive in the Actor Model. It is a process with encapsulated state that communicates with other concurrently running actors through asynchronous messages that are received sequentially. The Actor Model is relevant to the IC because canisters on the IC (a type of smart contract) follow the Actor Model for concurrent and asynchronous computation.

```
Asynchronous model: 异步模型
```

```
Autonomous: 自主
```

## B

```
Balance: 余额
```

- 余额是账本中所有存款总额减去所有取款总额。某些情况中，一个不在账本中的账户余额为0是有必要的。账本帐户的余额是ICP的标价，并以八位小数表示。因此，一个账户的最小正余额是0.00000001或10^-8 ICP;这个数量有时被称为一个e8。
- The balance of an account on the ledger is the sum of all deposits minus the sum of all withdrawals. As a degenerate case, it is sometimes useful to say that an account which is not present in the ledger has a balance of zero. The balance of a ledger account is denominated in ICP and is represented with eight decimals. Thus, the minimum positive balance of an account is 0.00000001 or 10^-8 ICP; this amount is sometimes referred to as one e8.

```
Beneficiary: 账号持有者
```

- `账号持有者` 是拥有`账号`余额的`主体`。`账号持有者`不能被变更。一个`账号持有者`有可能被允许对`账号`进行交易操作（见`账号受托者`）。
- The beneficiary of an account is the principal who owns the balance of the account. The beneficiary of an account cannot be changed. The beneficiary of an account may or may not be allowed to make transactions on the account (see fiduciary).

```
Blockchain: 区块链
```

- `区块链`是一列不断扩展的，通过加密技术链接在一起，经过`共识协议`确认的的很多区块的集合。在`互联网计算机`上，每个`子网`都是一条`区块链`，这些`区块链`通过`链钥密码学`进行交互。
- A blockchain is a growing list of cryptographically linked blocks, agreed upon by consensus. On the Internet Computer every subnet is a blockchain and these blockchains interact using chain key cryptography.

```
Block Making： 出块
```

```
Blockchain Singularity: 区块链奇点
```

```
Boundary Nodes: 边界节点
```

- IC（Internet Computer)的Nginx网关，这些Nodes用于充当HTTP路由器，通过他们可以到达各子网区块节点。`边界节点（Boundary Nodes）`有几个用途：他有助于*discover-ability*（ic0.dapp将域名指向一组`边界节点（Boundary Nodes）`），他们是*geo-aware*可以通将传入的请求转发至最近的子网节点上。它们可以用于承余额的查询与交易工作。他们在内容分发网络中作为验证加密数据缓存工作。它们可以抑制来自外部IP地址的过度交互，引导/安装service worker，它们还可以帮助保护子网免受DDoS攻击。
- Nginx gateways to the internet computer. These nodes act as HTTP routers through which the network’s subnet blockchain nodes can be reached. The boundary nodes have several purposes: they aid in discover-ability (the ic0.app domain name points to a set of boundary nodes), they are geo-aware and can route incoming requests to the nearest subnet node that hosts the canister involved, they can help load balance query transactions, they can cache cryptographically verified data in the role of a content distribution network, they can throttle excessive interactions from an outside IP address, bootstrapping/Installing the service worker, and they can help protect subnets from DDoS attacks.

```
Burning Transaction: 销毁交易
```

- 销毁交易是ICP“销毁”的过程，在这个过程中一定数量的ICP 被销毁，，他主要用于购买Cycles，当一定数量的ICP被销毁的同时会产生对应数量的 Cycles，对应的汇率为：1 ICP或（SDR)兑换1T（10E12)Cycles。它表示为从来源帐户到ICP供应帐户的一笔交易。
- A burning transaction is the process of "burning" ICP, whereby a certain amount of ICP are destroyed. The main use case is that of purchasing cycles, through which ICP are destroyed while at the same time a corresponding amount of cycles is created, using the current exchange rate between ICP and ( SDR), in such a way that one SDR corresponds to one trillion (10E12) cycles. It is represented as a transaction from the source account to the ICP supply account.

## C

```
Candid: Candid
```

- Candid 是为Internet Computer专门制作的IDL，为应用程序接口提供一种公共语言，以促进不同变成语言编写服务间的通信
- Candid is an IDL crafted specifically for the Internet Computer, providing a common language for application interfaces to facilitate communication between services that are written in different programming languages

```
Canister: 容器
```

- `容器`是一种集合了代码和状态的`智能合约`。一个`容器`可以作为智能合约被部署在`互联网计算机`上，而且可以通过互联网来做交互。
- A canister is a type of smart contract that bundles code and state. A canister can be deployed as a smart contract on the Internet Computer and accessed over the Internet.

```
Canister Account: 容器账号  
```

- 容器账号（Canister Account） 本身是一个容器（即：账户受托人（Fiduciary）是个容器（Canister)），一个**非容器账号**是账本账号，他的账户受托人（Fiduciary）是非容器（non-canister)主体。
- A canister account is a ledger account owned by a canister (i.e. whose fiduciary is a canister). A non-canister account is a ledger account whose fiduciary is a non-canister principal.

```
Canister Identifier: 容器ID
```

- 容器标识符或容器ID，用于标识一个容器，并可用于与之交互。
- The canister identifier or canister ID is a globally-unique identifier that identifies a canister and can be used to interact with it.

```
Canister Signature: 容器签名
```

- 容器签名是一种基于证书验证的签名方案，公钥包含一个容器ID+种子（所以每个容器可以有很多公钥）；签名是验证容器已将签名消息放在其状态树中的特定位置的证书。详细信息见[IC接口规范](https://smartcontracts.org/docs/interface-spec/#canister-signatures)。
- A canister signature uses a signature scheme based on certified variables. Public “keys” include a canister id plus a seed (so that every canister has many public keys); signatures are certificates that prove that the canister has put the signed message at a specific place in its state tree. Details in the The Internet Computer Interface Specification.

```
Canister State: 容器状态
```

- 容器状态是容器在给定时间点的整体状态。 容器的状态分为用户状态和系统状态。 用户状态有 WebAssembly 模块实例，系统状态有：IC代表容器维护的辅助状态，例如，算力（计算）分配、Cycle余额、输入和输出队列以及其他元数据。 容器与自己的系统状态进行隐式交互，例如在消耗Cycles时，或者通过系统 API 进行交互，例如在发送消息时。
- A canister state is the entire state of a canister at a given point in time. A canister’s state is divided into user state and system state. The user state is a WebAssembly module instance and the system state is the auxiliary state maintained by the Internet Computer on behalf of the canister, such as its compute allocation, balance of cycles, input and output queues, and other metadata. A canister interacts with its own system state either implicitly, such as when consuming cycles, or through the System API, such as when sending messages.

```
Catch-up Package (CUP): 同步包
```

- 同步包（CUP）是一个数据包，其中包含引导子网副本所需的一切
- A catch-up package is a data bundle that contains everything needed to bootstrap a subnet replica.

```
Certified Query: 可认证查询
```

- 可认证查询是响应经过认证的查询调用结果。
- A certified query is a query call for which the response is certified.

```
Certified Variable: 可认证变量
```

- 容器在处理更新调用（或容器间调用）时可以存储在其子网规范状态中的一条数据，所以，在处理查询调用时，容器将返回一个证书，以确认数据被承认(Committed)
- A piece of data that a canister can store in its subnet’s canonical state in the processing of an update call (or inter-canister call), so that during the handling of a query call, the canister can return a certificate to the user that proves that it really committed to that value.

```
Chain Key Cryptography: 链钥密码学
```

- 链钥密码由一组密码协议组成，这些协议共同组成了Internet Computer。链式密钥密码学最明显的创新是IC只有一个公钥。这是一个巨大的优势，因为它允许任何设备，包括智能手表和手机，来验证来自IC的**authenticity of artifacts**。
- Chain key cryptography consists of a set of cryptographic protocols that orchestrate the nodes that make up the Internet Computer. The most visible innovation of chain key cryptography is that the Internet Computer has a single public key. This is a huge advantage as it allows any device, including smart watches and mobile phones, to verify the authenticity of artifacts from the Internet Computer.

```
Composable: 可组合
```

```
Consensus: 共识
```

- 在分布式计算中，共识是一种容错机制，通过该机制，多个节点可以就某个值或状态达成一致。 共识是副本软件的核心组成部分。 共识层从点对点**artifact**池中选择消息，并从其他子网的跨网络流中拉取消息并组织成一个批次，然后传递给消息路由层。
- In distributed computing, consensus is a fault tolerant mechanism by means of which a number of nodes can reach agreement about a value or state. Consensus is a core component of the replica software. The consensus layer selects messages from the peer-to-peer artifact pool and pulls messages from the cross-network streams of other subnets and organizes them into a batch, which is delivered to the message routing layer.

```
Consensus Layer：共识层
```

```
Controller: 控制者
```

- 容器的控制者```(Controller）```是对容器具有管理权限的个人、组织或其他容器。 控制者```(Controller）```由其主体```（principals）```标识。 例如，容器的控制者```(Controller）```可以升级容器的 WebAssembly 代码或删除容器。
- A controller of a canister is a person, organization, or other canister that has administrative rights over the canister. Controllers are identified by their principals. For example, a controller of a canister can upgrade the WebAssembly code of the canister or delete the canister.

```
Cross-Subnet Messages：跨子网消息
```

```
Cycles: Cycles
```

- 在 IC上，Cycle是以处理、内存、存储和网络带宽的形式消耗的资源的计量单位。 每个容器都有一个Cycles帐户，对容器消耗的资源进行收费。 IC的```虚拟货币（ utility token）``` (ICP) 可以转换为cycles并转移到容器（Canister）中。 Cycle也可以通过将它们附加到 [inter-canister] 消息在容器之间转移，也可以在容器之间传输Cycle。 ICP 始终可以使用以 [SDR] 衡量的当前 ICP 价格转换为Cycles，使用1T ycles对应一个 SDR 的汇率。
- On the Internet Computer, a cycle is the unit of measurement for resources consumed in the form of processing, memory, storage, and network bandwidth. Every canister has a cycles account to which resources consumed by the canister are charged. The Internet Computer’s utility token (ICP) can be converted to cycles and transferred to a canister. Cycles can also be transferred between canisters by attaching them to an [inter-canister] message. ICP can always be converted to cycles using the current price of ICP measured in [SDR] using the convention that one trillion cycles correspond to one SDR.

## D

```
Dapp: 去中心化应用
```

- dapp 或去中心化应用程序是在IC上运行的容器。
- A dapp, or decentralised application is a canister running on the Internet Computer.

```
DAO-controlled network: DAO治理网络
```

```
Datacenter: 数据中心
```

- 数据中心 (DC) 是托管节点的物理站点，这些节点对IC作出贡献。他们主要包括节点部署所需的硬件和软件基础设施。DC在IC上由唯一标识符标识。
- A data center (DC) is a physical site that hosts nodes which contribute to the Internet Computer. It includes the hardware and software infrastructure required for node deployment. A DC is identified on the Internet Computer by a unique identifier.

```
Decentralized Autonomous Organization (DAO)： 去中心化自治组织
```

```
Direct Integration (with BTC/ETH): 直接集成
```

```
Distributed Key Generation (DKG)：分布式密钥生成器 
```

```
Dissolve Delay: 溶解延迟
```

- 溶解延迟是神经元在溶解之前必须花费的时间。
- The dissolve delay is the amount of time that neurons must spend dissolving before becoming dissolved.

```
Dissolved State: 溶解完成状态
```

- 溶解状态是一种神经元状态，其特征在于溶解延迟为零。 （通常说处于这种状态的神经元没有“溶解延迟”。）正是在这种状态下，一个神经元可以“**分配（disbursed）**”，之后它的`股份（stake)`转移到别处，其相应的神经元账户关闭。 溶解的神经元的年龄``生命周期归零。``
- The dissolved state is a neuron state characterized by a dissolve delay equal to zero. (It is conventionally said that a neuron in this state does not "have" a dissolve delay.) It is in this state that a neuron can be "disbursed," hence its stake moved elsewhere, and its corresponding neuron account closed. The age of a dissolved neuron is considered to be zero.

```
Dissolving State: 溶解进行状态
```

- 溶解状态是在其所有者发出“开始溶解”命令后改变的神经元状态，并一直持续到发出“停止溶解”命令，或直到溶解延迟计时结束。 溶解神经元的年龄**生命周期**归零。
- A dissolving state is a neuron state that follows immediately after its owner issues a "start dissolving" command and continues until a "stop dissolving" command is issued, or until the dissolve delay timer runs out. The age of a dissolving neuron is considered to be zero.

## E

```
Execution Environment: 执行环境
```

- 执行环境是副本软件的核心层之一
- The execution environment is one of the core layers of the replica software.

```
Execution Layer： 执行层
```

## F

```
Fast Forwarding: 快进
```

```
Fiduciary: 账号受托者
```

- 账户的受托人是被允许在账户上进行交易的委托人；因此，将其视为帐户的所有者可能会更好理解，但需要注意的是，它不一定是帐户的受益人。神经元账户就是一个突出范例，受益人和受托人不一致**coincide**（受托人是治理容器，受益人是神经元持有人）。账本账户的受托人不会随着时间而改变。受托人和受益人的区别在于，对于与IC账本交互的DeFi dapp（容器）非常重要，在这种情况下，受托人是DeFi容器，而受益人是使用DeFi容器服务的个人或组织.
- The fiduciary of an account is the principal allowed to make transactions on the account; as such, it may be useful to think of it as the owner of the account, with the caveat that it may or may not be the beneficiary of the account. The neuron account is a prominent example of an account for which the beneficiary and fiduciary do not coincide (the fiduciary is the governance canister while the beneficiary is the neuron holder). The fiduciary of a (ledger) account does not change over time. The distinction between fiduciary and beneficiary is also important for DeFi dapps (canisters) that interact with the IC ledger: in this case, the fiduciary is the DeFi canister while the beneficiary is the individual or organization that uses the DeFi canister’s services.

```
Finalization： 最终确认
```

## G

```
Garbage Collection： 内存垃圾回收
```

```
General Purpose: 通用
```

```
Genesis Block： 创始区块
```

```
Governance Canister: 治理容器
```

- 治理容器是实现NNS治理系统的容器，即存储和管理神经元和提案，并实现NNS投票环境。
- The governance canister is a system canister that implements the NNS governance system, i.e., among others, stores and manages neurons and proposals, and implements the NNS voting environment.

## H

```
HTTP Integration: HTTP集成
```

## I

```
ICP: 互联网计算机协议
```

- 互联网计算机协议货币**token**（ICP）是互联网计算机的数字货币```utility token```。 ICP 允许更广泛的互联网社区通过将 ICP 锁定在神经元中来参与 Internet Computer 区块链网络的治理。 ICP 也可以转换为cycles，然后用于为保持容器运转。
- The Internet Computer Protocol token (ticker "ICP") is the utility token of the Internet Computer. ICP allows the broader internet community to participate in the governance of the Internet Computer blockchain network by locking ICP in neurons. ICP can also be converted into cycles, which are then used to power canisters.

```
ICP Supply Account: ICP供应账号
```

- ICP 供应账号是一个准虚构的账本账号，其余额始终为零。 它在 ICP 销毁和铸造操作中发挥着核心作用。
- The ICP supply account is a quasi-fictitious ledger account whose balance is always zero. It has a central role in ICP burning and minting operations.

```
Identity: 身份
```

- 身份（Identity）是一串字节字符串，用于标识与IC交互的实体，例如主体（Principal）。对于用户，身份是用户的 DER 编码公钥的 SHA-224 哈希值。更多信息详见[IC接口规范](https://smartcontracts.org/docs/interface-spec/)
- An identity is a byte string that is used to identify an entity, such as a principal, that interacts with the Internet Computer. For users, the identity is the SHA-224 hash of the DER-encoded public key of the user. The Internet Computer Interface Specification has more detail.

```
Immutability: 不变性
```

```
Internet Identity: 互联网身份
```

- [互联网身份](https://identity.ic0.app)是一个运行在`互联网计算机`上的匿名化的身份验证系统。
- [Internet Identity](https://identity.ic0.app/#authorize) is an anonymizing blockchain authentication system running on the Internet Computer.

```
Induction Pool: 导入池
```

- 子网区块链的导入池是驻留在子网上的所有容器的所有输入队列的集合。
- The induction pool of a subnet blockchain is the collection of all input queues of all canisters residing on the subnet.

```
Ingress Message: 入口消息
```

- 入口消息是最终用户发送到子网区块链上运行的容器的消息。 该消息由最终用户身份对应的密钥签名，并发送到参与子网的副本。
- An ingress message is a message sent by an end-user to a canister running on a subnet blockchain. The message is signed by the secret key corresponding to the end-user’s identity and sent to one of the replicas that participate in the subnet.

```
Ingress Message History: 入口消息历史
```

- 入口消息历史记录了副本处理的每条入口消息的当前状态，并跟踪消息是否成功包含在导入池中以及执行消息的响应。
- The ingress message history records the current status of every Ingress message processed by a replica and keeps track of whether messages were successfully included in the induction pool and the responses of executed messages.

```
Input Queue: 输入队列
```

- 容器的输入队列包含绑定到该容器的所有消息。 另见导入池。 当容器计划执行时，将执行来自其输入队列的消息。
- The input queue of a canister contains all messages bound for the canister. See also induction pool. When the canister is scheduled for execution, messages from its input queue will be executed.

```
Inter-canister Message: 容器间消息
```

- `容器间消息`指的是从一个`容器`被发送到另外一个`容器`的消息。它跟用户启动的`入口消息`不同。
- An inter-canister message is a message sent from one canister to another. Inter-canister messages are different from user-initiated ingress messages.

```
Internet Computer (IC): 互联网计算机
```

- `互联网计算机`是一个去中心化的`区块链`，通过独立`节点供应商`在区域分布的`数据中心`来为部署在区块链上的`容器``智能合约`提供可扩展的计算能力。
- The Internet Computer (IC) is a decentralized blockchain that provides scalable compute capacity for running canisters through independent node providers running nodes in geographically distributed data centers.

## J

## K

## L

```
Latency: 延迟
```

```
Leader (orBlock Maker)：出块者 
```

```
Ledger: 账本
```

```
Ledger Canister: 账本容器
```

```
Ledger Canister: 账本容器
```

- 账本容器是一个系统容器，主要作用是存储账户及其对应的交易。
- The ledger canister is a system canister whose main role is to store accounts and their corresponding transactions.

```
Liveness： 活性
```

## M

```
Message: 消息
```

- 消息是从一个容器发送到另一个容器或从用户发送到容器的数据。
- A message is data sent from one canister to another or from a user to a canister.

```
Message Routing: 消息路由
```

- 消息路由层接收来自共识层的批次，并将它们引入到导入池中。 然后消息路由安排一组容器来执行来自其输入队列的消息。
- The message routing layer receives batches from the consensus layer and inducts them into the induction pool. Message routing then schedules a set of canisters to execute messages from their input queues.

```
Minting Transaction: 铸造交易
```

- 铸币交易是“铸币”ICP的过程，从而产生一定数量的ICP。 铸造ICP是为了奖励神经元的投票，并通过节点运行提供算力来奖励参与IC的节点提供者。 铸币交易表示为从 ICP 供应账户到目标账户的交易。
- A minting transaction is the process of "minting" ICP, whereby a certain amount of ICP comes into existence. ICP is minted in order to reward neurons for voting, and reward node providers for participating in the IC by providing compute capacity through the running of nodes. A minting transaction is represented as a transaction from the ICP supply account to a destination account.

```
Motoko: Motoko
```

- Motoko 是一种编程语言，旨在直接支持 IC的编程模型，从而更容易高效地构建应用程序并利用该平台的一些独有功能，例如智能合约的 Actor 模型和 WebAssembly 的编译。
- Motoko is a programming language designed to directly support the programming model of the Internet Computer, making it easier to efficiently build applications and take advantage of some of the more unusual features of this platform, including the Actor Model for smart contracts and compilation to WebAssembly.

## N

```
Non-dissolving State: 非溶解状态
```

- 未溶解或溶解中（dissolving）的神经元被称为处于未溶解状态（或“老化”）。 因此，不溶解的神经元会累积“年龄”，但需要注意的是，任何时候开始溶解的神经元都会将这个年龄**逐渐**降低到零。 非溶解（又称“老化”）神经元的溶解延迟参数不能为零，因为这样的神经元必须已经溶解。
- A neuron that is not dissolved or dissolving is said to be in a non-dissolving state (or "aging"). Non-dissolving neurons thus accrue "age", with the caveat that beginning to dissolve at any time reduces this age back to zero. The dissolve delay parameter of a non-dissolving (aka "aging") neuron cannot be zero, because such a neuron would have to already be dissolved.

```
Network Nervous System (NNS): 网络神经系统
```

- 网络神经系统 (NNS) 是系统容器（又名“NNS 容器”）的集合，它们组装成一个治理IC各个方面的系统。
- The network nervous system (NNS) is a collection of system canisters (aka "NNS canisters") assembled into a system that governs all aspects of the Internet Computer.

```
Neuron: 神经元
```

- 神经元是一种 IC 实体，可以提出提案并对IC平台治理相关的提案进行投票。 为了提供负责任的治理，以保持系统稳定，神经元需要存储一定数量的 ICP（“stake”），以便提出提案并对其进行投票。 这会将代币锁定一段时间，然后开始溶解。 一个神经元的 ICP 权益存储在一个神经元帐户中。 神经元所有者有权对治理问题提出建议和投票，并根据所质押的 ICP 数量和解散期限的持续时间获得投票奖励。
- A neuron is an IC entity that can make proposals and vote on proposals related to the governance of the Internet Computer platform. To provide the stability required for responsible governance, neurons need to store ("stake") a certain amount of ICP in order to be able to make and vote on proposals. This locks the tokens for a period of time, after which it starts dissolving. The ICP stake of a neuron is stored in a neuron account. The neuron owner has the right to propose and vote on governance issues, and is granted rewards for voting in proportion to the amount of ICP staked, and the duration of the dissolve period.

```
Neuron Account: 神经元账号
```

- 神经元帐户是一个容器帐户，其受益人是神经元（或神经元的所有者）。 治理容器是所有神经元账户的受托人。
- A neuron account is a canister account whose beneficiary is a neuron (or the neuron’s owner). The governance canister is the fiduciary of all neuron accounts.

```
Neuron Age: 神经元年龄
```

- 神经元年龄是一个神经元参数，粗略地表示自其创建以来或自其最后进入非溶解状态以来所经过的时间。 计算神经元的年龄需要考虑神经元是否花费时间溶解或正在溶解，两者都会重置此参数。
- The neuron age is a neuron parameter roughly indicative of the time that has passed since its creation or since when it last entered into a non-dissolving state. Calculation of a neuron’s age needs to take into account whether the neuron has spent time dissolving or dissolved, both of which reset this parameter.

```
Node: 节点
```

- 节点是一个物理或虚拟网络端点，它承载参与IC所需的所有硬件、副本软件和配置设置
- A node is a physical or virtual network endpoint that hosts all the hardware, replica software, and configuration settings required to participate in the Internet Computer.

```
Node Operators: 节点操作者 ***
```

- A node operator (NO) is a non-canister principal who has the authority to add/remove nodes to/from the IC. Node providers come in possession of Hardware Security Modules (HSM), and register the HSMs with the NNS. (The HSM registration process consists essentially in deriving an IC principal ID from the key stored on the HSM, and persisting that ID with the NNS.) NPs hand registered HSMs over to legal persons, who now gain the authority to physically “operate nodes” (aka install replicas). The caveat is that, as opposed to "regular" principals, where a great deal of care goes into making sure that one principal ID corresponds to only one person, HSMs can routinely exchange hands, hence many persons can act as the same NO principal at different times.

```
Node Providers: 节点供应商
```

- 节点提供者 (NP) 是一种非容器委托人，它接收来自节点参与 IC 的奖励（又名“payout principal”）。 通常，节点提供者是节点的所有者，也可能参与节点的操作和相关的任务。 节点提供者可以从多个数据中心的多个节点接收奖励。
- A node provider (NP) is a non-canister principal that receives the rewards stemming from node participation to the IC (aka “payout principal”). Usually, though not necessarily, a node provider is the owner of the node, and may also be involved in node operation and related tasks. A node provider may receive rewards from multiple nodes in multiple data centers.

```
Notarization：公证
```

## O

```
Orthogonal Persistence： 正交持久化
```

```
Output Queue: 输入队列
```

- 每个容器都有一个绑定到其他容器的消息输出队列。
- Each canister has an output queue of messages bound for other canisters.

## P

```
Peer-to-peer (P2P): 点对点
```

- In common usage, peer-to-peer (P2P) computing or networking is a distributed application architecture that partitions workload across a network of equally-privileged computer nodes so that participants can contribute resources such as processing power, disk storage, or network bandwidth to handle application workload. The peer-to-peer layer collects and disseminates messages and artifacts from users and from other nodes. The nodes of a subnet form a dedicated peer-to-peer broadcast network that facilitates the secure bounded-time/eventual delivery broadcast of artifacts (such as ingress messages, control messages and their signature shares). The consensus layer builds upon this functionality.
  
  ```
  Peer-to-Peer Layer： 点对点网络层
  ```
  

```
Permissioned : 已许可
```

```
Permissionless： 无需许可
```

```
Per-round Certified State：每轮认证状态 
```

```
Principal: 主体
```

- 主体是可以通过IC进行身份验证的实体。 这与 Wikipedia 定义的```Principal```一词的含义相同。 主体使用特定身份与IC交互。
- A principal is an entity that can be authenticated by the Internet Computer. This is the same sense of the word principal as the Wikipedia definition. Principals that interact with the Internet Computer do so using a certain identity.

```
Proof-of-Stake： 持有量证明
```

```
Proof-of-Work: 工作量证明
```

```
Proposal: 提案
```

- 提案是描述修改 IC 或其任何子系统的某些参数的操作声明。 它是具有各种属性的 IC 实体，例如 ID、URL、摘要等。提案由符合条件的神经元所有者提交，供 IC 社区考虑，并经过投票过程，然后可以通过或拒绝。 然后执行通过的提案。 提案有几种分类方法，其中最突出的一种是将提案分为“话题”，**其采纳后会触发某些类别的操作**，例如创建子网、将节点添加到子网以及 ICP汇率的修改。
- A proposal is a statement describing an action to modify certain parameters of the IC, or of any of its subsystems. It is implemented as an IC entity having various attributes, such as an ID, a URL, a summary etc. Proposals are submitted by eligible neuron owners for the consideration of the IC community, and undergo a voting process, following which they can be adopted or rejected. Adopted proposals are then executed. There are several taxonomies of proposals, the most prominent of which groups proposals into "topics," whose adoption, in turn, triggers certain categories of actions, such as the creation of a subnet, the addition of a nodes to a subnet, and the modification of the ICP exchange rate.

```
Proto-node: 原初节点
```

- 原初节点是由硬件和软件组合组成的 IC 实体，与节点的不同之处在于它尚未向 IC 注册。 简而言之，原初节点是“等待中的节点”，因此除了副本软件之外，它拥有成为节点所需的一切。**（容易被理解为元初节点）**
- A proto-node is an IC entity consisting of a combination of hardware and software, that differs from a node in that it has not yet been registered with the IC. A proto-node is, in short, a "node-in-waiting," hence has all that it takes to be a node except the replica software.

```
Pseudorandom Generator (PRG): 伪随机数生成器
```

## Q

```
Query: 查询
```

- 查询是在不需要保留状态更改的容器上执行操作的优化方式。 查询是同步的，可以对托管容器的任何节点进行。 查询不需要共识来验证结果。
- A query is an optimised way to execute operations on a canister where the state changes are not preserved. Queries are synchronous and can be made to any node that hosts the canister. Queries do not require consensus to verify the result.

```
Query Calls：查询调用
```

## R

```
Random Beacon：随机数信标
```

```
Replica: 节点副本
```

- 节点副本是节点参与子网所必需的协议组件的集合。
- The replica is a collection of protocol components that are necessary for a node to participate in a subnet.

```
Registry: 注册表
```

- IC 注册表管理，在网络神经系统 (NNS) 上维护并由所有子网区块链访问的系统元数据。
- The IC registry manages the system meta-data maintained on the network nervous system (NNS) and accessed by all subnet blockchains.

```
Registry Canister： 注册表容器
```

```
Routing Layer： 路由层
```

## S

```
Scalability: 扩展性
```

```
Service Nervous System (SNS): 服务神经系统
```

```
Smart Contract: 智能合约
```

- 智能合约是一种有状态的计算机程序，旨在根据合同或协议的条款自动执行、控制或记录相关事件和行动。 智能合约可以以容器捆绑数据和代码的形式部署在互联网计算机上。 一个容器可以有一个或多个控制器，这些控制器被允许修改容器的代码，从而修改智能合约的条款。 对于具有不可变代码的容器智能合约，其控制器列表必须为空。
- A smart contract is a stateful computer program designed to automatically execute, control or document relevant events and actions according to the terms of a contract or an agreement. A smart contract can be deployed on the Internet Computer in the form of a canister bundling data and code. A canister can have one or more controllers that are permitted to modify the code of the canister, thereby modifying the terms of the smart contract. For a canister smart contract to have immutable code, its list of controllers must be empty.

```
Staking: 质押
```

```
State Change: 状态改变
```

- 状态改变是指更改存储在容器中的信息的任何行为、函数调用或操作的结果。 例如，如果一个函数进行更新调用，将两个数字相加或从列表中删除一个名称，则结果是容器状态的改变。
- A state change is the result of any transaction, function call, or operation that changes the information stored in a canister. For example, if a function makes an update call that adds two numbers together or removes a name from a list, the result is a change to the canister state.

```
State Machine: 状态机
```

```
State Manager: 状态管理 ***
```

- The state manager is responsible for: 1) maintaining (multiple versions of) the replicated state the deterministic state machine implemented by message routing and the execution environment operates on; 2)converting back and forth between the replicated state and its canonical version (latter can be understood independent of the concrete implementation); 3)obtaining certifications of parts of the canonical state, which allow other stakeholders such as other subnets and/or users, to verify that some piece of state indeed originates from a valid subnetwork, and 4) providing capabilities to sync the canonical state with other replicas in the same subnet so that replicas that have fallen behind can catch up.

```
Synchronous model: 同步模型
```

```
Subnet: 子网
```

- 子网（子网）是节点的集合，它们运行自己的共识算法实例以生成子网区块链，该子网使用链密钥加密与 IC 的其他子网进行交互。
- A subnet (subnetwork) is a collection of nodes that run their own instance of the consensus algorithm to produce a subnet blockchain that interacts with other subnets of the IC using chain key cryptography.

```
System Canister: 系统容器
```

- 系统容器是预先安装的容器，它执行维护IC所需的某些任务。
- A system canister is a pre-installed canister that performs certain tasks needed to maintain the Internet Computer.

## T

```
Tamperproof： 防篡改
```

```
Threshold ECDSA: 阈值ECDSA签名
```

```
Threshold Signature： 阈值签名
```

```
Throughput: 吞吐
```

```
Tokenization: 代币化
```

```
Transaction: 交易
```

- 总账账户交易是将ICP从一个账户转移到另一个账户的过程； 它可以分为三种类型：（a）常规转账交易，（b）销毁交易（burning transaction）,（c）铸币交易。
- A ledger account transaction is the process of transferring ICP from one account to another; it can be of three types: (a) regular transfer transaction, (b) burning transaction, and (c) minting transaction.

```
Transfer Transaction: 转账交易
```

- 转账交易是将ICP从任何常规账本账户（即除了ICP供应账户之外的任何账本账户）转移到另一个常规账本账户的过程。
- A transfer transaction is the process of transferring ICP from any regular ledger account (i.e. any ledger account except the ICP supply account) to another regular ledger account.

## U

```
User: 用户
```

- 用户是与IC交互的任何实体。 用户包括使用部署在 IC 上的 dapp 的最终用户、dapp 开发者、ICP代币持有者和神经元持有者。
- A user is any entity that interacts with the Internet Computer. Users include end-users that use dapps deployed on the IC, dapp developers, holders of ICP utility tokens, and neuron holders.

```
Update Calls： 更新调用
```

## V

```
Valid Set rule: 有效集合规则
```

- 有效集合规则是确定有效归纳池的规则。 入口消息和容器间消息必须通过某些检查，以确保在将它们添加到导入池之前遵守有效的设置规则。
- The valid set rule is the rule that determines a valid induction pool. Ingress messages and inter-canister messages must pass certain checks to ensure that the valid set rule is upheld before they can be added to the induction pool.

```
Voting: 投票
```

- 投票是选择通过和实施提案的过程。 它的直接参与者是神经元，他们（a）提交提案（b）对提案进行投票。 投票过程是一项相当复杂的工作，涉及神经元资格、投票权、**神经元追随者链**等方面。在设计时考虑了安全性和可靠性，并且正在不断改进以防止投票结果集中在少数神经元拥有者的手中。
- Voting is the process through which proposals are selected for adoption and implementation. Its direct participants are the neurons, who both (a) submit proposals and (b) vote on proposals. The voting process is a rather intricate undertaking, involving aspects such as neuron eligibility, voting power, chains of neuron followees etc. This has been designed with security and dependability in mind, and is being continuously improved in order to prevent the concentration of voting power in the hands of just a few neuron owners.

## W

```
WebAssembly: WebAssembly
```

- WebAssembly (abbreviated Wasm) is a binary instruction format for a stack-based virtual machine.

## X

## Y

## Z
