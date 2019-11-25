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
ms.openlocfilehash: 1acc724bb14c3610f14d06452c30b3d5dac42e13
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089072"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="195b2-102">\<specifiedPickupDirectory >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="195b2-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="195b2-103">Configure le répertoire local pour un serveur SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="195b2-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="195b2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="195b2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="195b2-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="195b2-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="195b2-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings**](mailsettings-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="195b2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="195b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**SMTP**](smtp-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="195b2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="195b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<specifiedPickupDirectory >**</span><span class="sxs-lookup"><span data-stu-id="195b2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="195b2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="195b2-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="195b2-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="195b2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="195b2-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="195b2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="195b2-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="195b2-112">Attributes</span></span>  
  
|<span data-ttu-id="195b2-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="195b2-113">Attribute</span></span>|<span data-ttu-id="195b2-114">Description</span><span class="sxs-lookup"><span data-stu-id="195b2-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="195b2-115">Répertoire dans lequel les applications enregistrent des messages électroniques en vue d’un traitement ultérieur par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="195b2-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="195b2-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="195b2-116">Child Elements</span></span>  
 <span data-ttu-id="195b2-117">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="195b2-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="195b2-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="195b2-118">Parent Elements</span></span>  
  
|<span data-ttu-id="195b2-119">Élément</span><span class="sxs-lookup"><span data-stu-id="195b2-119">Element</span></span>|<span data-ttu-id="195b2-120">Description</span><span class="sxs-lookup"><span data-stu-id="195b2-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="195b2-121">\<l’élément de > SMTP (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="195b2-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="195b2-122">Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="195b2-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="195b2-123">Notes</span><span class="sxs-lookup"><span data-stu-id="195b2-123">Remarks</span></span>  
 <span data-ttu-id="195b2-124">L’attribut `specifiedPickupDirectory` définit le répertoire dans lequel les applications enregistrent les messages électroniques à traiter par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="195b2-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="195b2-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="195b2-125">Example</span></span>  
 <span data-ttu-id="195b2-126">L’exemple suivant spécifie c:\maildrop comme répertoire de collecte des messages.</span><span class="sxs-lookup"><span data-stu-id="195b2-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="195b2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="195b2-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="195b2-128">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="195b2-128">Network Settings Schema</span></span>](index.md)
