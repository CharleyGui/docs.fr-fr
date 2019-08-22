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
ms.openlocfilehash: b2e31dee4f5aff2bf6cedf5c4e9ca235695b0a53
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659096"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="27059-102">\<specifiedPickupDirectory >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="27059-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="27059-103">Configure le répertoire local pour un serveur SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="27059-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="27059-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="27059-104">\<configuration></span></span>  
<span data-ttu-id="27059-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="27059-105">\<system.net></span></span>  
<span data-ttu-id="27059-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="27059-106">\<mailSettings></span></span>  
<span data-ttu-id="27059-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="27059-107">\<smtp></span></span>  
<span data-ttu-id="27059-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="27059-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27059-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27059-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27059-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="27059-110">Attributes and Elements</span></span>  
 <span data-ttu-id="27059-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="27059-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27059-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="27059-112">Attributes</span></span>  
  
|<span data-ttu-id="27059-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="27059-113">Attribute</span></span>|<span data-ttu-id="27059-114">Description</span><span class="sxs-lookup"><span data-stu-id="27059-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="27059-115">Répertoire dans lequel les applications enregistrent des messages électroniques en vue d’un traitement ultérieur par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="27059-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27059-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="27059-116">Child Elements</span></span>  
 <span data-ttu-id="27059-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="27059-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27059-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="27059-118">Parent Elements</span></span>  
  
|<span data-ttu-id="27059-119">Élément</span><span class="sxs-lookup"><span data-stu-id="27059-119">Element</span></span>|<span data-ttu-id="27059-120">Description</span><span class="sxs-lookup"><span data-stu-id="27059-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27059-121">\<Élément > SMTP (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="27059-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="27059-122">Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="27059-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27059-123">Notes</span><span class="sxs-lookup"><span data-stu-id="27059-123">Remarks</span></span>  
 <span data-ttu-id="27059-124">L' `specifiedPickupDirectory` attribut définit le répertoire dans lequel les applications enregistrent les messages électroniques à traiter par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="27059-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27059-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="27059-125">Example</span></span>  
 <span data-ttu-id="27059-126">L’exemple suivant spécifie c:\maildrop comme répertoire de collecte des messages.</span><span class="sxs-lookup"><span data-stu-id="27059-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="27059-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27059-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="27059-128">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="27059-128">Network Settings Schema</span></span>](index.md)
