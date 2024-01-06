---
tags: disinfo
---
# 零時資訊傳播資料標準 0archive Data Standard

## Language

The key words MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, and OPTIONAL in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

## Glossary

* Producer
* Publication
* Author
* Dataset compiler

> All "identifier" fields in the followings may be a "localized" identifier for the entity issued by the publisher of the data set.  They can be anonymized through reindexing or hashing algorithms.  Such a localized identifier should be prefixed with an identifier of the publisher in an [org-id](http://org-id.guide/)-like practice.

## Classes and properties

### Producer

The Producer class should have the following properties:

* **id**: a unique identifier within the scope of this dataset for the content producer.
* **name**: a name of the company, organization, discussion board, social network profile, or other kinds of information channel that produces contents.
* **alternate names**: shorter names, abbreviates, names of the producer in various languages of the producer that are in common use.
* **identifiers**: ways to identify the producer, such as its legal entity if there is one, its tracking IDs used in services such as Google Analytics, or others. 
* **description**: a short description of the content producer given by the dataset compiler.
* **classification**: the classification of the content producer given by the dataset compiler.
* **url**: an URL to the web site, online news outlet, discussion board, social network profile, where the content made by the producer is published.
* **languages**: languages primarily used to produce the contents.
* **licenses**: licenses primarily used on the contents.
* **date of first seen**: the publishing date and time of the earliest content by the producer included in the dataset.
* **date of last update**: the publishing date and time of the newest content by the producer included in the dataset.
* **followership**: number of subscribers, followers, users who "like" the channel, or other information about the followership of the producer.


#### JSON Serialization

* The name `other_names` is used instead of alternate names, whose value is a list of name strings.
* The value of `identifiers` property is a list of identifier objects.  An identifier object has `scheme` and `identifier` propreties.  The dataset compiler is responsible for specifying the identifier objects it uses in the dataset.
* The name `first_seen_at` is used instead of date of first seen.
* The name `last_update_at` is used instead of date of last update.
* The value of `followership` property is a followership object.  The dataset compiler is responsible for specifying the format of followership objects it uses in the dataset.

#### JSON Schema

TODO

#### Refereneces

* Ronny's newsdiff [data](https://github.com/ronnywang/newsdiff/blob/master/webdata/stdlibs/url-normalizer.js/map.csv)
* Gugod's people-in-news [news-sites.txt](https://github.com/g0v/people-in-news/blob/master/etc/news-sites.txt)
* 零時檔案局 [Sites](https://airtable.com/shrd0utGHlTWmQsYt)
* Schema.org: [Organization](https://schema.org/Organization), [Person](https://schema.org/Person), [Project](https://schema.org/Project)
* "Account information" in [Twitter datasets](https://transparency.twitter.com/en/information-operations.html)
* Popolo standard: [Organization](https://www.popoloproject.com/specs/organization.html)
* Open Contracting Data Standard [Organization](https://standard.open-contracting.org/latest/en/schema/reference/#organization)
*  
* "[Followership and social media marketing](https://www.researchgate.net/publication/282685486_Followership_and_social_media_marketing)", "[Social Media Followership as a Predictor of News Website Traffic](https://www.tandfonline.com/doi/abs/10.1080/17512786.2019.1635040?journalCode=rjop20)"

### Publication

The Publication class should have the following properties:

* **id**: a unique identifier within the scope of this dataset for the publication.
* **version**: version of this copy of the publication.
* **identifiers**: ways to identify the publication, such as ID used by popular content databases.
* **producer_id**: identifier of the producer that made the publication.
* **canonical_url**: an URL to the publication, normalized to be a unique identifier within the scope of this dataset.
* **title**: title of the publication.
* **text**: text of the publication.
* **author**: author of the content of the publication.
* **about**: the subject this publication is replying to, such as on Twitter.
* **language**: language used by text of the publication.
* **license**: license of the publication.
* **date of publication**: the date and time when the content was published.
* **date of first seen**: the date and time when the publication was first observed by the dataset compiler.
* **date of last update**: the date and time when the latest update to the content was observed by the dataset compiler.
* **urls**: URLs, excluding the ones pointing to the publication itself, appeared in the text of the publication.
* **hashtags**: hashtags, as used in Twitter tweets and Facebook posts, used in the content.
* **mentions**: mentions to other users, as used in Twitter tweets and Facebook posts, made in the content.
* **keywords**: keywords of the content as given by the producer in meta-tags or in the publication. 
* **reactions**: numbers of reader reactions, such as Facebook "like" or other emotions, Twitter "like", Medium "claps", or user views.
* **comments**: comments to the publication, such as PTT and Facebook replies.
* **internet connection**: information about the connection used to publish this content, such as IP address on PTT articles, or geolocation of Twitter tweets.

#### JSON Serialization

* The value of `identifiers` property is a list of identifier objects.  An identifier object has `scheme` and `identifier` propreties.  The dataset compiler is responsible for specifying the identifier objects it uses in the dataset.
* The name `publication_text` is used instead of text.
* The name `reply_to` is used instead of about.
* The name `published_at` is used instead of date of publication.
* The name `first_seen_at` is used instead of date of first seen.
* The name `last_update_at` is used instead of date of last update.
* The value of `reactions` property is a reactions object.  The dataset compiler is responsible for specifying the format of reactions objects it uses in the dataset.
* The value of `comments` property is a list of comment objects.  
* The name `connect_from` is used instead of internet connection.

#### JSON Schema

TODO

#### References

* Schema.org: [Article](https://schema.org/Article), [WebPage](https://schema.org/WebPage), [Message](https://schema.org/Message), [SocialMediaPosting](https://schema.org/SocialMediaPosting)
* "articles" in [cofacts opendata](https://github.com/cofacts/opendata)
* "Tweet information" in [Twitter datasets](https://transparency.twitter.com/en/information-operations.html)
* Popolo standard [Speech](https://www.popoloproject.com/specs/speech.html), [Motion](https://www.popoloproject.com/specs/motion.html)
* Gugod's people-in-news [Article.pm](https://github.com/g0v/people-in-news/blob/master/lib/Sn/Article.pm), [NewsExtractor::Article](https://github.com/perltaiwan/NewsExtractor/blob/master/lib/NewsExtractor/Article.pm)

### Comment

The Comment class should have the following properties:

* **id**: a unique identifier within the scope of all comments about the same subject.
* **author**: author of the comment.
* **text**: text of the comment.
* **date of publication**: the date and time when the comment was published.
* **about**: the subject this comment is in reply to.
* **reactions**: numbers of reader reactions, such as Facebook “like” or other emotions, upvotes or downvotes.
* **internet connection**: information about the connection used to publish this content, such as IP address on PTT comments.

#### JSON Serialization

* The name `comment_text` is used instead of text.
* The name `published_at` is used instead of date of publication.
* The name `reply_to` is used instead of about.
* The value of `reply_to` property, if the subject of this comment is another comment, is the `id` of the other comment.  If the subject of this comment is the publication it belongs to, there need not be a `reply_to` value.
* The value of `reactions` property is a reactions object. The dataset compiler is responsible for specifying the format of reactions objects it uses in the dataset.
* The name `connect_from` is used instead of internet connection.

#### JSON Schema

TODO

## Specifications by 0archive

### Publication

* `version` is UNIX timestamp of the time when the copy of the publictaion was archived.

## Serialization and packaging

The following serialization scheme is supported:

* JSON Lines

Datasets are packaged in the following format:

* Frictionless Data [Data Package](https://frictionlessdata.io/specs/data-package/)

## Similar projects

* [The OpenArchive Project](https://open-archive.org/)
* [Civil Archive](https://grants.g0v.tw/projects/586a7be0a327a4001ee49126) in g0v grants
* [WARC](https://en.wikipedia.org/wiki/Web_ARChive)

# Work in progress

The followings are pending features to the standard that may or may not going to be included in the final draft.

## Classes and properties

### Media

* identifier
* canonical_url
* author
* title
* description
* location
* content_type
* content_length
* content
* content_hash
* original_filename
* first_seen_at
* last_updated_at
* tags

#### References

* [Open Archive "SAVE Space" Specification](https://github.com/OpenArchive/Save-app-android/blob/master/docs/OpenArchiveSpaceCapsuleSpec.md)
* Schema.org [MediaObject](https://schema.org/MediaObject)

### Claim

#### References

* Schema.org [Claim](https://schema.org/Claim)

### ClaimReview

* summary
* canonical_url
* item_reviewed
* review_body
* review_rating
* references

#### References

* Schema.org [ClaimReview](https://schema.org/ClaimReview)
