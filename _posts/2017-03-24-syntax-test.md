---
layout: post
title: Syntax Highlighting Test
date: 2017-03-24 
tags: Markdown    
---

Jekyll uses Rouge by default for syntax highlighting, here are some tests.

Ruby:
```ruby
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
```

Python with line numbers:
```python
def print_hi(name):
    print("Hi, {}".format(name))

print_hi('Tom')
# prints 'Hi, Tom' to STDOUT.
```

C with line numbers:
```C
void print_hi(string name) {
  printf("Hi, %s", name);
}
print_hi("Tom");
/* prints 'Hi, Tom' to STDOUT. */
```