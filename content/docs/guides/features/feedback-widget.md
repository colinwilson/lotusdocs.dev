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

## Why use an Analytics service to collect feedback?

Short answer? Because it's **FREE**! Other benefits include:

- No need to sign up to yet another service just to collect basic visitor feedback.
- Easy to configure. Once you configure Google or Plausible Analytics (or both) in Lotus Docs, the Feedback Widget it ready to go.


## How it works

The Feedback Widget works by leveraging custom events:

- **Google Analytics v4** via [Custom events](https://support.google.com/analytics/answer/12229021)
- **Plausible Analytics** via [Custom event goals](https://plausible.io/docs/custom-event-goals)

These events send visitors' data from the Feedback Widget to the analytics service.

When enabled, the widget appears at the bottom of every content page. Once a visitor answers the initial call-to-action, '**Was this page helpful?**', a positive or negative feedback form is presented.

<div class="row flex-xl-wrap pb-1">
<div id="list-item" class="col-md-6 col-12 py-2">

![Positive Feedback Form](https://res.cloudinary.com/lotuslabs/image/upload/v1692290308/Lotus%20Docs/images/lotusdocs_positive_feedback_form_mod_uh9s3d.webp "**Positive Feedback Form**")

</div>

<div id="list-item" class="col-md-6 col-12 py-2">

![Negative Feedback Form](https://res.cloudinary.com/lotuslabs/image/upload/v1692290397/Lotus%20Docs/images/lotusdocs_negative_feedback_form_mod_rqjqi4.webp "**Negative Feedback Form**")

</div>
</div>

Positive