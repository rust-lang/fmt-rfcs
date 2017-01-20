- Start Date: 2017-01-20
- RFC Issue: #30
- RFC PR:
- Implementation Issue:

# Summary
[summary]: #summary

Define the format for struct and union declarations.


# Details
[details]: #details

Struct names follow on the same line as the `struct` keyword, with the opening brace on
the same line when it fits within the right margin. All struct fields are indented once and
end with a trailing comma. The closing brace is not indented and appears on its own line.

```rust
struct Foo {
    a: A,
    b: B,
}
```

If and only if the opening brace does not fit within the right margin, it is pulled down to its 
own line.

```rust
struct Foo /* Margin ends at `Foo` */
{
    a: A,
    b: B,
}
```

If and only if the type name does not fit within the right margin, it is pulled down to its 
own line and indented again.

```rust
struct Foo {
    a: A,
    long_name: 
        LongName,
}
```


# Implementation
[implementation]: #implementation



# Rationale
[rationale]: #rationale

Requiring a trailing comma on the last struct field has the following benefits:

- Avoids the need to add a comma when adding another field
- Avoids the need to delete a comma with deleting a field
- Allows easier copying of fields between different structs


# Alternatives
[alternatives]: #alternatives

Some prefer to omit the trailing comma from the final struct field.


# Unresolved questions
[unresolved]: #unresolved-questions

Unions have not been stabilized yet, and thus the syntax could possibly change. `rustfmt` does not
currently have testing for union declarations.