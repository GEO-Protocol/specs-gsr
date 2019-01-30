# Overview of GEO Voting Service (GVS)

GEO Voting Service (GVS) is the Ethereum smart-contract which stores the information about all users who staked tokens, amount of tokens they staked and observers which user voted for. 
In GEO Network users are able to vote for any observer. To participate in voting, a tokens holder should stake some of his tokens and provide the system with the ETH address where tokens are staked. Information about both, address and amount of tokens user staked is recorded in GVS. 

**Voting goes as follows:**
1) User deposits tokens on GVS
2) The user chooses the list of the observers to vote for. Then, user is delegating some of his tokens to the observer(s). Also, if the user chooses more than 1 candidate to vote for, he is setting up the percentage of tokens he delegates to the particular candidate.

   _Thereby, if the user wants to vote for 3 different observers, he have to determine the amount of the total amount that will go to each candidate. 

3) Afterward, the system records that “...user A delegates n amount of tokens to the observer O...” which means that provider O received n amount of votes from user A.
   
   _The user is able to change the list of observers he votes for, as well as the amount of tokens he delegates to a particular candidate. There is no penalty predefined for these actions._
   
4) Every week, at the end of 7th day, the voting result is being concluded and the lists of observers are updating. After the update, each observer is arranged in the list considering the number of votes it received from users.
5) After the update, all delegated tokens return back to ETH address of that user, that delegated them to the service provider(s).

**Why should users delegate their tokens?**

Every observer has to raise their interest in a particular way. For example, a Delegator could be an application the users of which receive special services from a observer, and this motivates the application to delegate its vote to this observer. Or, a Delegator has an altruistic motivation, so he/she evaluates the quality of the services and then delegates his/her tokens to the best observer. Also, by analogy with other rating marketplaces based on decentralized technologies, observer can give away a part of their profits. Profit is a kind of user feedback about their satisfaction with the quality of the provider’s services.

**The user can take the following actions:**
- Deposit tokens and participate in the voting. If deposit = 0 then the user can not vote.

- Participate in voting during the token lockup period

- Vote for different service roles. At the same time, the user can delegate tokens to the provider, observer, state keeper, hub and other service roles.

- Vote for more than 1 candidate in each registry (the registry of observers, the registry of providers etc.). The user can vote for up to 20 different candidates, indicating the distribution of votes in percentages. 

- Change candidates and the amount of delegated tokens which were set up previously.

- Partially or completely withdraw tokens from the GVS.


