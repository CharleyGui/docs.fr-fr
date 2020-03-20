---
title: <specifiedPickupDirectory>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 4b0cbaf9a7bfe2a9b1610811f4201253d219a6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154606"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="199b9-102">\<specifiedPickupDirectory> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="199b9-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="199b9-103">Configure l’annuaire local pour un serveur Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="199b9-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="199b9-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="199b9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="199b9-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="199b9-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="199b9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="199b9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="199b9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>smtp**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="199b9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="199b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>spécifiéPickupDirectory**</span><span class="sxs-lookup"><span data-stu-id="199b9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="199b9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="199b9-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="199b9-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="199b9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="199b9-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="199b9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="199b9-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="199b9-112">Attributes</span></span>  
  
|<span data-ttu-id="199b9-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="199b9-113">Attribute</span></span>|<span data-ttu-id="199b9-114">Description</span><span class="sxs-lookup"><span data-stu-id="199b9-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="199b9-115">L’annuaire où les applications enregistrent le courrier électronique pour le traitement ultérieur par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="199b9-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="199b9-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="199b9-116">Child Elements</span></span>  
 <span data-ttu-id="199b9-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="199b9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="199b9-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="199b9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="199b9-119">Élément</span><span class="sxs-lookup"><span data-stu-id="199b9-119">Element</span></span>|<span data-ttu-id="199b9-120">Description</span><span class="sxs-lookup"><span data-stu-id="199b9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="199b9-121">\<smtp> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="199b9-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="199b9-122">Configure les options d’envoi de courrier simple par protocole de transport de courrier (SMTP).</span><span class="sxs-lookup"><span data-stu-id="199b9-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="199b9-123">Notes </span><span class="sxs-lookup"><span data-stu-id="199b9-123">Remarks</span></span>  
 <span data-ttu-id="199b9-124">L’attribut `specifiedPickupDirectory` définit l’annuaire lorsque les applications enregistrent les messages postaux à traiter par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="199b9-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="199b9-125"> Exemple</span><span class="sxs-lookup"><span data-stu-id="199b9-125">Example</span></span>  
 <span data-ttu-id="199b9-126">L’exemple suivant spécifie c: 'maildrop comme répertoire de ramassage de courrier.</span><span class="sxs-lookup"><span data-stu-id="199b9-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="199b9-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="199b9-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="199b9-128">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="199b9-128">Network Settings Schema</span></span>](index.md)
