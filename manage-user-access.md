---
title: Manage User Access
summary: Learn how to manage the user access in your TiDB Cloud cluster.
---

# Manage User Access

This document describes how to manage the user access in your TiDB Cloud cluster.

## Sign in

If you already created a TiDB Cloud account using your Google account, sign in to your Google account.

1. Navigate to the TiDB Cloud login page: <https://tidbcloud.com>.

2. Click Sign in with Google.

> **Note:**
>
> The email/password sign-in is not supported yet, so you need to sign in with Google.

## Sign out

After you have signed into TiDB Cloud, if you need to sign out, perform the following steps:

1. Click the account name on the upper right of the window.

2. Click **Logout**.

## View the organization

TiDB Cloud provides a hierarchy based on organizations to facilitate the management of your TiDB clusters. In the organization's hierarchy, an organization can contain multiple clusters and users.

Under this structure:

1. Billing happens at the organization level while preserving visibility into usage in each cluster.

2. You can view all users within an organization.

To access one organization or a cluster within this organization, the user must be a member of the organization. Depending on the user's role in the organization, there is only one administrator who is also the creator of the organization. Users can be invited by the administrator to create and manage the clusters in the organization.

To view your organization, perform the following steps:

1. Click the account name on the upper right of the window.

2. Click **Preferences**. The **Organization** tab displays by default.

## Invite a team member

To invite a team member in an organization, perform the following steps:

1. Click the account name on the upper right of the window.

2. Click **Preferences**. The organization preferences page displays.

3. Click **User Access**.

4. Click the **+ Invite** icon.

5. Enter the email of the user that you want to invite in the dialog.

6. Click **Confirm**. Then the new user is successfully added into the user list. At the same time, an email is sent to the invited email with a verification link.

7. When the user receives this email, click the link in the email to verify the identity, and a new page displays.

8. On the new page, the user needs to view and agree with our license, and then click **Submit** to create the account in TiDB Cloud. After that, the user is redirected to the login page.

> **Note:**
>
> - Currently, TiDB Cloud only supports accounts signed in using Google accounts.
> - The verification link in the email will expire in 24 hours. If your user doesn't receive the email, click the **Resend** button.

## Remove a team member

To remove a team member from an organization, perform the following steps:

1. Click the account name on the upper right of the window.

2. Click **Preferences**. The organization preferences page displays.

3. Click **User Access**.

4. Click the **Delete** button of the user row that you want to delete.

## Set the local time zone

You can modify the system display time according to your time zone. To change the local timezone setting, perform the following steps:

1. Click the account name on the upper right of the window.

2. Click **Preferences**. The organization preferences page displays.

3. Click **Time Zone**.

4. Click the drop-down list and select your time zone.

5. Click **Confirm**.
