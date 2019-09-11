---
title: <add> de <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: adf4cd7f02db6535c5950443d09476a9a5ff63fb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850309"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="a2a44-102">\<Ajouter > de \<la > transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="a2a44-102">\<add> of \<transportConfigurationType></span></span>
<span data-ttu-id="a2a44-103">Cet élément est une paire clé/valeur, qui identifie le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="a2a44-103">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
<span data-ttu-id="a2a44-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a2a44-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a2a44-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a2a44-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a2a44-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="a2a44-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="a2a44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<transportConfigurationTypes >** ](transportconfigurationtypes.md)</span><span class="sxs-lookup"><span data-stu-id="a2a44-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)</span></span>\
<span data-ttu-id="a2a44-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="a2a44-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a44-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2a44-109">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2a44-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a2a44-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a2a44-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a2a44-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2a44-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a2a44-112">Attributes</span></span>  
  
|<span data-ttu-id="a2a44-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="a2a44-113">Attribute</span></span>|<span data-ttu-id="a2a44-114">Description</span><span class="sxs-lookup"><span data-stu-id="a2a44-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2a44-115">name</span><span class="sxs-lookup"><span data-stu-id="a2a44-115">name</span></span>|<span data-ttu-id="a2a44-116">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="a2a44-116">Required String attribute.</span></span><br /><br /> <span data-ttu-id="a2a44-117">Contient une clé définie par l'utilisateur qui identifie uniquement le type de transport.</span><span class="sxs-lookup"><span data-stu-id="a2a44-117">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="a2a44-118">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="a2a44-118">transportConfigurationType</span></span>|<span data-ttu-id="a2a44-119">Chaîne contenant le type qui implémente le transport spécifique.</span><span class="sxs-lookup"><span data-stu-id="a2a44-119">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2a44-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a2a44-120">Child Elements</span></span>  
 <span data-ttu-id="a2a44-121">Aucun</span><span class="sxs-lookup"><span data-stu-id="a2a44-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2a44-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a2a44-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a2a44-123">Élément</span><span class="sxs-lookup"><span data-stu-id="a2a44-123">Element</span></span>|<span data-ttu-id="a2a44-124">Description</span><span class="sxs-lookup"><span data-stu-id="a2a44-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2a44-125">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="a2a44-125">\<transportConfigurationTypes></span></span>](transportconfigurationtypes.md)|<span data-ttu-id="a2a44-126">Collection de types implémentant le transport spécifique.</span><span class="sxs-lookup"><span data-stu-id="a2a44-126">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a2a44-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="a2a44-127">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="a2a44-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2a44-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="a2a44-129">Hébergement</span><span class="sxs-lookup"><span data-stu-id="a2a44-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
