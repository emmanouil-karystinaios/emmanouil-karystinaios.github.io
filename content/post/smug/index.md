# From Notes to Insights: Visualizing Graph Neural Network Explanations with SMUG-Explain

Graph Neural Networks (GNNs) are making waves in the world of Music Information Research (MIR). From predicting cadences to generating expressive performances, these networks are unlocking new potentials in understanding and processing musical scores. But there’s a catch — their complex, “black-box” nature makes them hard to interpret. That’s where SMUG-Explain comes in. This innovative framework is designed to generate and visualize explanations for GNNs applied to musical scores. Let’s dive into how SMUG-Explain works, its application in cadence detection, and its potential to bring AI and musicology closer together.

![Graph Score Explainer Pipeline](./figs/image(4).png "")

## The Challenge: Understanding GNNs in Music

GNNs are fantastic at capturing intricate relationships in graph-structured data, which is perfect for tasks like cadence detection and voice separation in music. However, they’re notoriously difficult to interpret. For musicians and researchers, this opacity can be a big problem. Imagine having a super-smart assistant who helps you analyze music but never explains why it made certain decisions. Frustrating, right?

Enter SMUG-Explain, or Score MUsic Graph Explain. This is a framework for interpreting GNNs applied to music but it also integrates these explanations directly into the musical scores. By visualizing how each note and its features contribute to the model’s predictions, SMUG-Explain makes GNNs more transparent and understandable.

## How Does SMUG-Explain Work?

### Graph-Based Representation of Musical Scores

SMUG-Explain transforms a musical score into a graph where notes are vertices, and edges represent their temporal relationships. It uses four types of edges:

- Onset edges: Connect notes that start together. 
- Consecutive edges: Link notes where one ends as the next begins. 
- During edges: Connect notes that occur within the duration of another note. 
- Rest edges: Connect notes across rests.


![Score Graph Example](./figs/Example_Score.png "In this example, we view the score graph on an excerpt of a Perfect Authentic Cadence (PAC) with harmonic annotations written in Roman numerals.")

### Explanation Techniques

SMUG-Explain employs several post-hoc, gradient-based explanation methods such as Saliency, Integrated Gradients, Deconvolution, and Guided Backpropagation. These techniques evaluate the importance of each note and its features in predicting specific musical events, such as cadences. Additionally, these methods allow us to derive attribution weights for every edge in the input graph. By selecting the top-k most important edges, we can construct an explanation subgraph that highlights the critical components influencing the model’s predictions.

### Evaluation of Explanations

The quality of an explanation is assessed using fidelity metrics. For each explanation subgraph, the underlying cadence prediction model is run on the subgraph alone or on the input graph without the explanation subgraph. If the correct cadence label can be predicted using only the explanation subgraph, the explanation is deemed sufficient. Conversely, if the label changes when the input graph is used without the explanation subgraph, the explanation is considered necessary. An explanation that is both necessary and sufficient achieves a perfect fidelity score, indicating it provides a comprehensive and accurate insight into the model’s decision-making process.

## Interactive Visualization

The framework features an interactive web interface built with the Verovio music engraving library. Users can click on individual notes to see the subgraphs that most contribute to the model’s predictions and the feature importance of each note. This interface not only makes the explanations accessible but also aligns them with traditional music notation, making it easier for musicians and researchers to understand.


## Real-World Applications: Mozart to Chopin

### Mozart’s Piano Sonata K280

In an excerpt from Mozart’s Piano Sonata K280, the underlying GNN analysis model accurately identified a perfect authentic cadence. Using the SMUG-Explain framework we can see that the explanations outline the descending melodic line and the bass arpeggiation leading to the cadence, aligning closely with traditional harmonic analysis. This example highlights the framework’s potential to support musicological research.

![Mozart's Piano Sonata K280](./figs/smug.gif "Potential reduction process of Smug-Explain. PAC indicates the predicted arrival point of the cadence.")

When we isolate the explanation and apply a reduction process, retaining only the subgraph involved in the explanation, we are left with the essential structure of a textbook harmonic Perfect Authentic Cadence (PAC). This streamlined subgraph highlights the critical notes and relationships that define the PAC. While this process shows how SMUG-Explain can break down complex musical structures into their core elements, due to the complexity of musical reduction it isn’t a built-in feature just yet.

### Chopin’s Nocturne in C Minor

In Chopin’s Nocturne, SMUG-Explain correctly identified a complex cadence despite unconventional voice leading. The explanation subgraph included notes from earlier measures, indicating the model’s consideration of long-range musical dependencies, much like human musicological analysis. Notice how the explanation highlights the first chord in the first measure probably as an indication of the key.

![Chopin's Nocturne in C Minor](./figs/choping_smug.webp "Explanation of the cadence detection in Chopin's Nocturne in C Minor.")

## Future Directions

SMUG-Explain is paving the way for making GNNs in music more interpretable and user-friendly. Future work will focus on developing new explanation techniques tailored to musical data, enhancing user-based evaluations, and making the framework more accessible through online platforms.
Limitations of SMUG-Explain

While SMUG-Explain represents a significant step forward in making Graph Neural Networks (GNNs) more interpretable in the context of musical scores, it is not without its limitations. Understanding these constraints is crucial for setting realistic expectations and guiding future improvements. Here are some key limitations of the SMUG-Explain framework:

#### 1. Model Dependence

An important limitation of SMUG-Explain lies in its dependence on the underlying GNN model used for cadence detection. Since SMUG-Explain employs post-hoc explanation methods, the accuracy and quality of its explanations are directly tied to the performance of the cadence detection model.

The explanations generated by SMUG-Explain are only as good as the predictions made by the cadence detection model. If the underlying model has poor accuracy or fails to capture essential musical elements, the explanations provided will reflect these shortcomings. This means that any inaccuracies or biases in the model will be present in the explanations, potentially leading to misleading insights.

The performance of the cadence detection model depends heavily on the quality and comprehensiveness of the training data. If the training dataset lacks diversity or contains errors, the model’s ability to generalize to new pieces will be compromised. Consequently, the explanations generated for these predictions may not be reliable or musically meaningful.

Some musical compositions, especially those with complex structures and unconventional harmonies, might pose significant challenges for the cadence detection model. If the model struggles with these complexities, the explanations provided by SMUG-Explain may fail to accurately represent the underlying musical relationships, leading to incomplete or incorrect interpretations.

#### 2. Complexity of Graph Constructions

Creating accurate graph representations of musical scores is inherently complex. While SMUG-Explain uses onset, consecutive, during, and rest edges to model relationships between notes, this approach might not capture all the nuances of a musical piece. Elements like dynamics, articulations, and tempo changes are not explicitly represented in the current graph model, potentially overlooking important musical information.

#### 3. User Experience and Accessibility

Although the interactive interface of SMUG-Explain makes it accessible to users, it still requires a certain level of technical proficiency to operate effectively. Users need to be familiar with both music theory and the technical aspects of GNNs to fully leverage the framework. Additionally, the current implementation relies on local deployment, which might be a barrier for widespread use. An online, server-based version could enhance accessibility but has yet to be developed.

#### 4. Interpretation of Explanations

While SMUG-Explain provides visual explanations that align with traditional music notation, interpreting these explanations still requires a deep understanding of music theory and machine learning. The explanations might not be immediately intuitive to all users, particularly those without a background in musicology or computational music research.

## Conclusion

SMUG-Explain bridges the gap between the sophisticated world of GNNs and the nuanced demands of musicology. By providing clear, interactive explanations directly within the context of musical scores, it empowers users to understand and trust the decisions of AI models, paving the way for more effective and insightful musical analyses.

If you’re intrigued and want to explore SMUG-Explain further, check out the code on [GitHub](https://github.com/manoskary/SMUG-Explain) or [read the paper](https://arxiv.org/abs/2405.09241). Dive in and discover how AI can illuminate the intricate beauty of musical compositions.

## Acknowledgments

I extend my gratitude to Francesco Foscarin, co-author of the original paper, for his invaluable assistance with the writing of this blog post and for providing some of the graphics.
