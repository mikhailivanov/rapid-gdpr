---
description: One time installation steps.
---

# Installation

## Enable Individual object

Rapid GDPR uses a new standard Salesforce object named _Individual_. You can read more about the object [here](https://help.salesforce.com/articleView?id=individuals_store_data_privacy.htm).

You must enable _Individual_ object before installing Rapid GDPR managed package. Follow the steps to enable it:

1. From _Setup_, enter _Data Protection and Privacy_ in the _Quick Find_ box, and then select **Data Protection and Privacy**.
2. Click **Edit** and select _Make data protection details available in records_ and click **Save**.

## Register My Domain

Rapid GDPR contains a set of Lightning components. For Salesforce Classic the components embedded into a Visualforce pages. And Lightning components require _My Domain_ feature to be enabled.

Enable _My Domain_ if it is not enabled yet. To do this follow the [steps](https://help.salesforce.com/articleView?id=domain_name_define.htm&type=5).

## Install Rapid GDPR app from AppExchange

* Go to [AppExchange](https://appexchange.salesforce.com) and click **Get In Now** button.
* Login to your Org with Administrator credentials  .
* Select _Install for All Users_ option and click **Install** button.

## Create and setup a Salesforce Site

* If you haven't created a public Salesforce Site yet then create a new one. If you already have it created than you can use existing one. To create a public Salesforce Site follow the [steps](https://help.salesforce.com/articleView?id=sites_creating_and_editing_sites.htm).
* Once the Salesforce Site is created click **Public Access Settings** button to open the _Profile_ page for your _site profile_. This page includes all the functionality for viewing and editing profile permissions and settings.
* On the _Profile_ page go to the _Visualforce Page Access_ page or related list and click **Edit** button.

  Select _RGDPR.Privacy_ option from the _Available Visualforce Pages_ list and click **Add** button. Click **Save** button. Go back to the _Profile_ page.

* Click **Edit** button. Set read access to _Documents_ in _Standard Object Permissions_ section.

## Associate Salesforce Site with Rapid GDPR fields.

Set Salesforce Site URL for _Privacy Page Link_ and _Privacy Page URL_ fields.

* From Setup, enter _Sites_ in the Quick Find box, then select **Sites**.
* Highlight Salesforce Site URL from _Site URL_ column and copy it to a clipboard.
* Choose _Rapid GDPR_ app from a list of Salesforce apps. Open the app's **Setup** tab if it wasn't opened automatically. If you can't find the Setup tab in Lightning Experience then [read this](installation.md#opened-rapid-gdpr-app-in-lightning-experience-but-setup-tab-is-not-there), please.
* Click on **General** subtab. Paste Salesforce Site URL into _URL_ field of _Force.com Site_ section.
* Click **Save** button.

## Setup sharing settings for Individual object

* From Setup, enter _Sharing Settings_ in the Quick Find box, then select **Sharing Settings**.
* Enable [External Organization-Wide Defaults](https://help.salesforce.com/articleView?id=security_owd_external_setting.htm).
* Click **Edit** button in _Organization-Wide Defaults_ section.
* For _Individual_ object set _Public Read/Write_ in _Default External Access_ column.
* Click **Save** button.

## Modify Lead and Contact page

[Edit](https://help.salesforce.com/articleView?id=accessing_layout_standard.htm) _Lead_ or _Contact_ page layout. 

* Add a new _GDPR_ section. 
* Add _Privacy Page Link_ and _Individual_ fields to the section.
* If you will use the page in Salesforce Classic then
  * Add an additional section right above _GDPR_ section. Name it _Consents Given_. Uncheck _Detail Page_ and _Edit Page_ checkboxes for _Display Section Header On_ field. Select _1-Column_ layout. Click **OK** button.
  * Drag and drop _Consents Given_ Visualforce page to the _Consents Given_ section.
* If you will use the page in Lightning Experience then [edit](https://help.salesforce.com/articleView?id=lightning_app_builder_customize_lex_pages.htm) Lead or Contact page.
  * Add _ConsentsGiven_ component on the page.

## Modify Individual page

[Edit](https://help.salesforce.com/articleView?id=accessing_layout_standard.htm) _Individual_ page layout. 

* Add a new _GDPR_ section. 
* Add _Profiling Allowed_ field to the section.

## Prepare Leads and Contacts

Create and attach _Individual_ records to existing _Leads_ and _Contacts_. Generate unique secure IDs for all existing _Leads_ and _Contacts._ This unique secure IDs will be stored in _Secure ID_ field and used to generate unique privacy page URL for each _Lead_ or _Contact._

* Chose _Rapid GDPR_ app from a list of Salesforce apps. Open the app's **Setup** tab if it wasn't opened automatically. If you can't find the Setup tab in Lightning Experience then [read this](installation.md#opened-rapid-gdpr-app-in-lightning-experience-but-setup-tab-is-not-there), please.
* Click on **General** subtab.
* Click **Create Individuals & Generate Secure IDs** button in _Individuals_ section.

{% hint style="info" %}
It takes some time in a background to process all _Leads_ and _Contacts_. Once it is done you will receive an acknowledgement email. Individual records will be created and attached to _Leads_ and _Contacts_ records and for each record a _Secure ID_ field will be populated.
{% endhint %}

{% hint style="warning" %}
This background process may fail because of Salesforce Limits. Usually it happens when there are a lot of automation processes \(Apex Triggers, Process Builder Flows, etc.\) run on Lead or Contact record updates. By default it updates 50 records simultaneously.

If you receive an error in the acknowledgement email then you can try to decrease a batch size in _Batch Size_ field and click **Create Individuals & Generate Secure IDs** button again.
{% endhint %}

## FAQ

### Opened _Rapid GDPR_ app in _Lightning Experience_ but _Setup_ tab is not there.

Make sure you finished a setup of _My Domain_. If it's so then go to your user profile and make _Setup_ tab visible.

