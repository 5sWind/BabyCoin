## Welcome to BabyCoin site, the ERC-20 Standard Token based on Ethereum

<img src="https://i.loli.net/2018/05/24/5b064afff2c37.png" alt="Biocards_front.png" title="Biocards_front.png" width="250"/>
<img src="https://i.loli.net/2018/05/24/5b064b00226b9.png" alt="Biocards_back.png" title="Biocards_back.png" width="250"/>

> BabyCoin is a gateway which introduce cryptocurrency to you.

### Let's start your journey with BabyCoin

- Install MetaMask
(https://metamask.io/)

    Chrome or Firefox are recommended.

    [![WX20180421-235321@2x.png](https://i.loli.net/2018/04/22/5adb615596620.png)](https://i.loli.net/2018/04/22/5adb615596620.png)

- Add Token

    BabyCoin Token Address:     0xF20A773b3d9f2a1F080fBAe1156A5E9768ceb615

    Add to MetaMask Wallet:

    [![WX20180422-000809@2x.png](https://i.loli.net/2018/04/22/5adb62975f365.png)](https://i.loli.net/2018/04/22/5adb62975f365.png)
    [![WX20180422-000832@2x.png](https://i.loli.net/2018/04/22/5adb6297600e6.png)](https://i.loli.net/2018/04/22/5adb6297600e6.png)
    [![WX20180422-000910@2x.png](https://i.loli.net/2018/04/22/5adb62975f9b7.png)](https://i.loli.net/2018/04/22/5adb62975f9b7.png)
    [![WX20180422-000940@2x.png](https://i.loli.net/2018/04/22/5adb629760727.png)](https://i.loli.net/2018/04/22/5adb629760727.png)

    Then the token will display in all your accounts.

### About ERC-20 Standard Token

 ERC-20 是一个代币标准，我们可以通过它创建自己的代币，关于如何创建代币，可以参考我的讲座教程：
 > https://docs.google.com/presentation/d/1GyCfQO3oHxO4NTnejNDnHwibom9uFQ8F381ng_AU8SA/edit?usp=sharing

### User Picture

- 宝宝币如何获得？

    A: 参与我的讲座, 陪我打比赛, 玩我做的游戏, etc.

- 宝宝币可以用来干什么？

    A: 收集一定数量的宝宝币, 可以兑换实物, 门票, 虚拟道具等等。

- 我如何使用宝宝币？

    A: BabyCoin Store.

### Future Plan

- 宝宝币兑换周边计划

- 宝宝币个人品牌计划

### Appendix

- 关于代币空投的实现

    声明代币现有数量，每个用户拥有量，发行总量
    ```
    uint256 public currentTotalSupply = 0; // 现发行数量
    uint256 public airdropNum = 2 ether; // 每个用户拥有量
    uint256 public airdropSupply = 2000; // 发行总量
    ```

    定义用户是否已经被空投过
    ```
    mapping(address => bool) touched; // 用户地址返回true和false的映射
    ```
    
    空投函数
    ```
    /// @dev 如果用户没有被空投过，且现发行量小于发行总量，则进入此函数分支，把用户设为已被空投，给当前用户余额添加 2 BBC，现发行量数量 +2.
    function _airdrop(address _owner) internal {
        if(!touched[_owner] && currentTotalSupply < airdropSupply) {
            touched[_owner] = true;
            balances[_owner] = balances[_owner].add(airdropNum);
            currentTotalSupply = currentTotalSupply.add(airdropNum);
        }
    }
    ```

    查询用户是否为可空投用户
    ```
    /// @dev 外部函数将调用此函数，如判定先现发行数量大于等于总量，或添加Token的人为该合约拥有者，则不进入分支返回当前余额。反之，进入分支判断为接受过空投，返回当前余额，没有接受空投的用户添加Token则余额+2。
    function getBalance(address _who) internal constant returns (uint256)
    {
        if(currentTotalSupply < airdropSupply && _who != owner) {
            if(touched[_who])
                return balances[_who];
            else
                return balances[_who].add(airdropNum);
        } else
            return balances[_who];
    }
    ```

- 我的社交网站

    知乎: https://www.zhihu.com/people/5swind

    Google+: https://plus.google.com/+5sWindZhang

    Twitter: https://twitter.com/Fiveswind

    Github: https://github.com/5sWind

    Facebook: https://www.facebook.com/5sWind

