XML. Home Work 1
===============
1\. Prepare XML schema (XSD)
---------------
You have to prepare XML schema for the following elements hierarchy:
```
Book Shelf:
    id:
        value
    tag_1
    tag_2
    tag_3
    ...
    tag_n               (tag value 64 chars max)
    book_1
    book_2
    book_3
    ...
    book_n:
        id:
            value
        author:
            name        (64 chars max)
            surname     (128 chars max)
            email       (256 chars max, should be valid email)
        title:
            value       (256 chars max)
        description:
            value       (2048 chars max)
        ISBN:
            value       (should be valid ISBN13 code)
        number_of_pages:
            value       (should be positive integer)
    periodical_1
    periodical_2
    periodical_3
    ...
    periodical_n:
        id:
            value
        publisher:
            title       (64 chars max)
            email       (256 chars max, should be valid email)
        title:
            value       (256 chars max)
        description:
            value       (2048 chars max)
        ISSN:
            value       (should be valid ISSN8 code)
        number_of_pages:
            value       (should be positive integer)
        issue_number:
            value       (should be positive integer)
```

### Book shelf
The book shelf described above could have both books and periodicals,
but could be empty too.

Book shelf could have any number of tags associated with the shelf.

The only required field that **must** be filled is shelf id.

#### Tag

Tag should always have `value` attribute with its value, like:
```xml
<tag value="tag1"/>
```
Tag content value should be always `0` and only `value` attribute should be allowed.

Value attribute length should be not more than 64 characters.

#### Book

Book **must** have following fields filled:
* id
* ISBN
* author:
    * name
    * surname
* title

Other fields could be empty.

#### Periodical

Periodical **must** have following fields filled:
* id
* ISSN
* publisher:
    * title
* title
* issue_number

2\. Valid and invalid test XML documents
-----------

You have to prepare 2-3 test XML documents with at least one valid and
one invalid document, that **must** be valid against created XSD.

3\. Entities
-----------

You have to create Java POJO classes that will represent your XML structure.

Classes should be valid POJO (all fields are private, every field has getter and setter).

In addition - override `equals` and `hashcode` for the entities:
* Books should be compared using ISBN
* Periodical should be compared using ISSN
* Tags should be compared using their text
* Publishers should be compared by title
* Authors should be compared by name-surname pair

Try to avoid code duplication.

4\. DOM Parser
-----------
You have to create DOM Parser for the proposed XSD schema in order to be 
able to parse XML documents into the Java POJO representation.

#### *Optional* task

Add reverse implementation - create DOM structure from the Java POJO representation in order to
save valid XML document.
