---
layout: default-layout
title: Dynamsoft Licensing FAQ
keywords: Barcode reader, licensing
description: This page lists the frequently asked questions about Dynamsoft's License Tracking Service.
breadcrumbText: Licensing FAQ
needAutoGenerateSidebar: true
---

# Dynamsoft Licensing FAQ

## Does the Barcode Reader JavaScript library disclose any information to the outside world?

The library is based on JavaScript and WebAssembly. At runtime, the browser running the barcode reading page will download & compile the `.wasm` file from the server. After that, all barcode reading is done inside the browser. In other words, the images or video stream that are passed to the library for barcode reading will stay in the browser memory and go no further.

Once the reading completes, the library returns the results in a callback to be further processed in customers’ own JavaScript code. The image data is purged as soon as the reading is done. The results stay in the memory for a little while before it’s purged. Neither is sent anywhere.

For licensing purposes, by default the library keeps track of the symbology types and the number of scans (nothing about the actual barcode text) and will send the info to the License Tracking Service for license tracking purpose. Also, the library generates a random number and map that to an UUID which identifies the device for license tracking purpose. All the information is encrypted and stored in the browsers’ indexed DB and will be purged once it's submitted to the License Tracking Service.

A few things to note

* The License Tracking Service can either be the official one provided by Dynamsoft or one that’s hosted by the customers on their own servers.
* Offline license that doesn't require any information to be sent anywhere is also supported. Contact [Dynamsoft Sales](mailto:sales@dynamsoft.com) for more information.
* For debugging purposes, the actual images that are read for barcodes can be exported and saved. However, this is controlled by customer's code.

## How secure is the License Tracking Service?

The License Tracking Service is the only software that Dynamsoft SDKs would be communicating with at runtime, so the security of the service matters. The following are the security features of the service.

* The service is responsible for authorizing the library as well as tracking the usage. It is designed to send/receive static data only when requested. No script can be run remotely on the server nor from the server to the requesting clients.
* The service supports HTTPS and should be used after HTTPS has been configured.
* The service supports domain binding. With domain binding, authorization to use the library is only granted to requests sent from the specified domains.
* The authorization sent back from the service and the usage reports sent to the service are both encrypted.
* The service also supports setting a session password to avoid abuse.

## Can a client device work offline?

Yes, once a client device gets authorized, it can be used offline for some time. Different license options have different allowance.

* Per Device, Per Domain

  The device can be used offline till the license itself expires which usually means 365 days.

* Active Device

  The device can be used offline for at least 7 days and at most till the license expires. Contact [Dynamsoft Team](mailto:sales@dynamsoft.com) for more information.

* Other options

  The device can be used for a maximum of 7 days after which it must connect to `LTS` again for further authorization. Otherwise, it will stop working.

During the offline period, all usage data is kept on the client side and will be sent to the `LTS` all at once the next time the device gets online.

## Can I use Dynamsoft SDKs in an environment with no internet connection?

Yes. There are two scenarios in this case

* All client devices can connect to a local network within the organization.

  In this case, you can simply host your own `LTS` for license tracking.

* Client devices are never connected to any network.

  In this case, you may require a special license. Please contact [Dynamsoft Support Team](mailto:support@dynamsoft.com) for details.

## Can I unregister an inactive device?

Yes, Dynamsoft has a mechanism to delete inactive devices. The following explains how it is done.

As mentioned in [per device license]({{site.about}}licensetypes.html#per-device), Dynamsoft keeps a list of UUIDs which identify the active devices. For a "Per Device" license, each active device will consume the license quota. With a default official "Per Device" license, the list of UUIDs is automatically refreshed once every 365 days. That means, if a device hasn't been used over 365 days, its UUID will be deleted on the `LTS` .

However, if you are in a business with a high turnover rate of your devices/users, you might want the refreshing to happen more frequently so that you can buy less "seats". In this case, you can contact your account manager to refresh your device allowance every three or six months or set a faster pace for automatical renewals. Please note that an additional fee is required for the special configuration.

## Can I extend the quota of my license to support more devices or process more documents?

Yes, you can either contact [sales@dynamsoft.com](mailto:sales@dynamsoft.com) to add quota or log in the [customer portal](https://www.dynamsoft.com/customer/order/list) and place an order for extra quota yourself.

Rest assured that the Handshake Code remains unchanged during the upgrade process, so no code change is required to your application.

> Read more on [What is a Handshake Code]({{site.about}}terms.html#handshake-code)

## Can I renew my license before its current expiration date?

Yes, you can log into the customer portal to renew your license by credit card or PayPal any time before it expires. Or, you can contact [sales@dynamsoft.com](mailto:sales@dynamsoft.com) if you prefer other payment methods (wire transfer or check).

Rest assured that the Handshake Code remains unchanged during the renewal process, so no code change is required to your application.

> Read more on [What is a Handshake Code]({{site.about}}terms.html#handshake-code)

## Can I purchase a license valid for more than one year?

Yes. Please contact [sales@dynamsoft.com](mailto:sales@dynamsoft.com) with your request.

## Will the unused quota be rolled over to the next period?

No.

## What is counted as a single application?

In the following, we are listing some common scenarios. If none of these fits your situation, please feel free to contact sales@dynamsoft.com.

### Same Software Engine, Multiple Products

If you develop a software engine that is contained in two products sold separately, you need a license for each product, even if the engine is basically the same in each of the separate products.

Note: If your application is for resale, each of your customers requires separate licenses.

### Same Software, Multiple Domains

(for web applications) 

If you are using the Domain License option, to deploy the same web application to multiple domains, you need a Domain License for each domain. 

"Domain" is defined as a primary domain of your business or organization.  

For instance, the following are taken as two Domains: 

- companyA.com and companyB.com;  
- company.com and company.ca;  
- sectorA.gov.ca and sectorB.gov.ca. 

For sites that use public domain names of multi-tenant cloud platforms, a Domain is defined as a unique subdomain such as dynamsoft.force.com. 

Subdomains like subdomainA.company.com and subdomainB.company.com are counted as one Domain.  
 
Note: Domain License is not for resale. 

### Consultants and Works Made for Hire 

If you develop an application for one customer and then subsequently develop another application for another customer, this is taken as two applications even the two applications are similar. 

### Modular Application 

If a system is composed of multiple software modules that use Dynamsoft SDKs but all modules are part of the same system, Dynamsoft considers the system and all its component modules to be one "application" for licensing purposes. 

### Application Suite for External Sale 

If you develop a "suite" of applications that are always sold as a suite, Dynamsoft considers the suite as one application for licensing purposes. 

Note: If your application is for resale, each of your customers requires separate licenses. 

### Evaluation and "Light" Application Versions 

If you develop an evaluation version or a light version of your application using Dynamsoft SDKs, Dynamsoft does not require a separate development license for the evaluation/lite version. 

### New Versions and Updates of Existing Applications 

If you develop a new version of or update to an existing application, Dynamsoft does not consider the update or new version to require an additional development license. 

### Unlimited Development License 

An Unlimited Development License allows an unlimited number of programmers (working for the same organization) to use the Dynamsoft SDKs for the development of an unlimited number of internal applications. Please contact sales@dynamsoft.com if you are interested in obtaining an Unlimited Development License. 

## Policies

[Learn more about our policies ›](https://www.dynamsoft.com/Products/policies.aspx)
