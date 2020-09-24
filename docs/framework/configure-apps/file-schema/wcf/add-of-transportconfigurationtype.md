---
title: <add> de <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 9bef44ed39ee892080342058206f779b38fb460d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151153"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="14820-102">\<add> de \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="14820-102">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="14820-103">Cet élément est une paire clé/valeur, qui identifie le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="14820-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="14820-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14820-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14820-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="14820-105">Attributes and Elements</span></span>  

 <span data-ttu-id="14820-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="14820-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14820-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="14820-107">Attributes</span></span>  
  
|<span data-ttu-id="14820-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="14820-108">Attribute</span></span>|<span data-ttu-id="14820-109">Description</span><span class="sxs-lookup"><span data-stu-id="14820-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14820-110">name</span><span class="sxs-lookup"><span data-stu-id="14820-110">name</span></span>|<span data-ttu-id="14820-111">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="14820-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="14820-112">Contient une clé définie par l'utilisateur qui identifie uniquement le type de transport.</span><span class="sxs-lookup"><span data-stu-id="14820-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="14820-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="14820-113">transportConfigurationType</span></span>|<span data-ttu-id="14820-114">Chaîne contenant le type qui implémente le transport spécifique.</span><span class="sxs-lookup"><span data-stu-id="14820-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14820-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="14820-115">Child Elements</span></span>  

 <span data-ttu-id="14820-116">None</span><span class="sxs-lookup"><span data-stu-id="14820-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14820-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="14820-117">Parent Elements</span></span>  
  
|<span data-ttu-id="14820-118">Élément</span><span class="sxs-lookup"><span data-stu-id="14820-118">Element</span></span>|<span data-ttu-id="14820-119">Description</span><span class="sxs-lookup"><span data-stu-id="14820-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="14820-120">Collection de types implémentant le transport spécifique.</span><span class="sxs-lookup"><span data-stu-id="14820-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="14820-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="14820-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="14820-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14820-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="14820-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="14820-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
