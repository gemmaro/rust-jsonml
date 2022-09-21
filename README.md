# JsonML crate

[JsonML](http://www.jsonml.org/) deserialization and serialization

Deserialization example:

```rust
# use std::collections::HashMap;
use jsonml::{Element, AttributeValue, Tag};

let element: Element =
    serde_json::from_str(r#"[ "li", { "style": "color:red" }, "First Item" ]"#)
        .expect("deserialize element tag");
assert_eq!(
    element,
    Element::Tag(Tag {
        name: "li".to_string(),
        attributes: HashMap::from([(
            "style".to_string(),
            AttributeValue::String("color:red".to_string())
        )]),
        element_list: vec![Element::String("First Item".to_string())]
    })
);
```

Serialization example:

```rust
# use std::collections::HashMap;
use jsonml::{Element, AttributeValue, Tag};

let element = Element::Tag(Tag {
    name: "li".to_string(),
    attributes: HashMap::from([(
        "style".to_string(),
        AttributeValue::String("color:red".to_string()))]
    ),
    element_list: vec![Element::String("First Item".to_string())]
});
assert_eq!(
    serde_json::to_string(&element).expect("serialize element tag"),
    r#"["li",{"style":"color:red"},"First Item"]"#
);
```

## License

Licensed under either of the following at your option:

* [`LICENSE-APACHE.txt`](LICENSE-APACHE.txt) or [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
* [`LICENSE-MIT.txt`](LICENSE-MIT.txt) or [The MIT License](https://opensource.org/licenses/MIT)
