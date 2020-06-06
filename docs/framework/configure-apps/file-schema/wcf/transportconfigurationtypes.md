---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854926"
---
# \<transportConfigurationTypes>
<span data-ttu-id="4abef-101">Représente une collection d’éléments de configuration identifiant le type d’un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="4abef-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="4abef-102">Peut être utilisé pour ajouter des protocoles WAS personnalisés.</span><span class="sxs-lookup"><span data-stu-id="4abef-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="4abef-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4abef-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4abef-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4abef-104">Attributes and Elements</span></span>  
 <span data-ttu-id="4abef-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4abef-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4abef-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="4abef-106">Attributes</span></span>  
  
|<span data-ttu-id="4abef-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="4abef-107">Attribute</span></span>|<span data-ttu-id="4abef-108">Description</span><span class="sxs-lookup"><span data-stu-id="4abef-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4abef-109">name</span><span class="sxs-lookup"><span data-stu-id="4abef-109">name</span></span>|<span data-ttu-id="4abef-110">Nom du transport.</span><span class="sxs-lookup"><span data-stu-id="4abef-110">The name of the transport</span></span>|  
|<span data-ttu-id="4abef-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="4abef-111">transportConfigurationType</span></span>|<span data-ttu-id="4abef-112">Type qui implémente le transport.</span><span class="sxs-lookup"><span data-stu-id="4abef-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4abef-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4abef-113">Child Elements</span></span>  
  
|<span data-ttu-id="4abef-114">Élément</span><span class="sxs-lookup"><span data-stu-id="4abef-114">Element</span></span>|<span data-ttu-id="4abef-115">Description</span><span class="sxs-lookup"><span data-stu-id="4abef-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="4abef-116">Ajoute un élément de configuration identifiant le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="4abef-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4abef-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4abef-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4abef-118">Élément</span><span class="sxs-lookup"><span data-stu-id="4abef-118">Element</span></span>|<span data-ttu-id="4abef-119">Description</span><span class="sxs-lookup"><span data-stu-id="4abef-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="4abef-120">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="4abef-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4abef-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4abef-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="4abef-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="4abef-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
