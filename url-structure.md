# Request structure

## URL Structure

The URL is a sentence, where HTTP methods \(GET, POST, DELETE, PUT\) are **verbs **and resources are **nouns**.

Example: Creating a new Manager into an Organization

Use this

* POST`/organizations/:id/managers` 
  * A Verb \(post\) + nouns.

Do NOT use this

* POST `/organizations/:id/createManager` 
  * Erroneous use of verb instead of a noun \(createManager\).



