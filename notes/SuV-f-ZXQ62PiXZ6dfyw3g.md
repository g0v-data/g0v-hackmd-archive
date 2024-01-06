---
title: "extend popolo"
tags: kuansim,hackpad
---

# extend popolo

> [點此觀看原始內容](https://g0v.hackpad.tw/4FYtOSv9vl6)

Upstream issues: [https://github.com/opennorth/popolo-spec/issues](https://github.com/opennorth/popolo-spec/issues)
Base on [Popolo project](http://popoloproject.com/)
> 因為格式不太夠用, 所以需要做 extend., 到時彙整回 popolo.
> [name=HisnYi C]

> 除此之外也列出現有spec不包含的case及其對應的popolo issue id.
> [name=HisnYi C]


**目前 Popolo Spec 不包含的 Case**

- [ ] 組織的轄區
> [opennorth/popolo spec#21](https://github.com/opennorth/popolo-spec/issues/21)
> [name=HisnYi C]

- [ ] 組織的 Office Hour
> 不同function有不同時段
> [name=HisnYi C]

- [ ] 公務員的職等
- [ ] 職位產生方式的資訊
    - [ ] 立委, 議員的選區, 得票數之類的
    - [ ] 政務官任命方式
> [opennorth/popolo spec#29](https://github.com/opennorth/popolo-spec/issues/29)
> [name=HisnYi C]

- [x] 組織的裁撤, 轉移, 合併, 建立的關係
> [opennorth/popolo spec#41](https://github.com/opennorth/popolo-spec/issues/41)
> [name=HisnYi C]

- [ ] 地址的格式
> [opennorth/popolo spec#10](https://github.com/opennorth/popolo-spec/issues/10)
> [name=Superbil]

    分區要能夠表示 縣市/市 -> 區 -> 里 -\> 鄰
> 參考 [VCARD 4.0 ADR](https://tools.ietf.org/html/rfc6350#section-6.3)
> [name=Superbil]

- [ ] 電話的格式
- [ ] 任務式職位的關係記載方式
    - [ ] e.x: 國會會長
    - [ ] e.x 立法院的XXX委員會委員
- [ ] 多重名稱
    - [ ] 中華民國常因政治因素而必須使用Chinese Taipei之類的英文名稱, 使得會有兩種官方中文名稱
> 中華民
> [name=Superbil]

- [ ] 任務式組織的記載方式
    - [ ] 因計劃而產生的單位
- [ ] 資料的有效性
> [opennorth/popolo spec#46](https://github.com/opennorth/popolo-spec/issues/46)
> [name=HisnYi C]

- [ ] 候選人記載方式
> [opennorth/popolo spec#43](https://github.com/opennorth/popolo-spec/issues/43)
> [name=HisnYi C]

- [ ] 歷史記錄
> [opennorth/popolo spec#47](https://github.com/opennorth/popolo-spec/issues/47)
> [name=HisnYi C]

- [ ] 資料更新的頻率
- [ ] 多重 source 的記載方式
- [ ] 組織大事紀?
- [ ] 人物大事紀?
- [ ] contact detail 沒有 primary porpoerty
> 例如用來指出該email是主要的email
> [name=HisnYi C]


## Classes


spec 討論基於 JSON-LD context ，比較知道要從那邊引用和定義

**Person**
- origin [spce ref](http://popoloproject.com/specs/person.html)
```javascript
{
  "Person": "http://www.w3.org/ns/person#Person",
  "name": "http://xmlns.com/foaf/0.1/name",
  "other_names": {
 "@id": "http://www.w3.org/ns/opengov#otherName",
 "@type": "@id"
  },
  "identifier": "@value",
  "scheme": "@type",
  "identifiers": "http://xmlns.com/foaf/0.1/nick",
  "family_name": "http://xmlns.com/foaf/0.1/familyName",
  "given_name": "http://xmlns.com/foaf/0.1/givenName",
  "additional_name": "http://schema.org/additionalName",
  "honorific_prefix": "http://schema.org/honorificPrefix",
  "honorific_suffix": "http://schema.org/honorificSuffix",
  "patronymic_name": "http://www.w3.org/ns/person#patronymicName",
  "sort_name": "http://www.w3.org/2000/10/swap/pim/contact#sortName",
  "email": {
 "@id": "http://schema.org/email",
 "@type": "@id"
  },
  "gender": "http://xmlns.com/foaf/0.1/gender",
  "birth_date": {
 "@id": "http://schema.org/birthDate",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "death_date": {
 "@id": "http://schema.org/deathDate",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "image": {
 "@id": "http://schema.org/image",
 "@type": "@id"
  },
  "summary": "http://purl.org/vocab/bio/0.1/olb",
  "biography": "http://purl.org/vocab/bio/0.1/biography",
  "national_identity": "http://www.w3.org/ns/opengov#nationalIdentity",
  "contact_details": {
 "@id": "http://www.w3.org/ns/opengov#contactDetail",
 "@type": "@id"
  },
  "links": {
 "@id": "http://www.w3.org/2000/01/rdf-schema#seeAlso",
 "@type": "@id"
  },
  "memberships": {
 "@id": "http://www.w3.org/ns/org#memberOf",
 "@type": "@id"
  },
  "created_at": {
 "@id": "http://purl.org/dc/terms/created",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "updated_at": {
 "@id": "http://purl.org/dc/terms/modified",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "sources": {
 "@id": "http://purl.org/dc/terms/source",
 "@type": "@id"
  }
}
```
- extend spec

**Organization**
- origin [spec ref](http://popoloproject.com/specs/organization.html)
```javascript
{
  "Organization": "http://www.w3.org/ns/org#Organization",
  "name": "http://www.w3.org/2004/02/skos/core#prefLabel",
  "other_names": {
 "@id": "http://www.w3.org/ns/opengov#otherName",
 "@type": "@id"
  },
  "identifier": "@value",
  "scheme": "@type",
  "identifiers": "http://www.w3.org/ns/org#identifier",
  "classification": {
 "@id": "http://www.w3.org/ns/org#classification",
 "@type": "@id"
  },
  "parent": {
 "@id": "http://www.w3.org/ns/org#subOrganizationOf",
 "@type": "@id"
  },
  "founding_date": {
 "@id": "http://schema.org/foundingDate",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "dissolution_date": {
 "@id": "http://www.w3.org/ns/opengov#dissolutionDate",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "image": {
 "@id": "http://schema.org/image",
 "@type": "@id"
  },
  "contact_details": {
 "@id": "http://www.w3.org/ns/opengov#contactDetail",
 "@type": "@id"
  },
  "links": {
 "@id": "http://www.w3.org/2000/01/rdf-schema#seeAlso",
 "@type": "@id"
  },
  "memberships": {
 "@id": "http://www.w3.org/ns/org#hasMember",
 "@type": "@id"
  },
  "posts": {
 "@id": "http://www.w3.org/ns/org#hasPost",
 "@type": "@id"
  },
  "created_at": {
 "@id": "http://purl.org/dc/terms/created",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "updated_at": {
 "@id": "http://purl.org/dc/terms/modified",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "sources": {
 "@id": "http://purl.org/dc/terms/source",
 "@type": "@id"
  }
}
```
- extend spec

**Membership**
- origin [spec ref](http://popoloproject.com/specs/membership.html)
```javascript
{
  "Membership": "http://www.w3.org/ns/org#Membership",
  "label": "http://www.w3.org/2004/02/skos/core#prefLabel",
  "role": {
 "@id": "http://www.w3.org/ns/org#role",
 "@type": "id"
  },
  "person": {
 "@id": "http://www.w3.org/ns/org#member",
 "@type": "@id"
  },
  "organization": {
 "@id": "http://www.w3.org/ns/org#organization",
 "@type": "@id"
  },
  "post": {
 "@id": "http://www.w3.org/ns/opengov#post",
 "@type": "@id"
  },
  "on\_behalf\_of": {
 "@id": "http://www.w3.org/ns/opengov#onBehalfOf",
 "@type": "@id"
  },
  "start_date": {
 "@id": "http://schema.org/validFrom",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "end_date": {
 "@id": "http://schema.org/validThrough",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "contact_details": {
 "@id": "http://www.w3.org/ns/opengov#contactDetail",
 "@type": "@id"
  },
  "links": {
 "@id": "http://www.w3.org/2000/01/rdf-schema#seeAlso",
 "@type": "@id"
  },
  "created_at": {
 "@id": "http://purl.org/dc/terms/created",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "updated_at": {
 "@id": "http://purl.org/dc/terms/modified",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "sources": {
 "@id": "http://purl.org/dc/terms/source",
 "@type": "@id"
  }
}
```
- extend spec


**Post**
- origin [spec ref](http://popoloproject.com/specs/post.html)
```javascript
{
  "Post": "http://www.w3.org/ns/org#Post",
  "label": "http://www.w3.org/2004/02/skos/core#prefLabel",
  "role": {
 "@id": "http://www.w3.org/ns/org#role",
 "@type": "id"
  },
  "organization": {
 "@id": "http://www.w3.org/ns/org#postIn",
 "@type": "@id"
  },
  "start_date": {
 "@id": "http://schema.org/validFrom",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "end_date": {
 "@id": "http://schema.org/validThrough",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "contact_details": {
 "@id": "http://www.w3.org/ns/opengov#contactDetail",
 "@type": "@id"
  },
  "links": {
 "@id": "http://www.w3.org/2000/01/rdf-schema#seeAlso",
 "@type": "@id"
  },
  "memberships": {
 "@id": "http://www.w3.org/ns/opengov#heldThrough",
 "@type": "@id"
  },
  "created_at": {
 "@id": "http://purl.org/dc/terms/created",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "updated_at": {
 "@id": "http://purl.org/dc/terms/modified",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "sources": {
 "@id": "http://purl.org/dc/terms/source",
 "@type": "@id"
  }
}

```
- extend spec

**Contact Detail**
- origin [spec ref](http://popoloproject.com/specs/contact-detail.html)
```javascript
{
  "ContactDetail": "http://www.w3.org/ns/opengov#ContactDetail",
  "label": "http://www.w3.org/2000/01/rdf-schema#label",
  "type": "http://www.w3.org/1999/02/22-rdf-syntax-ns#type",
  "value": "http://www.w3.org/1999/02/22-rdf-syntax-ns#value",
  "note": "http://www.w3.org/2004/02/skos/core#note",
  "created_at": {
 "@id": "http://purl.org/dc/terms/created",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "updated_at": {
 "@id": "http://purl.org/dc/terms/modified",
 "@type": "http://www.w3.org/2001/XMLSchema#dateTime"
  },
  "sources": {
 "@id": "http://purl.org/dc/terms/source",
 "@type": "@id"
  }
}

```
- extend spec

## 相關專案

- [g0v/addressbook.parser](https://github.com/g0v/addressbook.parser)
-

