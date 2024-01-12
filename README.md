I find that long and often nested expression are a problem in a codebase, usually the represent bad abstractions and
hide complexity the programmer should be aware of. 
This config does not favour code verticality, instead it makes long expressions clearly visible in the 
code base by allowing them to grow wider. By using a config with a low `max_width` this expressions will be
split in different lines, therefore hiding its complexity and encouraging Rust programmers to use them. 
Bare in mind that just because a higher width is allowed, it does not mean is ok to reach it. In fact I use 
this higher limit to identify complex expressions that need to be reconsidered.

With this in mind the question is: Do I need a `max_width`? In my opinion yes, sometimes we don't have control over the
code we use and it affects how we write our code in a project, this scenarios should not end in contributors having to deal 
with very wide lines of code.

I think the max width for Rust code should be that allowed for function declarations, and it should take into account that this is a typed
programming language. I find that good functions usually don't need more than three parameters and if they do, usually it makes sense that some of them can be stored together. Assuming that a good argument name and its type name will need more or less 15 characters each, this 
gives us 90 characters for 3 arguments. Adding other 30 characters for the function name and the return type we get to 120 characters, the `max_width` of this
config.


In Rust everything is an expression, but that does not mean every construct should be use freely as such. Hidden complexity in expressions is a problem in Rust and this config tries to make such complexity clear to the eyes, that is why the following arguments are set:

```toml
struct_lit_width = 0
single_line_let_else_max_width = 0
single_line_if_else_max_width = 0
struct_variant_width = 0
```