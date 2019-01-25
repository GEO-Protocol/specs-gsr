# Overview of GEO Service Registry (GSR)

Each service in GEO Network should be registered and recorded. Otherwise, there would be no possibility for users to reach this service. GEO Service Registry is the Ethereum smart-contract which stores information about every service in GEO Network. When a user wants to start using service of any provider, he should address the request to the GSR in order to get the IP-address of this provider.


**How does it work?**

_GSR participants interact as follows_: service providers who want to get into the rating submit their names to the table. At the same time, they explain to the GEO token holders why the latter should delegate their vote to them. The Delegators, in turn, decide who they think are the best service providers and delegate their tokens to those.	

_All tables, except the Observers table, function as follows:_ the token quantity that is delegated to every participant makes up his/her rating in the current table. Based on this rating, participants can determine a good service provider and apply for their services.

**In GSR following information is stored**:
1) Name of the participant
2) Participant's IP address. 
3) Type of the service it provides
4) Ethereum address. 
  _It is required because users will need to delegate their staked tokens in order to vote for a particular candidate ([check GVS description](https://github.com/GEO-Protocol/specs-gsr/blob/master/specs/gns.md)
5) Observer’s public keys. 
  _In case if the participant is playing the role of observer_

**Functions of GSR**:
1) GSR is the registry of all registries. The main role of GSR is to store information about each service provider. Different service providers will form different registries considering the service they provide. Thereby, there will be different registries for providers, observers, state keepers, hubs and market makers
2) GSR records the IP-addresses of every service provider. Obtaining the IP-address of a service provider is the only way for the user to connect with this service provider.
3) GSR stores observer’s public keys 

