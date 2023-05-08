---
title: "A Flexible Design for Funding Public Goods - Quadratic Funding"
datePublished: Mon May 08 2023 04:15:52 GMT+0000 (Coordinated Universal Time)
cuid: clhebye5p000e09labony8tw4
slug: a-flexible-design-for-funding-public-goods-quadratic-funding
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683519134083/20392360-c57f-4719-8927-fad760050c48.jpeg
tags: github, blockchain, cryptocurrency, funding

---

In 2018, [Vitalik Buterin](https://twitter.com/vitalikbuterin), the founder of [Ethereum](https://twitter.com/ethereum), along with [Zoë Hitzig](https://twitter.com/zhitzig) and [E. Glen Weyl](https://twitter.com/glenweyl), released a paper called "[A Flexible Design for Funding Public Goods.](https://arxiv.org/pdf/1809.06421.pdf)" The paper aimed to change the way public goods are funded.

They propose a funding system that supports public goods in a decentralized and self-organizing way, using philanthropic donations or public funding. This system is based on Quadratic Voting principles, allowing citizens to invest in projects that matter to them.

The amount of funding a project receives is proportional to the square of the sum of the square roots of the donations it receives (Sounds complex? Don't worry, I'll explain it later in this article.). This method is optimal for providing public goods in the "standard model," and can be modified to reduce costs, prevent collusion, and improve coordination.

As of writing this article, this system is being used by [Gitcoin Grants](https://bounties.gitcoin.co/grants), [Pomelo Grants](https://pomelo.io/grants), and Downtown Stimulus, distributing a total of $22,907,689. In this article, we will discuss public goods, why Quadratic Funding is necessary, how Quadratic Funding works, and what Quadratic Voting is.

## What are Public Goods?

Public goods are things that are accessible to everyone and do not diminish in availability for individual consumption. They are referred to as non-excludable and non-rivalrous. For example, the articles published by DAO Times can be considered public goods because they are free and do not diminish the availability for other individual consumption. some of the other examples of public goods are clean air, knowledge, official statistics, national security, common languages, law enforcement, open-source software, public parks, and free roads. To fully understand the concept of public goods, it is important to know about other types of goods as well.

The goods can be divided into four parts **Private**, **Common, Club,** and **Public** goods. And each good can be Excludable or Non-excludable, Rivalrous or Non-rivalrous. Excludable means that the good or service can be restricted to certain individuals or groups. Rivalrous means that the consumption of a good or service by one individual reduces the availability of that good or service for others.

* Private Goods are goods that are both excludable and rivalrous. Private goods can be owned by individuals and used at their discretion, and the consumption of one person diminishes the amount available for others. Examples of private goods include food, clothing, and housing.
    
* Common goods are goods that are available for free but are competitive. For example, if one person used all the water from a pond, others will be affected. Private goods are rivalrous but not excludable. Some other examples of common goods are fish stocks, timber, coal, and free public transport.
    
* Club goods, also known as "artificially scarce goods" are goods that are non-rivalrous but excludable. Unlike public goods, club goods are not available for free to everyone. However, the consumption of the good by one individual does not diminish its availability to others. For example, satellite television is considered a club good because an individual can only use it if they have a subscription. Some other examples of public goods are cinemas, private parks, and public transport.
    

## Why do we need Quadratic Funding?

Public goods are important for human flourishing, as they benefit society as a whole. However, because they are non-excludable, individuals may choose not to pay for them, assuming that others will bear the cost. This leads to a problem known as the "free-rider problem," where individuals benefit from the provision of public goods without contributing to their costs.

Different organizations have been created to solve the problem of public goods. The most important organization is the democratic nation-state, which uses taxation and voting to decide which public goods should be provided. Unfortunately, democratic systems (even when they work well) follow the majority, not always what's best for everyone. They sometimes hurt minorities or are taken over by minorities to avoid harm. They are also expensive to create, inflexible, and don't easily change to meet new needs. Other organizations use moral, cultural, religious, or social reasons to encourage people to donate to public goods. However, all of these groups have limits.

To address this problem, economists have proposed funding mechanisms, such as Quadratic Funding. Quadratic Funding is a funding system that supports public goods in a decentralized and self-organizing way, using philanthropic donations or public funding. This method is optimal for providing public goods in the "standard model," and can be modified to reduce costs, prevent collusion, and improve coordination. This mechanism allows for greater flexibility in choosing what goods to fund, eliminates the assumption of complete information, and satisfies individual rationality constraints.

# How does Quadratic Funding work

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683517364767/cd47ea42-2b1c-41ca-a6d9-7aed01bfa28d.gif align="center")

Quadratic Funding assigns a "matching pool" to each project or public good. This pool is filled with funds from philanthropic donations or public funding. For example, suppose we receive a total of $1000 in public funding, and we need to distribute this amount among three projects. To do so, we first need to determine the voting power and ratio of each project. Then, we can calculate how much each project receives from the matching pool.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683517405826/06594be6-21c9-477d-8b29-e7a710c83882.png align="center")

### Voting Power

Voting power is a measure of the influence that a donor has in the allocation of funds to a project. In Quadratic Funding, it is calculated based on the square roots of the amounts donated by each individual to a particular project. The sum of these square roots is then squared to obtain the voting power for that project.

Suppose four individuals donate to Project A. Each individual donates $100, resulting in a total donation of $400.

To calculate the Voting Power for Project A, first, add up the square roots of 100, and then square the sum of VP, which equals 1,600.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683517459739/09c9e8e1-089b-4dda-a161-b1db3831f091.png align="center")

Suppose 20 individuals donate to Project B. Each individual donates $20, so the total amount donated is $400.

To calculate the Voting Power for Project B, first sum all the square roots of 20, and then square the result to obtain the sum of VP, which equals 8,000.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683518223659/d018137e-484e-4b24-b730-d50a6bad4e6a.png align="center")

Suppose 10 individuals donate to Project C, with each donating $20. The total amount donated is $200.

To calculate the Voting Power for project C, first sum the square roots of 20, then square the sum of the VP. The result is 2,000.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683518261634/49c42bf2-224a-40b5-98ed-3470777f8518.png align="center")

Project A received a voting power of 1,600, Project B received a voting power of 8000, and Project C received a voting power of 2000.

### Ratio

The ratio determines the amount of funding that a project will receive. It is calculated by dividing the voting power of the project by the sum of the voting powers of all projects.

To begin, we must determine the total voting power. This can be achieved by adding up the voting power of each project, resulting in a total of 11,600.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683518306801/31476664-4461-4059-8ba5-2a855153486f.png align="center")

Once we have obtained the total voting power, we only need to determine the ratio. To do this, we divide the voting power of the project by the sum of the voting powers of all projects.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683518338165/e6f64d87-bb0b-4de3-a686-2f121f16ceb3.png align="center")

### Match Amount

The match amount is the amount of funding a project receives from the matching pool. It is calculated by multiplying the ratio by the total matching pool amount. For example, suppose the total matching pool is $1000. Using the ratios calculated earlier, we get the following match amounts:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683518374031/9b0eca57-1e5f-4234-8fa8-2efbfc40538d.png align="center")

Therefore, Project B receives the most funding, followed by Projects C and A. This system ensures that projects with the most support from the community receive the most funding. It also encourages a diverse range of projects to be funded, as smaller projects with strong community support can receive more funding than larger projects with weaker support.

### Total Donation (Original + Match Amount)

This total donation includes both the original donation and the match amount.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683518400140/f38ac1e9-752f-4f72-b330-1bff5788b82c.png align="center")

Quadratic Funding offers a fair and democratic way to fund public goods while ensuring the most popular projects receive the most funding. It has already been successfully implemented in several organizations, and its potential for supporting public goods is enormous.

# What is Quadratic Voting

Quadratic Voting is a way of voting where people can "buy" votes based on a quadratic cost function. Everyone gets a certain number of "voice credits" they can use to buy votes on different issues or projects. Each vote after the first one costs more than the previous one, with the cost getting higher and higher the more votes you buy. This means that everyone gets a chance to have their say, and no one person or group can control the process. It has been used by organizations like Gitcoin Grants to make sure that funding decisions are fair and democratic.

Gitcoin has also implemented several measures to combat bot voting. One of the most effective measures is called Sybil detection. Sybil detection identifies and prevents fake accounts from participating in the funding process. This is achieved by analyzing the behavior of the accounts and identifying patterns that suggest they are not real users. Another measure is to require accounts to be linked to an Ethereum address. This ensures that each account is associated with a real person who has a stake in the outcome of the funding process.

# Reference

* *Vitalik Buterin, Zoe ̈ Hitzig, E. Glen Weyl* \[2018\] A Flexible Design for Funding Public Goods. [Link](https://arxiv.org/pdf/1809.06421.pdf)
    
* *Whiteboard Crypto* \[2021\] Quadratic Funding - Crypto Charity that SUPERCHARGES donations. [Link](https://youtu.be/LrdG-pZw2Fc)