# Request structure

## URL Structure

The URL is a sentence, where HTTP methods \(GET, POST, DELETE, PUT\) are **verbs **and resources are **nouns**.

Examples: Creating a new Manager

Good

* POST`/organizations/:id/managers` 
  * A Verb \(post\) + nouns.

Bad

* POST `/organizations/:id/createManager` 
  * Erroneous use of verb instead of a noun \(createManager\).



