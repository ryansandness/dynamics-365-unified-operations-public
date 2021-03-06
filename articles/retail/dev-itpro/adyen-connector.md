---
# required metadata

title: Dynamics 365 Payment Connector for Adyen
description: This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for Adyen.
author: rassadi
manager: AnnBe
ms.date: 01/04/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Dynamics 365 Payment Connector for Adyen

[!include [banner](../includes/banner.md)]

This topic provides an overview of the Microsoft Dynamics 365 Payment Connector for Adyen. It includes a comprehensive list of supported features and functionality, a guide to setting up and configuring the connector, troubleshooting information, and descriptions of some common issues.

## Key terms

| Term | Description |
|---|---|
| Payment connector | An extension that facilitates communication between Microsoft Dynamics 365 for Retail (and associated components) and a payment service. The connector that is described in this topic was implemented by using the standard payments software development kit (SDK). |
| Card present | When a payment terminal is implemented by using the **INamedRequestHandler** interface, it's typically referred to as a card-present payment connector. The term *card present* is used because this type of payment connector supports transactions where a physical card is presented. |
| Card not present | Payment connectors that are intended to be used in the back office, a call center, or e-Commerce integrations are implemented by using the **IPaymentProcessor** interface. They are typically referred to as card-not-present payment connectors. |

## Overview

This topic includes the following main sections to help you evaluate and set up the Dynamics 365 Payment Connector for Adyen.

- **[Supported features, functionality, and payment terminals](#Supported-features-functionality-and-payment-terminals)** – This section describes the set of features and functionalities that the Dynamics 365 Payment Connector for Adyen supports.
- **[Sign up with Adyen](#Sign-up-with-Adyen)** – This section explains how to sign up for a merchant account with Adyen.
- **[Setup and configuration](#Setup-and-configuration)** – This section explains, in detail, how to set up and configure the Dynamics 365 Payment Connector for Adyen across the point of sale (POS), call center, and e-Commerce channels.

## Supported features, functionality, and payment terminals

The out-of-box Dynamics 365 Payment Connector for Adyen uses the standard payments SDK. Therefore, it doesn't have special capabilities that aren't also available to other payment connectors.

### Supported versions of Microsoft Dynamics

The first-party out-of-box Dynamics 365 Payment Connector for Adyen is supported in Microsoft Dynamics 365 for Finance and Operations version 8.1.3 (January 2019) or later, and in Microsoft Dynamics 365 for Retail version 8.1.3 or later. However, third parties can still develop other payment connectors for Adyen for earlier versions of Microsoft Dynamics 365.

### Supported payment terminals

The Dynamics 365 Payment Connector for Adyen takes advantage of the device-agnostic [Adyen Payment Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api). It supports all payment terminals that this application programming interface (API) supports. For a complete list of supported payment terminals, visit the [Adyen POS terminals](https://www.adyen.com/pos-payments/terminals) page.

### Supported input methods

| Connector type | Dip | Swipe | Tap | Manual entry |
|---|---|---|---|---|
| Card present | Yes | Yes | Yes | Yes |
| Card not present | No | No | No | Yes |

### Supported payment instruments

#### Supported debit and credit cards

| Brand | Variant | Supported | Card present | Card not present |
|---|---|---|---|---|
| MasterCard | Credit | ✔ | Yes | Yes |
| MasterCard | Debit | ✔ | Yes | Yes |
| MasterCard | Alpha Bank Bonus | ✔ | Yes | Yes |
| MasterCard | Apple Pay | ✔ | Yes | No |
| MasterCard | Samsung Pay | ✔ | Yes | No |
| MasterCard | Maestro | ✔ | Yes | Yes |
| MasterCard | Maestro Samsung Pay | ✔ | Yes | No |
| MasterCard | Maestro UK | ✔ | Yes | Yes |
| VISA | Credit | ✔ | Yes | Yes |
| VISA | Debit | ✔ | Yes | Yes |
| VISA | Alpha Bank Bonus | ✔ | Yes | Yes |
| VISA | Android Pay | ✔ | Yes | No |
| VISA | Apple Pay | ✔ | Yes | No |
| VISA | Samsung Pay | ✔ | Yes | No |
| VISA | VISA Checkout | ✔ | Yes | Yes |
| VISA | VISA Dankort | ✔ | Yes | Yes |
| VISA | VISA Hipotecario | ✔ | Yes | Yes |
| VISA | VISA Aravia Card | ✔ | Yes | Yes |
| AMEX | Credit | ✔ | Yes | Yes |
| AMEX | Debit | ✔ | Yes | Yes |
| AMEX | Android Pay | ✔ | Yes | No |
| AMEX | Apple Pay | ✔ | Yes | No |
| AMEX | Samsung Pay | ✔ | Yes | No |
| AMEX | AMEX Commercial | ✔ | Yes | Yes |
| AMEX | AMEX Consumer | ✔ | Yes | Yes |
| AMEX | AMEX Corporate | ✔ | Yes | Yes |
| AMEX | AMEX Small Business | ✔ | Yes | Yes |
| Discover | Standard | ✔ | Yes | Yes |
| Discover | Android Pay | ✔ | Yes | No |
| Discover | Apple Pay | ✔ | Yes | No |
| Discover | Samsung Pay | ✔ | Yes | No |
| Diners | Standard | ✔ | Yes | Yes |
| Dineromail | Standard | ✔ | Yes | Yes |
| JCB | Standard | ✔ | Yes | Yes |
| Union Pay* | Standard | Support will be added in a future release. | No | Not applicable |
| Interac Debit | Standard | Support will be added in a future release. | No | No |

*Adyen does not support recurring tokens for Union Pay, so it cannot be used for card not present purchases.


#### Supported gift cards

| Scheme | Card present | Card not present |
|---|---|---|
| Givex | ✔ (version 8.1.3) | Support will be added in a future release. |
| SVS | ✔ (version 8.1.3) | Support will be added in a future release. |

To support these external gift card schemes through the Dynamics 365 Payment Connector for Adyen, you must complete additional steps. For more information, see [Support for external gift cards](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/gift-card).

#### Supported wallets

| Scheme | Card present | Card not present |
|---|---|---|
| Alipay | Support will be added in a future release. | No |
| WeChat | Support will be added in a future release. | No |

#### Supported Dynamics 365 payment features

The following table shows the set of Dynamics 365 payment features that the Dynamics 365 Payment Connector for Adyen supports. These features use enhancements that were introduced in the payments SDK and some Retail components in December 2018. They aren't exclusive to the Dynamics 365 Payment Connector for Adyen. For more information about how to uptake these enhancements for a different payment connector, see [Create an end-to-end payment integration for a payment terminal](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/end-to-end-payment-extension).

| Scheme | Card present | Card not present |
|---|---|---|
| Duplicate Payment Protection | Yes (version 8.1.3) | No |
| Omni Channel Tokenization | Yes (version 8.1.3) | Yes (version 8.1.3) |
| Linked Refunds | Support will be added in a future release. | Support will be added in a future release. |

## Sign up with Adyen

To use the Dynamics 365 Payment Connector for Adyen, you must have a separate agreement with Adyen. To learn more about Adyen's services, or to create a test merchant account that you can use for the Dynamics 365 Payment Connector for Adyen, visit the [Adyen website](https://www.adyen.com/partners/dynamics).

If you prefer that Adyen contact you directly, send an email to <partnerships@adyen.com>. In the subject line of the email, include the term "Microsoft Dynamics connector." In the body of the email, be sure to include enough information so that the inquiry can be routed correctly:

- Business name
- Nature of business (for example, "merchant" or "Microsoft partner")
- Business website
- Business address
- Contact name, title, email, and phone
- Annual processing volume (Optional)
- Description of the required services (for example "e-Commerce only" or "e-Commerce and card present, with *X* number of payment terminals")

## Setup and configuration

> [!NOTE]
> These instructions assume that you've already signed up for a merchant account with Adyen, and that you have access to the Adyen merchant dashboard.

### Prerequisites

The following prerequisites must be completed before payments can be configured in any channel.

#### Set up a processor for new credit cards

To process payments across point of sale (POS) terminals, a call center, or e-Commerce, you must configure a new default payment processor for new credit cards. Follow these steps to configure a default payment processor.

1. Sign in to Retail headquarters, and go to **Accounts receivable \> Payments setup \> Payment services**.
2. On the Action Pane, select **New**, and then, on the **Setup** tab, enter the following information.

    | Field | Description | Sample value |
    |---|---|---|
    | Payment service | Enter the name of the payment service to configure. | Adyen Payment Service |
    | Payment connector | Select the payment connector to use for new credit card payments. | Dynamics 365 Payment Connector for Adyen |
    | Test mode | Select whether the connector should run in test mode. In production environments, you should set this field to **false**. In test environments (for example, sandbox and dev environments), you should set it to **true**. | true |
    | Default processor for credit cards | Specify whether this payment processor should be the default processor that's used for new credit cards. | Yes |
    | Bypass payment processor for zero transactions | Specify whether this payment processor should be skipped for transactions that have a 0 (zero) amount. | Yes |

3. On the **Payment service account** tab, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|---|---|---|
    | Assembly Name | Enter the name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | Microsoft.Dynamics.Commerce.Payments.Connector.Adyen.Processor.Portable, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 |
    | Service account ID | Enter the unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | f107ba65-06c5-4609-ae36-ba1c228b52c8 |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. Currently, only version V001 is supported. | Yes | Yes | V001 |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | Enter the domain to use when payment requests are made to Adyen. | No | No | `https://terminal-api-live.adyen.com/sync` |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#Sign-up-with-Adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Password phrase | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Identifier | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Version | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | Yes | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key) page on the Adyen website. | Yes | No | *✔ |* |
    | Supported Currencies | Enter the currencies that the connector should process. Note that, in card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. | No | No | SVS |

### POS payment terminal

#### Onboard and configure an Adyen payment terminal

> [!NOTE]
> These instructions assume that you have access to an Adyen payment terminal.

Go to the [Point of sale](https://docs.adyen.com/developers/point-of-sale) page on the Adyen website, and follow the instructions to onboard your Adyen payment terminal. Skip any steps that instruct you to download Adyen-specific apps. During the onboarding process, make a note of the following information for each payment terminal. You will need this information in the [Configure the payment terminal IP address and EFT POS register number](#Configure-the-payment-terminal-IP-address-and-EFT-POS-register-number) section later in this topic.

- IP address of the payment terminal
- POIID (POIID is comprised of the serial number and model number of the device. It is used to uniquely identify the device.)

After the payment terminal is onboarded, sign in to the [Adyen Customer Area](https://ca-test.adyen.com/ca/ca/login.shtml), go to the terminal that you want to configure, and make a note of the following information for each payment terminal. You will need this information in the [EFT service](#EFT-service) section later in this topic.

- Key identifier
- Key passphrase
- Key version

#### Set up a Dynamics 365 POS hardware profile

1. Sign in to Retail headquarters, and go to **Retail \> Channel setup \> POS setup \> POS profiles \> Hardware profiles**.
2. Select the hardware profile to add the Dynamics 365 Payment Connector for Adyen for.
3. Follow the steps in the [EFT service](#EFT-service) and [PIN pad](#PIN-pad) sections that follow.

##### EFT service

1. On the **EFT service** FastTab, in the **EFT Service** field, select **Payment Connector**.
2. On the **Connectors** tab, select **New**, and then, in the **Connector** field, select **Dynamics 365 Payment Connector for Adyen**. Make sure that the value in the **Sequence number** field is lower than the value for all other connectors.
3. In the **Connector properties** section, enter the following information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|---|---|---|
    | Assembly Name | Enter the name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | Microsoft.Dynamics.Commerce.Payments.Connector.Adyen.Processor.Portable, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 |
    | Service account ID | Enter the unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | f107ba65-06c5-4609-ae36-ba1c228b52c8 |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. Currently, only version V001 is supported. | Yes | Yes | V001 |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. You should set this field to **Live** only for production devices and transactions. | Yes | Yes | Live |
    | Optional Domain | Enter the domain to use when payment requests are made to Adyen. | No | No | `https://terminal-api-live.adyen.com/sync` |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#Sign-up-with-Adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | Enter the Adyen Terminal API architecture to use. The possible values are **Local** and **Cloud**. In most cases, when Microsoft Dynamics 365 for Retail Modern POS is on the same network as the Adyen payment terminal, you should set this field to **Local**. For more information about the different Terminal API architectures, see the [Introducing the Terminal API](https://www.adyen.com/blog/introducing-the-terminal-api) page on the Adyen website. | Yes | Yes | Local |
    | Local Password phrase | Enter the Adyen key passphrase for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#Sign-up-with-Adyen) section. | Yes | No | keypassphrase123 |
    | Local Key Identifier | Enter the Adyen key identifier for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#Sign-up-with-Adyen) section. | Yes | No | mykey |
    | Local Key Version | Enter the Adyen key version for the payment terminal. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#Sign-up-with-Adyen) section. | Yes | No | 0 |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | Yes | 1 |
    | Cloud API Key | This field is used only for the card-not-present payment integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Supported Currencies | Enter the currencies that the connector should process. Note that, in card-present scenarios, Adyen can support additional currencies through [Dynamic Currency Conversion](https://www.adyen.com/pos-payments/dynamic-currency-conversion) after the transaction request is sent to the payment terminal. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. The possible values are **SVS** and **GIVEX**. | No | No | SVS |

4. On the Action Pane, select **Save**.

##### PIN pad

1. On the **PIN pad** FastTab, in the **PIN pad** field, select **Network**.
2. In the **Device name** field, enter **MicrosoftAdyenDeviceV001**.

#### <a id="Set-up-a-Dynamics-365-register"></a>Set up a Dynamics 365 register

> [!NOTE]
> These instructions assume that there is a dedicated mapping between a POS register and an Adyen payment terminal. For a hardware station that is based on Microsoft Internet Information Services (IIS), go to **Retail \> Channels \> Retail stores \> All retail stores**, and select the store that you're setting up. Then, on the page for that store, on the **Hardware Stations** FastTab, follow the same instructions.

##### Configure the payment terminal IP address and EFT POS register number

1. Sign in to Retail headquarters, and go to **Retail \> Channel setup \> POS setup \> Registers**.
2. Select the register to link to the Adyen payment terminal.
3. On the **POS Registers** page, on the **General** FastTab, in the **EFT** section, in the **EFT POS register number** field, enter a unique number. The register number must be exactly four digits long, and it must be unique across all POS registers that are under the same Adyen merchant account ID.
4. In the **Profiles** section, in the **Hardware profile** field, select the hardware profile that you configured earlier.
5. Save your changes.
6. On the Action Pane, on the **Register** tab, in the **Hardware** group, select **Configure IP addresses**.
7. On the **IP address configuration** page, on the **PIN pad** FastTab, in the **IP address** field, enter the IP address of the terminal in the following format: `https://<IP address>:8443/nexo/<POIID>`. Here, **\<IP address\>** and **\<POIID\>** are the values that you made a note of when you onboarded the Adyen payment terminal. Here is an example: `https://192.168.1.3:8443/nexo/MX925-123456789`.

#### <a id="Update-the-Modern-POS-or-IIS-Hardware-Station-configuration"></a>Update the Modern POS or IIS Hardware Station configuration

If you're packaging your own version of Modern POS by using the Retail SDK, you must follow these steps only one time in the SDK code before the installer is packaged. Otherwise, you must follow these steps after the standard Modern POS or IIS Hardware Station is installed.

1. Open the **dllhost.exe.config** file (for Modern POS) or the **web.config** file (for IIS Hardware Station).
2. Update the **PreloadedComposition** section as shown here, to switch from the legacy payment device adapter to the standard payment device adapter.

    ``` xml
    <PreloadedComposition>
        <composition>
            <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.PaymentDeviceAdapter" />
            <!-- Switch from legacy to standard Payment Device Adapter.
            <add source="assembly" value="Microsoft.Dynamics.Commerce.HardwareStation.Peripherals.Legacy.PaymentDeviceAdapter" />
            -->
        </composition>
    </PreloadedComposition>
    ```

### Call center

To configure the Dynamics 365 Payment Connector for Adyen for call center payments, follow the instructions in the [Set up a processor for new credit cards](#Set-up-a-processor-for-new-credit-cards) section earlier in this topic.

### E-Commerce

1. Sign in to Retail headquarters, and go to **Retail \> Channels \> Online stores**.
2. Select the online store to add the Dynamics 365 Payment Connector for Adyen for.
3. On the **Online store** page, on the **Payment accounts** FastTab, select **Add**.
4. In the **Connectors** field, select **Dynamics 365 Payment Connector for Adyen**.
5. Enter the following additional information.

    | Field | Description | Required | Automatically set | Sample value |
    |---|---|---|---|---|
    | Assembly Name | Enter the name of the assembly for the Dynamics 365 Payment Connector for Adyen. | Yes | Yes | Microsoft.Dynamics.Commerce.Payments.Connector.Adyen.Processor.Portable, Version=7.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35 |
    | Service Account ID | Enter the unique identifier for the setup of the merchant properties. This identifier is stamped on payment transactions and identifies the merchant properties that downstream processes (such as invoicing) should use. | Yes | Yes | f107ba65-06c5-4609-ae36-ba1c228b52c8 |
    | Version | Enter the version of the Dynamics 365 Payment Connector for Adyen to use. Currently, only version V001 is supported. | Yes | Yes | V001 |
    | Gateway environment | Enter the Adyen gateway environment to map to. The possible values are **Test** and **Live**. | Yes | Yes | Live |
    | Optional Domain | Enter the domain to use when payment requests are made to Adyen. | No | No | `https://terminal-api-live.adyen.com/sync` |
    | Merchant account ID | Enter the unique Adyen merchant identifier. This value is provided when you sign up with Adyen as described in the [Sign up with Adyen](#Sign-up-with-Adyen) section. | Yes | No | MerchantIdenfier |
    | Terminal architecture | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Password phrase | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Identifier | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Key Version | This field is used only for the POS payment terminal integration and should be left blank. | No | Yes | *Leave this field blank.* |
    | Local Cryptor Version | Enter the Adyen cryptor version to use when you interact with the Adyen gateway. You should set this field to **1**. | Yes | No | 1 |
    | Cloud API Key | Enter the Adyen cloud API key. You can obtain this key by following the instructions on the [How to get the API key](https://docs.adyen.com/developers/user-management/how-to-get-the-api-key) page on the Adyen website. | Yes | No | *The full cloud API key* |
    | Supported Currencies | Enter the currencies that the connector should process. | Yes | Yes | USD;EUR |
    | Supported Tender Types | Enter the tender types that the connector should process. | Yes | Yes | Visa;MasterCard;Amex;Discover;Debit |
    | Gift card provider | Enter the gift card provider that the connector should use to process gift cards. The possible values are **SVS** and **GIVEX**. | No | No | SVS |

6. On the Action Pane, select **Save**.

## Frequently asked questions

### Can I reuse my existing payment terminal with the Adyen connector?

No. Adyen payment terminals are injected with the Adyen software. Therefore, existing payment terminals that aren't preconfigured with Adyen can't be reused with the Dynamics 365 Payment Connector for Adyen.

### Do I need a static IP address for the Adyen payment terminal?

Yes. Modern POS requires a known IP address to communicate with the Adyen payment terminal. Although the IP address of the Adyen payment terminal can be changed in the Retail client, attempts to keep up with changing IP addresses involve significant overhead and could cause business disruption.

### Can I use my merchant bank?

Yes. Adyen can work with any merchant bank.

## Troubleshooting

### POS payment terminals

#### General issues

For all general issues, you should always consult the Modern POS or IIS Hardware Station event logs first. You can find these logs found under the following nodes in the Microsoft Windows event log:

- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-ModernPOS
- Application and Services Logs \> Microsoft \> Dynamics \> Commerce-Hardware Station

#### Failing payment transactions

When payment transactions aren't successfully processed through the Adyen payment terminal, the corresponding error messages in the Dynamics 365 POS will contain a PSP reference number(PSP is the reference ID provided by Adyen used to uniquely identify each transaction). Provide this reference number when you contact Adyen support for help with specific transactions.

## Common issues

### POS payment terminals

#### The EFT terminal ID isn't set

<table>
<tbody>
<tr>
<td><strong>Title</strong></td>
<td>EFT Terminal ID is not set</td>
</tr>
<tr>
<td><strong>Symptom</strong></td>
<td>Payment authorization calls fail, and a hardware error occurs. An error message in the event log indicates that the <strong>EFT Terminal ID</strong> value isn't set.</td>
</tr>
<tr>
<td><strong>Root cause</strong></td>
<td>This issue can occur when the <strong>EFT POS Register Number</strong> field isn't set on the register or the IIS Hardware Station. It can also occur if the value is set but isn't correctly synced to the POS terminal. Finally, it can also occur when the value is cached.</td>
</tr>
<td><strong>Fix</strong></td>
<td>Follow the instructions in the <a href="#Set-up-a-Dynamics-365-register">Set up a Dynamics 365 register</a> section earlier in this topic. Then run the <strong>1070</strong> and <strong>1090</strong> distribution schedules. If the issue isn't resolved, consider reactivating Modern POS, because the value of the <strong>EFT POS Register Number</strong> field might be cached and might need to be reset.</td>
</tr>
</tbody>
</table>

#### The Modern POS or IIS Hardware Station configuration isn't updated

<table>
<tbody>
<tr>
<td><strong>Title</strong></td>
<td>Config is not updated</td>
</tr>
<tr>
<td><strong>Symptom</strong></td>
<td>Modern POS error: "Sign in Error. The initialization data couldn't be loaded."</td>
</tr>
<tr>
<td><strong>Root cause</strong></td>
<td>This issue can occur when the POS is redeployed but the dllhost.config file hasn't been updated.</td>
</tr>
<td><strong>Fix</strong></td>
<td>Follow the instructions in the <a href='#Update-the-Modern-POS-or-IIS-Hardware-Station-configuration'>Update the Modern POS or IIS Hardware Station configuration</a> section earlier in this topic. Then end the dllhost.exe task on the <strong>Details</strong> tab in Task Manager, and reopen Modern POS. If you're using an IIS Hardware Station, reset IIS.</td>
</tr>
</tbody>
</table>

## Related articles

- [Payments FAQ](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/payments-retail)
