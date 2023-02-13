

# html module
#python/html


> ==`html` module== is used for escaping reserved characters from HTML markup

This module has a function `escape(s, quote=True)`. If the optional flag quote is true, the characters `"` and `'` are also translated
```python
import html
html.escape('x > 2 && x < 7')
# 'x &gt; 2 &amp;&amp; x &lt; 7'
```



