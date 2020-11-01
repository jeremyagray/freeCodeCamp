---
title: Vector Dot Product
id: 594810f028c0303b75339ad3
challengeType: 5
forumTopicId: 302343
---

## Description
<section id='description'>

A vector is a quantity having both magnitude and direction, as opposed to a scalar (a regular number) that only has magnitude. Geometrically, a vector is a directed line segment and may be represented by an ordered tuple such as (X, Y) in two dimensions or (X, Y, Z) in three. In programming, vectors are commonly represented as one dimensional arrays, with the number of elements representing the mathematical dimension of the vector.

Vectors have four different types of multiplication defined for them:

- dot (scalar or inner) product
- cross product
- scalar cross product
- vector triple product

Each type of multiplication has its own set rules of implementation, mathematical properties, and physical application.
</section>

## Instructions
<section id='instructions'>

Write a function that takes any even number of vectors (arrays) as input and computes the dot product. Your function should return <code>null</code> on invalid inputs such as vectors of different lengths.
</section>

## Tests
<section id='tests'>

```yml
tests:
  - text: <code>dotProduct</code> should be a function.
    testString: assert.equal(typeof dotProduct, 'function');
  - text: <code>dotProduct()</code> should return <code>null</code>.
    testString: assert.equal(dotProduct(), null);
  - text: <code>dotProduct([])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([]), null);
  - text: <code>dotProduct([], [])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([], []), null);
  - text: <code>dotProduct([1], [1])</code> should return <code>1</code>.
    testString: assert.equal(dotProduct([1], [1]), 1);
  - text: <code>dotProduct([1], [1, 2])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([1], [1, 2]), null);
  - text: <code>dotProduct([1, 2], [1])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([1, 2], [1]), null);
  - text: <code>dotProduct([], [1, 2])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([], [1, 2]), null);
  - text: <code>dotProduct([1, 2], [])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([1, 2], []), null);
  - text: <code>dotProduct([1, 2], [3, 4])</code> should return <code>11</code>.
    testString: assert.equal(dotProduct([1, 2], [3, 4]), 11);
  - text: <code>dotProduct([1, 2], [3, 4, 5])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([1, 2], [3, 4, 5]), null);
  - text: <code>dotProduct([1, 2, 3], [4, 5])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([1, 2, 3], [4, 5]), null);
  - text: <code>dotProduct([1, 3, -5], [4, -2, -1])</code> should return <code>3</code>.
    testString: assert.equal(dotProduct([1, 3, -5], [4, -2, -1]), 3);
  - text: <code>dotProduct([1, 0, 0], [0, 1, 0])</code> should return <code>0</code>.
    testString: assert.equal(dotProduct([1, 0, 0], [0, 1, 0]), 0);
  - text: <code>dotProduct([1, 0, 0], [0, 0, 1])</code> should return <code>0</code>.
    testString: assert.equal(dotProduct([1, 0, 0], [0, 0, 1]), 0);
  - text: <code>dotProduct([0, 1, 0], [0, 0, 1])</code> should return <code>0</code>.
    testString: assert.equal(dotProduct([0, 1, 0], [0, 0, 1]), 0);
  - text: <code>dotProduct([1, 0, 0], [0, 1, 0], [0, 0, 1])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([1, 0, 0], [0, 1, 0], [0, 0, 1]), null);
  - text: <code>dotProduct([0, 1, 2, 3, 4], [0, 2, 4, 6, 8], [0, 3, 6, 9, 12], [0, 4, 8, 12, 16], [0, 5, 10, 15, 20])</code> should return <code>null</code>.
    testString: assert.equal(dotProduct([0, 1, 2, 3, 4], [0, 2, 4, 6, 8], [0, 3, 6, 9, 12], [0, 4, 8, 12, 16], [0, 5, 10, 15, 20]), null);
  - text: <code>dotProduct([0, 1, 2, 3, 4], [0, 2, 4, 6, 8], [0, 3, 6, 9, 12], [0, 4, 8, 12, 16])</code> should return <code>21600</code>.
    testString: assert.equal(dotProduct([0, 1, 2, 3, 4], [0, 2, 4, 6, 8], [0, 3, 6, 9, 12], [0, 4, 8, 12, 16]), 21600);

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function dotProduct(...vectors) {

}
```

</div>



</section>

## Solution
<section id='solution'>


```js
function dotProduct(...vectors) {
  if (!vectors || !vectors.length) {
    return null;
  }
  if (!vectors[0] || !vectors[0].length) {
    return null;
  }
  if (vectors.length % 2 !== 0) {
    return null;
  }

  const vectorLen = vectors[0].length;
  const numVectors = vectors.length;

  let dot = null;

  for (let i = 1; i < numVectors; i++) {
    if (vectors[i].length !== vectorLen) {
      return null;
    }
  }

  for (let i = 0; i < numVectors / 2; i++) {
    let sum = 0;

    for (let j = 0; j < vectorLen; j++) {
      sum += vectors[2 * i][j] * vectors[2 * i + 1][j];
    }

    if (dot === null) {
      dot = sum;
    } else {
      dot *= sum;
    }
  }
  return dot;
}
```

</section>
