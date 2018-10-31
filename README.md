# dita-badges
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
`<p id="p_badge_icon_cloud-connect_section_yes">`<br />
`  <image href="images/badge_cloud-connect_small_yes.png">`<br />
`    <alt>This section applies exclusively to Cloud Connect.</alt>`<br />
`  </image>`<br />
`  <ph> This section applies exclusively to Cloud Connect.</ph>`<br />
`</p>`<br />|![Icon rendered](/images/render1.png)
xx|zz





Badge + yes

Badge + no
 

## Establishing logic

DITA badging and DITA conditional filtering both depend upon establishing a logic for all the content developers and technical reviewers. 

Happens at two levels:

1. Global

Publications that document multiple products or releases require a global statement that defines the baseline logic. 

Minimal logic:

* All content applies to all platforms unless specified otherwise. 

Better logic:

* All content applies to all platforms specifically excluded. 

2. Local 

Here are the options:

*  , understanding how to exclude (conditional filtering) or include  


# The challenge of badging

DITA writers and architects can be experts at excluding DITA content with conditional filtering, but clueless about how to "badge" that hypervisor-specific content for a unified publication. DITA conditional filtering is actually opposite of badging. 

Conditional processing is not teh same as badging. Exclusuions (filtering) is not the same as badging.


## Badging logic

Establish a baseline . . . this publication supports the following products/features/releases unless otherwise idicated. 

How to read the documentation . . . 

Object + switch = badge

yes = switch/no, ful/partiao/none

The content development team knows where all the hypervisor-specific content 

## Badging design

icon-based badges

label-based badginbg



## Badging scope

Topic = after <abstract> ??

Section = after <section><title>

Element



## Badging governance

If personalization fails . . . 

## Badging and shared topics

xxxx

# Implementation

## Literal badges

xxxxx

## Libraries

<p id-"xxx">
   <image href="xxx.png" 
      <alt>xxxx<alt>
   </image>
This topic/section xxx . . . 
</p>



## Conref references to badge libraries

xxxxx

## Conkeytref references to badge libraries

xxxxx

## Conkeyref push 

xxxxx


 



