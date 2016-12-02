Use the latest version of C# with ReSharper.

# Formatting
- Indentation: 4 space, no tabs.
- Keep types in their own files named accordingly.
- Use Hexadecimals for large constants.
- Remove trailing whitespace.
- No License Header.

# Language Features
- Split large classes into multiple files using `partial` declarations.
- BASS library as `static class`.
- Related constants as `enum`.
- Flags as `enum` marked with `[Flags]` attribute.
- Callbacks as `Delegates`.
- BASS structures as `struct`.
- `struct` returned as `out` parameters.
- Avoid `using static`.
- `[In, Out]` marshalling for retrieving data into arrays.