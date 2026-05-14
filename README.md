# Mersenne Twister

[
![npm version](https://badge.fury.io/js/mersenne-twister.svg)
](https://badge.fury.io/js/mersenne-twister)

A JavaScript implementation of the Mersenne Twister MT19937 pseudorandom number generator.

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

## Features

-   Generates pseudorandom numbers with a period of 2¹⁹⁹³⁷-1.
-   Supports seeding with a number or an array for repeatable sequences.
-   Provides multiple methods for different intervals and resolutions.
-   Works in both Node.js and browser environments.

## Installation

```bash
npm install mersenne-twister
```

## Usage

**CommonJS (Node.js)**

```javascript
const MersenneTwister = require('mersenne-twister');
const generator = new MersenneTwister();

// Generate a random number on [0,1)
const randomNumber = generator.random();
```

**ES Modules**

```javascript
import MersenneTwister from 'mersenne-twister';
const generator = new MersenneTwister();

// Generate a random number on [0,1)
const randomNumber = generator.random();
```

## Seeding

For reproducible sequences of random numbers, you can provide a seed to the generator. If no seed is provided, the generator is seeded with the current timestamp.

### Seed with a Number

Pass an integer to the constructor or the `init_seed` method.

```javascript
// Seed during instantiation
const generator = new MersenneTwister(123);

// Or seed an existing instance
generator.init_seed(456);
```

Generators initialized with the same seed will produce the exact same sequence of numbers.

### Seed with an Array

The generator can also be seeded with an array of numbers. This method is compatible with the seeding behavior of other implementations, such as Python's `random` module.

```javascript
const seedArray = [0, 42, 1337];
const generator = new MersenneTwister(seedArray);
```

## API Methods

An instance of `MersenneTwister` has the following methods:

-   `random()`: Returns a random float in the interval `[0, 1)`. This is the most common method and is equivalent to `Math.random()`.
-   `random_int()`: Returns a random 32-bit integer in the interval `[0, 4294967295]`.
-   `random_incl()`: Returns a random float in the interval `[0, 1]`. (Inclusive of 1.0).
-   `random_excl()`: Returns a random float in the interval `(0, 1)`. (Exclusive of 0.0 and 1.0).
-   `random_long()`: Returns a random float in the interval `[0, 1)` with 53-bit resolution for higher precision.
-   `random_int31()`: Returns a random 31-bit integer in the interval `[0, 2147483647]`.

## Credits

This code is based on the original C-program for MT19937 by Makoto Matsumoto and Takuji Nishimura. The JavaScript adaptation was originally created by Sean McCullough.

## License

MIT License — see [LICENSE](LICENSE).