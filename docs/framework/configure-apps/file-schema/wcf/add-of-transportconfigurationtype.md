---
title: <add> de <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850309"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="d9ea3-102">\<add> de \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="d9ea3-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="d9ea3-103">Cet élément est une paire clé/valeur, qui identifie le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="d9ea3-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="d9ea3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9ea3-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9ea3-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d9ea3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d9ea3-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d9ea3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9ea3-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="d9ea3-107">Attributes</span></span>  
  
|<span data-ttu-id="d9ea3-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="d9ea3-108">Attribute</span></span>|<span data-ttu-id="d9ea3-109">Description</span><span class="sxs-lookup"><span data-stu-id="d9ea3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9ea3-110">name</span><span class="sxs-lookup"><span data-stu-id="d9ea3-110">name</span></span>|<span data-ttu-id="d9ea3-111">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="d9ea3-111">Required String attribute.</span></span><br /><br /> <span data-ttu-id="d9ea3-112">Contient une clé définie par l'utilisateur qui identifie uniquement le type de transport.</span><span class="sxs-lookup"><span data-stu-id="d9ea3-112">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="d9ea3-113">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="d9ea3-113">transportConfigurationType</span></span>|<span data-ttu-id="d9ea3-114">Chaîne contenant le type qui implémente le transport spécifique.</span><span class="sxs-lookup"><span data-stu-id="d9ea3-114">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9ea3-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d9ea3-115">Child Elements</span></span>  
 <span data-ttu-id="d9ea3-116">Aucune</span><span class="sxs-lookup"><span data-stu-id="d9ea3-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9ea3-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d9ea3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d9ea3-118">Élément</span><span class="sxs-lookup"><span data-stu-id="d9ea3-118">Element</span></span>|<span data-ttu-id="d9ea3-119">Description</span><span class="sxs-lookup"><span data-stu-id="d9ea3-119">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="d9ea3-120">Collection de types implémentant le transport spécifique.</span><span class="sxs-lookup"><span data-stu-id="d9ea3-120">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d9ea3-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9ea3-121">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="d9ea3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9ea3-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="d9ea3-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="d9ea3-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
