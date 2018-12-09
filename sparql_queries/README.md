# SPARQL Queries

The following SPARQL Queries are our first attempts to infer answers to our competency questions.

#### Accuracy & Misclassified Attributes
These queries are for the competency question, “What type of image attributes does the model have the most trouble classifying?" This query calculates the accuracy of images across a result set. It can be modified with image/person restrictions to calculate accuracy across images with a specific conditions (Long Hair, mug shots, etc.). Note for our current data, we have generate classification results artificially - FaceNet and DLib will have a 50% accuracy such that when one misclassified an image the other will identify it correctly.


#### Accuracy (Long Hair)
This is the query for the competency question, “Which of these two models is better at classifying people with long hair?"


#### Mugshot
This is the query for the competency question, “How well would my model work at classifying mugshot photos?" The query below returns the image IRI and the depicted persons name for every image that is inferred by the ontology to be a mugshot photo. Because this query relies on the inferencing in our ontology it can only run in the Snap SPARQL Query, which when a reasoner is run generates the extra inferred triple: image rdf:type MugShotPhoto. In the future we plan to run an inference engine to generate these triples and include them in our triple store.


#### Occlusion Accuracy
This is the query for the competency question, “What part of the face does my facial recognition model depend on the most?” What the query actually grabs is the accuracy rate for all sources of occlusion in the individuals that are used, along with the type of the occlusion source object. From here, we can use a seperate description logic inferencing software to connect the type of the occlusion source to the body region being occluded and so answer the question.


#### George W. Bush
This is the query for the competency question, "What type of image attributes does the model most associate with George W. Bush?" Since the model test results are known, we can link them to our “smart” images that contain attribute tagging. From this we can look at all the images of George W. Bush that were classified properly using the LFW ground truth and count which attributes occur more frequently by running a SPARQL query counting the number of occurrences of each attribute in images that were classified as "George W. Bush" by the user’s model - for instance, “wearing necktie”. Then, using our ontology’s taxonomy structure for attributes, we can determine that this attribute is a type of “wearable.” We then display the results of these queries using the hierarchy view as mentioned before, only this time instead of showing the accuracy statistics and percentages we show the accumulated number of images that the model has classified as George W. Bush and contains one or more of the associated attributes (or sub attributes). The user is then able to look at the hierarchy to determine which attributes are most associated with George W. Bush at the level of detail that they are interested in. This query could work for any attribute we (using the Kumar features) or the model have tagged, be it the person’s name or an image attribute.