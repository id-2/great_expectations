---
title: Renderer
---

import TechnicalTag from '@site/docs/reference/learn/term_tags/_tag.mdx';

A Renderer is a class for converting <TechnicalTag relative="../" tag="expectation" text="Expectations" />, <TechnicalTag relative="../" tag="validation_result" text="Validation Results" />, etc. into <TechnicalTag relative="../" tag="data_docs" text="Data Docs" /> or other output such as email notifications or Slack messages.

Every Expectation has its own Renderer(s) that allows that Expectation to be expressed in a human-readable format in Data Docs.  From an architectural/contributor standpoint, Expectations are rendered into an intermediate canonical format and then from there turned into docs and other output (think of it more of a rendering pipeline).  Likewise, Renderers can be used to send Slack messages and email alerts.  Renderers for these purposes are already available in Great Expectations, but you can create custom ones and use them by specifying them in the <TechnicalTag relative="../" tag="action" text="Action" /> that sends the message after <TechnicalTag relative="../" tag="validation" text="Validation" />.

## Relationship to other objects

The most common use of Renderers is to render Expectations and Validation Results into output for Data Docs.  Renderers can also be used to send Slack messages and email alerts.  Great Expectations makes these Renderers available by default.  If you create a <TechnicalTag relative="../" tag="custom_expectation" text="Custom Expectation" />, you may also want to create a custom Renderer for it.

## Use cases

Creating Custom Expectations, including their custom Renderers, is a process that falls outside the Great Expectations Validation workflow.

Great Expectations will use a Renderer behind the scenes if you build Data Docs to view your Expectations. 

If you want to send Slack, email, or other alerts after a Checkpoint runs you will do so by specifying a Renderer in an Action in the Checkpoint's `action_list`.  Renderers will also be used behind the scenes if you update your Data Docs through a Checkpoint Action, or if you rebuild your Data Docs outside the Validation process.

## Access

When looking for Renderers with Expectations, you will find them specified as part of the Python class defining the Expectation.  With alerts and messaging, however, you will specify the Renderer to use in an Action's configuration.  To do this, you will specify a `module_name` and `class_name` indicating the Renderer's Python class under the `renderer` key (found nested under the `action` key) in an Action entry in a Checkpoint's `action_list`.

## Configure

If you need instructions on how to configure the renderer portion of an Action to send a message or alert, please see the relevant guide:

- [How to trigger email as a Validation Action](/docs/oss/guides/validation/validation_actions/how_to_trigger_email_as_a_validation_action)
- [How to trigger Slack notifications as a Validation Action](/docs/oss/guides/validation/validation_actions/how_to_trigger_slack_notifications_as_a_validation_action)
- [How to trigger Opsgenie notifications as a Validation Action](/docs/oss/guides/validation/validation_actions/how_to_trigger_opsgenie_notifications_as_a_validation_action)
