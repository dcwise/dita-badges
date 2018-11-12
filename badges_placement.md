# Placing badges in your topics

Where you place badges is part common sense and part team preference. 

## Topic placement

The following markup places the badge in the first sentence of the body of the topic.

```xml
<topic id="test1">
  <title>Topic title</title>
  <shortdesc>Short description</shortdesc>
  <body>
    <p>Topic-level badge reference</p>
  </body>
</topic>
```

This markup places the badge inside the `<abstract>` element at the beginning of the topic.

```xml
<topic id="test2">
  <title>Topic title</title>
  <abstract>
    <shortdesc>Short description</shortdesc>
    <p>Topic-level badge reference</p>
  </abstract>
  <body>
    <p>Running text</p>
  </body>
</topic>
```

## Section placement

The following markup places the badge in the first sentence of the `<section>`.

```xml
<section>
  <title>Section title</title>
  <p>Section-level badge reference</p>
  <p>Running text</p>
</section>
```
In this case, consistency is the important thing.
