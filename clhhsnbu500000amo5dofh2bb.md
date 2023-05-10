---
title: "The Centralization Paradox of Decentralized Autonomous Organizations"
datePublished: Wed May 10 2023 14:26:28 GMT+0000 (Coordinated Universal Time)
cuid: clhhsnbu500000amo5dofh2bb
slug: the-centralization-paradox-of-decentralized-autonomous-organizations
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683728719811/3d286847-83d3-4e67-8967-49a8d7d9ac8f.jpeg
tags: blockchain, daos

---

Decentralized autonomous organizations use blockchain technology and can revolutionize business and society. They enable quick and fair decision-making through transparent voting and open discussion. By 2023, they are projected to manage $12 billion. However, they face challenges, such as concentrated voting power and high blockchain voting costs, with some governance systems still immature. The analysis of 21 DAOs, including those governing decentralized exchanges, lending protocols, infrastructure projects, and common goods funding, with blockchain-based governance systems, reveals several issues, including unnecessary transactions. The aim of data collection and analysis is to facilitate improvements and enhance DAO effectiveness.

This article summarizes a research paper titled "[The Hidden Shortcomings of (D)AOs - An Empirical Study of On-Chain Governance](https://tik-db.ee.ethz.ch/file/3e40de2048a77cb71d2eefbbbfa5045f/2302.12125.pdf)" by Rainer Feichtinger, Robin Fritsch, Yann Vonlanthen, and Roger Wattenhofer.

# Dataset

They use The Graph to gather information about different groups. Each group has its own set of information, which they get using a subgraph and a GraphQL API. For each group, they track who has voting tokens (their address, how many tokens they have, and who they are voting for) and who can vote (their address, how many votes they have, and who they are receiving votes from). They also monitor when someone receives or loses voting tokens and record information about the groups and their votes.

Before analyzing the information, they remove accounts managed by computer programs or exchanges as they cannot be used for voting. They use Alchemy and Etherscan to identify these accounts.

The below table displays the groups they studied, with information collected up to block 16,530,000 (31 Jan 2023).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727016233/4756ae80-8ff9-4390-a64b-4680f6560920.png align="center")

# Distribution of Voting Power

The distribution of voting power in DAOs using the Gini and Nakamoto coefficients.

* The Gini coefficient, which ranges from 0.0 to 1.0, measures inequality in the distribution of any fungible good, like voting power.
    
* The Nakamoto coefficient measures how decentralized a system is by counting how many parties are needed to take control of the system.
    

The analysis shows that voting power in DAO governance systems is highly centralized, with less than 10 addresses having full control over most DAOs. While there is a slight trend towards decentralization over time, the findings raise questions about the "D" in DAO.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727052671/2aad0923-ddc4-427b-b5c7-a8fdee1adf45.png align="center")

# Structure of Voting Power Delegation

When deciding on voting power delegations, we must consider who the delegates represent: a large token holder or a group of community members. There are two types of delegates: single holder and community. Single-holder delegates represent one holder and their interests, and they usually have more than half of their delegated tokens from one token holder. Community delegates get less than half of their delegated tokens from one token holder. If a governance system has more community delegates, it's like a representative system where the community elects representatives. But if the share of community delegates is low, then the governance system represents the interests of big token holders directly.

For ENS, Gitcoin, and Hop, about half of all votes are in the hands of community delegates, while for Compound, Fei, and Uniswap, the vote share of community delegates is low at about 10% or less. Decentralization is low, and it's worth questioning whether a delegation system is even necessary due to its significant costs, as shown in the following sections.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727129152/2317d2f7-423a-4afe-a933-89232c89942a.png align="center")

# Governance Participation

The governance participation rate can be measured in different ways, depending on tokens, delegates, or voting power. For token holders, it is the proportion of those voting out of the total number of token holders. For delegates, it is the proportion of those voting out of the total number of delegates. The indirect participation rate of holders is the proportion of those involved in a vote out of all holders. The participation rate of voting power is the number of governance tokens voting relative to the total number delegated.

The participation rates for four protocols: Compound, Uniswap, ENS, and Gitcoin. Voting power is typically higher than token holder and delegate rates. This means that voters with high voting power are more active, which is not surprising. The participation rate of token holders is particularly low for all DAOs. The interest in proposals depends on their content.

ENS and Gitcoin have a comparatively low delegate participation rate. This may be because these protocols required delegating when claiming their airdrop. On the other hand, a large proportion of ENS token holders (on average about 60%) are represented during votes, indicating a working governance system and an argument in favor of requiring delegations when claiming tokens.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727171161/3afa3e8c-0ed7-490f-a58a-272338fab130.png align="center")

# Pointless Governance Transactions

To get an accurate picture of a DAO's activity, it's not enough to just look at the number of votes and delegations. Some transactions are "pointless" - they may be due to people trying to get future rewards or just mistakes. they’ve identified three types of pointless transactions:

* Pointless transfers,
    
* Pointless votes, and
    
* Pointless delegations.
    

By measuring the number of these transactions, they can gauge a community's maturity in using governance protocols.

Pointless transfers are rare, but there is a high proportion of pointless votes and delegations. For instance, nearly 30% of all daily votes for ENS are pointless. They suspect that many users are unaware that they need to delegate their voting power to themselves before they can vote.

Many DAOs have shockingly high proportions of useless votes and delegations. Even conservative definitions of pointless transactions show Uniswap having an 88% voting power below 10 tokens, and 47% of votes having a voting power below 1 token, despite requiring 2.5 and 40 million tokens to submit and pass a proposal respectively.

Overall, ENS has only a few pointless transactions (&lt;2%), but this is because most of their governance transactions occurred after their airdrop when the percentage of pointless transactions was low. They conclude that DAOs are still in their infancy, as the proportion of pointless delegations and votes per day is increasing over time for ENS and Compound.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727189969/aacc3f17-e3c0-4718-9f4a-fab12d6dbd93.png align="center")

# Monetary Price of Governance

The cost of governance on-chain. When you do a transaction on a blockchain like Ethereum, you have to pay a fee based on the amount of work the transaction needs (measured in gas units) and how much people want to use the space in the block (which affects gas prices).

To find out the cost of governance in money, we look at three types of transactions: voting, giving someone else voting power, and making proposals. They only consider the cost of the governance part of the transaction, even if multiple things happen in a single transaction.

The cost of governance is calculated using the ETH price on Etherscan from the day of the transaction, taking into account the fluctuating prices of ETH and gas in ETH.

## Price of Governance Transactions

Transactions that suggest ideas cost more than delegations or votes, but they happen less often. Most of the cost is from delegations, except for Compound, which has more voting costs than delegation costs. ENS has much higher costs than other DAOs, with about $3.5 million, because of very high delegation costs after the launch of the governance system. This happened during the ENS Airdrop in November 2021, when Ether and gas prices were very high. Gitcoin also enforced delegations during their airdrop but started in May 2021, so they paid less in fees. Gitcoin has fewer token holders than ENS.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727227916/cd1b19f1-72f2-4890-b576-313c52b99b1e.png align="center")

Uniswap and other protocols did not require delegation like ENS and Gitcoin, so the costs were spread out over time. A large peak between Nov 29, 2022, and Dec 1, 2022, for Uniswap, possibly due to people setting up wallets for airdrop farming. These users created new accounts with minimal tokens and conducted similar transactions, suggesting they were airdrop hunters.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727244376/1c6aa557-5f6d-4a8a-9ade-1077fe5572ce.png align="center")

Assigning voting power during the airdrop can be expensive, but it allows for more people to participate and share voting power fairly. Governance tokens are primarily used for voting, so not assigning voting power could be seen as not using the token for its main purpose.

After calculating the cost of assigning voting power, they found it actually saves money on transaction fees for voting. Without assigning voting power, voting would be more expensive for everyone. However, for Uniswap, fewer people use assigned voting power, resulting in fewer savings.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727281226/727daf3b-35f5-44af-bac9-3bbc4fbe55fc.png align="center")

## Price of Transfer Overhead

A DAO's governance token serves two purposes: voting rights in the protocol's governance and as a tradable asset for participating in the project's success. Token holders can also generate revenue through staking, lending, or dividends. However, when a token has both monetary and voting functions, there is an additional hidden cost. Token transfers can change the voting power of delegates, requiring extra smart contract logic. For Uniswap, this cost is almost 3 million USD, much higher than the cost of direct governance transactions. The total cost of governance, including transfer overhead and governance costs. This implementation may be questioned for projects with low revenue or infrequent and inactive governance protocols.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727379554/11760407-5059-4e4a-929e-068973042df7.png align="center")

# Conclusion

DAOs were originally created to simplify community decision-making, enabling quick responses to opportunities and challenges. Proposals for DAOs range from protocol improvements to managing mergers, dealing with hacks, and even deciding on their own shutdown. While voting fosters open discussions, some signs raise concerns. For instance, DAOs may be used as a marketing tool or a way to hide decisions made by a ruling dictatorship under the guise of community governance. Their analysis helps designers create more affordable and accessible DAOs, considering costs and decentralization in different scenarios, and creating the next generation of DAOs with improved airdrop mechanisms and governance incentivization.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683727416107/d78d844a-7466-449a-917c-f854eefb5e9a.png align="center")

# Reference

* *Rainer Feichtinger, Robin Fritsch, Yann Vonlanthen, and Roger Wattenhofer* \[2023\] The Hidden Shortcomings of (D)AOs - An Empirical Study of On-Chain Governance [Link](https://tik-db.ee.ethz.ch/file/3e40de2048a77cb71d2eefbbbfa5045f/2302.12125.pdf)