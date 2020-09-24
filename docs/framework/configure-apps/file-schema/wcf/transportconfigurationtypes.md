---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 6545e1f1be2695d165b89a38c7218e0acdc88bfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162021"
---
# \<transportConfigurationTypes>

<span data-ttu-id="fd28e-101">Représente une collection d’éléments de configuration identifiant le type d’un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="fd28e-101">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="fd28e-102">Peut être utilisé pour ajouter des protocoles WAS personnalisés.</span><span class="sxs-lookup"><span data-stu-id="fd28e-102">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="fd28e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd28e-103">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd28e-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd28e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fd28e-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fd28e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd28e-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd28e-106">Attributes</span></span>  
  
|<span data-ttu-id="fd28e-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="fd28e-107">Attribute</span></span>|<span data-ttu-id="fd28e-108">Description</span><span class="sxs-lookup"><span data-stu-id="fd28e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd28e-109">name</span><span class="sxs-lookup"><span data-stu-id="fd28e-109">name</span></span>|<span data-ttu-id="fd28e-110">Nom du transport.</span><span class="sxs-lookup"><span data-stu-id="fd28e-110">The name of the transport</span></span>|  
|<span data-ttu-id="fd28e-111">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="fd28e-111">transportConfigurationType</span></span>|<span data-ttu-id="fd28e-112">Type qui implémente le transport.</span><span class="sxs-lookup"><span data-stu-id="fd28e-112">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd28e-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd28e-113">Child Elements</span></span>  
  
|<span data-ttu-id="fd28e-114">Élément</span><span class="sxs-lookup"><span data-stu-id="fd28e-114">Element</span></span>|<span data-ttu-id="fd28e-115">Description</span><span class="sxs-lookup"><span data-stu-id="fd28e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="fd28e-116">Ajoute un élément de configuration identifiant le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="fd28e-116">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd28e-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd28e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fd28e-118">Élément</span><span class="sxs-lookup"><span data-stu-id="fd28e-118">Element</span></span>|<span data-ttu-id="fd28e-119">Description</span><span class="sxs-lookup"><span data-stu-id="fd28e-119">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="fd28e-120">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="fd28e-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd28e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd28e-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="fd28e-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="fd28e-122">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
