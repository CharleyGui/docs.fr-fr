---
title: <smtp>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 625c3cb82a8659c742b540724e5cf31be65a705e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089101"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="e758d-102">\<l’élément de > SMTP (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="e758d-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="e758d-103">Configure le format de remise, la méthode de remise et l’adresse d’expéditeur pour l’envoi d’e-mails.</span><span class="sxs-lookup"><span data-stu-id="e758d-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
<span data-ttu-id="e758d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e758d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e758d-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e758d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e758d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings**](mailsettings-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="e758d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="e758d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**SMTP** ></span><span class="sxs-lookup"><span data-stu-id="e758d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="e758d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e758d-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e758d-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e758d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e758d-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e758d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e758d-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="e758d-111">Attributes</span></span>  
  
|<span data-ttu-id="e758d-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="e758d-112">Attribute</span></span>|<span data-ttu-id="e758d-113">Description</span><span class="sxs-lookup"><span data-stu-id="e758d-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="e758d-114">Spécifie le format de remise pour les messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="e758d-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="e758d-115">Les valeurs acceptables sont SevenBit et international.</span><span class="sxs-lookup"><span data-stu-id="e758d-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="e758d-116">Spécifie la méthode de remise des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="e758d-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="e758d-117">Les valeurs acceptables sont Network, PickupDirectoryFromIis et SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="e758d-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="e758d-118">Spécifie l’adresse d’expédition pour les messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="e758d-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e758d-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e758d-119">Child Elements</span></span>  
  
|<span data-ttu-id="e758d-120">Attribut</span><span class="sxs-lookup"><span data-stu-id="e758d-120">Attribute</span></span>|<span data-ttu-id="e758d-121">Description</span><span class="sxs-lookup"><span data-stu-id="e758d-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="e758d-122">Configure le répertoire local pour un serveur SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="e758d-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="e758d-123">Configure les options réseau pour un serveur SMTP externe.</span><span class="sxs-lookup"><span data-stu-id="e758d-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e758d-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e758d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e758d-125">**Élément**</span><span class="sxs-lookup"><span data-stu-id="e758d-125">**Element**</span></span>|<span data-ttu-id="e758d-126">**Description**</span><span class="sxs-lookup"><span data-stu-id="e758d-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e758d-127">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="e758d-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="e758d-128">Configure les options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="e758d-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e758d-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="e758d-129">Example</span></span>  
 <span data-ttu-id="e758d-130">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l’aide des informations d’identification réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="e758d-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e758d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e758d-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="e758d-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="e758d-132">Network Settings Schema</span></span>](index.md)
