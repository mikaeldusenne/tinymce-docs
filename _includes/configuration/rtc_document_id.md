## `rtc_document_id`

The RTC plugin requires a unique identifier for editor content to enable collaboration, known as the document ID. The identifier set by the integrator is used by the RTC server as a permanent reference for the content. {{site.companyname}} recommends using the same unique ID used by your server where possible, such as the unique page or document ID from a Content Management System (CMS).

> **Warning**: Do not reuse the document ID for different documents, otherwise content will be overwritten. Each document must have a unique identifier.

When a client (user) connects:
* If the document ID already exists, the most recent version of the content is sent to the client's editor.
* If the document ID does not exist, the client uploads the initial content as the first version of that document.

> **Warning**: If the content is changed outside of an RTC session, a new document ID must be generated. Changes made outside the RTC session will be overwritten by the content on the RTC server during the next collaboration session.

{% if plugincode != "rtc" %}
Required plugin
: [Real-time Collaboration (`rtc`)]({{site.baseurl}}/plugins/premium/rtc/)
{% endif %}

Type
: String

### Example: Using `rtc_document_id`

This example shows the minimum required configuration for the Real-time Collaboration plugin, including the `rtc_document_id` option.

{% include rtc/rtc-min-configuration-example.md %}
