# Question Bank (Beta)

Note: this is currently a beta feature. To give feedback, contact us at [beta-feedback-questionbank@cardz.tech](mailto:beta-feedback-questionbank@cardz.tech).

Documentation is also in the beta stages and subject to major revisions before the final edition is published.

## Summary

The Question Bank is a new feature of Cardz that inegrates a slightly different type of machine learning pipleine in order to generate thousands of question - and answers - at a time. 

This allows our users to access a wide variety of content on any subject - even unfamiliar ones.

## Usage

The Question Bank is available by pressing the 'QBank' link in the header at any time within Cardz. You can also directly access it from [this link](https://app.cardz.tech/q).

## Data organization

### Questions
Questions are generated from content, usually in bstches of thousands at a time. Each question includes three answers that are also generated.

When you click 'check answers', we originally check against the answer with the highest probability of being correct. If you think this is wrong, we can also perform a check against the other two answers.

Since this system depends of machine learning, there is always an element of error. Therefore, we check answers by performing sentence similarity analysis with the answer that you supply and the one within our records. A difference of one or two letters should still be accepted as correct.

You can convert a question into a flashcard at any time. Note that you will not be able to edit this flashcard, as it is not created by your user account but instead by the system.

### Collections

Accessed by path `/q/<collection_id>/set/<set_number>`.

We generate questions from content sourced from the Internet under appropriate licenses. Due to the way our question generation works, usually thousands of questions are generated from small pieces of content, such as a couple of Wikipedia articles.

Therefore, every question that is generated from a piece of content goes into a collection specific to that piece of content. Collections include information such as:

- A title
- A short description
- Information about the generation process

### Sets

Since collections have hundreds, if not thousands of questions, we split them into sets. Each set has 10 questions within it. 

This means you can refer to a specific set of questions easier, for example with the link [https://app.cardz.tech/q/BGMMFrI7r6jHJa19bBHg/set/327](https://app.cardz.tech/q/BGMMFrI7r6jHJa19bBHg/set/327) which refers to the 'VCE Biology' collection, set #327.

You can complete and check questions in sets.

## Access

You can see the list of collections and the details about each individual collection without signing in. 

Viewing and checking questions requires you to have a Cardz account.