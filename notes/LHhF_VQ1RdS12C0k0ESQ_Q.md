---
tags: 
---

# Cofacts research on image-hash

From: https://g0v.hackmd.io/aJqHn8f5QGuBDLSMH_EinA?both#Hashed-file-names

## Hash function

- The perceptual hash lib used by OpenDream is [image-hash](https://github.com/danm/image-hash#readme)
    - Just a wrapper
- It uses [blockhash-js](https://github.com/commonsmachinery/blockhash-js) under the hood
    - It exports a hamming distance function for us to use
- [blockhash-js](https://github.com/commonsmachinery/blockhash-js) implements the hash mechanism mentioned in  "[Block Mean Value Based Image Perceptual Hashing](https://docs.google.com/document/d/1o-yry0GX0ylesWmsqBXIOWN5I0hKEhjUOV8GNno9QC4/edit?usp=sharing)" by Yang at el, 
- Core concept in Algorithm
    - Divide into chunks equal size 
    - Calculate medium
    - If ligher than medium then use 1; otherwise 0
    - Hash = All the bits from the chunks. 
- Resilient against:
    - Scaled images
        - Because they will be divided simiarly into blocks
    - Color normalization
        - Because bits are encoded using medium of the image
        - Example: these images may have the same hash: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_94bfc2446725e7a0122e3095301bae92.png =x200)
- Vulnerable against:
    - screenshotted images / scaled / cropped images
        - The scale is off and the added pillarbox
        - `8387878383879383`: ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_671d41b373d1b78cbb7f8da075c4403e.png)
        - `83878707470743c3` (d=10): ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_49fbdf620b5ee6d36440d246ae41ba9f.png)
        - `8f818783838781b5` (d=10) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6d506f43ce5013edf4b4e87b165f802d.png)


## blockhash-js implementation

```javascript=
blockhash(src, bits, method, callback)
```
> `src` is an image URL, `bits` is the number of bits in a row, `method` is a number 1-2 (see below), and `callback` is a function with (error, result) signature. On success, result will be array of binary values.
>
> The available methods are:
>
> 1. Quick and crude, non-overlapping blocks
> 2. Precise but slower, non-overlapping blocks (Note: should be "overlapping"?)
> 
> Method 2 is recommended as a good tradeoff between speed and good matches on any image size. The quick ones are only advisable when the image width and height are an even multiple of the number of blocks used.
>
> -- https://github.com/commonsmachinery/blockhash-js

Only method 1 and method 2 described in the paper is supported. Also, the meaning of `bits` actually differs from the paper --  the `bits` argument in blockhash.js actually means # of blocks (1 bit = 1 block) for each *side*
- 4 bits means that the image should be divided into 4 blocks in width and height
- That gives $4^2 = 16$ number of blocks, which means 16 bits of hash
    - When converted into hex (`0`~`F`), each character represents 4 bits
    - $16/4 = 4$, thus the hex hash has 4 characters
- Q: Which color channel does it use?

## Observations

- Dataset: [Cofacts collected images](https://g0v.hackmd.io/bhL6csQ8T1e81E2De7ZS5Q#Collected-images)
    - 104K images
    - 17GB in size 
    - ~160KB per image in average
- Parameters: `Bits`: number of slice per side
    - `Bits=4` (16-bit hash)
        - 745 hashes in total
    - `Bits=6` (36-bit hash)
        - 42K hashes in total
        - ~7K hashes w/ multiple images
    - `Bits=8` (64-bit hash)
        - 45K hashes in total
        - 7K hashes w/ multiple images
    - `Bits=12` (144-bit hash)
        - ~47.4K hashes in total
    - `Bits=16` (256-bit hash)
        - ~49.6K hashes in total
        - ~7.5K hashes w/ multiple images

### Bits=4 (16-bit hash)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7238819096c8dd20fe009455ec894600.png)

- barely usable
    - Different images collide in a hash

### Bits=6 (36-bit hash)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_23113b7f8b0226c8756bd0eb8ada303e.png)

- Looks descent
  - Resilient against screenshots & minor annotations
  - Unrelated images rarely found
  - However, visually similar images may appear in different hash
    - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_a4200707adce9619351d0e8f088a0fac.png)
- Examples
  - Hash `ce38f3867` ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_08983cea3d1e94d5838931cf43b98f04.png)
  - Hash `9e38e3ae3` ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2d438a7fc332619fb716cb6a61a5e035.png)
  - `9e38e3de1` (292 images) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_e56e336d51d21eb08547f74dc6618bf3.png)
  - `9e7863c73` (63 images)
 ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7ead1814cbdf027b424edd6e107756c0.png)
  - `ce38e78e3` (7 images) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_7e55b88fbc299a0ce8cbb68a56ee14a8.png)


- Similarity works, but d=1 is rare and contains images looking very different. Similar images may still appear for d >= 3.
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_6f9be2e605b0772dce20bfc7fac5184d.png =x300)
  - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_b491e96c14b8548400a3692c76a58b16.png =x500)



### Bits=8 (64-bit hash)
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fe54643b29a8ceae216b79476327eda3.png)
- looks pretty good
    - Different images almost don't collide
        - Exception: hash `8783838787838387` ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_2d3e474f2087668581809885198a1ed6.png)
        ````
        87  10000111
        83  10000011
        83  10000011
        87  10000111
        87  10000111
        83  10000011
        83  10000011
        87  10000111
        ````
    - Allows some level of difference
        - Example: hash `8387878383879383` ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_afd3bd8b00672342af9cab3bf349afa6.png)
        - Example: hash `8783838787838387` ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_ac0e7b96869217c2858b60313e9ae43a.png)
    - Similar images do have lower distances
        - `f510301f1533213e` and its similar hashes ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_69304ddd99b38f54a90700e6cd807db8.png)
    - Text on image all look similar ......
        - Example: hash `8387878383879383`'s similar images' ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_5b91e52b2f532c5498e862b148afc1bc.png)

### Bits=16 (256-bit hash)

![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_66d57228ac2ae7401e4422950f19c1f6.png)

- No collision found
- Extremely sensitive
    - Even scaling may affect hash by 1 ~ 2 bits
        - Example: 
            - `ffcefc00fc00dc02dc02d840e5cfa3d5cbd8c291fb80ff008700cf80ffb0ff04` - ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_fc9a69f827dca51001e5923d5d143cad.png)
            - `ffcefc00fc00dc02dc02d840e5cfa3d5cbd8c291fb80ff000700df80ffb0ff04` (d=1) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_58d4b484fe690d182b8732cfa7d045af.png)
            - `ffcefc00fc00dc02dc02d840e5cf83f5cbd8c291f380ff200710df80ffb0ff00` (d=8) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_932c7161e65fd7424d4977ac1520548d.png)
    - Jpeg artifact may also affect hash
        - `ffff800181ff800384ff81ff803f80078003c99bd993d99b8801818b818bffff` ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_30a565fc36d0b831a8a6bc65ae584178.png)
        - `ffff800181ff800384ff81ff803f80078003c99bd99bd9938801818b818bffff` (d=2) ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0618508f4f0b8fd71b8585ba0f5151d1.png)
- Can get many near duplicates with different distances ![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_0f7afe558919130a1e7f775745312cf5.png)
    - No other images within d=10 (10/256 ~= 0.04 difference, means >95% similarity)
    
