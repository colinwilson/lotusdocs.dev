---
weight: 527
title: "Feedback Widget"
description: "How to configure the Feedback Widget so visitors can rate or/and comment on your site's content."
icon: reviews
date: 2023-08-08T23:33:15+00:00
lastmod: 2023-08-08T23:33:15+00:00
draft: true
images: []
---

The feedback plugin integrates with Google or Plausible Analytics to allow your visitors to provide feedback on your site's content.

![Emoticon Icons Illustration](https://res.cloudinary.com/lotuslabs/image/upload/v1692622991/Lotus%20Docs/images/lotusdocs_emoticon_feedback_widget_screenshot_rd_wnj72x.webp)

## Why use web analytics to collect feedback?

Short answer? Because it's **FREE**! Other benefits include:

- No need to sign up to yet another service just to collect basic visitor feedback.
- Easy to configure. Once Google or Plausible Analytics (or both) are configured in `hugo.toml`, the Feedback Widget it ready to go.
- [No limit](https://support.google.com/analytics/answer/9267744) on the number of events that can be collected.


## How it works

The Feedback Widget works by leveraging custom events:

- **Google Analytics v4** via [Custom events](https://support.google.com/analytics/answer/12229021)
- **Plausible Analytics** via [Custom event goals](https://plausible.io/docs/custom-event-goals)

The above events send visitor interactions from the Feedback Widget to the corresponding analytics service.

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
        emoticonTpl = true                                                               # optional
        eventDest = ["plausible","google"]                                               # optional
        emoticonEventName = "Feedback"                                                   # optional
        positiveEventName = "Positive Feedback"                                          # optional
        negativeEventName = "Negative Feedback"                                          # optional
        positiveFormTitle = "What did you like?"                                         # optional
        negativeFormTitle = "What went wrong?"                                           # optional
        successMsg = "Thank you for helping to improve our documentation!"               # optional
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
            enabled: true                                                                 # default / not set = false
            emoticonTpl: true                                                             # optional
            eventDest:                                                                    # optional
                - plausible
                - google
            emoticonEventName: Feedback                                                   # optional
            positiveEventName: Positive Feedback                                          # optional
            negativeEventName: Negative Feedback                                          # optional
            positiveFormTitle: What did you like?                                         # optional
            negativeFormTitle: What went wrong?                                           # optional
            successMsg: Thank you for helping to improve our documentation!               # optional
            errorMsg: Sorry! There was an error while attempting to submit your feedback! # optional
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
                "emoticonTpl": true,
                "eventDest": [
                    "plausible",
                    "google"
                ],
                "emoticonEventName": "Feedback",
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

- **`emoticonEventName`** - The name of the event for the emoticon feedback template e.g. `Feedback` (**default**)

- **`positiveEventName`** - The name of the positive event for the default feedback template e.g. `Positive Feedback` (**default**)

- **`negativeEventName`** - The name of the negative event for the default feedback template e.g. `Negative Feedback` (**default**)

{{% alert context="info" text="**Note** - For **Google Analytics v4** (per [Google's recommendations](https://support.google.com/analytics/answer/13316687)), before an event is sent, Lotus Docs converts its name to lowercase letters, and replaces spaces with an underscore. e.g. `Positive Feedback` is converted to `positive_feedback`." /%}}

### Form Title

This option sets the title for each form in the **default feedback template**:

- **`positiveFormTitle`** - The title of the positive feedback form e.g. `What did you like?` (**default**)

- **`negativeFormTitle`** - The title of the negative feedback form e.g. `What went wrong?` (**default**)

### Success / Error Messages

Messages displayed after feedback is submitted (applies to both templates):

- **`successMsg`** - The message displayed after feedback has been successfully sent e.g. `Thank you for helping to improve our documentation!` (**default**)

- **`errorMsg`** - The message displayed if the widget fails to submit feedback e.g. `Sorry! There was an error while attempting to submit your feedback!` (**default**)

### Ratings & Description Configuration

A nested array of options for each form in the **default feedback template**. The first string in each nested array sets the name of the feedback rating. The second string sets a description for that feedback rating.

- **`positiveForm`** - A nested array consisting of a positive rating name and description (optional) for each feedback radio option e.g. `[["Accurate", "Accurately describes the feature or option."]]`.

- **`negativeForm`** - A nested array consisting of a negative rating name and description (optional) for each feedback radio option e.g. `[["Code sample errors", "One or more code samples are incorrect."]]`.

So `["Solved my problem", "Helped me resolve an issue."]` results in:

![Feedback Form Option](https://res.cloudinary.com/lotuslabs/image/upload/v1692328347/Lotus%20Docs/images/lotusdocs_feedback_form_option_selected_ppf1hb.webp)

The feedback rating `Solved my problem` is sent as an [event parameter](https://developers.google.com/analytics/devguides/collection/ga4/event-parameters?client_type=gtag) value of a key named `rating`, and any text entered in the text area, is sent as a value of a key named `message`.

