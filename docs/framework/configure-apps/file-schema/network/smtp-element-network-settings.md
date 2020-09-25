---
title: <smtp>, élément (paramètres réseau)
description: L' <smtp> élément paramètres réseau configure le format de remise, la méthode de remise et l’adresse de l’expéditeur pour l’envoi des options de courrier électronique dans la .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 58f496b4a07f7d5531df897dd54bb6176111f1c4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178318"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="e099a-103">\<smtp>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="e099a-103">\<smtp> Element (Network Settings)</span></span>

<span data-ttu-id="e099a-104">Configure le format de remise, la méthode de remise et l’adresse d’expéditeur pour l’envoi d’e-mails.</span><span class="sxs-lookup"><span data-stu-id="e099a-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="e099a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e099a-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e099a-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e099a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e099a-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e099a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e099a-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e099a-108">Attributes</span></span>  
  
|<span data-ttu-id="e099a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e099a-109">Attribute</span></span>|<span data-ttu-id="e099a-110">Description</span><span class="sxs-lookup"><span data-stu-id="e099a-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="e099a-111">Spécifie le format de remise pour les messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="e099a-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="e099a-112">Les valeurs acceptables sont SevenBit et international.</span><span class="sxs-lookup"><span data-stu-id="e099a-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="e099a-113">Spécifie la méthode de remise des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="e099a-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="e099a-114">Les valeurs acceptables sont Network, PickupDirectoryFromIis et SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="e099a-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="e099a-115">Spécifie l’adresse d’expédition pour les messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="e099a-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e099a-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e099a-116">Child Elements</span></span>  
  
|<span data-ttu-id="e099a-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="e099a-117">Attribute</span></span>|<span data-ttu-id="e099a-118">Description</span><span class="sxs-lookup"><span data-stu-id="e099a-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="e099a-119">Configure le répertoire local pour un serveur SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="e099a-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="e099a-120">Configure les options réseau pour un serveur SMTP externe.</span><span class="sxs-lookup"><span data-stu-id="e099a-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e099a-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e099a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e099a-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="e099a-122">**Element**</span></span>|<span data-ttu-id="e099a-123">**Description**</span><span class="sxs-lookup"><span data-stu-id="e099a-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e099a-124">\<mailSettings> , Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="e099a-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="e099a-125">Configure les options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="e099a-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e099a-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="e099a-126">Example</span></span>  

 <span data-ttu-id="e099a-127">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l’aide des informations d’identification réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="e099a-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e099a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e099a-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="e099a-129">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="e099a-129">Network Settings Schema</span></span>](index.md)
