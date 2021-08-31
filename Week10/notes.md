A. Uniswap uses an automated price discovery system
	1. User create liquidity pools to allow swaps 
	2. people can add liquidity to the pool and earn rewards

B. genisis operation
	1. Someone starts it all off with a transaction as the adress of the factory UTXO, and it contains the NFT that correctly identifies the UTXO
	2. In order to create a pool, a user creates a transaction with inputs of the liquidity being added as well as the Factory UTXO
	3. 3 outputs
		a. new created pool AB, contains the actuall liquidity of A and B and also contains identifying NFT. The datum also contains the amount of liquidity tokens that were created from adding
		   liquidity to the pool
		b. next output is the Uniswap Factory with same NFT that identifies it, and datum now contains new AB pool created
		c. last output goes to user who initially added liquidity and contains the newly created liquidity tokens
C. swap operations
	1. Lets say Bob wants to swap some of his A's for some B's, he creates a transaction with 2 inputs
		a. first input comes from Bob and the dataum contains how many A's he wants to swap
		b. second input is the AB pool he is swapping from and uses the Swap redeemer
	2. 2 outputs are created from these two inputs
		a. Bob recieves the corresponding amount of B's that he swapped for his A's
                 	I)   the amount of B's bob recieves in calcualed using the automated price discovery system
			II)  the rule is the product of the two tokens of the pools must never decrease when performing a swap
			III) The ratio of amount being swap should always be roughly the same if (Large amount being swapped can affect this)
			VI)  the fundamental fact of the pool containing an equal ratio of the two tokens in term of value has the natural affect of reflecting theses changes with the swap ratios
		b. Pool Ab now has updated liquidity values in datum 
D. Add operations
	1. someone provides pool with additional liquidity, two inputs
		a. the pool
		b. his added liquidity
	2. 2 outputs
		a. user recives corresponding amount of liquidity pair tokens
		b. Pools datum has new reflected liquidity value1
E. Remove operations (burning liquidty tokens)
	1. allows user to burn liquidity tokens to get back the actual pairs
	2. 2 inputs
		a. users liquidity tokens
		b. pool to be removed from
	3. 2 outputs
	  	a. user revieves appropriate value of A's and B's for their liquidity tokens
		b. pool with new updated values of liquidity in datum 		
D. close a pool
	1. only can happen when pool has no more liquidity tokens left
	2. lets say charlie wants to close pool AB, 3 inputs
		a. Factoroy adress that contains the pool to be closed
		b. the adress of the actuall pool AB
   		c. remaining liquidty tokens
	3. 2 outputs
		a. factory with updated list of pools
		b. charlies recieves remaining tokens from removing last liquidty 
