---
layout: page
weight: 0
title: Customer Unsubscribes
navigation:
   show: true
---

{% anchor h2 %}
Retrieve Unsubscribes 
{% endanchor %}

Note that you can use *either* the days parameter *or* the start_date and end_date parameter.


{% parameters get %}
 {% parameter 'user' 'Yes' 'Customer must be registered under your account' 'The customer we are retrieving unsubscribes from' %}
 {% parameter 'task' 'Yes' 'Must be set to <em>get</em>' 'This will allow you to retrieve the unsubscribes for the specified customer' %}
 {% parameter 'date' 'No' 'Must be set to 1' 'Retrieves the timestamps, it will return a date in a MySQL timestamp format - YYYY-MM-DD HH:MM:SS' %}
 {% parameter 'method' 'Yes' 'Must be set to <em>unsubscribes</em>' 'Allows you to access unsubscribe functionality' %}
{% endparameters %}


{% apiexample get POST https://api.sendgrid.com/apiv2/reseller.manage api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=unsubscribes&user=customer@example.com&task=get&date=1 %}
  {% response json %}
[
  {
    "email": "email1@domain.com",
    "created": "2009-06-01 19:41:39"
  },
  {
    "email": "email2@domain2.com",
    "created": "2009-06-01 19:41:39"
  }
]
  {% endresponse %}
  {% response xml %}
<unsubscribes>
   <unsubscribe>
      <email>email1@domain.com</email>
      <created>2009-06-10 12:40:30</created>
   </unsubscribe>
   <unsubscribe>
      <email>email2@domain2.com</email>
      <created>2009-06-10 12:40:30</created>
   </unsubscribe>
</unsubscribes>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Delete Unsubscribes 
{% endanchor %}

Since SendGrid does not deliver to unsubscribe addresses, users can remove unsubscribes from their list at any time if re-delivery to an unsubscribed address is desired.


{% parameters delete %}
 {% parameter 'user' 'Yes' 'Customer must be registered under your account' 'The customer we are retrieving unsubscribes from' %}
 {% parameter 'task' 'Yes' 'Must be set to <em>delete</em>' 'This will allow you to delete an unsubscribe record for the specified customer' %}
 {% parameter 'method' 'Yes' 'Must be set to <em>unsubscribes</em>' 'Allows you to access unsubscribe functionality' %}
 {% parameter 'email' 'No' 'Must be an unsubscribe record' 'You must specify the unsubscribe record to remove' %}
{% endparameters %}


{% apiexample delete POST https://api.sendgrid.com/apiv2/reseller.manage api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=unsubscribes&user=customer@example.com&task=delete&email=unsubscribe@sample.com %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}

* * * * *

{% anchor h2 %}
Add Unsubscribes 
{% endanchor %}

Add unsubscribe email records to their account if they need to stop sending email messages to a specific recipient.


{% parameters add %}
 {% parameter 'user' 'Yes' 'Customer must be registered under your account' 'The customer we are retrieving unsubscribes from' %}
 {% parameter 'task' 'Yes' 'Must be set to <em>add</em>' 'This will allow you to add an unsubscribe record for the specified customer' %}
 {% parameter 'method' 'Yes' 'Must be set to <em>unsubscribes</em>' 'Allows you to access unsubscribe functionality' %}
 {% parameter 'email' 'No' 'Must be an unsubscribe record' 'You must specify the unsubscribe record to add' %}
{% endparameters %}


{% apiexample add POST https://api.sendgrid.com/apiv2/reseller.manage api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=unsubscribes&user=customer@example.com&task=add&email=unsubscribe@sample.com %}
  {% response json %}
{
  "message": "success"
}
  {% endresponse %}
  {% response xml %}
<result>
   <message>success</message>
</result>

  {% endresponse %}
{% endapiexample %}
