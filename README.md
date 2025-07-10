# HUML test data

This repository contains a collection of centrally maintained test cases that HUML parser implementations can use as test inputs in addition to their own test cases.

This repository can be added as a git submodule to a parser library's repository, and the various test files described below can be read and evaluated by the parser's test code.

## assertions
The `./assertions` directory contains a series of JSON files. Each file is an array of test cases, where each item is an object with the following fields.

- `name` is the name of the testcase.
- `input` is the HUML string that the parser evaluates.
- `error` indicates whether input is expected to throw a parser error (`true` = parser should throw an error for the input)

Parsers can unserialize the JSON array to a structure in the respective language, iterate through the array, and execute the parsing test using the `input` string and assert a parser error based on the `error` field.

## documents
The `./docs` directory contains fully formed HUML documents (with the .huml extension) with a corresponding `.json` file with the representation of the HUML document as JSON. For instance `mixed.huml` and `mixed.json`.

Parsers can read each HUML document, deserialize it, and deep-compare it with the deserialized data structure read from the corresponding .json file.
