STATE MACHINES
State machine representation in blockchain:
State machine represented by UtxO sitting at state machine script address
State represented by datum of UtxO
Transition will be a transition that consumes current UtxO using a redeemer that characterizes that transition and produces a new UtxO sitting at script address with the datum reflecting the new state

Plutus.Contract.StateMachine

Data StateMachine s i
S -> datum
I -> redeemer
Constructors
smTransition :: State s-> i -> Maybe (TxConstraints Void Void, State s)
State s: stateData :: s (datum) stateValue :: Value (value of datum)
If transition not allowed, return nothing
Otherwise return tuple where State s is new datum and value
txConstaints can specify other constraints that transition may have

smFinal :: s -> Bool
Final state so does not produce new UtxO, just ends

smCheck :: s -> Bool
Additional checks that can’t be expressed with txConstraints

smThreadToken :: Maybe ThreadToken
Pinpoints right UtxO that contains the right NFT
Automatically mints NFT and threads it through state transitions

Data StateMachineClient s i

scInstance :: stateMachineInstance s i
Used to interact w wallet from our contract monad

stateMachine :: StateMachine s
typedValidator :: TypedValidator (StateMachine s i)

scChooser :: [onChainState s i] -> Either SmContractError (OnChainState s i)
mkStateMachineClient :: stateMachineInstance
scChooser used for picking right UtxO when you don’t use the nft thread
