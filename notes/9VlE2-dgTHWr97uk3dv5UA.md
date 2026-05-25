### Product Rating Comparison Using Loops and Conditionals

Complete the function `compareProductRatings(n, ratings, standard)`, which compares product ratings against a standard rating value and returns the comparison result.

Each product rating is compared with the standard:

- count ratings greater than the standard
- count ratings less than the standard
- ratings equal to the standard are not counted

Based on the comparison:

- return `""better""` if ratings greater than the standard are more
- return `""worse""` if ratings less than the standard are more
- return `""equal""` if both counts are the same

<MultiLineNote>
- There is no need to read any input inside the function.
- All values are passed directly to the function as parameters.
</MultiLineNote>

---

#### Input Format

- `n` an integer representing the number of product ratings
- `ratings` an array of `n` comma-separated integers representing product ratings
- `standard` an integer representing the standard rating value

---

#### Output Format

- Return one of the following strings:

  - `""better""`
  - `""worse""`
  - `""equal""`

---

#### Constraints

- 1 ≤ `n` ≤ 10<sup>5</sup>
- -10<sup>9</sup> ≤ `ratings[i]` ≤ 10<sup>9</sup>
- -10<sup>9</sup> ≤ `standard` ≤ 10<sup>9</sup>

---

#### Example

###### Sample Input

```
6
[1, 3, 0, -1, 4, 3]
2
```

###### Sample Output

```
equal
```

---

###### Explanation

The product ratings are compared with the standard value `2`.

- Ratings greater than the standard `3, 4, 3` count = `3`
- Ratings less than the standard `1, 0, -1` count = `3`

Since both counts are the same, the function returns:
`equal`

---




### Rainfall Level Comparison Using Loops and Conditionals

Complete the function `compareRainfallLevels(n, levels, average)`, which compares daily rainfall levels against an average value and returns the comparison result.

Each rainfall level is compared with the average:

- count levels greater than the average
- count levels less than the average
- levels equal to the average are not counted

Based on the comparison:

- return `""above""` if levels greater than the average are more
- return `""below""` if levels less than the average are more
- return `""equal""` if both counts are the same

<MultiLineNote>
- There is no need to read any input inside the function.
- All values are passed directly to the function as parameters.
</MultiLineNote>

---

#### Input Format

- `n` an integer representing the number of rainfall records
- `levels` an array of `n` comma-separated integers representing rainfall levels
- `average` an integer representing the average rainfall value

---

#### Output Format

- Return one of the following strings:

  - `""above""`
  - `""below""`
  - `""equal""`

---

#### Constraints

- 1 ≤ `n` ≤ 10<sup>5</sup>
- -10<sup>9</sup> ≤ `levels[i]` ≤ 10<sup>9</sup>
- -10<sup>9</sup> ≤ `average` ≤ 10<sup>9</sup>

---

#### Example

###### Sample Input

```
6
[1, 3, 0, -1, 4, 3]
2
```

###### Sample Output

```
equal
```

---

###### Explanation

The rainfall levels are compared with the average value `2`.

- Levels greater than the average `3, 4, 3` count = `3`
- Levels less than the average `1, 0, -1` count = `3`

Since both counts are the same, the function returns:
`equal`

---