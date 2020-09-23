<div align="center">

## Basic Cross\-Frame Javascript Tutorial


</div>

### Description

After helping to script extended events for a multi-framed (12 frames!) window, I am puting this together before I forget this myself!
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Rabid Nerd Productions](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/rabid-nerd-productions.md)
**Level**          |Intermediate
**User Rating**    |4.3 (26 globes from 6 users)
**Compatibility**  |
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__2-68.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/rabid-nerd-productions-basic-cross-frame-javascript-tutorial__2-2130/archive/master.zip)





### Source Code

<P align=center><FONT size=5>Cross-frame Javascript Tutorial<BR><FONT size=1>by
Herbert L. Riede, Programmer, WinDough.com, Inc.</FONT></FONT></P>
<P align=left><FONT face=Arial size=2>After creating extensive code for a window
with a dozen frames, I thought that submitting this article, even if only for my
future reference, would come in handy to someone. </FONT></P>
<P align=left><STRONG>Myth #1: Frames are complicated</STRONG></P>
<P align=left>While frames are not always ideal for many designs, they do
sometimes come in handy with specialized applications.</P>
<P align=left>Let's take a look at a fictional frameset:</P>
<P align=left><FONT face=System><FONT>&lt;frameset cols="100,*" border="0"
framespacing="0" frameborder="NO" <FONT
color=#339966>onbeforeunload="areyousure();"</FONT>&gt;<BR>&nbsp;&nbsp;&nbsp;
&lt;frameset rows="120,*,300,*,10"&nbsp; border="0" framespacing="0"
frameborder="NO"&gt;<BR>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;frame
name="logo" src="My100x120Logo.html" marginwidth="0" marginheight="0"
scrolling="no" frameborder="0"
noresize&gt;<BR></FONT>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;frame
name="spacer1" src="Spacer.html" marginwidth="0" marginheight="0" scrolling="no"
frameborder="0" noresize&gt;&nbsp;<BR></FONT><FONT
face=System>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;frame name="menu"
src="menu.html" marginwidth="0" marginheight="0" scrolling="no" frameborder="0"
noresize&gt;<BR>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;frame
name="spacer2" src="Spacer.html" marginwidth="0" marginheight="0" scrolling="no"
frameborder="0" noresize&gt;<BR>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&lt;frame name="notice" src="Notice.html" marginwidth="0" marginheight="0"
scrolling="no" frameborder="0" noresize&gt;<BR>&nbsp;&nbsp;&nbsp;
&lt;/frameset&gt;<BR>&nbsp;&nbsp;&nbsp; &lt;frame name="mainwindow"
src="content.html" marginwidth="0" marginheight="0" scrolling="yes"
frameborder="0"&gt;<BR>&lt;/frameset&gt;</FONT></P><FONT face="Times New Roman">
<P align=left>The first tag is the FRAMESET tag. It specifies two columns, one
is 100 pixels wide, and the other takes up the rest of the width. There is to be
no space between the two frames, no border, and before the frameset is unloaded,
you wish to execute the JavaScript function areyousure().</P>
<P align=left><STRONG><EM>onbeforeunload() is specific to Internet
Explorer.</EM></STRONG></P>
<P align=left>The second tag is a FRAMESET tag as well.. It will split up the
100 pixel wide column in the previous FRAMESET. It defines 5 rows, with the
first one 120 pixels high, the <EM>third</EM> one&nbsp;300 pixels high, and the
<EM>fifth</EM> one 10 pixels high.<BR>The second and fourth row will
<EM><U>evenly split</U></EM> any remaining vertical pixels left, if any.</P>
<P align=left>The next five tags assign the attributes to the five rows in the
first column.</P>
<P align=left>The next tag is necessary to close the inner frameset for the
first column. (&lt;/FRAMESET&gt;)</P>
<P align=left>The next tag is a FRAME tag that assigns ALL of the second column
to one page, and unlike all of the other frames, it enables scrolling, if
necessary.</P>
<P align=left>The FRAMESET map looks like this:</P>
<P align=left>&nbsp;&nbsp;
<U>LOGO&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </U>|<BR>&nbsp;&nbsp;
<U>SPACER1&nbsp;&nbsp;&nbsp;</U>|<BR>&nbsp;&nbsp;
<U>MENU&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</U>|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
MAINWINDOW<BR>&nbsp;&nbsp; <U>SPACER2&nbsp;&nbsp;&nbsp;</U>| <BR>&nbsp;&nbsp;
NOTICE&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|</P>
<P align=left>Most tuorials will show you simple stuff like navigating the
"mainwindow" frame&nbsp;from, say, the "menu" frame.</P>
<P align=left><FONT face=System>&lt;a href="anotherpage.html"
target="mainwindow"&gt;&nbsp;&nbsp; -OR-</FONT></P>
<P align=left><FONT face=System>top.mainwindow.document.location.href=
"anotherpage.html";</FONT></P>
<P align=left><FONT>But what if you want to set a variable in another frame? Or
run a function in another frame? Just as simple:</FONT></P><FONT
face=System><FONT face=System>
<P align=left><FONT face="Times New Roman">The first one runs menuClicked() in
the "mainwindow" frame, the second sets "mainwindow" frame's myvariable to
1.</FONT></P>
<P align=left>&lt;a href="javascript:doNothing();"
onClick="top.mainwindow.menuClicked(1); return false;"&gt; -OR-</FONT></P>
<P align=left><FONT face=System>&lt;a href="javascript:doNothing();"
onClick="top.mainwindow.myvariable = 1; return false;"&gt;</FONT></P>
<P align=left>[NOTE: doNothing() is usually a Javascript programmer's junk
function, which contains no commands but still exists in each page's
javascript]</P>
<P align=left><FONT face="Times New Roman">Now what if you have one of your
pages, say content.html, load a frameset of it's own? And you want to check to
see is it has been loaded before you try to address the frames? OK, let's assume
the content.html will split into two frames, named "topcontent" and
"bottomcontent".. Now say you want the "logo" frame to have a link that loads
something into "bottomcontent" if it exists, or into the entire "mainwindow" if
it doesn't:</FONT></P>
<P align=left>function LoadCopyright() {<BR>if (top.mainwindow.bottomcontent)
{<BR>&nbsp;
top.mainwindow.bottomcontent.document.location.href="Copyright.html";<BR>} else
{<BR>&nbsp; top.mainwindow.document.location.href = "Copyright.html";<BR>}</P>
<P align=left>&lt;A href="javascript:doNothing();" onClick="LoadCopyright();
return false;"&gt;</P>
<P align=left><FONT face="Times New Roman">It took more typing to explain it
than it did to DO it... Of course you need to surround javascript functions in a
&lt;SCRIPT&gt; tag, and each &lt;A href...&gt; needs an &lt;/A&gt; after the
text or image you use for your link...</FONT></P>
<P align=left><FONT face="Times New Roman">Now to a neat "Stu<a href=""></a>pid FrameSet Trick"
only available in IE using the FRAMESET or BODY tag's <b><i>onbeforeunload="areyousure();";</i></b> property:</FONT></P>
<P align=left>function areyousure() {<BR>event.returnValue = "Are you sure you
want to miss out on [My Offer]?";<BR>}</FONT></P>
<P align=left>This has great use in a frameset, because the viewer will only be
asked if they:<BR>A. Refresh the entire window<BR>B. Visit a site that breaks
out of the frameset<BR>C. Clicks the Back button to exit your site<BR><STRONG>D.
Clicks the 'X' Close button</STRONG></P>
<P align=left>Another neat side-effect is that if they click "Cancel", (to stay
at your site) NOTHING happens! If you use "onunload", the window closes and you
need to re-open the window!</P>
<P align=left>You can see all of this functionality in it's full glory where I
developed it at:<BR><A
href="http://www.windough.com">http://www.windough.com</A> </P>
<P align=left>Please note that what I present here is simplified and 'common
knowledge' of advanced Javascript programmers. You may develop based on this
tutorial, but you may not use code from Windough.com.</P>
<P align=left>If you have any comment or questions, please don't hesitate to
post them. I enjoy helping people.</P>
<P align=left>If this was of any use to you,<STRONG> please Vote</STRONG>.. I
don't expect to win, but&nbsp;positive votes help the ego now and then :)</P>
<P align=left>Also, if you have any other tutorial suggestions, please comment
here as well.</P>
<P align=left>Herbert Riede<BR>Programmer, WinDough.com,
Inc.</P></FONT>

