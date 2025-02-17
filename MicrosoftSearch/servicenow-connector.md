---
title: "ServiceNow connector for Microsoft Search"
ms.author: v-pamcn
author: TrishaMc1
manager: mnirkhe
ms.date: 10/08/2019
ms.audience: Admin
ms.topic: article
ms.service: mssearch
localization_priority: Normal
search.appverid:
- BFB160
- MET150
- MOE150
description: "Set up the ServiceNow connector for Microsoft Search"
---

# ServiceNow connector

With the ServiceNow connector, your organization can index knowledge-base articles that are visible to all users within your organization. After you configure the connector and index content from ServiceNow, end users can search for those articles from any Microsoft Search client.  

This article is for Microsoft 365 administrators or anyone who configures, runs, and monitors a ServiceNow connector. It explains how to configure your connector and connector capabilities, limitations, and troubleshooting techniques.

## Connect to a data source
To connect to your ServiceNow data, you need your organization's **ServiceNow instance URL**, credentials for this account, and the Client ID and Client Secret for OAuth authentication.  

Your organization’s **ServiceNow instance URL** typically looks like **https://&lt;your-organization-domain>.service-now.com**. Along with this URL, you will need an account for setting up the connection to ServiceNow as well as for allowing Microsoft Search to periodically update the articles from ServiceNow based on the refresh schedule.

To authenticate and sync content from ServiceNow, choose one of two supported methods: 
1. Basic authentication 
2. OAuth (recommended)

> [!Note]
> To use OAuth for authentication, a ServiceNow admin needs to provision an endpoint in your ServiceNow instance, so that the Microsoft Search app can access the instance. To learn more, see [Create an endpoint for clients to access the instance](https://docs.servicenow.com/bundle/newyork-platform-administration/page/administer/security/task/t_CreateEndpointforExternalClients.html) in the ServiceNow documentation.

The following table provides guidance on how to fill out the endpoint creation form:

**Field** | **Description** | **Recommended Value**
--- | --- | ---
Name | This unique value identifies the application that you require OAuth access for. | Microsoft Search
Client ID | A read-only, auto-generated unique ID for the application. The instance uses the client ID when it requests an access token. | NA
Client secret | With this shared secret string, the ServiceNow instance and Microsoft Search authorize communications with each another. | Follow security best-practices by treating this as a password.
Redirect URL | A required callback URL that the authorization server redirects to. | See [OAuth callback](https://gcs.office.com/v1.0/admin/oauth/callback).
Logo URL | A URL that contains the image for the application logo. | NA
Active | Select the check box to make the application registry active. | Set to active
Refresh token lifespan | The number of seconds that a refresh token is valid. By default, refresh tokens expire in 100 days (8640000 seconds). | 31,536,000 (1 year)
Access token lifespan | The number of seconds that an access token is valid. | 43,200 (12 hours)

## Set a sync filter 
With a sync filter, you can specify conditions for syncing articles. It's like a **Where** clause in a **SQL Select** statement. For example, you can choose to index only articles that are published and active. The SyncNow configuration page describes how to capture and set a sync filter.

## Manage the search schema
After successful connection, configure the search schema mapping. You can choose which properties to make **queryable**, **searchable**, and **retrievable**.

## Manage search permissions
The ServiceNow connector only supports search permissions visible to **Everyone**. Indexed data appears in the search results and is visible to all users in the organization.
 
## Set the refresh schedule 
The ServiceNow connector supports refresh schedules for both full and incremental crawls. We recommend that you set both.

A full crawl schedule finds deleted articles that were previously synced to the Microsoft Search index and any articles that moved out of the sync filter. When you first connect to ServiceNow, a full crawl runs to sync all the knowledge-base articles. To sync new items and make updates, you need to schedule incremental crawls.

The recommended default is one day for a full crawl and four hours for an incremental crawl.
