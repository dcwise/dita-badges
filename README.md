# Content Bading in DITA
OASIS DITA Adoption whitepaper on content badging.

Badging is a popular topic on several fronts. The three most popular forms of badging are:

* *Achievement badging*: organizations set up collections of social media "badges" to recognize the involvement and achievement in employees, partners, and customers. Imagine if someone developed a technical certification program for DITA and awarded badges to program participants who passed tests for particular features.  

  ![DITA conref push expert](/images/badge_dita_conref-push.png)  ![DITA reltables expert](/images/badge_dita_reltables.png)  ![DITA scoped keys expert](/images/badge_dita_scopedkeys.png)

* *Status badging*: collaborative development platforms allow administrators to incorporate macros in their portal pages that display the current status of builds, workflow stages, contributions, and test coverage.

  ![Test status](/images/badge_tests_pass-fail.svg)
  
  ![Build status passing](/images/badge_build_passing.svg)

  ![Build status unknown](/images/badge_build_unknown.svg)

  ![Build status failing](/images/badge_build_failing.svg)

  ![Build status failure](/images/badge_build_failure.svg)
    
* *Content badging*: content development organizations often decide to have one publication document a collection of closely-related products. Content badges alert readers that particular topics, sections, or elements in the publication are or are not applicable to a specific product or release version. 

  ![Topic not applicable to Cloud Compute](/images/badge_cloud-compute_no.png) Topic not applicable to Cloud Compute

  ![Topic applicable only to Cloud Compute](/images/badge_cloud-compute_yes.png) Topic applicable only to Cloud Compute

  ![Not applicable to Cloud Compute](/images/tag_cloud-compute_not-supported.svg)
  
  ![Applicable only to Cloud Compute](/images/tag_cloud-compute_supported.svg)

  Content badging is a medium- to high-risk content strategy for compound publications, that is, publications that document more than one product or version.


## A typical use case for content badging

A startup named CloudSquared develops resource monitoring software for cloud-based frameworks. For its first product, Cloud Compute Monitoring, the content development team develops a complete documentation set for this one product.

![Use case - one product](/images/use-case_1.png)

A year later CloudSquared releases Cloud Net Monitoring so the content development team uses DITA conditional filtering to publish separate Cloud Compute and Cloud Net publications. 

![Use case - two products](/images/use-case_2.png)

Content developers assign filtering attributes such as `@product="cloud-compute"` or `@product="cloud-net"` to topics, sections, or elements that need to be filtered OUT of a product-specific deliverable. 

The following year, Cloud Connect completes the monitoring suite and the writing team uses conditional filtering to publish three separate publications. 

![Use case - three products](/images/use-case_3.png)

Content developers add the filtering attribute `@product="cloud-connect"` to those topics, sections, or elements that need to be filtered OUT of the other two product-specific deliverables. 

Six months after launch, Marketing receives feedback that emphasizing the common design and services across the three suite components will enhance customer perception that CloudSquared can consolidate its achievements and move on to new product lines. Toward that end, Product Management requests that the content development team consolidate the three, product-specific publications into one, multi-product publication. All generic and product-specific information appears in the same output.

![Use case - one combined product](/images/use-case_4.png)

When transitioning from conditional filtering to badging, note that filtering metadata is *useful* in identifying where product-specific information lives in your sources but *useless* as markup to implement badging. 

Filtering markup: 

```xml
<p @product="cloud-connect">Cloud Connect is great.</p>
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

The real challenges with badging involve logic, aligning product-specific or version-specific content to visible badges in your sources. 

 
## Badge design and implementation

These sorts of logic and planning problems are best approached visually. Design exercises such as card sorting or affinitization depend upon multiple team members seeing all the variables and iteratively testing various arrangements or groupings. Similarly, making a first, complete pass designing all the content badges that you might need will accelerate the process of developing and refining the logic of your badging. If you want to code the badges up in a DITA library great, but that is not necessary for your opening discussions. Sticky notes or 3x5 cards do the job early on. 

Regardless of how you implement badging in DITA, the content badges themselves have four basic components:

Visual cue | Content ID | Content scope | Content switch
-----------|------------|----------------|--------------------
![Icon cue](/images/badge_cloud-net_small_yes.png)<br />![Tag cue](/images/cue_tags.png)|Cloud Net|This section | applies to . . . 
![Icon cue](/images/badge_cloud-net_small_no.png)<br />![Tag cue](/images/cue_tags.png)|Cloud Net|This topic  | does not apply to . . . 

Whether you and your graphic designers choose icons or tags, build a library of reusable DITA badges is straight-forward. Consider starting with just one library for badging, call it `library_content-badges.dita`. 

Markup | Rendered presentation
-------|----------------------
`<p id="p_badge_icon_cloud-connect_section_yes">`<br />`  <image href="images/badge_cloud-connect_small_yes.png">`<br />`    <alt>This section applies exclusively to Cloud Connect.</alt>`<br />`  </image>`<br />`  <ph> This section applies exclusively to Cloud Connect.</ph>`<br />`</p>`<br />|![Icon rendered](/images/render1.png)
`<p id="p_badge_tag_cloud-compute_topic_no">`<br />`<image href="images/tag_cloud-compute_not-supported.svg">`<br />`<alt>This topic does not apply to Cloud Compute.</alt>`<br \>`</image>`<br />`<ph> This topic does not apply to Cloud Compute.</ph>`<br />`</p>`|![Icon rendered](/images/render2.png)

Time you spend organizing these badge definitions in the library helps content developers when they view them in a DITA editor. 

![Badge library entries](/images/library1.png)

![Badge library entries](/images/library2.png)


## Establishing logic

If your badges are crisply defined and you apply them logically and consistently to your content, badging works. The first step toward providing logic for your publication is having a global statement about non-badged content.

> Unless otherwise indicated with a product badge such as ![Icon cue](/images/badge_cloud-net_small_no.png), all content applies equally to CloudSquared Cloud Compute, Cloud Net, and Cloud Connect. 

This global statement allows you to add exclusionary badges as sparingly as possible throughout your publication. The more simple your logic for inserting a badge, the more consistently content developers will apply and maintain them. In this scenario, you do not need to insert any inclusive badges, only exclusive ones (not unlike your DITA filtering attributes). 
  
![Tag exclude topic](/images/tag_cloud-compute_not-supported.svg)

![Tag exclude topic](/images/tag_cloud-net_not-supported.svg)

![Tag exclude topic](/images/tag_cloud-connect_not-supported.svg)


## Badging and scope 

When we content developers are looking at badged content in a DITA editor, asserting that a particular badge applies exclusively to this `<topic>` or that `<section>` is perfectly clear. Unfortunately the topic and section boundaries that we see in XML source are not visible or recoverable to customers. In a running PDF, where does the current "topic" or "section" end? If we chunk multiple source topics so they generate one HTML5 page in output, wouldn't the topic boundaries be misleading? If I insert a topic-level badge to indicate that no content in the topic applies to a particular product, what happens if another writer conref's a section from my topic? That conref'd section has no section badge. Messy stuff. 

You need to scope your badges (topic or section) to what the customer sees, not to our DITA sources. 

Is it technically possible to create badges scoped to the level of DITA elements, for example paragraphs, figures, table rows, or phrases? Yes. 

Practically, attempting to use the same badges for elements that you use for topics or sections can create a visual and logical train wreck. Teams that have successfully worked with badged documentation for multiple releases turn to `<note>` elements or in-line explanations for anything more granular than sections. Others use DITA flagging to color-code platform-specific information (accessibility - ouch). 

Document the logic and the scoping of your badging strategy. 

## Going on a test drive 

Once you have normed on your logic and authoring guidelines, apply them to a small publication. Badging is messy stuff and you do not want to implement it for a complete doc set until you have received a "go-ahead" from your stakeholders. When they actually see a sample of your "badged" documentation, they may have objections or concerns that you had not factored into your design. 

* *UXD*: "Shouldn't the graphic design of the badges conform to the new company UX guidelines?"
* *Support*: "Some customers are not careful readers and tend to ignore subtleties like these badges. They try something that is not appropriate for their product and then call us. Why are we doing this again? It is increasing our workload."
* *Test engineering*: "When we tested your procedures in the product-specific manuals, we could clearly identify issues with your writing. The new format is interesting, but we are never quite sure whether we are supposed to be testing all product procedures at once or be tiptoeing through the product-specific procedures one at a time." 
* *Software engineering*: "Sometimes the differences between product features are not so cut and dry, not quite so simple as 'supported' or 'not supported'. 
* *Sales*: In pre-sales discussions, handing prospective customers manual that documents three products kinda confuses them if they are interesting in buying one."
* *Marketing*: "I didn't realize that the docs would have so many badges."
* *Legal*: "Our product documentation serves as the definitive product description. If the documentation does not accurately describe the product that the cutomer has purchased, we cannot recognize revebue."

Showing everyone a robust sample of badged documentation generates discussion across the organization about badging and other requirements for product documentation. 

## Placing badges in your topics

Where you place badges is part common sense and team preference. 

Badge type|Placement options
----------|-------------------
Topic|`<topic id="test1">`<br />`<title>Title</title>`<br \>`<shortdesc>Short description</shortdesc>`<br />`<body>`<br />`<p>Topic badge</p>`<br />`</body>`<br />`</topic>`<br /><br />xxx



## Conref references to badge libraries

xxxxx

## Conkeytref references to badge libraries

xxxxx

## Conkeyref push 

xxxxx


 



