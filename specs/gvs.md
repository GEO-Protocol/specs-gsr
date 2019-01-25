# Overview of GEO Voting Service (GVS)

GEO Voting Service or GVS is the Ethereum smart-contract which stores the information about all users who staked tokens, amount of tokens they staked and service providers which user voted for. 
In GEO Network users are able to vote for any of service providers. It could be a provider, observer, state keeper or any other service role. To participate in voting, a user should stake some of his tokens and provide the system with the ETH address where tokens are staked. Information about both, address and amount of tokens user staked is recorded in GVS. 

**Voting goes as follows:**
1) User deposits tokens on GVS
2) The user chooses the list of the service providers to vote for. Then, user is delegating some of his tokens to the service provider(s). Also, if the user chooses more than 1 candidate to vote for, he is setting up the percentage of tokens he wants to use for voting for the particular candidate.
    _Thereby, if the user wants to vote for provider A, provider B, and provider C, he will have to determine the percentage of the total amount that will go to a particular candidate._
3) Afterward, the system records that “...user A delegates n amount of tokens to the provider B...” which means that provider B received n amount of votes from user A.
    _The user is able to change the list of service providers he votes for, as well as the percentage of tokens he delegates to a particular candidate. There is no penalty predefined for these actions._
4) Every week, at the end of 7th day, the voting result is being concluded and the lists of different service roles are updating. After the update, each service provider is arranged in the list considering the number of votes it received from users.
5) After the update, all delegated tokens return back to ETH address of that user, that delegated them to the service provider(s).

**Why should users delegate their tokens?**

Every service provider has to raise their interest in a particular way. For example, a Delegator could be an application the users of which receive special services from a service provider, and this motivates the application to delegate its vote to this service provider. Or, a Delegator has an altruistic motivation, so he/she evaluates the quality of the services and then delegates his/her tokens to the best service provider. Also, by analogy with other rating marketplaces based on decentralized technologies, Service providers can give away a part of their profits. Profit is a kind of user feedback about their satisfaction with the quality of the provider’s services.

**The user can take the following actions:**
1) Deposit tokens and participate in the voting. If deposit = 0 then the user can not vote.
2) Participate in voting during the token lockup period
3) Vote for different service roles. At the same time, the user can delegate tokens to the provider, observer, state keeper, hub and other service roles.
4) Vote for more than 1 candidate in each registry (the registry of observers, the registry of providers etc.). The user can vote for up to 20 different candidates, indicating the distribution of votes in percentages. 
5) Change candidates and the percentage of delegated tokens which were set up previously. 
6) Partially or completely withdraw tokens from the GVS.


