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

A product development team releases Version 1.0 of its VMware hypervisor application. The content development team develops the complete documentation set for the VMware version of the product. A year later the same team releases its KVM version. The content development team uses DITA conditional filtering to publish separate VMware and KVM versions of the product documentation from the same DITA sources. A year later, the Hyper-V version of the application is available and the writing team uses conditional filtering to publish a third hypervisor-specific publication. 

One year later Program Management decides that it wants to emphasize the commonality of the product across hypervirsor platforms and would like the content development team to develop one publication that "badges" any differences between the VMware, KVM, and Hyper-V versions of the product. 

= The challenge of badging

DITA writers and architects can be experts at excluding DITA content with conditional filtering, but clueless about how to "badge" that hypervisor-specific content for a unified publication. DITA conditional filtering is actually opposite of badging. 

Conditional processing is not teh same as badging. Exclusuions (filtering) is not the same as badging.


== Badging logic

Establish a baseline . . . this publication supports the following products/features/releases unless otherwise idicated. 

How to read the documentation . . . 

Object + switch = badge

yes = switch/no, ful/partiao/none

The content development team knows where all the hypervisor-specific content 

== Badging design

icon-based badges

label-based badginbg



== Badging scope

Topic = after <abstract> ??

Section = after <section><title>

Element



== Badging governance

If personalization fails . . . 

== Badging and shared topics

xxxx

= Implementation

== Literal badges

xxxxx

== Libraries

<p id-"xxx">
   <image href="xxx.png" 
      <alt>xxxx<alt>
   </image>
This topic/section xxx . . . 
</p>



== Conref references to badge libraries

xxxxx

== Conkeytref references to badge libraries

xxxxx

== Conkeyref push 

xxxxx


 



