---
title: "Chainlink's solutions for decentralized governance challenges"
datePublished: Mon May 15 2023 16:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clhp2aa6g03t0l7nv4w1k38nj
slug: chainlinks-solutions-for-decentralized-governance-challenges
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1684037963809/04481677-18e7-4ae2-a108-1d41716ad9f9.jpeg
tags: blockchain, web3, chainlink, daos

---

In our previous article, we discussed how Decentralized Autonomous Organizations (DAOs) can be [centralized](https://daotimes.com/the-centralization-paradox-of-decentralized-autonomous-organizations-daos/) and how [bad actors](https://daotimes.com/an-interview-with-a-dao-money-grabber-how-they-are-draining-treasuries/) within the DAO can cause significant harm. While these challenges exist, there are still potential solutions to address them.

In this article, we will discuss how DAOs can benefit from using Chainlink's data and computing services. We will first outline the challenges of decentralized governance, including token ownership concentration, low participation and high costs, unmanageable proposals, and unreliable execution of DAO functions. Then describes how Chainlink helps solve these challenges by providing various services, such as Chainlink Keepers for reliable DAO execution, Chainlink Data Feeds for rewarding the right contributors, and Chainlink VRF for random sample voting, Chainlink Any API and Keepers can be used to relay off-chain votes on-chain, and Chainlink oracles can reduce proposal spam through off-chain voting mechanisms. Additionally, we will explore some examples of DAOs that utilize Chainlink to gain a better understanding of how this technology can be applied in practice.

# Challenges of Decentralized Governance

Decentralized governance relies on governance tokens, on-chain voting, and open access to proposals. However, additional support is often necessary to ensure that the DAO is secure against bad actors and remains decentralized. Here are a few challenges with basic DAO governance structures:

* **Token Ownership Concentration:** In a simple token governance model, one token equals one vote. This can result in a single DAO member or a small group of members having too much influence and centralizing control over the DAO.
    
* **Low Participation and High Costs:** For a DAO to be decentralized, many members must participate in votes. However, if only a small percentage of token-holding members participate in votes, decision-making is controlled by only a few members. On-chain voting can make this worse by adding transaction fees that can become expensive during times of high network activity.
    
* **Unmanageable Proposals:** Open proposals can attract spam and detract attention from important ones. Poorly structured proposals and unrelated topics can undermine the DAO's ability to execute.
    
* **Unreliable Execution of DAO Functions:** DAOs need to ensure that passed proposals are executed reliably. This requires directly tying a passed vote to the execution of a particular smart contract function, creating a single point of failure.
    

# How Chainlink Powers DAO Transparency and Decentralization

DAOs are in the early stages, often blockchain-based and fully online, offering various services. [Chainlink](https://chain.link/) provides secure data and computing services for DAOs, with examples of how they help in the present and future as DAOs become more integrated with the real world.

* **Solving Unreliable DAO Execution With Chainlink Keepers:** DAOs are becoming increasingly complex, but Chainlink can help them create automated and decentralized processes from beginning to end. Chainlink Keepers can assist with common tasks such as rebalancing the treasury, staking or unstacking governance tokens, executing a function when a voting period ends, and dispersing governance token rewards over time. The issue with DAOs is that smart contracts cannot trigger themselves. Instead, an external entity must trigger a function in the smart contract when a vote passes. Chainlink Keepers can solve this by having professionals monitor the DAO vote and trigger the smart contract if the vote passes.
    
* **Awarding the Right Contributor With Chainlink Data Feeds:** As DAOs become more connected with the real world, they can track behavior outside the blockchain to create a strong token governance system that rewards members who carry out the mission. For example, Reforestation DAO wants to use its treasury to reforest land around the world. Members get a part of the budget to organize reforestation projects. To make the token governance system work, the DAO needs to monitor outside activity. Members who carry out their mission well get more power over the treasury through governance tokens. Chainlink Data Feeds can help. Reforestation DAO can use satellite pictures to measure success and send real-world data to the blockchain through Chainlink. This way, the right people get rewarded for helping the DAO's mission.
    
* **Random Sample Voting With Chainlink VRF:** Voting is a complex issue, whether on-chain or off-chain. To ensure a democratic process, a large number of people must participate. One solution is random sample voting, where a group of DAO members is randomly selected to vote on a proposal. This simplifies reaching quorum requirements while still representing the larger group's opinion. However, randomized voting requires a secure on-chain random number generator (RNG) to ensure the selection process is fair and trustworthy. Chainlink VRF is a reliable on-chain RNG that has been tested over time and can be used for random sample voting. It is also useful in some dispute adjudication models, where a group of randomly chosen participants decides on a dispute, similar to a court jury. Verifiable randomness has many benefits for fairer voting processes.
    
* **Leveraging Chainlink Any API and Keepers to Relay Off-Chain Votes On-Chain:** Currently, DAO members pay a fee to vote on-chain, which can lead to lower participation when gas prices are high. This can prevent the DAO from making decisions that everyone agrees with. To solve this issue, Chainlink Any API can be used to monitor off-chain votes and securely send results to the blockchain. Chainlink Keepers can inform the smart contract of the voting outcome, which eliminates the cost of gas for voting. This benefits people with less influence in the DAO, as they can voice their opinions without paying fees. Using Chainlink services is a comprehensive solution that lowers gas fees while still ensuring that votes are recorded on the blockchain.
    
* **Reducing Proposal Spam Through Off-Chain Votes Using Chainlink Oracles:** Off-chain voting can filter out bad proposals and prevent proposal spam in DAOs by using multiple layers of proposals. To introduce an initial proposal, DAO members must first gather a certain number of votes. This requirement stops low-quality proposals or those submitted by bad actors from being part of an official vote. Off-chain voting mechanisms with on-chain delivery through Chainlink oracles minimize network costs while filtering out erroneous and malicious proposals.
    

# Examples of DAOs that Use Chainlink

* **OlympusDAO** integrated Chainlink VRF on Ethereum mainnet to ensure provably fair and transparent no-loss raffles on its decentralized financial reserve protocol. Chainlink VRF provides a secure random number generator that is tamper-proof and verifiable on-chain, ensuring that raffle drawings are not manipulated by outside entities. OlympusDAO also offers staking rewards through sOHM, which can be redeemed for OHM and delegated to the (3,3) Together raffle. Further integrations of Chainlink products, such as Chainlink Keepers, are being considered to automate supply rebases of sOHM.
    
* **MoonDAO**, a DAO sending two people into space, integrated Chainlink Verifiable Random Function (VRF) on the Ethereum mainnet to select the winning NFT Ticket to Space through a public draw. Chainlink VRF provides a tamper-proof and auditable source of randomness, creating a more transparent user experience. MoonDAO selected Chainlink VRF because it's based on cutting-edge academic research, supported by a time-tested oracle network, and secured through the generation and on-chain verification of cryptographic proofs that prove the integrity of each random number supplied to smart contracts.
    
* **BitDAO** integrated Chainlink's decentralized price oracles to optimize trading of BIT on DEXs and enable listing as collateral on DeFi platforms. Chainlink's high-quality data, blockchain-agnostic infrastructure, robust monitoring, and reputation for security and reliability make it the obvious choice for BitDAO's mission to support builders of the decentralized economy. The blockchain-agnostic platform allows proposals to its treasury that are voted upon by BIT token holders, including partnerships, swaps, and expansion via specialized autonomous entities.