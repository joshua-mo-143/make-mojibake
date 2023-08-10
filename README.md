## make-mojibake: A macro library for making mojibake.
Mojibake (Japanese: 文字化け; IPA: mod͡ʑibake, "character transformation") is the garbled text that is the result of text being decoded using an unintended character encoding.

Currently this library assists in the creation of mojibake by allowing you to use a procedural macro on a struct with named fields. 

## Getting Started

Currently this crate isn't on crates.io but but you can install it with the following one-line command:

```sh
cargo add make-mojibake --git https://www.github.com/joshua-mo-143/make-mojibake.git
```

You can get started by declaring the macro with your given encoding type and how much you want to decrease or increase the mojibake (more = more difference in the value).

```rs
#[mojibake(SHIFT_JIS, up(10))]
pub struct MyStruct {
  string: String,
  number: i32,
}

fn main() {
  let my_struct = MyStruct {
    string: "Hello world!".to_string(),
    number: 432432,
  };

  println!("my_struct.number as mojibake: {}", my_struct.number_to_mojibake());
}
```

The field to output your mojibake will always be `struct.<field_name>_to_mojibake()` for ease of use.

This crate currently only supports `SHIFT_JIS` at the moment but it is planned for this to be expanded upon.

## Roadmap
- All other types of encoding
- Make a macro to turn simple variables into mojibake
- Figure out how to stop u8 overflow buffer errors
- Unicode points

## Contributions
All contributions are welcome! Feel free to open issues for things that are wrong or could use improving, as well as any PRs if you would like to improve the crate.

## Licensing
MIT license.