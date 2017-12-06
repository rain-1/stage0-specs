# hex2

Extension of hex0.

* Adds labels.
* Supports a variety of references.

# labels

```
:label123
```

# references

## absolute

* `$<label>` 2 byte address
* `&<label>` 4 byte address

## relative

* `!<label>` 1 byte relative
* `@<label>` 2 byte relative
* `%<label>` 4 byte relative

## displacement

* `%foo>bar` for 32 bit
* `@foo>bar` for 16 bit
* `!foo>bar` for 8 bit
