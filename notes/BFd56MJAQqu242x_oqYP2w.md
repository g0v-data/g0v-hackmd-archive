---
title: Rentea Data Models
tags: Rentea
---
# Rentea Data Model

This document provides high level concept of data model relations. 

![](https://g0vhackmd.blob.core.windows.net/g0v-hackmd-images/upload_9483862bf4599b4d59b2fb716cc2c170)
[diagram source](https://drive.google.com/file/d/1MCpy5iRM3dDy2_FcHljLR844kQqLDb9f/view?usp=sharing)

1. User is idendified by email, and is allowed to be sign-in via multiple channel, say, username-password and google oAuth.
2. Keep only id in `Raw House`, so we know how to redirect user to target 3rd party page.
3. When any field value changed in a unique house, split them into multiple unique house.

## Forward Compatibility

1. May need to search/show house meta when exceed some level of user concensus, say, more than 5 users repored `is_rooftop=true`

