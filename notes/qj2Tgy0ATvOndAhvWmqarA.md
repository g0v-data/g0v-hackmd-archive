# zkEVM Design
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_206d67541192c47a11a691bcaac5daaf.png)
* The circuits are usually defined over prime fields of 254-bit size, so efficient range proofs are needed to ensure there is no overflow.
* zk-unfriendly opcodes like keccak hash function require a separate circuit which needs to be linked to the main circuit.
* what you are reading is the same as what you are writing. (more clarification needed)
eg: you can pop only those elements that were already pushed onto the stack.

The first 3 properties (efficient range proof, circuit connection, mapping) makes use of **lookup**. The 4th property (efficient on/off selectors) makes use of **custom gates**. Combining all the factors, **Plonkish** arithmetisation is the best choice.

zkEVM proof system:
* public input: world_state(t), world_state(t+1), transactions.
* witness: execution trace.

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2db6eec04e5128dc19b59ea5876ef8a0.png)
unroll the execution onto a table.
case switch sets 1 for the current opcode and 0 for the rest.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7e77c9cbf168f7088acc1174c59d69ba.png)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2a1b446fec2ae04d390f3f0e759837c4.png)
need to also prove that a & b in sADD are the values that were previously pushed to the stack (Read/Write consistency)
RAM circuit constrains that the table (opcode specific witness) is generated in the correct order.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_bb662033ef7a5af8fd53bdd1ee12850d.png)
how is the hash lookup table computed? hash circuit proves that the hash lookup table values are computed correctly. Soln: hash is computed as witness generation, the (input, hash) correctness is proved in the hash circuit

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5bfe58d3b4ee6ee53d0e1c3a4905a3ff.png)
zkEVM circuit is a set of specialized circuits connected by lookup tables. 

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_991dd01a9b75a7905261a60c2d4c761b.png)
use nova to prove for repeated keccak. 
original halo2 is not used because it is based on IAP over pasta curves. verification time O(log n) making it expensive, pasta curves not supported on ethereum. 

verification cost is linear in column number.
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6034e99459bc1e8b50e6ddf8748866b4.png)

aggregation layer can again be split into 2 layers -- first layer 23 columns, second layer 5 columns. It can be even reduced from optimisations from Axiom. (need clarification).

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_1506288577fd9f0b04e9b0227f2f0215.png)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_c16b26c77a737505206c45213df1ef31.png)
why is second layer more expensive even though it has much fewer columns?







### QUESTION?
* how is a custom gate degree computed?