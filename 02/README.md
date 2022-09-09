What is **Prelude**? Prelude is a library of standard functions. Opening GHCi or Stack GHCi automatically loads those functions 
so they can be used without needing to do anything special.

**ghci commands**:

`:load <file.hs>` -- load this module, changes prompt from Prelude> to maybe `*Main>`
`:module` -- "quit" the loaded module, back to `Prelude>`
`:module *Main` -- jump back to the `*Main` module
`:reload` -- reload current module (e.g., re-read file)
`:type` and `:kind` look fun :)
`:info` -- type information for function, including infix, associativity, precedence
