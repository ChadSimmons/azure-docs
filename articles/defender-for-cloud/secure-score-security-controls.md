---
title: Secure score in Microsoft Defender for Cloud
description: Description of Microsoft Defender for Cloud's secure score and its security controls 
ms.topic: article
ms.date: 11/09/2021
---

# Secure score in Microsoft Defender for Cloud

[!INCLUDE [Banner for top of topics](./includes/banner.md)]

## Introduction to secure score

Microsoft Defender for Cloud has two main goals: 

- to help you understand your current security situation
- to help you efficiently and effectively improve your security

The central feature in Defender for Cloud that enables you to achieve those goals is **secure score**.

Defender for Cloud continually assesses your resources, subscriptions, and organization for security issues. It then aggregates all the findings into a single score so that you can tell, at a glance, your current security situation: the higher the score, the lower the identified risk level.

The secure score is shown in the Azure portal pages as a percentage value, but the underlying values are also clearly presented:

:::image type="content" source="./media/secure-score-security-controls/single-secure-score-via-ui.png" alt-text="Overall secure score as shown in the portal.":::

To increase your security, review Defender for Cloud's recommendations page for the outstanding actions necessary to raise your score. Each recommendation includes instructions to help you remediate the specific issue.

Recommendations are grouped into **security controls**. Each control is a logical group of related security recommendations, and reflects your vulnerable attack surfaces. Your score only improves when you remediate *all* of the recommendations for a single resource within a control. To see how well your organization is securing each individual attack surface, review the scores for each security control.

For more information, see [How your secure score is calculated](secure-score-security-controls.md#how-your-secure-score-is-calculated) below. 

## How your secure score is calculated 

The contribution of each security control towards the overall secure score is shown clearly on the recommendations page.

:::image type="content" source="./media/secure-score-security-controls/security-controls.png" alt-text="Microsoft Defender for Cloud's security controls and their impact on your secure score" lightbox="./media/secure-score-security-controls/security-controls.png":::

To get all the possible points for a security control, all your resources must comply with all of the security recommendations within the security control. For example, Defender for Cloud has multiple recommendations regarding how to secure your management ports. You'll need to remediate them all to make a difference to your secure score.

### Example scores for a control

:::image type="content" source="./media/secure-score-security-controls/remediate-vulnerabilities-control.png" alt-text="Apply system updates security control." lightbox="./media/secure-score-security-controls/remediate-vulnerabilities-control.png":::


In this example:

| #  | Name                                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-:|------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 | **Remediate vulnerabilities security control** | This control groups multiple recommendations related to discovering and resolving known vulnerabilities.                                                                                                                                                                                                                                                                                                                                   |
| 2 | **Max score**                                  | The maximum number of points you can gain by completing all recommendations within a control. The maximum score for a control indicates the relative significance of that control and is fixed for every environment. Use the max score values to triage the issues to work on first.<br>For a list of all controls and their max scores, see [Security controls and their recommendations](#security-controls-and-their-recommendations). |
| 3 | **Number of resources**                        | There are 35 resources affected by this control.<br>To understand the possible contribution of every resource, divide the max score by the number of resources.<br>For this example, 6/35=0.1714<br>**Every resource contributes 0.1714 points.**                                                                                                                                                                                          |
| 4 | **Current score**                              | The current score for this control.<br>Current score=[Score per resource]*[Number of healthy resources]<br> 0.1714 x 5 healthy resources = 0.86<br>Each control contributes towards the total score. In this example, the control is contributing 0.86 points to current total secure score.                                                                                                                                               |
| 5 | **Potential score increase**                   | The remaining points available to you within the control. If you remediate all the recommendations in this control, your score will increase by 9%.<br>Potential score increase=[Score per resource]*[Number of unhealthy resources]<br> 0.1714 x 30 unhealthy resources = 5.14<br>                                                                                                                                                        |




### Calculations - understanding your score

|Metric|Formula and example|
|-|-|
|**Security control's current score**|<br>![Equation for calculating a security control's score.](media/secure-score-security-controls/secure-score-equation-single-control.png)<br><br>Each individual security control contributes towards the Security Score. Each resource affected by a recommendation within the control, contributes towards the control's current score. The current score for each control is a measure of the status of the resources *within* the control.<br>![Tooltips showing the values used when calculating the security control's current score](media/secure-score-security-controls/security-control-scoring-tooltips.png)<br>In this example, the max score of 6 would be divided by 78 because that's the sum of the healthy and unhealthy resources.<br>6 / 78 = 0.0769<br>Multiplying that by the number of healthy resources (4) results in the current score:<br>0.0769 * 4 = **0.31**<br><br>|
|**Secure score**<br>Single subscription|<br>![Equation for calculating a subscription's secure score](media/secure-score-security-controls/secure-score-equation-single-sub.png)<br><br>![Single subscription secure score with all controls enabled](media/secure-score-security-controls/secure-score-example-single-sub.png)<br>In this example, there is a single subscription with all security controls available (a potential maximum score of 60 points). The score shows 28 points out of a possible 60 and the remaining 32 points are reflected in the "Potential score increase" figures of the security controls.<br>![List of controls and the potential score increase](media/secure-score-security-controls/secure-score-example-single-sub-recs.png)|
|**Secure score**<br>Multiple subscriptions|<br>![Equation for calculating the secure score for multiple subscriptions.](media/secure-score-security-controls/secure-score-equation-multiple-subs.png)<br><br>When calculating the combined score for multiple subscriptions, Defender for Cloud includes a *weight* for each subscription. The relative weights for your subscriptions are determined by Defender for Cloud based on factors such as the number of resources.<br>The current score for each subscription is calculated in the same way as for a single subscription, but then the weight is applied as shown in the equation.<br>When viewing multiple subscriptions, secure score evaluates all resources within all enabled policies and groups their combined impact on each security control's maximum score.<br>![Secure score for multiple subscriptions with all controls enabled](media/secure-score-security-controls/secure-score-example-multiple-subs.png)<br>The combined score is **not** an average; rather it's the evaluated posture of the status of all resources across all subscriptions.<br>Here too, if you go to the recommendations page and add up the potential points available, you will find that it's the difference between the current score (24) and the maximum score available (60).|


### Which recommendations are included in the secure score calculations?

Only built-in recommendations have an impact on the secure score.

Recommendations flagged as **Preview** aren't included in the calculations of your secure score. They should still be remediated wherever possible, so that when the preview period ends they'll contribute towards your score.

An example of a preview recommendation:

:::image type="content" source="./media/secure-score-security-controls/example-of-preview-recommendation.png" alt-text="Recommendation with the preview flag.":::

## Improve your secure score

To improve your secure score, remediate security recommendations from your recommendations list. You can remediate each recommendation manually for each resource, or by using the **Fix** option (when available) to resolve an issue on multiple resources quickly. For more information, see [Remediate recommendations](implement-security-recommendations.md).

Another way to improve your score and ensure your users don't create resources that negatively impact your score is to configure the Enforce and Deny options on the relevant recommendations. Learn more in [Prevent misconfigurations with Enforce/Deny recommendations](prevent-misconfigurations.md).

## Security controls and their recommendations

The table below lists the security controls in Microsoft Defender for Cloud. For each control, you can see the maximum number of points you can add to your secure score if you remediate *all* of the recommendations listed in the control, for *all* of your resources. 

The set of security recommendations provided with Defender for Cloud is tailored to the available resources in each organization's environment. The recommendations can be further customized by [disabling policies](tutorial-security-policy.md#disable-security-policies-and-disable-recommendations) and [exempting specific resources from a recommendation](exempt-resource.md). 
 
We recommend every organization carefully review their assigned Azure Policy initiatives. 

> [!TIP]
> For details of reviewing and editing your initiatives, see [Working with security policies](tutorial-security-policy.md). 

Even though Defender for Cloud's default security initiative is based on industry best practices and standards, there are scenarios in which the built-in recommendations listed below might not completely fit your organization. Consequently, it'll sometimes be necessary to adjust the default initiative - without compromising security - to ensure it's aligned with your organization's own policies, industry standards, regulatory standards, and benchmarks you're obligated to meet.<br><br>

[!INCLUDE [security-center-controls-and-recommendations](../../includes/asc/security-control-recommendations.md)]



## FAQ - Secure score

### If I address only three out of four recommendations in a security control, will my secure score change?
No. It won't change until you remediate all of the recommendations for a single resource. To get the maximum score for a control, you must remediate all recommendations, for all resources.

### If a recommendation isn't applicable to me, and I disable it in the policy, will my security control be fulfilled and my secure score updated?
Yes. We recommend disabling recommendations when they're inapplicable in your environment. For instructions on how to disable a specific recommendation, see [Disable security policies](./tutorial-security-policy.md#disable-security-policies-and-disable-recommendations).

### If a security control offers me zero points towards my secure score, should I ignore it?
In some cases, you'll see a control max score greater than zero, but the impact is zero. When the incremental score for fixing resources is negligible, it's rounded to zero. Don't ignore these recommendations as they still bring security improvements. The only exception is the "Additional Best Practice" control. Remediating these recommendations won't increase your score, but it will enhance your overall security.

## Next steps

This article described the secure score and the included security controls. 

> [!div class="nextstepaction"]
> [Access and track your secure score](secure-score-access-and-track.md)

For related material, see the following articles:

- [Learn about the different elements of a recommendation](review-security-recommendations.md)
- [Learn how to remediate recommendations](implement-security-recommendations.md)
- [View the GitHub-based tools for working programmatically with secure score](https://github.com/Azure/Azure-Security-Center/tree/master/Secure%20Score)
