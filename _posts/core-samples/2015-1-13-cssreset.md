---
layout: post
category : cssreset
title : css Reset
---
{% include JB/setup %}

###常用的cssreset

<pre><code>
/*reset*/
body, h1, h2, h3, h4, h5, h6, p, dl, dd, form, ul, ol, pre, blockquote, textarea, input, figure {
  margin: 0;
}

ul, ol, th, td, button, textarea, input {
  padding: 0;
}

ul, ol {
  list-style: none;
}

img {
  max-width: 100%;
}

a {
  text-decoration: none;
  color: #000;
}

/*common*/
.clearfix:before,
.clearfix:after {
  content: "";
  display: table;
  clear: both;
}
</code></pre>
		 












































