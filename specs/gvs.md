# Overview of GEO Voting Service (GVS)


GEO Voting Service or GVS is the Ethereum smart-contract which stores the information about all token holder who delegates  tokens, amount of tokens they delegate and service providers they voted for. Moreover, smart-contract also keep delegated tokens, so token holders need to deposit tokens on GVS to be able to vote.					

In GEO Network the delegator is able to vote for any of service providers. It could be a provider, observer, state keeper or any other service role.


**Voting goes as follows:**
1) Token holder deposits tokens on GVS
2) The token holder chooses the list of the service providers to vote for. He should choose the type of service and certain Ethereum address. Then, the token holder is delegating some of his tokens to the owner of this Ethereum address. Also, if the token holder chooses more than 1 candidate to vote for, he is setting up the percentage of tokens he wants to delegate to certain candidate.

   _Thereby, if the token holder wants to vote for provider A, provider B, and provider C, he will have to determine the percentage of the total amount that will go to a specific candidate._

3) Afterward, the system records that “...token holder A delegates n amount of tokens to the provider B...” which means that provider B received n amount of votes from token holder A.
   
   _The token holder is able to change the list of service providers he votes for, as well as the percentage of tokens he delegates to a certain candidate. There is no penalty predefined for these actions._
   
4) Every week, at the end of 7th day, the voting result is being concluded and the lists of different service roles are updating. After the update, each service provider is arranged in the list considering the number of votes it received from token holders.

The percentage that delegator set up for previous week will stay unchanged unless token holder deposit, withdraw or rearrange tokens he staked on GVS.

**The token holder can take the following actions:**
- Deposit tokens and participate in the voting. If deposit = 0 then the token holder can not vote.

- Participate in voting during the token lockup period

- Vote for different service roles. At the same time, the token holder can delegate tokens to the provider, observer, state keeper, hub and other service roles.

- Vote for more than 1 candidate in each registry (the registry of observers, the registry of providers etc.). The user can vote for up to 20 different candidates, indicating the distribution of votes in percentages. 

- Change candidates and the percentage of delegated tokens which were set up previously.

- Partially or completely withdraw tokens from the GVS. In case if the token holder decides to partially withdraw tokens, then the number of votes recounts, but the percentages remain unchanged


