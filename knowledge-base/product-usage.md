# Product Usage

### How can we ask newly added Data Subject for permissions if we add the person to Salesforce manually?

Associate a Privacy Source with Individual and Data Subject checkboxes. Use a workflow or a process of Process Builder to set checkbox of the Data Subject object.

### We want to add a checkbox "I agree with your privacy policy" to our public website and save the agreed permissions to Salesforce. How to achieve this?

Associate a Privacy Source with Individual and Data Subject checkboxes. Associate your website checkbox with the Data Subject's checkbox. Once the Data Subject will set the checkbox on your website the permissions for the associated Privacy Source will be set for that Data Subject.

### How to ask all existing Data Subjects for permissions?

There is a field Privacy Page URL on candidate object/layout. You can add the field to your own email template. When a candidate receives the email he/she will be able to click the URL and proceed to Privacy Page and set their consents.
To send emails you can use built-in Salesforce feature Mass Email Contacts in Salesforce Classic: https://help.salesforce.com/articleView?id=mass_email_parent.htm or Send List Email in Lightning Experience: https://help.salesforce.com/articleView?id=email_list_email.htm. But note you will be able to send 5000 per/day maximum. So you should divide all your candidates into smaller list views, for ex. by name's first letter, and send each list view on a separate date.
Also, you can use some third-party app for email sending to send to all candidates at one time (e.g., MailChimp: https://appexchange.salesforce.com/listingDetail?listingId=a0N3000000B3byfEAB).

### How to run additional processes once permissions are given by Data Subject?

### Must we export and import again all existing Leads/Contacts to associate them with Individual records and to create unique Privacy Page URLs?


