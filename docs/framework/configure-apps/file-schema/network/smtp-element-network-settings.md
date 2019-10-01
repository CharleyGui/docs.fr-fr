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
ms.openlocfilehash: 2105a6dd25a7f6e5e4c1ce286be7f60beae1dca0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697607"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="6645b-102">\<smtp >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6645b-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="6645b-103">Configure le format de remise, la méthode de remise et l’adresse d’expéditeur pour l’envoi d’e-mails.</span><span class="sxs-lookup"><span data-stu-id="6645b-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[<span data-ttu-id="6645b-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="6645b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6645b-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6645b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="6645b-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6645b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>  
<span data-ttu-id="6645b-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<smtp >**</span><span class="sxs-lookup"><span data-stu-id="6645b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6645b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6645b-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6645b-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6645b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6645b-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6645b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6645b-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="6645b-111">Attributes</span></span>  
  
|<span data-ttu-id="6645b-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="6645b-112">Attribute</span></span>|<span data-ttu-id="6645b-113">Description</span><span class="sxs-lookup"><span data-stu-id="6645b-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="6645b-114">Spécifie le format de remise pour les messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="6645b-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="6645b-115">Les valeurs acceptables sont SevenBit et international.</span><span class="sxs-lookup"><span data-stu-id="6645b-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="6645b-116">Spécifie la méthode de remise des messages électroniques.</span><span class="sxs-lookup"><span data-stu-id="6645b-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="6645b-117">Les valeurs acceptables sont Network, PickupDirectoryFromIis et SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="6645b-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="6645b-118">Spécifie l’adresse d’expédition pour les messages électroniques sortants.</span><span class="sxs-lookup"><span data-stu-id="6645b-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6645b-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6645b-119">Child Elements</span></span>  
  
|<span data-ttu-id="6645b-120">Attribut</span><span class="sxs-lookup"><span data-stu-id="6645b-120">Attribute</span></span>|<span data-ttu-id="6645b-121">Description</span><span class="sxs-lookup"><span data-stu-id="6645b-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="6645b-122">Configure le répertoire local pour un serveur SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="6645b-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="6645b-123">Configure les options réseau pour un serveur SMTP externe.</span><span class="sxs-lookup"><span data-stu-id="6645b-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6645b-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6645b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6645b-125">**Élément**</span><span class="sxs-lookup"><span data-stu-id="6645b-125">**Element**</span></span>|<span data-ttu-id="6645b-126">**Description**</span><span class="sxs-lookup"><span data-stu-id="6645b-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6645b-127">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="6645b-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="6645b-128">Configure les options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="6645b-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6645b-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="6645b-129">Example</span></span>  
 <span data-ttu-id="6645b-130">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l’aide des informations d’identification réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="6645b-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6645b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6645b-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="6645b-132">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="6645b-132">Network Settings Schema</span></span>](index.md)
