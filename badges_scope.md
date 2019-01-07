# Badging and scope 

When we content developers are looking at badged content in a DITA editor, we see where `<topic>` and `<section>` elements begin and end. We see the scope of the element relative to the topic displayed in our DITA editor. Unfortunately, these topic and section boundaries are neither visible nor recoverable to customers. In a running PDF, where does the current "topic" or "section" end? If we chunk multiple source topics so they generate one HTML5 page in output, wouldn't the topic boundaries be misleading? If I insert a topic-level badge to indicate that no content in the topic applies to a particular product, what happens if another writer conref's a section from my topic? That conref'd section has no section badge. Messy stuff. 

You need to scope your topic-level or section-level badges to what you expect the customer will see on the page or in a browser, not what we see in our DITA sources. How do you figure that out? You test it out and show it to people in all your generated output formats. 

Is it technically possible to create badges scoped to the level of DITA elements, for example paragraphs, figures, table rows, or phrases? Yes. 

Practically, attempting to use the same badges for elements that you use for topics or sections can create a visual and logical train wreck. Teams that have successfully worked with badged documentation for multiple releases turn to `<note>` elements or in-line explanations for anything more granular than sections. Others use DITA flagging to color-code platform-specific information. 

Document the logic and the scoping of your badging strategy. 