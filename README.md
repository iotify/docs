##Understanding Templates

Templates are the heart of your IoT simulation. In order to get the best benefits out from our tools, it is important to understand template well. Let's dig deeper into the template syntax.

## What is a Template? {#what-is-a-template}

A template is a text document which specifies how your generated data is going to look like. It could be in any format, but we prefer JSON. Any dynamic field in the template should be enclosed within two curly braces**\#{{}}**

Let's look at simple example of a template:

```
 Hello {{ chance.word() }}
```

Above represents a simple string which will translate into some random word as 

```
Hello
 izpu
```

Template could also be in JSON format

```
{


"hello"
: 
"{{ chance.word() }}"


}
```

or in XML format

```
<
?
xml version=
"1.0"
 encoding=
"UTF-8"
?
>


<
note
>


<
to
>
{{chance.email()}}
<
/
to
>


<
from
>
{{chance.email()}}
<
/
from
>


<
heading
>
Reminder
<
/
heading
>


<
body
>
Don't forget me this weekend!
<
/
body
>


<
/
note
>
```

or even in URL encoded format like this

```
value
={{chance.integer()}}
&
field={{chance.word()}}
```

As you may have noticed, all the fields which are enclosed within the \#{{ }} will be replaced by the values generated by your expression.  


## What is an expression? {#what-is-an-expression}

Within the template, you want certain fields to have a dynamic value generated. These fields are called an expression. All the expression will be replaced by the template engine before generating the value for that record. Here is a simple example of expression

```
{


"hello"
: 
"{{ 'I am an expression' }}"


}
```



## What can you write inside expression? {#what-can-you-write-inside-expression}

IoTIFY's expression syntax is based on**Javascript**. If you are not familiar with Javascript, don't worry. It is super easy. Just checkout few tutorials and you will be ready in no time. 

You can write any standard Javascript code within an expression as follows:

```
{


"hello"
: 
"{{ 5 + 10 % 21 + Math.floor(Math.random()*123) }}"


}
```

The expression will be interpreted at the runtime and output will be a string, replacing the original expression.



## Automatic Parsing of Integer values {#automatic-parsing-of-integer-values}

It is important to note that the template engine will automatically try to parse the values and convert them to the integer or float or boolean if possible. If you would like to preserve the output value as string, just append an empty single quote character as follows to the end

```
{


"number"
: 
"{{ 5 + 5 }}"
,


"numberString"
: 
"{{ 5 + 5 }}''"


}
```

Above template will produce following

```
{


"number"
: 
10
,


"numberString"
: 
"10"


}
```

Notice that the two single quote characters at the end of the string. They will be eventually replaced by our engine, but the resulting value will remain as a string, despite being an integer or float.



#### Could expression be also used inside JSON keys? Like this:-

```
{


"{{chance.word()}}"
: 
10
,


"numberString"
: 
"10"


}
```

Unfortunately, this is**not**supported for JSON structures.  
  
Look interesting? Let's dig deeper into what kind of expression you could write in IoTIFYGetting Started with Templates

This file file serves as your book's preface, a great place to describe your book's content and ideas.

