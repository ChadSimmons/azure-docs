---
title: Harden your Windows and Linux OS with Azure security baseline and Microsoft Defender for Cloud
description: Learn how Microsoft Defender for Cloud uses the guest configuration to compare your OS hardening with the guidance from Azure Security Benchmark
ms.topic: how-to
ms.author: benmansheim
author: bmansheim
ms.date: 11/09/2021

---
# Apply Azure security baselines to machines

[!INCLUDE [Banner for top of topics](./includes/banner.md)]

To reduce a machine's attack surface and avoid known risks, it's important to configure the operating system (OS) as securely as possible.

The Azure Security Benchmark has guidance for OS hardening which has led to security baseline documents for [Windows](../governance/policy/samples/guest-configuration-baseline-windows.md) and [Linux](../governance/policy/samples/guest-configuration-baseline-linux.md).

Use the security recommendations described in this article to assess the machines in your environment and:

- Identify gaps in the security configurations
- Learn how to remediate those gaps

## Availability
|Aspect|Details|
|----|:----|
|Release state:|Preview.<br>[!INCLUDE [Legalese](../../includes/defender-for-cloud-preview-legal-text.md)]|
|Pricing:|Free|
|Prerequisites:|Machines must (1) be members of a workgroup, (2) have the Guest Configuration extension, (3) have a system-assigned managed-identity, and (4) be running a supported OS:<br>• Windows Server 2012, 2012r2, 2016 or 2019<br>• Ubuntu 14.04, 16.04, 17.04, 18.04 or 20.04<br>• Debian 7, 8, 9, or 10<br>• CentOS 7 or 8<br>• Red Hat Enterprise Linux (RHEL) 7 or 8<br>• Oracle Linux 7 or 8<br>• SUSE Linux Enterprise Server 12|
|Required roles and permissions:|To install the Guest Configuration extension and its prerequisites, **write** permission is required on the relevant machines.<br>To **view** the recommendations and explore the OS baseline data, **read** permission is required at the subscription level.|
|Clouds:|:::image type="icon" source="./media/icons/yes-icon.png"::: Commercial clouds<br>:::image type="icon" source="./media/icons/no-icon.png"::: National (Azure Government, Azure China 21Vianet)|


## What are the hardening recommendations?

Microsoft Defender for Cloud includes two recommendations that check whether the configuration of Windows and Linux machines in your environment meet the Azure security baseline configurations:

- For **Windows** machines, [Vulnerabilities in security configuration on your Windows machines should be remediated (powered by Guest Configuration)](https://portal.azure.com/#blade/Microsoft_Azure_Security/RecommendationsBlade/assessmentKey/1f655fb7-63ca-4980-91a3-56dbc2b715c6) compares the configuration with the [Windows security baseline](../governance/policy/samples/guest-configuration-baseline-windows.md).
- For **Linux** machines, [Vulnerabilities in security configuration on your Linux machines should be remediated (powered by Guest Configuration)](https://portal.azure.com/#blade/Microsoft_Azure_Security/RecommendationsBlade/assessmentKey/8c3d9ad0-3639-4686-9cd2-2b2ab2609bda) compares the configuration with the [Linux security baseline](../governance/policy/samples/guest-configuration-baseline-linux.md).

These recommendations use the guest configuration feature of Azure Policy to compare the OS configuration of a machine with the baseline defined in the [Azure Security Benchmark](/security/benchmark/azure/overview).

## Compare machines in your subscriptions with the OS security baselines

To compare machines with the OS security baselines:
 
1. From Defender for Cloud's portal pages, open the **Recommendations** page. 
1. Select the relevant recommendation:
    - For **Windows** machines, [Vulnerabilities in security configuration on your Windows machines should be remediated (powered by Guest Configuration)](https://portal.azure.com/#blade/Microsoft_Azure_Security/RecommendationsBlade/assessmentKey/1f655fb7-63ca-4980-91a3-56dbc2b715c6)
    - For **Linux** machines, [Vulnerabilities in security configuration on your Linux machines should be remediated (powered by Guest Configuration)](https://portal.azure.com/#blade/Microsoft_Azure_Security/RecommendationsBlade/assessmentKey/8c3d9ad0-3639-4686-9cd2-2b2ab2609bda)

    :::image type="content" source="media/apply-security-baseline/recommendations-baseline.png" alt-text="The two recommendations for comparing the OS configuration of machines with the relevant Azure security baseline." lightbox="media/apply-security-baseline/recommendations-baseline.png":::

1. On the recommendation details page you can see:
    1. The affected resources.
    1. The specific security checks that failed.

    :::image type="content" source="media/apply-security-baseline/recommendation-details-page-vulnerabilities-windows.png" alt-text="Recommendation details page for the Windows recommendation about vulnerabilities in the baseline configuration of Windows machines." lightbox="media/apply-security-baseline/recommendation-details-page-vulnerabilities-windows.png":::

1. To learn more about a specific finding, select it.

    :::image type="content" source="media/apply-security-baseline/finding-details.png" alt-text="Learning more about a specific finding from the guest configuration comparison of an OS configuration with the defined security baseline." lightbox="media/apply-security-baseline/finding-details.png":::

1. Other investigation possibilities:

    - To view the list of machines that have been assessed, open **Affected resources**.
    - To view the list of findings for one machine, select a machine from the **Unhealthy resources** tab. A page will open listing only the findings for that machine.


## FAQ - Hardening an OS according to the security baseline

- [How do I deploy the prerequisites for the security configuration recommendations?](#how-do-i-deploy-the-prerequisites-for-the-security-configuration-recommendations)
- [Why is a machine shown as not applicable?](#why-is-a-machine-shown-as-not-applicable)

### How do I deploy the prerequisites for the security configuration recommendations?

To deploy the Guest Configuration extension with its prerequisites:

- For selected machines, follow the security recommendation **Guest Configuration extension should be installed on your machines** from the **Implement security best practices** security control.

- At scale, assign the policy initiative **Deploy prerequisites to enable Guest Configuration policies on virtual machines**.


### Why is a machine shown as not applicable?

The list of resources in the **Not applicable** tab includes a **Reason** column. Some of the common reasons include:

| Reason                                                            | Details                                                                                                                                                                        |
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **No scan data available on the machine**                         | There aren't any compliance results for this machine in Azure Resource Graph. All compliance results are written to Azure Resource Graph by the Guest Configuration extension. You can check the data in Azure Resource Graph using the sample queries in [Azure Policy Guest Configuration - sample ARG queries](../governance/policy/samples/resource-graph-samples.md?tabs=azure-cli#azure-policy-guest-configuration).|
| **Guest Configuration extension is not installed on the machine** | The machine is missing the Guest Configuration extension, which is a prerequisite for assessing the compliance with the Azure security baseline.                               |
| **System managed identity is not configured on the machine**      | A system-assigned, managed identity must be deployed on the machine.                                                                                                           |
| **The recommendation is disabled in policy**                      | The policy definition that assesses the OS baseline is disabled on the scope that includes the relevant machine.                                                               |


## Next steps
In this document, you learned how to use Defender for Cloud's guest configuration recommendations to compare the hardening of your OS with the Azure security baseline.

To learn more about these configuration settings, see:

- [Windows security baseline](../governance/policy/samples/guest-configuration-baseline-windows.md)
- [Linux security baseline](../governance/policy/samples/guest-configuration-baseline-linux.md)
- [Azure Security Benchmark](/security/benchmark/azure/overview)
