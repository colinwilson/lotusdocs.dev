---
weight: 527
title: "Feedback Widget"
description: "How to configure the Feedback Widget so visitors can rate or comment on your site's content."
icon: reviews
date: 2023-08-08T23:33:15+00:00
lastmod: 2023-08-08T23:33:15+00:00
draft: true
images: []
---

The feedback plugin integrates with Google or Plausible Analytics to allow your visitors to provide feedback on your site's content.

![Feedback Widget Initial](https://res.cloudinary.com/lotuslabs/image/upload/v1692284302/Lotus%20Docs/images/feedback_widget_init_kplua6.svg)

## Why use web analytics to collect feedback?

Short answer? Because it's **FREE**! Other benefits include:

- No need to sign up to yet another service just to collect basic visitor feedback.
- Easy to configure. Once Google or Plausible Analytics (or both) are configured in `hugo.toml`, the Feedback Widget it ready to go.
- [No limit](https://support.google.com/analytics/answer/9267744) on the number of events that can be collected.


## How it works

The Feedback Widget works by leveraging custom events:

- **Google Analytics v4** via [Custom events](https://support.google.com/analytics/answer/12229021)
- **Plausible Analytics** via [Custom event goals](https://plausible.io/docs/custom-event-goals)

The above events send visitor interactions from the Feedback Widget to the analytics service.

When enabled, the widget appears at the bottom of every content page. Once a visitor answers the initial call-to-action ('**Was this page helpful?**') **Yes** or **No**, a positive or negative feedback form is presented.

<div class="row flex-xl-wrap pb-1">
<div id="list-item" class="col-md-6 col-12 py-2">

![Positive Feedback Form](https://res.cloudinary.com/lotuslabs/image/upload/v1692290308/Lotus%20Docs/images/lotusdocs_positive_feedback_form_mod_uh9s3d.webp "**Positive Feedback Form**")

</div>

<div id="list-item" class="col-md-6 col-12 py-2">

![Negative Feedback Form](https://res.cloudinary.com/lotuslabs/image/upload/v1692290397/Lotus%20Docs/images/lotusdocs_negative_feedback_form_mod_rqjqi4.webp "**Negative Feedback Form**")

</div>
</div>

The visitor can now choose an option and submit it with an optional comment.

## Configure your analytics for Custom Events

**TBA**

## How to configure the Feedback Widget

The Feedback Widget is configured via the `[params.feedback]` parameter:

{{< tabs tabTotal="3">}}
   {{% tab tabName="hugo.toml" %}}

   ```toml
    [params.feedback]
        enabled = true                                                                   # default / not set = false
        positiveEventName = "Positive Feedback"                                          # optional
        negativeEventName = "Negative Feedback"                                          # optional
        positiveFormTitle = "What did you like?"                                         # optional
        negativeFormTitle = "What went wrong?"                                           # optional
        successMsg = "Thank you for helping to improve our documentation!"       # optional
        errorMsg = "Sorry! There was an error while attempting to submit your feedback!" # optional
        positiveForm = [
          ["Accurate", "Accurately describes the feature or option."],
          ["Solved my problem", "Helped me resolve an issue."],
          ["Easy to understand", "Easy to follow and comprehend."],
          ["Something else"]
        ]
        negativeForm = [
          ["Inaccurate", "Doesn't accurately describe the feature or option."],
          ["Couldn't find what I was looking for", "Missing important information."],
          ["Hard to understand", "Too complicated or unclear."],
          ["Code sample errors", "One or more code samples are incorrect."],
          ["Something else"]
        ]
   ```

   {{% /tab %}}
   {{% tab tabName="hugo.yaml" %}}

   ```yaml
    params:
        feedback:
            enabled: true
            positiveEventName: Positive Feedback
            negativeEventName: Negative Feedback
            positiveFormTitle: What did you like?
            negativeFormTitle: What went wrong?
            successMsg: Thank you for helping to improve our documentation!
            errorMsg: Sorry! There was an error while attempting to submit your feedback!
            positiveForm:
                - - Accurate
                  - Accurately describes the feature or option.
                - - Solved my problem
                  - Helped me resolve an issue.
                - - Easy to understand
                  - Easy to follow and comprehend.
                - - Something else
            negativeForm:
                - - Inaccurate
                  - Doesn't accurately describe the feature or option.
                - - Couldn't find what I was looking for
                  - Missing important information.
                - - Hard to understand
                  - Too complicated or unclear.
                - - Code sample errors
                  - One or more code samples are incorrect.
                - - Something else
   ```

   {{% /tab %}}
   {{% tab tabName="hugo.json" %}}

   ```json
    {
        "params": {
            "feedback": {
                "enabled": true,
                "positiveEventName": "Positive Feedback",
                "negativeEventName": "Negative Feedback",
                "positiveFormTitle": "What did you like?",
                "negativeFormTitle": "What went wrong?",
                "successMsg": "Thank you for helping to improve our documentation!",
                "errorMsg": "Sorry! There was an error while attempting to submit your feedback!",
                "positiveForm": [
                    [
                        "Accurate",
                        "Accurately describes the feature or option."
                    ],
                    [
                        "Solved my problem",
                        "Helped me resolve an issue."
                    ],
                    [
                        "Easy to understand",
                        "Easy to follow and comprehend."
                    ],
                    [
                        "Something else"
                    ]
                ],
                "negativeForm": [
                    [
                        "Inaccurate",
                        "Doesn't accurately describe the feature or option."
                    ],
                    [
                        "Couldn't find what I was looking for",
                        "Missing important information."
                    ],
                    [
                        "Hard to understand",
                        "Too complicated or unclear."
                    ],
                    [
                        "Code sample errors",
                        "One or more code samples are incorrect."
                    ],
                    [
                        "Something else"
                    ]
                ]
            }
        }
    }
   ```

    {{% /tab %}}
{{< /tabs >}}

## Configuration Options

The following options are available for the Feedback Widget:

### Event Name

This option sets the name of the event that's sent to the web analytics service:

- **`positiveName`** - The name of the positive event e.g. `Positive Feedback` (**default**)

- **`negativeName`** - The name of the negative event e.g. `Negative Feedback` (**default**)

{{% alert context="info" text="**Note** - For **Google Analytics v4** (per [Google's recommendations](https://support.google.com/analytics/answer/13316687)), before an event is sent, Lotus Docs converts its name to lowercase letters, and replaces spaces with an underscore. e.g. `Positive Feedback` is converted to `positive_feedback`." /%}}

### Form Title

This option sets the title for each form:

- **`positiveFormTitle`** - The title of the positive feedback form e.g. `What did you like?` (**default**)

- **`negativeFormTitle`** - The title of the negative feedback form e.g. `What went wrong?` (**default**)

### Form Success / Error Messages

Messages displayed after feedback is submitted:

- **`successMsg`** - The message displayed after feedback has been successfully sent e.g. `Thank you for helping to improve our documentation!` (**default**)

- **`errorMsg`** - The message displayed if the widget fails to submit feedback e.g. `Sorry! There was an error while attempting to submit your feedback!` (**default**)

### Form Feedback Options

An array of options for each feedback form. The first item in each nested array sets the name of the feedback option/rating. The second item sets the description of that feedback option/rating. So `["Solved my problem", "Helped me resolve an issue."]` results in:

![Feedback Form Option](https://res.cloudinary.com/lotuslabs/image/upload/v1692325859/Lotus%20Docs/images/lotusdocs_feedback_form_option_mpskqm.webp)

The feedback option name, `Solved my problem` is sent as a parameter of the [event name](#event-name).

- **`positiveForm`** - A nested array consisting of positive feedback rating names and their optional descriptions e.g. `["Accurate", "Accurately describes the feature or option."]`.(**default**)

- **`negativeForm`** - A nested array consisting of negative feedback rating names and their optional descriptions e.g. `["Code sample errors", "One or more code samples are incorrect."]`.(**default**)