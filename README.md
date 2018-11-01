# Content Bading in OASIS DITA (FIRST REVIEW)

OASIS DITA Adoption whitepaper on content badging.

Badging is a popular topic on several fronts. The three most popular forms of badging are:

* *Achievement badging*: Organizations set up collections of social media "badges" to recognize the involvement and achievement in employees, partners, and customers. Imagine if someone developed a technical certification program for DITA and awarded badges to program participants who passed tests for particular features.  

  ![DITA conref push expert](/images/badge_dita_conref-push.png)  ![DITA reltables expert](/images/badge_dita_reltables.png)  ![DITA scoped keys expert](/images/badge_dita_scopedkeys.png)

* *Status badging*: Collaborative development platforms allow administrators to incorporate macros in their portal pages that display the current status of builds, workflow stages, contributions, and test coverage.

  ![Test status](/images/badge_tests_pass-fail.svg)
  
  ![Build status passing](/images/badge_build_passing.svg)

  ![Build status unknown](/images/badge_build_unknown.svg)

  ![Build status failing](/images/badge_build_failing.svg)

  ![Build status failure](/images/badge_build_failure.svg)
    
* *Content badging*: Content development organizations often decide to have one publication document multiple,  closely-related products. Content badges alert readers whether the relevance of a particular topic, section, or element is restricted to a specific product or release version. Here are some samples of icon-based and tag-based badges.

  ![Topic not applicable to Cloud Compute](/images/badge_cloud-compute_no.png) This topic does not apply to Cloud Compute.

  ![Topic applicable only to Cloud Compute](/images/badge_cloud-compute_yes.png) This topic applies exclusively to Cloud Compute.

  ![Not applicable to Cloud Compute](/images/tag_cloud-compute_not-supported.svg) This section does not apply to Cloud Compute.
  
  ![Applicable only to Cloud Compute](/images/tag_cloud-compute_supported.svg) This topic applies exclusively to Cloud Compute. 

Content badging is a medium- to high-risk content strategy for compound publications, that is, publications that document more than one product or version.


## A typical use case for content badging

A startup named CloudSquared develops resource monitoring software for cloud-based frameworks. For its first product, Cloud Compute Monitoring, the content development team develops a complete documentation set.

![Use case - one product](/images/use-case_1.png)

A year later CloudSquared releases Cloud Net Monitoring so the content development team uses DITA conditional filtering to publish separate Cloud Compute and Cloud Net publications. 

![Use case - two products](/images/use-case_2.png)

Content developers assign filtering attributes such as `@product="cloud-compute"` or `@product="cloud-net"` to topics, sections, or elements that need to be filtered OUT of a product-specific deliverable. 

The following year, CloudSquared releases Cloud Connect and completes the monitoring suite. The writing team then uses conditional filtering to publish three separate publications. 

![Use case - three products](/images/use-case_3.png)

Content developers add the filtering attribute `@product="cloud-connect"` to those topics, sections, or elements that need to be filtered OUT of the other two product-specific deliverables. 

Six months after this launch, Marketing receives feedback that emphasizing common design and services across the three suite components will enhance customer perception that CloudSquared can consolidate its achievements and move on to new product lines. Toward that end, Product Management requests that the content development team consolidate the three, product-specific publications into one, multi-product publication. All generic and product-specific information would need to appear in the same deliverable.

![Use case - one combined product](/images/use-case_4.png)

When transitioning from conditional filtering to badging, note that filtering metadata is *useful* in identifying where product-specific information lives in your sources but *useless* as markup to implement badging. In DITA, the logic to include or exclude elements tagged with filtering attributes such as @product or @audience lives in DITAVAL scripts outside the DITA topics themselves.  

Filtering markup in a topic: 

```xml
<p @product="cloud-connect">Cloud Connect is great.</p>
```

Filtering markup in a DITAVAL script:

```xml
<val>
   <prop att="product" val="cloud-connect" action="exclude" />
</val>
```

Badging markup: 

```xml
<p id="p_badge_icon_cloud-connect_section_yes">
  <image href="images/badge_cloud-connect_small_yes.png"></image>
  <ph>This section applies exclusively to Cloud Connect.</ph>
</p>
<p>Cloud Connect is great.</p>
```

Filtering does a brilliant job supporting a many-to-one relationship between source content and delivered content. Many product-specific variations are filtered out to produce that one product-specific deliverable. Badging involves a many-to-many relationship. All the product-specific variations in the sources need to be accounted for in a multi-product deliverable.   

The real challenges with badging involve logic. 

 
## Badge design and implementation

Logic and planning problems of this sort are best approached visually. Design exercises such as card sorting or affinitization depend upon multiple team members seeing all the variables and iteratively testing various arrangements or groupings. Similarly, making a first, complete pass at designing all the content badges that you might need will accelerate the process of developing and refining the logic of your badging. If you have time to code the badges in a DITA library, that's great -- but sticky notes or 3x5 cards will suffice for team discussions early on. Move the cards around. Tape them to whitebaords. Staple them to printouts of your existing docs. Any exercise that simulates applying a badge to your content and thenasking whether that application makes sense is goodness.

Regardless of how you implement badging in DITA, the content badges themselves have four basic components:

Visual cue | Content ID | Content scope | Content switch
-----------|------------|----------------|--------------------
![Icon cue](/images/badge_cloud-net_small_yes.png)<br />![Tag cue](/images/cue_tags.png)|Cloud Net|This section | applies to . . . 
![Icon cue](/images/badge_cloud-net_small_no.png)<br />![Tag cue](/images/cue_tags.png)|Cloud Net|This topic  | does not apply to . . . 

Whether you and your graphic designers choose icons or tags, building a library of reusable DITA badges is straight-forward. Consider starting with just one library for badging, call it `library_content-badges.dita`. 

Markup | Rendered presentation
-------|----------------------
`<p id="p_badge_icon_cloud-connect_section_yes">`<br />`  <image href="images/badge_cloud-connect_small_yes.png">`<br />`    <alt>This section applies exclusively to Cloud Connect.</alt>`<br />`  </image>`<br />`  <ph> This section applies exclusively to Cloud Connect.</ph>`<br />`</p>`<br />|![Icon rendered](/images/render1.png)
`<p id="p_badge_tag_cloud-compute_topic_no">`<br />`<image href="images/tag_cloud-compute_not-supported.svg">`<br />`<alt>This topic does not apply to Cloud Compute.</alt>`<br \>`</image>`<br />`<ph> This topic does not apply to Cloud Compute.</ph>`<br />`</p>`|![Icon rendered](/images/render2.png)

Time that you spend organizing these badge definitions in a DITA library topic has a big payoff for content developers on your team. If writers can easily find the appropriate badge, they'll thank you -- eventually.  

![Badge library entries](/images/library1.png)

![Badge library entries](/images/library2.png)


## Establishing logic

If your badges are crisply defined and you apply them logically and consistently to your content, badging works. The first step toward providing logic for your publication is having a global statement about non-badged content.

> Unless otherwise indicated with a product badge such as ![Icon cue](/images/badge_cloud-net_small_no.png), all content applies equally to CloudSquared Cloud Compute, Cloud Net, and Cloud Connect. 

This global statement sets the baseline logically. The only badges that the customer should expect to see would be ones that are exclusionary, identifying topics or sections that are *not* applicable to a particular product. The simpler your logic for inserting a badge, the more consistently content developers can apply them and customers can understand them. In this scenario, you do not need to insert any inclusive badges, only exclusive ones. This is not unlike DITA filtering attributes that are designed, generally, to exclude content from processed output. 
  
![Tag exclude topic](/images/tag_cloud-compute_not-supported.svg) This topic does not apply to Cloud Compute.

![Tag exclude topic](/images/tag_cloud-net_not-supported.svg) This section does not apply to Cloud Net.

![Tag exclude topic](/images/tag_cloud-connect_not-supported.svg) This topic does not apply to Cloud Connect.

In our use case, you would then require only six badges -- 3 products x 2 scopes (topic or section).

## Badging and scope 

When we content developers are looking at badged content in a DITA editor, we see where `<topic>` and `<section>` elements begin and end. We see the scope of the element relative to the topic displayed in our DITA editor. Unfortunately these topic and section boundaries are not visible or recoverable to customers. In a running PDF, where does the current "topic" or "section" end? If we chunk multiple source topics so they generate one HTML5 page in output, wouldn't the topic boundaries be misleading? If I insert a topic-level badge to indicate that no content in the topic applies to a particular product, what happens if another writer conref's a section from my topic? That conref'd section has no section badge. Messy stuff. 

You need to scope your topic-level or section-level badges to what you expect the customer will see on the page or in a browser, not what we see in our DITA sources. How do you figure that out? You test it out and show it to people in all your generated output formats. 

Is it technically possible to create badges scoped to the level of DITA elements, for example paragraphs, figures, table rows, or phrases? Yes. 

Practically, attempting to use the same badges for elements that you use for topics or sections can create a visual and logical train wreck. Teams that have successfully worked with badged documentation for multiple releases turn to `<note>` elements or in-line explanations for anything more granular than sections. Others use DITA flagging to color-code platform-specific information (accessibility - ouch). 

Document the logic and the scoping of your badging strategy. 

## Going on a test drive 

Once you have normed on your logic and authoring guidelines, apply them to a small publication. Badging is messy stuff and you do not want to implement it for a complete doc set until you have received a "go-ahead" from your stakeholders. When they actually see a sample of your "badged" documentation, they may have objections or concerns that you had not factored into your initial design. 

* *UXD*: "Shouldn't the graphic design of the badges conform to the new company UX guidelines?"
* *Support*: "Some customers are not careful readers and tend to ignore subtleties like these badges. They try something that is not appropriate for their product and then call us. Why are we doing this again? It is increasing our workload."
* *Test engineering*: "When we tested your procedures in the product-specific manuals, we could clearly identify issues with your writing. The new format is interesting, but we are never quite sure whether we are supposed to be testing all product procedures at once or be tiptoeing through the product-specific procedures one at a time." 
* *Software engineering*: "Sometimes the differences between product features are not binary, not quite so simple as 'supported' or 'not supported'. Some features are "minimally supported" or "mostly supported." 
* *Sales*: In pre-sales discussions, handing prospective customers manual that documents three products kinda confuses them if they are interesting in buying one."
* *Marketing*: "I didn't realize that the docs would need so many badges. Can you make them smaller or put them in the margin somewhere?"
* *Legal*: "Our product documentation serves as the definitive product description. If the documentation does not accurately describe the product that the cutomer has purchased, we cannot recognize revenue."

Showing everyone a robust sample of badged documentation generates discussion across the organization about badging and other requirements for product documentation. 

## Placing badges in your topics

Where you place badges is part common sense and part team preference. 

Badge type|Placement options
----------|-------------------
Topic|This places the badge in the first sentence of the body of the topic.<br />`<topic id="test1">`<br />`<title>Title</title>`<br />`<shortdesc>Short description</shortdesc>`<br />`<body>`<br />**`<p>Topic badge reference</p>`**<br />`</body>`<br />`</topic>`<br /><br />This places the badge inside the `<abstract>` element at the beginning of the topic.<br />`<topic id="test2">`<br />`<title>Title</title>`<br />`<abstract>`<br />`<shortdesc>Short description</shortdesc>`<br />**`<p>Topic badge reference</p>`**<br />`</abstract>`<br />. . .
Section|This places the badge in the first sentence of the `<section>`.<br />`<section>`<br />`<title>Section title</title>`<br />**`<p>Section badge reference</p>`**<br />`<p>. . .</p>`<br \>`</section>` 

## Referencing badges in your topics

If you have build a library for your badges and assigned each of them a unique ID, you can use @conref or @conkeyref to insert them by reference them into your current topic. 

Let's assume that you created a badging library named `library_content-badges.dita` with a topic @id of `library1`. That library contains the following badge definition.  

```xml
<p id="p_badge_tag_cloud-compute_topic_yes">
  <image href="images/tag_cloud-compute_supported.svg">
    <alt>This topic applies exclusively to Cloud Compute.</alt>
  </image>
  <ph> This topic applies exclusively to Cloud Compute.</ph>
</p>
```

To insert this badge using @conref (URL referencing), you would enter the following markup.

```xml
<p conref="library_content-badges.dita#library1/p_badge_tag_cloud-connect_topic_yes"/>
```

To insert this badge using DITA keys, you must first define a key for the badging library in your current map.

```xml
<topicref keys="badgelib" href="library_content-badges.dita"/>
```

You can then reference the badge using @conkeyref (indirect referencing).

``xml
<p conkeyref="badgelib/p_badge_tag_cloud-connect_topic_yes"/>
```

## Referencing badges in shared topics

If any of the topics that you badge for one of your team deliverables are referenced by content developers outside your team or outside your division, those badges will generate build errors or cause reader confusion. Be practical. Clone the shared topic and move on.

If you *really* want to share a topic across teams but do not want badges to appear in all contexts, consider one of the more underutilized reuse mechanisms in DITA, conref push. 

By default, conrefs and conkeyrefs "pull" referenced content into the corrent topic. Conref and conkeyref push insert referenced content into a specific location in a target topic. 

For example, let's say that a topic named `lag-props.dita` contained the following section.

```xml
<section>
  <title>Conref push example</title>
  <p id="p_first-para">The badge should be inserted above this paragraph. </p>
  <p>. . . </p>
</section>
```

In its current state, this markup generates the following output.

![Section without conref push content.](/images/conref-push_1.png)

To "push" a section-level badge into the toopic before the paragraph with @id="first-para", insert the following markup into a fresh topic that is referenced in your publication map as @processing-role="resource-only". 

```xml
<p conaction="pushbefore">
  <image href="images/badge_cloud-compute_small_yes.png">
    <alt>This topic applies exclusively to Cloud Compute.</alt>
  </image>
  <ph> This topic applies exclusively to Cloud Compute.</ph>
</p>
<p conaction="mark" conref="Untitled1.dita#untitled/p_first-para" />
```

The first paragraph instructs the DITA processor to insert the contents of this paragraph *before* the target paragraph element. The second paragraph specifies that target  insertion point, in this case `<p id="p_first-para">The badge should be inserted above this paragraph.</p>`. 

![Section with conref push content.](/images/conref-push_2.png)

This would be the location where you would normally insert a section-level badge manually.line with @conaction="mark" specifies the target insertion point, the paragraph with @id="p_first-line".

As with many of these gee-whiz features in DITA, you need to weight the benefits of implementing conref push against the complexity that it introduces. 

## Conclusion

