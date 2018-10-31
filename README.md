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


## Typical use case for content badging

A startup named CloudSquared develops resource monitoring software for cloud-based frameworks. For its first product, Cloud Compute Monitoring, the content development team develops a complete documentation set for this one product.

![Use case - one product](/images/use-case_1.png)

A year later CloudSquared releases Cloud Net Monitoring so the content development team uses DITA conditional filtering to publish separate Cloud Compute and Cloud Net publications. 

![Use case - two products](/images/use-case_2.png)

The following year, Cloud Connect completes the monitoring suite and the writing team uses conditional filtering to publish three separate publications. 

![Use case - three products](/images/use-case_3.png)


Marketing receives feedback that emphasizing the common design and services across the three suite components will enhance customer perception that CloudSquared can consolidate its achievements and move on to new product lines. Toward that end, Product Management requests that the content development team consolidate the three, product-specific publications into one, multiproduct publication.

![Use case - one combined product](/images/use-case_4.png)


## Badge design and implementation

Strange as it may seem, laying out all the badges that you might need will help you to prototype and validate your logic. 

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


 



