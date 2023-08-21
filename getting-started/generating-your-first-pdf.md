# Generating your first PDF

The DocuZen API allows you to generate dynamic PDF documents at runtime. Simply send a HTTP request which includes custom data in the request body, and the HTTP response body will include the PDF file data.

### Building the API request

Your API request must include the following parameters:

* Your DocuZen API Key.
  * Visit [Creating an API key](creating-an-api-key.md) to learn how to get your API key.
* The ID of the DocuZen Template you wish to use.
  * If you don't yet have a template, visit [Creating your first template](creating-your-first-template.md).

### Sending the API request

To generate a PDF using the command line, enter the following command (make sure to insert your API key and template ID in the command):

{% tabs %}
{% tab title="macOS" %}
<pre class="language-bash" data-line-numbers data-full-width="false"><code class="lang-bash"><strong>curl --request GET \
</strong>  --url 'https://api.docuzen.co/v1/pdf/generate' \
  --header 'Authorization: Bearer DOCUZEN_API_KEY' \
  --header 'Content-Type: application/json' \
  --data '{"templateId":"DOCUZEN_TEMPLATE_ID","templateData":{"friendsFirstName":"Elliot","friendsLastName":"Chaim"}}' \
  --output docuzen.pdf; open docuzen.pdf;
</code></pre>
{% endtab %}

{% tab title="Windows" %}
{% code lineNumbers="true" %}
```sh
curl --request GET \
  --url 'https://api.docuzen.co/v1/pdf/generate' \
  --header 'Authorization: Bearer DOCUZEN_API_KEY' \
  --header 'Content-Type: application/json' \
  --data '{"templateId":"DOCUZEN_TEMPLATE_ID","templateData":{"friendsFirstName":"Elliot","friendsLastName":"Chaim"}}' \
  --output docuzen.pdf; docuzen.pdf;
```
{% endcode %}
{% endtab %}

{% tab title="Linux" %}
{% code lineNumbers="true" %}
```bash
curl --request GET \
  --url 'https://api.docuzen.co/v1/pdf/generate' \
  --header 'Authorization: Bearer DOCUZEN_API_KEY' \
  --header 'Content-Type: application/json' \
  --data '{"templateId":"DOCUZEN_TEMPLATE_ID","templateData":{"friendsFirstName":"Elliot","friendsLastName":"Chaim"}}' \
  --output docuzen.pdf; xdg-open docuzen.pdf;
```
{% endcode %}
{% endtab %}
{% endtabs %}

If everything worked, the PDF should have opened in your default PDF viewer.

### What happened?

Here's what happened when you ran that command:

1. Your CLI sent a `GET` request to the [DocuZen API](../developer-resources/using-the-docuzen-api/docuzen-api-documentation.md) located at `api.docuzen.co`.
2. The API server received the request, injected the data from the request body into the template, and generated a new PDF document.
3. The API server returned a response to your CLI which included the new PDF document in a binary format, and your CLI saved that to a file called `docuzen.pdf`.

You used the DocuZen API to generate a new PDF document. That's pretty cool!

### Next steps

Now that you've generated your first PDF, you're ready to do more with DocuZen!

* To learn more about what's possible with the DocuZen API, visit the [DocuZen API documentation](../developer-resources/using-the-docuzen-api/).
* You can also use the DocuZen API to generate PDFs with static HTML input. To learn more, visit [Generating PDFs from HTML](../generating-pdfs/generating-pdfs-from-html.md).
