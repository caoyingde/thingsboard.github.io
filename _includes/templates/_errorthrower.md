# ERROR: You must define a {{ include.missing\_block }} block

{: style="color:red" }

This template requires that you provide text that . The text in this block will be displayed under the heading .

To get rid of this message and take advantage of this template, define the `{{ include.missing_block }}` variable and populate it with content.

```text
{% raw %}{%{% endraw %} capture {{ include.missing_block }} {% raw %}%}{% endraw %}
Text that {{ include.purpose }}.
{% raw %}{%{% endraw %} endcapture {% raw %}%}{% endraw %}
```

