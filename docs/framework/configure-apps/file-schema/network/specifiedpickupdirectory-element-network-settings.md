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
ms.sourcegitcommit: 0a798a7e9680e2d0a5a81a3eaa203870ea782883
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "79154606"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="82687-102">\<specifiedPickupDirectory>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="82687-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="82687-103">Configure le répertoire local pour un serveur SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="82687-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="82687-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82687-104">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82687-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="82687-105">Attributes and Elements</span></span>  
 <span data-ttu-id="82687-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="82687-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82687-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="82687-107">Attributes</span></span>  
  
|<span data-ttu-id="82687-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="82687-108">Attribute</span></span>|<span data-ttu-id="82687-109">Description</span><span class="sxs-lookup"><span data-stu-id="82687-109">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="82687-110">Répertoire dans lequel les applications enregistrent des messages électroniques en vue d’un traitement ultérieur par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="82687-110">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82687-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="82687-111">Child Elements</span></span>  
 <span data-ttu-id="82687-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="82687-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82687-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="82687-113">Parent Elements</span></span>  
  
|<span data-ttu-id="82687-114">Élément</span><span class="sxs-lookup"><span data-stu-id="82687-114">Element</span></span>|<span data-ttu-id="82687-115">Description</span><span class="sxs-lookup"><span data-stu-id="82687-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82687-116">\<smtp>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="82687-116">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="82687-117">Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="82687-117">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82687-118">Notes</span><span class="sxs-lookup"><span data-stu-id="82687-118">Remarks</span></span>  
 <span data-ttu-id="82687-119">L' `specifiedPickupDirectory` attribut définit le répertoire dans lequel les applications enregistrent les messages électroniques à traiter par le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="82687-119">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82687-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="82687-120">Example</span></span>  
 <span data-ttu-id="82687-121">L’exemple suivant spécifie c:\maildrop comme répertoire de collecte des messages.</span><span class="sxs-lookup"><span data-stu-id="82687-121">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82687-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82687-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="82687-123">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="82687-123">Network Settings Schema</span></span>](index.md)
