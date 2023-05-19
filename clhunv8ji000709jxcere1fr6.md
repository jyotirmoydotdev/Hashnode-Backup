---
title: "Understanding the advantages and disadvantages of DAO voting schemes"
datePublished: Fri May 19 2023 14:33:39 GMT+0000 (Coordinated Universal Time)
cuid: clhunv8ji000709jxcere1fr6
slug: understanding-the-advantages-and-disadvantages-of-dao-voting-schemes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684506764275/3334ea1d-5519-4802-ab3d-024fde32fbe6.jpeg
tags: blockchain, daos

---

In this article, we will provide an overview of the various voting schemes available in the DAO industry, including their advantages, disadvantages, and real-world examples. DAOs can use different voting schemes to make decisions, from token-based quorum voting to rage-quitting voting. Each scheme has its own strengths and limitations, making it essential for DAOs to choose the right one that best fits their needs. By understanding the various voting schemes available, DAOs can make informed decisions and promote a fair and effective decision-making process.

There are several practical voting methods used in the DAO industry. We will discuss eight popular voting methods:

* Token-based quorum voting
    
* Weighted voting
    
* Reputation-based voting
    
* Multisig voting
    
* Quadratic voting
    
* Conviction voting
    
* Rage Quitting voting
    
* Knowledge-extractable voting
    
* Holographic consensus
    

# Token-based quorum voting

DAOs commonly use quorum voting to make decisions. To approve a proposal, a certain percentage of voters must participate and vote in favor of it. The required percentage varies. Once the threshold is met, the proposal with the most votes is approved. This ensures a significant portion of the community is involved.

This protocol has advantages over quorum voting. A proposal can be approved even with low voter turnout, as long as enough voters support it. Compound, Curve, and Kleros use this protocol because it is simple and does not require a quorum.

The threshold can be measured in tokens or voter participation. Token-based voting has issues, such as giving more influence to those with more tokens. The participant threshold required for this protocol can also be costly and time-consuming. Finding the right balance is important for a fair and effective decision-making process. [KyberDAO](https://twitter.com/kyberdao?s=21&t=vjBYzjYSXMBL29PbjNqogw) and [Aave](https://twitter.com/aaveaave?s=21&t=vjBYzjYSXMBL29PbjNqogw) use this voting scheme.

# Weighted & Reputation-based voting

Weighted voting allows each voter to cast a certain number of votes, with the weight of each vote being determined by the total number of votes a voter has. This means that a voter with more votes has more influence on the outcome of the vote than a voter with fewer votes. Reputation-based voting, on the other hand, determines the weight of a voter's vote based on their reputation or trustworthiness within the community. Factors such as past contributions to the DAO, level of engagement, or stake in the DAO determine a voter's reputation or influence. This means that voters with more trust or reputation within the community have more influence on the outcome of the vote compared to those with less reputation. This voting scheme rewards voters who have a track record of contributing to the DAO rather than simply holding tokens. Specifically, voters with a proven track record are rewarded with a portable reputation, which gives their votes more weight.

Under this mechanism, reputation is more important than wealth. Track record is one measure of reputation. The length of time that users hold specific tokens could also be considered a measure of reputation, conviction, or alignment of interests. Reputation is like a credit that accumulates over time through contributions to the DAO community. It is less likely to be transferred or traded. Reputation can be dynamic, meaning it could expire or diminish over time to avoid the effects of early easy-gainers and maintain fairness to all voters.

Weighted voting and reputation voting make it harder to launch Sybil's attacks, but there is still a risk. This method is more efficient and sustainable than token-based voting. However, creating a good reputation system can be difficult. [BPC DAO](https://twitter.com/ndaucollective?s=21&t=-S997wlu5mI2KkvtiB8RNA) and [OrangeDAO](https://twitter.com/orangedaoxyz?s=21&t=HPxFQOhlo_avE01bXW9bFw) use a reputation-based voting system.

# The multi-sig voting

Multisig voting is a way to make decisions on the blockchain. Before any action is taken, a group of users, called signers, must approve a proposal by signing it. This helps to ensure that decisions are made democratically and that no one person or group can make decisions alone. Multisig voting is commonly used in decentralized systems, like DAOs, to manage pooled funds. It requires a minimum number of members to sign off on transactions, which prevents any one member from moving funds on their own.

The main advantage of multi-sig voting is that it provides extra security and ensures that each transaction is thoroughly verified before it is completed. However, multi-sig voting is not suitable for all types of proposals, and it may require some basic technical knowledge to set up a multisig wallet. It is also possible for the multi-sig key holders to collude and make decisions against the interests of other DAO members.

[Gnosis Safe](https://safe.global/), [Aragon Client DAOs](https://aragon.org/), and [BitDAO](https://www.bitdao.io/) are examples of projects that use multi-sig voting. The number of signers required for a proposal to be approved can vary, depending on the specific needs of the organization. For example, a 7-of-10 multi-sig protocol would require seven out of ten parties to sign off on a transaction before it can be executed.

# Quadratic voting

Vitalik Buterin, the co-founder of Ethereum, developed [quadratic voting](https://daotimes.com/a-flexible-design-for-funding-public-goods-quadratic-funding/) as a new way of voting that allows people to show how much they care about a proposal. Unlike other voting methods, quadratic voting gives more power to those who care more about the proposal and use more tokens to vote. However, it becomes more costly to increase voting power, to limit one person from having too much power. Quadratic voting ensures that proposals with little support don't pass and that small groups still have power.

Despite its benefits, there are also some issues with quadratic voting. It still favors those with more money, which is unfair. Also, it's harder to verify voters' identities, which could let fake people vote and distort results. Some platforms, such as [Gitcoin](https://twitter.com/gitcoin?s=21&t=vjBYzjYSXMBL29PbjNqogw) and [BrightID](https://twitter.com/brightidproject?s=21&t=vjBYzjYSXMBL29PbjNqogw), utilize quadratic voting for decision-making.

# Conviction Voting

Conviction voting is a new way to vote that combines how much someone wants something with how long they want it for. It was created to make sure that people with tokens care about the organization's long-term success. In conviction voting, people in the community can vote on ideas by putting their tokens in for a certain amount of time. If they keep their tokens in for a long time, their vote counts more. This means people have to think about what's best for the organization in the future, not just what's best for them right now. By keeping their tokens in for a long time, people show that they really believe in the idea and think it will help the organization in the future.

# Rage Quitting Voting

Rage quitting happens when token holders in decentralized communities, like DAOs that use token-weighted voting systems, are unhappy with a vote or the organization's direction. They withdraw their stake and sell their tokens instead of supporting the organization. This can reduce future participation and decrease the token's value.

In [Moloch DAO](https://molochdao.com/), there are full shares with both voting and "Ragequit" rights, and loot shares with only "Ragequit" rights. Proposals need at least one member's support to proceed to the voting process. The voting process collects "agree" or "disagree" votes from members, and a proposal passes if "agree" votes are more than "disagree" votes. There's no quorum requirement.

When a proposal passes, members who disagreed with it can withdraw their shares before its implementation. This is the "Ragequit" design to protect members from unwanted proposals. The mechanism is secure against Sybil attacks and scales trustless coordination with more stakeholders than other voting mechanisms like Multisig.

[Moloch DAO](https://molochdao.com/) also has Minion as a supplement, which allows early execution on proposals without "Ragequit" and the grace period. However, this changes the security properties of a DAO's funds, especially when the stakes in the proposal are high enough. There's a trade-off between security and efficiency.

To avoid rage quitting voting, organizations can implement measures like reducing the token liquidation speed or making it difficult to withdraw the stake. [MetaCartel Ventures](https://metacartel.xyz/), [MolochDAO](https://molochdao.com/), and [DAOhaus](https://daohaus.club/) are experimenting with this voting scheme.

# Knowledge-extractable voting (KEV)

Knowledge-extractable voting is a voting system that considers the knowledge or expertise of voters when deciding the outcome of a vote. Voters can show their knowledge on a topic or an algorithm can assess their contributions to a discussion. The goal is to make decisions based on the group's collective wisdom, not just a few people's preferences. It's used in online communities, decentralized autonomous organizations (DAOs), and other collective decision-making. The system gives more weight to votes from experts and divides proposals into different categories, each with a representative token. The token enhances the weight of the votes. The final outcome is a weighted average of the votes using the knowledge tokens as weights. Voters get rewards for using knowledge tokens to vote and lose tokens if they make bad choices. This discourages voters without enough knowledge from voting. Knowledge tokens cannot be traded or transferred, so voters can't manipulate the system. This new scheme is gaining attention in the industry. DIT Protocol (Decentralized Information Theory) is an example of using the scheme. It's a decentralized protocol that encourages knowledge sharing and allows users to vote on the quality and relevance of information. Users earn reputation points by contributing valuable information and can use these points to vote on other user's submissions. The DIT Protocol is a decentralized and self-governing platform for collective knowledge sharing and organization.

# Holographic Consensus

Holographic consensus is a way to make decisions in a decentralized system. It works by looking at the decisions of a small number of powerful nodes to figure out what the larger group of nodes wants. This is kind of like how you can figure out what's inside a room by looking at what's on the walls around it. This method is faster and more efficient than other ways of making decisions.

To use this method, people stake their tokens to show they care about the decision. They can also earn rewards for doing this. Different organizations use different ways of staking, but it usually involves holding onto tokens for a certain amount of time. This lets people participate in making decisions for the organization. Anyone who meets certain requirements can suggest a decision. But only the ones that get a lot of attention will be reviewed and voted on. The voting is done by a small group of people who decide for everyone. An incentive is given to make sure everyone's interests are aligned. To make sure the right decision is picked, a cryptocurrency called GEN is used. People use GEN to bet on which decision they think is the best. The decision with the most GEN gets the most attention and is more likely to be picked. If someone bets on the right decision, they can earn more GEN. But if they bet on the wrong decision, they lose their GEN. This makes people investigate each decision and choose the best one. GEN is used to improve the DAOstack ecosystem. It makes sure that everyone has the same interest in making the organization better. Using other cryptocurrencies like Ether might distract people from the organization's goals. This system lets anyone with GEN choose the best decision. The decision with the most attention is more likely to be picked. This makes it easier for a small group of people to make decisions that everyone agrees with. Holographic consensus has some benefits. It works well for large, decentralized organizations. It's transparent and easy to check. It makes sure everyone is involved and engaged.

However, there is a risk that the decision with the most attention might not be the best one. Some organizations that use this system are [DXdao](https://dxdao.eth.link/), [necDAO](https://twitter.com/necdao?s=21&t=LMdUqisXpiPZcN4SRZulgg), and [DAOstack](https://daostack.io/).

# Conclusion

In conclusion, DAOs have a variety of voting schemes to choose from when making decisions. Each scheme has its own strengths and limitations, and it is important for DAOs to choose the right one that best fits their needs. Token-based quorum voting, quadratic voting, weighted voting and reputation-based voting, knowledge-extractable voting, multi-sig voting, holographic consensus, conviction voting, and rage quitting voting are some of the most commonly used voting schemes in the DAO industry. By understanding the pros and cons of each scheme, DAOs can make informed decisions and promote a fair and effective decision-making process.