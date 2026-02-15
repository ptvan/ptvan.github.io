---
layout: post
title: Privacy and Data Safety
---

Data scientists are often tempted to dive into datasets as soon as we receive them. After all, in my experience, getting the data is usually the hardest part:
assay data requires waiting for experiments which are often slow, and demographic data rightfully requires institutional reviews before it can be accessed.
However with the continual rise in both data generation and [data breaches](https://privacyrights.org/data-breaches), it's interesting to think about the issues
surrounding data privacy and safety in both conceptual and practical terms. I was inspired to write this post by Katharine Jarmul's [Practical Data Privacy](https://practicaldataprivacybook.com/) book, which covered these topics very well.

### The importance of data privacy

The problem with data privacy in the information age is that even seemingly innocuous information can be used to identify you, and often this information is collected silently, continuously and without your consent.

While the idea of data needing to remain private might appear obvious, there are many nuances and considerations. Personally Identifiable Information (PII)'s legal definition includes things that we don't typically think of, like the identity of your employer. Maybe you don't mind people knowing that you worked for your uncle's restaurant one summer in college. But if you know an individual belongs to a particular group, you can use the individual's information to learn more about that group. A competing restaurant could figure out how much your uncle is paying his chefs, or who his grocer is, and if they used that information to push your restaurant out of business, I would guess your uncle would mind !

Handling data often involves striking a balance between privacy and accessibility: an inaccessible dataset is private, and vice versa. Some questions to ask yourself when addressing data privacy includes: how often does the data need to be accessed, how serious would a data breach be ?

### Common attack types

Some of the threats against data privacy include:

**Singling out attacks** focuses on gathering information about a single individual in a public dataset. Imagine you have a dataset on a company's employees with their names replaced with randomly-generated IDs. It's a safe bet that the individual with the highest salary is the CEO, but you can also identify specific individuals if you know for example, their gender, age and department. This attack can also be combined with the next attack.

**Linkage attack** links multiple data sources together to gain more information about individuals or re-identify them. One example of this is the Netflix Prize dataset which I [wrote about previously](https://ptvan.github.io/recommender-systems/), which when combined with IMDB data could identify specific individuals.

**Attribute privacy attack** attempts to learn information about individuals belonging to the same group. Facebook likes are a strong determinant of sexual orientation, gender and political affiliation. An extension of this type of attack is _membership inference attack_ where the attacker trains a _shadow model_ closely resembling the real model that determines if an individual belongs to a group or not. A Generative Adversarial Network (GAN) trains a _discriminator_ that infers if a datapoint belongs in the original training data.

**Model-inversion attack** identifies individuals by exploiting machine learning models. For example, suppose you have access to a facial recognition API. You can use a search method that maximized activation to return an image that closely resemble a specific person in the training set.

### Processes and tools to improve data privacy

Data privacy can include _data loss prevention_, measuring inbound and outbound traffic to detect if sensitive data is being exfiltrated without authorization.

The most basic approach to improve privacy is **pseudonymization**, including **masking** (replacing PII with a randomly chosen string), **table-based tokenization** (replacing sensitive values with a corresponding entry from a look up table), **hashing** and similarly **format-preserving encryption**.  

These techniques come with some drawbacks: table-based tokenization may run into collisions if you combine multiple datasets, hashing may remove too much information for the data to be useful. But the most serious drawback is psychological: pseudonymization gives a false sense of security, and only really applicable when the data will only be used internally by a small number of analysts. Some implementations of pseudonymization are [Hashicorp Vault](https://www.hashicorp.com/en/products/vault), its open-source derivative [OpenBao](https://openbao.org/), and [Akeyless](https://www.akeyless.io/). [Presidio](https://github.com/microsoft/presidio) provides a quick way to programmatically detect PII in text then anonymize it.  

A more sophisticated privacy tool is **differential privacy (DP)** developed by Cynthia Dwork and her colleagues. The US Census Bureau used differential privacy for the 2020 Census.

Like any system, DP has its shortcomings. It has been shown that if you know the distribution DP draws from and the DP implementation takes no special steps in ensuring that it is generating truly random noise (a well-known problem for computers), information can be gained about datasets that had undergone DP.

Some of the data privacy concerns involve having data being concentrated at a single source. **Federated learning** can address some of these issues by sending the centralized model to each individual device that performs data collection and training the model on those devices before sending model updates back to the central server and aggregating.

### Further reading

The Flower framework has a good [explanation of federated learning](https://flower.ai/docs/framework/tutorial-series-what-is-federated-learning.html).

Battista Biggio has done a lot of work on [machine learning attacks](https://battistabiggio.github.io/publications/).
