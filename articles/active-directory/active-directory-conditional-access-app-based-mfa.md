---
title: Quickstart - Require multi-factor authentication (MFA) for specific apps with Azure Active Directory conditional access | Microsoft Docs
description: In this quickstart, you learn how you can tie your authentication requirements to the type of accessed cloud app using Azure Active Directory (Azure AD) conditional access.
services: active-directory
keywords: conditional access to apps, conditional access with Azure AD, secure access to company resources, conditional access policies
documentationcenter: ''
author: MarkusVi
manager: mtillman
ms.assetid: 
ms.service: active-directory
ms.topic: quickstart 
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 05/10/2018
ms.author: markvi
ms.reviewer: calebb
#Customer intent: As an IT admin, I want to configure MFA on a per app basis, so that my users have a convenient sign-on experience and our mission critical apps are protected with strong authentication.
---

# Quickstart: Require MFA for specific apps with Azure Active Directory conditional access 

To simplify the sign-in experience of your users, you might want to allow them to sign in to your cloud apps using a user name and a password. However, many environments have at least a few apps for which it is advisable to require a stronger form of account verification, such as multi-factor authentication. This might be, for example true, for access to your organization's email system or your HR apps. In Azure Active Directory, you can accomplish this goal with a conditional access policy.    

This quickstart shows how to configure an [Azure AD conditional access policy](active-directory-conditional-access-azure-portal.md) to require multi-factor authentication for a set of selected cloud apps in your environment.


## Scenario description

The scenario in this article uses the Azure portal as placeholder for a cloud app that requires multi-factor authentication for a specific user. Isabella Simonsen is a user in your organization. When she signs in to your Azure portal, you want her to further verify her account with multi-factor authentication.

![Multi-factor authentication](./media/active-directory-conditional-access-app-based-mfa/22.png)



## Prerequisites 

To complete the scenario in this quickstart, you need:

- **Access to an Azure AD Premium edition** - Azure AD conditional access is an Azure AD Premium capability. If you don't have access to an Azure AD Premium edition, you can [sign-up for a trial](https://azure.microsoft.com/trial/get-started-active-directory/).

- **A test account called Isabella Simonsen** - If you don't know how to create a test account, read [these instructions](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory).



## Create your conditional access policy 

This section shows how to create the required conditional access policy.  
In your policy, you set:

|Setting |Value|
|---     | --- |
|Users and groups | Isabella Simonsen |
|Cloud apps | Microsoft Azure Management |
|Grant | Require multi-factor authentication |
 

![Create policy](./media/active-directory-conditional-access-app-based-mfa/21.png)




**To configure your conditional access policy:**

1. Sign in to your [Azure portal](https://portal.azure.com) as global administrator.

2. In the Azure portal, on the left navbar, click **Azure Active Directory**. 

    ![Azure Active Directory](./media/active-directory-conditional-access-app-based-mfa/02.png)

3. On the **Azure Active Directory** page, in the **Manage** section, click **Conditional access**.

    ![Conditional access](./media/active-directory-conditional-access-app-based-mfa/03.png)
 
4. On the **Conditional Access** page, in the toolbar on the top, click **Add**.

    ![Add](./media/active-directory-conditional-access-app-based-mfa/04.png)

5. On the **New** page, in the **Name** textbox, type **Require MFA for Azure portal access**.

    ![Name](./media/active-directory-conditional-access-app-based-mfa/05.png)

6. In the **Assignment** section, click **Users and groups**.

    ![Users and groups](./media/active-directory-conditional-access-app-based-mfa/06.png)

7. On the **Users and groups** page, perform the following steps:

    ![Users and groups](./media/active-directory-conditional-access-app-based-mfa/24.png)

    a. Click **Select users and groups**, and then select **Users and groups**.

    b. Click **Select**.

    c. On the **Select** page, select **Isabella Simonsen**, and then click **Select**.

    d. On the **Users and groups** page, click **Done**.

8. Click **Cloud apps**.

    ![Cloud apps](./media/active-directory-conditional-access-app-based-mfa/08.png)

9. On the **Cloud apps** page, perform the following steps:

    ![Select cloud apps](./media/active-directory-conditional-access-app-based-mfa/26.png)

    a. Click **Select apps**.

    b. Click **Select**.

    c. On the **Select** page, select **Microsoft Azure Management**, and then click **Select**.

    d. On the **Cloud apps** page, click **Done**.


10. In the **Access controls** section, click **Grant**.

    ![Access controls](./media/active-directory-conditional-access-app-based-mfa/10.png)

11. On the **Grant** page, perform the following steps:

    ![Grant](./media/active-directory-conditional-access-app-based-mfa/11.png)

    a. Select **Grant access**.

    a. Select **Require multi-factor authentication**.

    b. Click **Select**.

12. In the **Enable policy** section, click **On**.

    ![Enable policy](./media/active-directory-conditional-access-app-based-mfa/18.png)

13. Click **Create**.


## Evaluate your conditional access policy

Now that you have configured your conditional access policy, you probably want to know whether it works as expected. As a first step, you can use the [conditional access what if policy tool](active-directory-conditional-access-whatif.md) to simulate a sign-in of a user. When you configure the tool with **Isabella Simonsen** as user and **Microsoft Azure Management** as cloud app, the tool shows **Require MFA for Azure portal access** under **Policies that will apply** and **Require multi-factor authentication** as **Grant Controls**.

![What if policy tool](./media/active-directory-conditional-access-app-based-mfa/23.png)



**To evaluate your conditional access policy:**

1. On the [Conditional access - Policies](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) page, in the menu on the top, click **What If**.  
 
    ![What If](./media/active-directory-conditional-access-app-based-mfa/14.png)

2. Click **Users**, select **Isabella Simonsen**, and then click **Select**.

    ![User](./media/active-directory-conditional-access-app-based-mfa/15.png)

2. To select a cloud app, perform the following steps:

    ![Cloud apps](./media/active-directory-conditional-access-app-based-mfa/16.png)

    a. Click **Cloud apps**.

    b. On the **Cloud apps page**, click **Select apps**.

    c. Click **Select**.

    d. On the **Select** page, select Microsoft Azure Management**, and then click **Select**.

    e. On the cloud apps page, click **Done**.

3. Click **What If**.


## Test your conditional access policy

The previous section In the previous section, you 

To test your policy, try to sign-in to your [Azure portal](https://portal.azure.com) using your **Isabella Simonsen** test account. You should see a dialog that requires you to set your account up for additional security verification.

![Multi-factor authentication](./media/active-directory-conditional-access-app-based-mfa/22.png)


## Next steps

If you would like to learn more about conditional access, see [Azure Active Directory conditional access](active-directory-conditional-access-azure-portal.md).

