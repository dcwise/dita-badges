# Badge design and implementation

Logic and planning problems of this sort are best approached visually. Design exercises such as card sorting or affinitization depend upon multiple team members seeing all the variables and iteratively testing various arrangements or groupings. Similarly, making a first, complete pass at designing all the content badges that you might need will accelerate the process of developing and refining the logic of your badging. If you have time to code the badges in a DITA library, that's great -- but sticky notes or 3x5 cards will suffice for team discussions early on. Move the cards around. Tape them to whiteboards. Staple them to printouts of your existing docs. Any exercise that simulates you applying a badge to your content and then asking whether that makes sense is goodness.

Regardless of how you implement badging in DITA, content badges have four basic components:

Visual cue | Content ID | Content scope | Content switch
-----------|------------|----------------|--------------------
![Icon cue](./images/badge_cloud-net_small_yes.png)|Cloud Net|This section | applies to . . . 
![Icon cue](./images/badge_cloud-net_small_no.png)|Cloud Net|This topic  | does not apply to . . . 

Whether you and your graphic designers choose icons or tags, building a library of reusable DITA badges is straight-forward. Consider starting with just one library for badging, call it `library_content-badges.dita`. 

The following markup for a positive badge . . .

```xml
<p id="p_badge_icon_cloud-connect_section_yes">
    <image href="images/badge_cloud-connect_small_yes.png">  
      <alt>This section applies exclusively to Cloud Connect.</alt>
    </image>
    <ph> This section applies exclusively to Cloud Connect.</ph>
</p>
```

. . . generates this badge in output. 

![Icon rendered](./images/render1.png)

The following markup for a negative badge . . . 

```xml
<p id="p_badge_tag_cloud-compute_topic_no">
  <image href="images/tag_cloud-compute_not-supported.svg">
    <alt>This topic does not apply to Cloud Compute.</alt>
  </image>
  <ph> This topic does not apply to Cloud Compute.</ph>
</p>
```

. . . generates this badge in output. 

![Icon rendered](./images/render2.png)

Time that you spend organizing these badge definitions in a DITA library topic has a big payoff for content developers on your team. If writers can easily find the appropriate badge, they'll thank you -- eventually.  

![Badge library entries](./images/library1.png)

![Badge library entries](./images/library2.png)