# Overview of GEO Service Registry (GSR)

Each service in GEO Network can be registered and recorded in GEO Services Registry. This action is not mandatory, but services that are listed in GEO Service Registry will be placed in rating in case if it has at least 0.01 votes. Also, GEO Network token-holders will be able to vote for different service providers which are recorded in GSR.

GEO Services Registry — is an Ethereum smart-contract which stores information about services in GEO Network. When a participant of GEO Network wants to connect to any service provider, he should address the request to the GSR in order to get the IP-address of this particular service provider. 




**How does it work?**

_GSR participants interact as follows_: service providers who want to get into the rating submit their names to the table. At the same time, they explain to the GEO token-holders why they should delegate their vote to service providers. In case if the token holder decided to delegate tokens to the service provider, we call him Delegator. The Delegators, in turn, decide who they think are the best service providers and delegate their tokens to those.			
 
 The token quantity that is delegated to every service provider makes up his/her rating in the table. Based on this rating, participants can determine a good service provider and apply for him.


**In GSR following information is stored**:
1) Name of the participant
2) Participant's IP address. 
3) Type of the service it provides
4) Ethereum address. 
_It is very important because token holders will delegate tokens to a particular ETH address)[(check GVS description)](https://github.com/GEO-Protocol/specs-gsr/blob/master/specs/gvs.md)_
5) Any additional information.
  

**Functions of GSR**:
1) GSR is the registry of all registries. The main role of GSR is to store information about each service provider. All information is stored as one registry. However, token holder will be able to choose a service provider from the list, if provider correctly stated type of service it provides.
2) GSR records the IP-addresses of every service provider. Obtaining the IP-address of a service provider is the only way for the user to connect with this service provider.
3) GSR stores observer’s public keys from observers blockchain and any other information about the service provider. 

