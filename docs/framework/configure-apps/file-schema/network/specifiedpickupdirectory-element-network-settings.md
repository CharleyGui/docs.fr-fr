---
title: <specifiedPickupDirectory>, élément (paramètres réseau)
description: L' <specifiedPickupDirectory> élément paramètres réseau configure le répertoire local pour les options de serveur SMTP dans la .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: f0c4c1845e9542d0f3b836ff03f16bdf2979ebd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504496"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="a5030-103">\<specifiedPickupDirectory>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a5030-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="a5030-104">Configure le répertoire local pour un serveur SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="a5030-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="a5030-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5030-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a5030-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a5030-106">Attributes and Elements</span></span>  
 <span data-ttu-id="a5030-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a5030-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a5030-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="a5030-108">Attributes</span></span>  
  
|<span data-ttu-id="a5030-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="a5030-109">Attribute</span></span>|<span data-ttu-id="a5030-110">Description</span><span class="sxs-lookup"><span data-stu-id="a5030-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="a5030-111">Répertoire dans lequel les applications enregistrent des messages électroniques en vue d’un traitement ultérieur par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="a5030-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a5030-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a5030-112">Child Elements</span></span>  
 <span data-ttu-id="a5030-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a5030-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a5030-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a5030-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a5030-115">Élément</span><span class="sxs-lookup"><span data-stu-id="a5030-115">Element</span></span>|<span data-ttu-id="a5030-116">Description</span><span class="sxs-lookup"><span data-stu-id="a5030-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a5030-117">\<smtp>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a5030-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="a5030-118">Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="a5030-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5030-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="a5030-119">Remarks</span></span>  
 <span data-ttu-id="a5030-120">L' `specifiedPickupDirectory` attribut définit le répertoire dans lequel les applications enregistrent les messages électroniques à traiter par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="a5030-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5030-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="a5030-121">Example</span></span>  
 <span data-ttu-id="a5030-122">L’exemple suivant spécifie c:\maildrop comme répertoire de collecte des messages.</span><span class="sxs-lookup"><span data-stu-id="a5030-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5030-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5030-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="a5030-124">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a5030-124">Network Settings Schema</span></span>](index.md)
