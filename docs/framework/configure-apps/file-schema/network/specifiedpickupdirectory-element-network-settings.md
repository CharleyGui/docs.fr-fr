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
ms.openlocfilehash: 5bb7fc5405b1ee2f0f054bc6e9f043a3f9fcd1ec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176160"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="cb1b1-103">\<specifiedPickupDirectory>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="cb1b1-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>

<span data-ttu-id="cb1b1-104">Configure le répertoire local pour un serveur SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="cb1b1-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="cb1b1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb1b1-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb1b1-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cb1b1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cb1b1-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cb1b1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb1b1-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="cb1b1-108">Attributes</span></span>  
  
|<span data-ttu-id="cb1b1-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="cb1b1-109">Attribute</span></span>|<span data-ttu-id="cb1b1-110">Description</span><span class="sxs-lookup"><span data-stu-id="cb1b1-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="cb1b1-111">Répertoire dans lequel les applications enregistrent des messages électroniques en vue d’un traitement ultérieur par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="cb1b1-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb1b1-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cb1b1-112">Child Elements</span></span>  

 <span data-ttu-id="cb1b1-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cb1b1-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb1b1-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cb1b1-114">Parent Elements</span></span>  
  
|<span data-ttu-id="cb1b1-115">Élément</span><span class="sxs-lookup"><span data-stu-id="cb1b1-115">Element</span></span>|<span data-ttu-id="cb1b1-116">Description</span><span class="sxs-lookup"><span data-stu-id="cb1b1-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb1b1-117">\<smtp> , Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="cb1b1-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="cb1b1-118">Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="cb1b1-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb1b1-119">Notes</span><span class="sxs-lookup"><span data-stu-id="cb1b1-119">Remarks</span></span>  

 <span data-ttu-id="cb1b1-120">L' `specifiedPickupDirectory` attribut définit le répertoire dans lequel les applications enregistrent les messages électroniques à traiter par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="cb1b1-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb1b1-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="cb1b1-121">Example</span></span>  

 <span data-ttu-id="cb1b1-122">L’exemple suivant spécifie c:\maildrop comme répertoire de collecte des messages.</span><span class="sxs-lookup"><span data-stu-id="cb1b1-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb1b1-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb1b1-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="cb1b1-124">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="cb1b1-124">Network Settings Schema</span></span>](index.md)
