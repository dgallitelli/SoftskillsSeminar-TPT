![paristech](./images/paristech.png)

# Softskills Seminar - Mining High-Speed Data Streams

## Abstract

In this paper by Pedro Domingos and Geoff Hulten from the University of Washington it is discussed how standard knowledge discovery systems are limited in multiple factors and should not be used to extract knowledge and patterns from *big streaming data*, mainly due to memory limitations. New KDD systems should operate continuously and indefinitely, incorporating examples as they arrive and making predictions at any moment in time. Thanks to the statistical certainty given by the *Hoeffding Bound*, it is possible to build a new model, the *Hoeffding Decision Tree*, which is built incrementally and is asymptotically similar to a batch tree built on the same training dataset, with a controllable margin of error. The Hoeffding Tree is finally implemented in the *VFDT (Very Fast Decision Tree) system*, which basically extends the Hoeffding Tree with enhancements for pratictal use. Finally, some empiric results of VFDT are shown.  

## Introduction

WIP

## Hoeffding Tree

Hoeffding Trees are born from the limitations of classical decision tree learners, which assume all training data can be simultaneously stored in main memory. Hoeffding trees are based on the assumption that, in order to find the best attribute at a node, it may be sufficient to consider only a small subset of the training examples that pass through that node. Given a stream of examples, the first ones will be used to choose the root test; once the root attribute is chosen, the succeeding examples will be passed down to the corresponding leaves and used to choose the appropriate attributes there, and so on recursively.

Deciding exactly how many examples are necessary at each node is still a critical point in building this kind of model. This can be done by using a statistical result known as the Hoeffding bound, which states that:

>Suppose we have made n independent observations of a variable *r* with domain *R*, and computed their mean *x*. The Hoeffding bound states that, with probability *1 - delta* , the true mean of the variable is at least *x - epsilon*, where:
>\[\epsilon = \sqrt\frac{R^2 \ln(1/\delta)}{2n}\]

Let's consider the following example.

![HT_example](./images/HT_example.png)

Let *G(x)* be the heuristic measure of choice, such as *Information Gain* or *Gini Index*. Once a new example arrives is read from the data stream, the chosen heuristic measure is computed for the attributes, and the two best attributes are selected. Then, a condition on the *G* values is checked:

\[\Delta \bar{G} = \bar{G}(X_a) - \bar{G}(X_b) > \epsilon \]

If the condition is met, then a new child node is created based on the best attribute. Otherwise, a new example is read from the stream.

This way, the decision tree is built incrementally, with each example requiring to be read *at most once*. The statical properties of the Hoeffding bound implies that, with high probability, a Hoeffding tree is asymptotically identical to the decision tree built by a batch learner. These characteristics make the Hoeffding Tree suitable for data stream mining, since it takes a constant time to learn an instance, and it can make class prediction in parallel. 

## Very Fast Decision Tree

WIP

## Results and conclusion

WIP

## Discussion

WIP
