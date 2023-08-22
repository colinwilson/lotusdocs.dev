---
weight: 518
title: "Feedback Widget"
description: "How to configure the Feedback Widget so visitors can rate or/and comment on your site's content."
icon: reviews
date: 2023-08-08T23:33:15+00:00
lastmod: 2023-08-08T23:33:15+00:00
draft: true
images: []
---

The Lotus Docs feedback plugin integrates with Google or Plausible Analytics to allow you to collect visitor feedback on your sites' content.

![Emoticon Icons Illustration](https://res.cloudinary.com/lotuslabs/image/upload/v1692622991/Lotus%20Docs/images/lotusdocs_emoticon_feedback_widget_screenshot_rd_wnj72x.webp)

## Why use web analytics to collect feedback?

Short answer? Because it's **FREE**! Other benefits include:

- No need to sign up to yet another service just to collect basic visitor feedback.
- Easy to configure. Once Google or Plausible Analytics (or both) are configured in `hugo.toml`, the Feedback Widget it ready to go.
- [No limit](https://support.google.com/analytics/answer/9267744) on the number of events that can be collected.


## How it works

When enabled, the feedback widget appears at bottom of every content page. Whenever a site visitor interacts with it, their feedback is collected and sent to whichever web analytics you have configured in your `hugo.toml` file.

### Custom Events

The Feedback Widget works by leveraging custom events. What is a custom event? From Google:

> A custom event is an event that you define so you can collect information about an interaction that's important to your business.

Here's more info on how custom events work with Plausible and Google:

- **Google Analytics v4** via [Custom events](https://support.google.com/analytics/answer/12229021)
- **Plausible Analytics** via [Custom event goals](https://plausible.io/docs/custom-event-goals)

The feedback form uses these custom events to send visitor interactions to the corresponding analytics service.

### Templates

Lotus Docs currently offers two template styles for the feedback widget:

#### Emoticon

<div class="d-flex justify-content-center pb-4">
    <video width="90%" controls>
    <source src="https://res.cloudinary.com/lotuslabs/video/upload/v1692663574/Lotus%20Docs/video/lotusdocs_emoticon_feedback_template_sjk1rm.webm" type="video/webm">
    <source src="https://res.cloudinary.com/lotuslabs/video/upload/v1692663574/Lotus%20Docs/video/lotusdocs_emoticon_feedback_template_sjk1rm.mp4" type="video/mp4">
    </video>
</div>

#### Default

<div class="d-flex justify-content-center pb-4">
    <video width="90%" controls>
    <source src="https://res.cloudinary.com/lotuslabs/video/upload/v1692664585/Lotus%20Docs/video/lotusdocs_default_feedback_template_ybut2q.webm" type="video/webm">
    <source src="https://res.cloudinary.com/lotuslabs/video/upload/v1692664585/Lotus%20Docs/video/lotusdocs_default_feedback_template_ybut2q.wmp4" type="video/mp4">
    </video>
</div>

## Configure your analytics for Custom Events

Your web analytics service may require some preparation prior to receiving custom events from the feedback widget.

### Plausible

Custom events aren't automatically displayed in the Plausible dashboard. You'll have to configure the custom event goal for you feedback to show up.

To configure a goal, go to [your website's settings](https://plausible.io/docs/website-settings) in your Plausible account and visit the "Goals" section. You should see an empty list with a prompt to add a goal.

![Add Goal in Plausible](https://res.cloudinary.com/lotuslabs/image/upload/v1692654403/Lotus%20Docs/images/plausible_goals_setup_1_mod_bglw1y.webp)

Click on the "**+ Add goal**" button to go to the goal creation form.

Select `Custom event` as the goal trigger and enter the name of the custom event you are triggering. The name must match the one you added as a CSS class name on your site for conversions to appear in your analytics dashboard. So in our example where you added a CSS class name `plausible-event-name=Form+Submit`, the goal to add to your Plausible account is `Form Submit` (plus is replaced by a space).

![Add Goal to Plausible Account](https://res.cloudinary.com/lotuslabs/image/upload/v1692655733/Lotus%20Docs/images/plausible_goals_setup_2_mod_uut38r.webp)

Head back to the stat page for your site and scroll to the bottom to view the `Goal Conversion` statistics. You'll see the Feedback goal along with the breakdown by `rating`.

![Lotus Docs Feedback Goal Conversion statistics](https://res.cloudinary.com/lotuslabs/image/upload/v1692656039/Lotus%20Docs/images/plausible_feedback_goal_conversions_mod_kcin8h.webp)

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

### Template

Option to choose the feedback template:

- **`emoticonTpl`** - Set to `true` to enable the emoticon feedback template. (**default**) is `false`.

### Event Destination

This determines which of your configured web analytics services to send your collected feedback to. If this parameter is not set, and the feedback widget is enabled, it will send feedback to all web analytics configured in `hugo.toml`:

- **`eventDest`** - Which web analytics services to send visitor feedback to e.g. `["plausible", "google"]` (**default**)

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

