# rendering
How the browser renders a web page

The process of displaying pages can be broken down into the following main stages:

1. Start parsing HTML

The first step in this parsing process is to break the HTML into tokens that represent start tags, end tags, and their content.
From this it builds the DOM.

2. Obtaining external resources

When the parser encounters an external resource such as a CSS or JavaScript file, it tries to get it. 
The parser will continue to run as the CSS file is loaded, but it will block rendering until the file is loaded and parsed.

3. Parsing CSS and Generating CSSOM

Similar to HTML and DOM files, when CSS files are loaded, they must be parsed and converted to a tree - this time the CSSOM. 
It describes all the CSS selectors on the page, their hierarchy and their properties.

The difference between CSSOM and DOM is that it cannot be built incrementally, as CSS rules can overwrite each other at different points due to specificity.
This is why loading CSS blocks rendering, because until all the CSS has been parsed and the CSSOM is built, the browser cannot know where and how to place each element on the screen.

4. JavaScript execution

How and when JavaScript resources are loaded determines when at some point they will be parsed, compiled, and executed. Different browsers use different JavaScript engines to accomplish this task.

5. Combining DOM and CSSOM to build a render tree

The render tree is a combination of DOM and CSSOM and represents everything that will be displayed on the page. This does not necessarily mean that all nodes in the render tree will be visually present.

6. Calculation of the layout and rendering of the result

Now that we have a complete render tree, the browser knows what to render, but it doesn't know where to render. Hence, the page layout needs to be calculated. The render engine traverses the render tree, starting at the top and going down, calculating the coordinates at which each node should be displayed.

Once that's done, the final step is to use this layout information to draw the pixels on the screen.
