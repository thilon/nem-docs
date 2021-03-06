### 账号(Account)

NEM支持两种不同类型的账号：普通账号和多签账号

* 普通账号

普通账号通过私匙创建和控制。账号的任何行为，如，通过被私匙签名的转账交易发送NEM到另一个帐户。如果攻击者获得私钥的内容，则他/她可以抢劫该帐户。因此私钥必须通过各种手段保密。

* 多签账号

多签账号可以通过普通账号转换来创建，并添加共同签署人，任何行为必须由联合签署人签署。这让多签账户比普通账户更安全。当一个共同签署人的私匙被攻击者获取，攻击者仍然无法操作该多签账号。强烈建议将任何含有高数量xem的账号转换成多签账号，并添加至少3个签署人。一旦转换为多签账户，原来的私匙将变成无效。

### 交易(Transaction)

交易是指从一个帐户到另一个转移XEM和/或消息的一种方式。一旦一笔交易被发起，仍然是未确认的，并且没有被网络所接受。这个时候还不清楚是否会被包入一个块中。这时的交易被称为未确认的交易。一旦被包入一个块中，交易将会被处理，并且如果是一个转账交易，交易中的金额从发送方的账户转账到接收方的账户。此外，交易费用从发送帐户中扣除。这时交易有0个确认。当另一个块添加到区块链时，交易有1个确认。下一个添加到链的区块将给予2个确认。

交易有不同的类型，每种类型都有其特定的作用，如从一个账户转移xem到另一个账或者将一个账户转换成一个多签账户。由于交易消耗了P2P的网络资源，因此，每笔交易都要收取手续费，手续费取决于交易的类型和交易的其他参数。交易有一个截止日期，如果一个交易在截止日期到来前还没有包含进区块中，该交易被认为已过期并且被节点丢弃。

加密货币有能力回滚区块链的一部分。这对于解决区块链的分叉非常重要。但是，可以回滚的块的最大数量称为重写限制。因此，分叉只能解决一定的深度。NEM有360块的改写极限。一旦交易超过360个确认，则不能逆转。在现实生活中，深度超过20个块的分叉不会发生，除非由于代码中的错误或某种攻击而导致区块链出现严重问题。

### 消息(Message)


### 命名空间(Namespace)
NEM支持类似于互联网域名概念的命名空间。命名空间是一个可识别的字符串，由一个或多个部分组成，每个部分由"点"联系起来。例如"makoto.metals.silver".所有的命名空间都是独有的，因此只能有一个拥有者。一个命名空间中只有一个部分被称为根命名空间，其他部分称为子命名空间。根命名空间可以通过帐户租用一年。在根命名空间到期前一个月，租赁合同可以续签一年。如果续订了根命名空间，那么所有子命名空间在下一年也有效。如果根命名空间不更新，到期后，连同所有子命名空间一起到期。根命名空间到期后一个月，另一个帐户能够租用该根命名空间。新所有者不会从以前的所有者继承子命名空间。如果帐户拥有相应的根命名空间，则只能租用子命名空间。

命名空间中的每一部分都有允许的字符和对长度有一定的限制。根命名空间可能有16个字符的长度，而子命名空间可能有64个字符的长度。有效字符串是：

  a, b, c, ..., z, A, B, C, ..., Z, 0, 1, 2, ..., 9, _ , -
  
但是，每一部分，只能以字母开头。因此对于根命名空间"alice"是允许的，而"1alice"是不被允许的。

某些字符串被保留，因此不允许作为命名空间部分。被保留的命名空间为：

  nem, user, account, org, com, biz, net, edu, mil, gov and info
  
该列表不是最终的，将来还会扩展。例如，'user.alice'或者'alice.user'在NEM命名空间系统中是无效的。命名空间最多有3个部分，因此'makoto.metals.silver'是有效的，而'makoto.metals.silver.coin'是无效的。

除了通常的手续费外，命名空间还有租金。这个费用是支付给所谓的租金帐户，这是一个特殊帐户地址。

  正式网络是：NAMESPACEWH4MKFMBCVFERDPOOP4FK7MTBXDPZZA
  
  测试网络是：TAMESPACEWH4MKFMBCVFERDPOOP4FK7MTDJEYP35
  
命名空间允许用户拥有独有的命名空间。个体或团体（多重签名方式）拥有一个命名空间。企业可以用自己拥有的命名空间证明其发布的商品或资产（在区块链中以马赛克方式存在）。

!> 注意：为了创建马赛克，需要命名空间的所有权

### 马赛克(Mosaics)

马赛克是NEM中定义的数字资产，展露了更多的特性和其他功能。马赛克可以用于管理数字货币，股票，优惠券，欠条，法币等价物或其他任何资产。任何人可定义发行自己的马赛克。每个马赛克后面都有一个马赛克定义。为了能够创建马赛克定义，帐户必须至少租用一个根命名空间，该命名空间可以被马赛克定义所引用。马赛克定义的基本概念包括：

* mosaic id: mosaic id包含两部分，namespace id和mosaic名字。当将mosaic id表示为字符串时，这两个部分通过"\*"连接起来:如namespace id是 'makoto.metals.silver'，mosaic id是 'coin'，那么，字符串表示应该是'makoto.metals.silver * coin'。由于mosaic id应该是唯一的，所以马赛克名称必须在马赛克定义引用的名称空间中是唯一的。马赛克名称的最大长度为32个字符。允许的字符是：

  a, b, c, ..., z, 0, 1, 2, ..., 9, ', _ , -
  
!> 注意：马赛克名称必须以字母开始

* description：每个马赛克定义都需要做一个描述，描述不能超过512个字符。在描述中字符没有限制

* properties：一个马赛克的行为可以通过一组属性来定义。如果没有提供属性，则使用默认属性。支持的属性如下：

  > 1.initialSupply：创建定义时，创建者可以指定马赛克的初始供应量。供应量给出了马赛克的总量，而不是最小的子单位。初始供应量必须在0和9000000000的范围内。默认值是“1000”。
  
  > 2.divisibility：可分性决定了马赛克能够最多被划分的小数点的位置。因此一个为3的可分性表示一个马赛克可以被分割的最小部分是0.001个马赛克。当通过转账交易传送马赛克时，所传送的数量是这些最小部分的倍数。可分性范围必须在0到6之间。默认值为"0"。
  
  > 3.supplyMutable：创建者能够选择当中的一个定义值，来允许一个马赛克的供应量是否能在以后改变或者不可变。该属性的允许值为“true”和“false”。默认值为“false”。
  
  > 4.transferable：创建者可以选择是否马赛克定义允许在除创建者之外的帐户中转移马赛克。如果该属性设置为“false”，则只有具有创建者作为发送方或接收方的转账交易才可以传输该类型的马赛克。如果设置为“true”，则马赛克可以从任意帐户转移到任意帐户。因此，属性的允许值是“true”和“false”。默认值为“true”。
  
* levy：创建者可以要求为每个类型的马赛克转移规定一个特殊的费用，该费用由发送者给出并发送到其选择的账户(因此，创作者可以指定自己的账户，以便收取该费用)。征收的数据如下：

  > 1.fee type：支持两种费用类型，绝对费用和百分比费用：
  
    >> 1.绝对费用：费用被指定为绝对数量，因此不取决于被转账的数量。
    
    >> 2.百分比费用：费用被指定为转移数量的百分之倍数。费用随着转账数量的增加而线性增加。
    
  > 2.recipient：征税人，可以是任何账户
  
  > 3.mosaic id：必须用于支付费用的mosaic id。可以指定任何现有的mosaic id。如果创造者要支付的费用是XEM，然后她/他用mosaic id"NEM * XEM"。
  
  > 4.fee：手续费。

除了交易费用外，马赛克还有创建费用。这个费用是支付给所谓的租金帐户，这是一个特殊帐户地址：

  正式网络是：NBMOSAICOD4F54EE5CDMR23CCBGOAM2XSIUX6TRS
  
  测试网络是：TBMOSAICOD4F54EE5CDMR23CCBGOAM2XSJBR5OLC

### 多重签名(Multisig)

NEM的多重签名以链上合约的方式工作。简单有效，保障无懈可击，直接作用于区块链
