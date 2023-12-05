LAB 4:
You must do the project individually. In this HW you will design a backdoor detector for
BadNets trained on the YouTube Face dataset using the pruning defense discussed in
class. Your detector will take as input:
1. B, a backdoored neural network classifier with N classes.
2. Dvalid, a validation dataset of clean, labelled images.

What you must output is G a “repaired” BadNet. G has N+1 classes, and given unseen test
input, it must:
1. Output the correct class if the test input is clean. The correct class will be in [1,N].
2. Output class N+1 if the input is backdoored.
You will design G using the pruning defense that we discussed in class. That is, you will prune
the last pooling layer of BadNet B (the layer just before the FC layers) by removing one
channel at a time from that layer. Channels should be removed in decreasing order of average
activation values over the entire validation set. Every time you prune a channel, you will
measure the new validation accuracy of the new pruned badnet. You will stop pruning once the
validation accuracy drops atleast X% below the original accuracy. This will be your new
network B'.
Now, your goodnet G works as follows. For each test input, you will run it through both B and
B'. If the classification outputs are the same, i.e., class i, you will output class i. If they differ you
will output N+1. Evaluat this defense on:
1. A BadNet, B1, (“sunglasses backdoor”) on YouTube Face for which we have already
told you what the backdoor looks like. That is, we give you the validation data, and
also test data with examples of clean and backdoored inputs.

**To run the code:** Go to the Lab_assignment.ipynb and run all the cells sequentially. You can access all the bad net models, data as well as the repaired net models in the following below Drive link:
[Drive Link](https://drive.google.com/drive/folders/1sxI0e2QlYM1QeYfvaavBnXdBoHmQJl2u?usp=sharing)

I have received various test accuracies while testing on the clean datasets with the “pruned” version of the bad nets which were given from the 2020 hacks git repository. We have used the pruning technique to remove the affected layers in the given bad neural networks which changes the behavior for some particular output classes. Pruning is an important technique in deep learning which will also help in reducing the complexity in terms of the time and space complexity which mainly reduces the number of parameters because we will be dealing with so many parameters once it reaches the final layer of the neural network.
Plot representing accuracy vs attack success rate for the validation dataset:
The Attack Success rate when the accuracy drops at least 30% is 6.954.
 
For the repaired net, which is by pruning out the bad net model by 2%, 4% and 10%, we received test accuracies as well as the attack rate for the following 3 repaired net models we have trained:
Performance of the Repaired Net:
For combined Good net models:
Combined 2% drops model, the clean test data Classification accuracy: 95.90023382696803
  
Combined 2% drops model, Attack Success Rate: 100.0
Combined 4% drops model, the clean test data Classification accuracy: 94.77007014809041 Combined 4% drops model, Attack Success Rate: 99.98441153546376
Combined 10% drops model, the clean test data Classification accuracy: 84.54403741231489 Combined 10% drops model, Attack Success Rate: 77.20966484801247


  
