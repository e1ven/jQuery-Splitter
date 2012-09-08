jQuery Splitter

This is a forked copy from from http://methvin.com/splitter/
I've updated his splitter just a bit, to make it happier on modern jQuery.

His version blows on on jQuery > 1.5. This version works on 1.7, which is the most recent as of posting.

See also:
http://stackoverflow.com/questions/10097458/splitter-js-wont-work-with-new-versions-of-jquery

To fix it the right way, you'd want to comment out lines 63 and 64 - They are triggering an infinite event loop.
Then, add e.stopPropagation(); on line 199, and stop the splitter resize event from bubbling back up to the window, which triggers a resize event, which triggers a resi...
Yeah.
This unfortunately stops the resize recursion entirely. To fix it right, we'd probably want to add something that replaces 63/64 to do it without triggering more resizes.

In the meantime, this should work around it, mainly by use of try/catch blocks.
