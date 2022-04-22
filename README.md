# 互联网计算机（IC）技术文档

Internet Computer (IC) Technical Doc

By [Paul Liu](https://github.com/ninegua), [Andrew Tang](https://twitter.com/andrew_lee_tang), [Vincent Zhang](https://github.com/zhangwei983), [Qi Jia](https://github.com/Qijia2Dfinity), [Herbert Yang](https://twitter.com/herbertyang) of [DFINITY Foundation](https://dfinity.org/)

# 核心词汇表 Glossary

[(original wiki glossary in English)](https://wiki.internetcomputer.org/wiki/Glossary)

## A 

```
Account: 账号
```

- A ledger account is a set of entries in the ledger canister, which is a smart contract that mimics the guise and behavior of a regular banking account, whose unit of measure is ICP (Internet Computer Protocol) utility tokens. Ledger accounts are owned by principals, and their ownerships do not change over time. Every account on the ledger has a positive balance measured in ICP with a precision of eight decimals.


```
Address: 地址
```

- 在谈论`账本`的时候，`地址` 跟`账号`是同一个意思。
- In the context of transactions on the ledger, address is synonymous with account.

```
Actor Model: 参与者模式
```

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

- Nginx gateways to the internet computer. These nodes act as HTTP routers through which the network’s subnet blockchain nodes can be reached. The boundary nodes have several purposes: they aid in discover-ability (the ic0.app domain name points to a set of boundary nodes), they are geo-aware and can route incoming requests to the nearest subnet node that hosts the canister involved, they can help load balance query transactions, they can cache cryptographically verified data in the role of a content distribution network, they can throttle excessive interactions from an outside IP address, bootstrapping/Installing the service worker, and they can help protect subnets from DDoS attacks.

```
Burning Transaction: 销毁交易
```

- A burning transaction is the process of "burning" ICP, whereby a certain amount of ICP are destroyed. The main use case is that of purchasing cycles, through which ICP are destroyed while at the same time a corresponding amount of cycles is created, using the current exchange rate between ICP and ( SDR), in such a way that one SDR corresponds to one trillion (10E12) cycles. It is represented as a transaction from the source account to the ICP supply account.

## C

```
Candid: Candid
```

- Candid is an IDL crafted specifically for the Internet Computer, providing a common language for application interfaces to facilitate communication between services that are written in different programming languages

```
Canister: 容器
```

- `容器`是一种集合了代码和状态的`智能合约`。一个`容器`可以作为智能合约被部署在`互联网计算机`上，而且可以通过互联网来做交互。
- A canister is a type of smart contract that bundles code and state. A canister can be deployed as a smart contract on the Internet Computer and accessed over the Internet.

```
Canister Account: 容器账号
```

- A canister account is a ledger account owned by a canister (i.e. whose fiduciary is a canister). A non-canister account is a ledger account whose fiduciary is a non-canister principal.

```
Canister Identifier: 容器ID
```

- The canister identifier or canister ID is a globally-unique identifier that identifies a canister and can be used to interact with it.

```
Canister Signature: 容器签名
```

- A canister signature uses a signature scheme based on certified variables. Public “keys” include a canister id plus a seed (so that every canister has many public keys); signatures are certificates that prove that the canister has put the signed message at a specific place in its state tree. Details in the The Internet Computer Interface Specification.

```
Canister State: 容器状态
```
- A canister state is the entire state of a canister at a given point in time. A canister’s state is divided into user state and system state. The user state is a WebAssembly module instance and the system state is the auxiliary state maintained by the Internet Computer on behalf of the canister, such as its compute allocation, balance of cycles, input and output queues, and other metadata. A canister interacts with its own system state either implicitly, such as when consuming cycles, or through the System API, such as when sending messages.

```
Catch-up Package (CUP): 同步包
```

- A catch-up package is a data bundle that contains everything needed to bootstrap a subnet replica.

```
Certified Query: 可认证查询
```

- A certified query is a query call for which the response is certified.

```
Certified Variable: 可认证变量
```
- A piece of data that a canister can store in its subnet’s canonical state in the processing of an update call (or inter-canister call), so that during the handling of a query call, the canister can return a certificate to the user that proves that it really committed to that value.

```
Chain Key Cryptography: 链钥密码学
```

- Chain key cryptography consists of a set of cryptographic protocols that orchestrate the nodes that make up the Internet Computer. The most visible innovation of chain key cryptography is that the Internet Computer has a single public key. This is a huge advantage as it allows any device, including smart watches and mobile phones, to verify the authenticity of artifacts from the Internet Computer.

```
Composable: 可组合
```

```
Consensus: 共识
```

- In distributed computing, consensus is a fault tolerant mechanism by means of which a number of nodes can reach agreement about a value or state. Consensus is a core component of the replica software. The consensus layer selects messages from the peer-to-peer artifact pool and pulls messages from the cross-network streams of other subnets and organizes them into a batch, which is delivered to the message routing layer.

```
Consensus Layer：共识层
```

```
Controller: 控制者
```

- A controller of a canister is a person, organization, or other canister that has administrative rights over the canister. Controllers are identified by their principals. For example, a controller of a canister can upgrade the WebAssembly code of the canister or delete the canister.

```
Cross-Subnet Messages：跨子网消息
```

```
Cycles: Cycles
```

- On the Internet Computer, a cycle is the unit of measurement for resources consumed in the form of processing, memory, storage, and network bandwidth. Every canister has a cycles account to which resources consumed by the canister are charged. The Internet Computer’s utility token (ICP) can be converted to cycles and transferred to a canister. Cycles can also be transferred between canisters by attaching them to an [inter-canister] message. ICP can always be converted to cycles using the current price of ICP measured in [SDR] using the convention that one trillion cycles correspond to one SDR.

## D

```
Dapp: 去中心化应用
```

- A dapp, or decentralised application is a canister running on the Internet Computer.

```
DAO-controlled network: DAO治理网络
```

```
Datacenter: 数据中心
```

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

- The dissolve delay is the amount of time that neurons must spend dissolving before becoming disolved.

```
Dissolved State: 溶解完成状态
```

- The dissolved state is a neuron state characterized by a dissolve delay equal to zero. (It is conventionally said that a neuron in this state does not "have" a dissolve delay.) It is in this state that a neuron can be "disbursed," hence its stake moved elsewhere, and its corresponding neuron account closed. The age of a dissolved neuron is considered to be zero.

```
Dissolving State: 溶解进行状态
```
- A dissolving state is a neuron state that follows immediately after its owner issues a "start dissolving" command, and continues until a "stop dissolving" command is issued, or until the dissolve delay timer runs out. The age of a dissolving neuron is considered to be zero.


## E

```
Execution Environment: 执行环境
```

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

- The fiduciary of an account is the principal allowed to make transactions on the account; as such, it may be useful to think of it as the owner of the account, with the caveat that it may or may not be the beneficiary of the account. The neuron account is a prominent example of an account for which the beneficiary and fiduciary do not coincide (the fiduciary is the governance canister while the beneficiary is the neuron holder). The fiduciary of a (ledger) account does not change over time. The distinction between fiduciary and beneficiary is also important for DeFi dapps (canisters) that interact with the IC ledger: in this case, the fiduciary is the DeFi canister while the beneficiary is the individual or organization ([[#principal|principal) that uses the DeFi canister’s services.

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

- The governance canister is a system canister that implements the NNS governance system, i.e., among others, stores and manages neurons and proposals, and implements the NNS voting environment.

## H

```
HTTP Integration: HTTP集成
```

## I

```
ICP: 互联网计算机协议
```

- The Internet Computer Protocol token (ticker "ICP") is the utility token of the Internet Computer. ICP allows the broader internet community to participate in the governance of the Internet Computer blockchain network by locking ICP in neurons. ICP can also be converted into cycles, which are then used to power canisters.


```
ICP Supply Account: ICP供应账号
```

- The ICP supply account is a quasi-fictitious ledger account whose balance is always zero. It has a central role in ICP burning and minting operations.

```
Identity: 身份
```

- An identity is a byte string that is used to identify an entity, such as a principal, that interacts with the Internet Computer. For users, the identity is the SHA-224 hash of the DER-encoded public key of the user. The Internet Computer Interface Specification has more detail.

```
Immutability: 不变性
```

```
Internet Identity: 互联网身份
```

- Internet Identity is an anonymizing blockchain authentication system running on the Internet Computer.

```
Induction Pool: 导入池
```

- The induction pool of a subnet blockchain is the collection of all input queues of all canisters residing on the subnet.

```
Ingress Message: 入口消息
```

- An ingress message is a message sent by an end-user to a canister running on a subnet blockchain. The message is signed by the secret key corresponding to the end-user’s identity and sent to one of the replicas that participate in the subnet.

```
Ingress Message History: 入口消息历史
```

- The ingress message history records the current status of every Ingress message processed by a replica and keeps track of whether messages were successfully included in the induction pool and the responses of executed messages.

```
Input Queue: 输入队列
```

- The input queue of a canister contains all messages bound for the canister. See also induction pool. When the canister is scheduled for execution, messages from its input queue will be executed.

```
Inter-canister Message: 容器间消息
```

- An inter-canister message is a message sent from one canister to another. Inter-canister messages are different from user-initiated ingress messages.

```
Internet Computer (IC): 互联网计算机
```

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

- The ledger canister is a system canister whose main role is to store accounts and their corresponding transactions.

```
Liveness： 活性
```
 
## M

```
Message: 消息
```

- A message is data sent from one canister to another or from a user to a canister.

```
Message Routing: 消息路由
```

The message routing layer receives batches from the consensus layer and inducts them into the induction pool. Message routing then schedules a set of canisters to execute messages from their input queues.

```
Minting Transaction: 铸造交易
```

- A minting transaction is the process of "minting" ICP, whereby a certain amount of ICP comes into existence. ICP is minted in order to reward neurons for voting, and reward node providers for participating in the IC by providing compute capacity through the running of nodes. A minting transaction is represented as a transaction from the ICP supply account to a destination account.

```
Motoko: Motoko
```

- Motoko is a programming language designed to directly support the programming model of the Internet Computer, making it easier to efficiently build applications and take advantage of some of the more unusual features of this platform, including the Actor Model for smart contracts and compilation to WebAssembly.

## N

```
Non-dissolving State: 非溶解状态
```

- A neuron that is not dissolved or dissolving is said to be in a non-dissolving state (or "aging"). Non-dissolving neurons thus accrue "age", with the caveat that beginning to dissolve at any time reduces this age back to zero. The dissolve delay parameter of a non-dissolving (aka "aging") neuron cannot be zero, because such a neuron would have to already be dissolved.

```
Network Nervous System (NNS): 网络神经系统
```

- The network nervous system (NNS) is a collection of system canisters (aka "NNS canisters") assembled into a system that governs all aspects of the Internet Computer.

```
Neuron: 神经元
```

- A neuron is an IC entity that can make proposals and vote on proposals related to the governance of the Internet Computer platform. To provide the stability required for responsible governance, neurons need to store ("stake") a certain amount of ICP in order to be able to make and vote on proposals. This locks the tokens for a period of time, after which it starts dissolving. The ICP stake of a neuron is stored in a neuron account. The neuron owner has the right to propose and vote on governance issues, and is granted rewards for voting in proportion to the amount of ICP staked, and the duration of the dissolve period.

```
Neuron Account: 神经元账号
```

- A neuron account is a canister account whose beneficiary is a neuron (or the neuron’s owner). The governance canister is the fiduciary of all neuron accounts.

```
Neuron Age: 神经元年龄
```

- The neuron age is a neuron parameter roughly indicative of the time that has passed since its creation or since when it last entered into a non-dissolving state. Calculation of a neuron’s age needs to take into account whether the neuron has spent time dissolving or dissolved, both of which reset this parameter.

```
Node: 节点
```

- A node is a physical or virtual network endpoint that hosts all the hardware, replica software, and configuration settings required to participate in the Internet Computer.

```
Node Operators: 节点操作者
```

- A node operator (NO) is a non-canister principal who has the authority to add/remove nodes to/from the IC. Node providers come in possession of Hardware Security Modules (HSM), and register the HSMs with the NNS. (The HSM registration process consists essentially in deriving an IC principal ID from the key stored on the HSM, and persisting that ID with the NNS.) NPs hand registered HSMs over to legal persons, who now gain the authority to physically “operate nodes” (aka install replicas). The caveat is that, as opposed to "regular" principals, where a great deal of care goes into making sure that one principal ID corresponds to only one person, HSMs can routinely exchange hands, hence many persons can act as the same NO principal at different times.

```
Node Providers: 节点供应商
```

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

- A proposal is a statement describing an action to modify certain parameters of the IC, or of any of its subsystems. It is implemented as an IC entity having various attributes, such as an ID, a URL, a summary etc. Proposals are submitted by eligible neuron owners for the consideration of the IC community, and undergo a voting process, following which they can be adopted or rejected. Adopted proposals are then executed. There are several taxonomies of proposals, the most prominent of which groups proposals into "topics," whose adoption, in turn, triggers certain categories of actions, such as the creation of a subnet, the addition of a nodes to a subnet, and the modification of the ICP exchange rate.

```
Proto-node: 原初节点
```

- A proto-node is an IC entity consisting of a combination of hardware and software, that differs from a node in that it has not yet been registered with the IC. A proto-node is, in short, a "node-in-waiting," hence has all that it takes to be a node except the replica software.


```
Pseudorandom Generator (PRG): 伪随机数生成器
```

## Q

```
Query: 查询
```

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

- The replica is a collection of protocol components that are necessary for a node to participate in a subnet.

```
Registry: 注册表
```

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

- A smart contract is a stateful computer program designed to automatically execute, control or document relevant events and actions according to the terms of a contract or an agreement. A smart contract can be deployed on the Internet Computer in the form of a canister bundling data and code. A canister can have one or more controllers that are permitted to modify the code of the canister, thereby modifying the terms of the smart contract. For a canister smart contract to have immutable code, its list of controllers must be empty.


```
Staking: 质押
```

```
State Change: 状态改变
```

- A state change is the result of any transaction, function call, or operation that changes the information stored in a canister. For example, if a function makes an update call that adds two numbers together or removes a name from a list, the result is a change to the canister state.


```
State Machine: 状态机
```

```
State Manager: 状态管理
```

- The state manager is responsible for: 1) maintaining (multiple versions of) the replicated state the deterministic state machine implemented by message routing and the execution environment operates on; 2)converting back and forth between the replicated state and its canonical version (latter can be understood independent of the concrete implementation); 3)obtaining certifications of parts of the canonical state, which allow other stakeholders such as other subnets and/or users, to verify that some piece of state indeed originates from a valid subnetwork, and 4) providing capabilities to sync the canonical state with other replicas in the same subnet so that replicas that have fallen behind can catch up.


```
Synchronous model: 同步模型
```

```
Subnet: 子网
```

- A subnet (subnetwork) is a collection of nodes that run their own instance of the consensus algorithm to produce a subnet blockchain that interacts with other subnets of the IC using chain key cryptography.

```
System Canister: 系统容器
```

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

- A ledger account transaction is the process of transferring ICP from one account to another; it can be of three types: (a) regular transfer transaction, (b) burning transaction, and (c) minting transaction.

```
Transfer Transaction: 转账交易
```

- A transfer transaction is the process of transferring ICP from any regular ledger account (i.e. any ledger account except the ICP supply account) to another regular ledger account.

## U

```
User: 用户
```

- A user is any entity that interacts with the Internet Computer. Users include end-users that use dapps deployed on the IC, dapp developers, holders of ICP utility tokens, and neuron holders.


```
Update Calls： 更新调用
```

## V

```
Valid Set rule: 有效集合规则
```

- The valid set rule is the rule that determines a valid induction pool. Ingress messages and inter-canister messages must pass certain checks to ensure that the valid set rule is upheld before they can be added to the induction pool.


```
Voting: 投票
```

- Voting is the process through which proposals are selected for adoption and implementation. Its direct participants are the neurons, who both (a) submit proposals and (b) vote on proposals. The voting process is a rather intricate undertaking, involving aspects such as neuron eligibility, voting power, chains of neuron followees etc. This has been designed with security and dependability in mind, and is being continuously improved in order to prevent the concentration of voting power in the hands of just a few neuron owners.

## W

```
WebAssembly: WebAssembly
```

- WebAssembly (abbreviated Wasm) is a binary instruction format for a stack-based virtual machine.

## X 

## Y

## Z
 


