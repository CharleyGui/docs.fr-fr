---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: bfd2147a8e772848fc98cab7a875a51bdb53b5cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941156"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="c298e-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="c298e-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="c298e-102">Représente une collection d’éléments de configuration identifiant le type d’un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="c298e-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="c298e-103">Peut être utilisé pour ajouter des protocoles WAS personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c298e-103">This can be used to add custom WAS protocols.</span></span>  
  
 <span data-ttu-id="c298e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c298e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c298e-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="c298e-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="c298e-106">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="c298e-106">\<transportConfigurationTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c298e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c298e-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c298e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c298e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c298e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c298e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c298e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="c298e-110">Attributes</span></span>  
  
|<span data-ttu-id="c298e-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="c298e-111">Attribute</span></span>|<span data-ttu-id="c298e-112">Description</span><span class="sxs-lookup"><span data-stu-id="c298e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c298e-113">name</span><span class="sxs-lookup"><span data-stu-id="c298e-113">name</span></span>|<span data-ttu-id="c298e-114">Nom du transport.</span><span class="sxs-lookup"><span data-stu-id="c298e-114">The name of the transport</span></span>|  
|<span data-ttu-id="c298e-115">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="c298e-115">transportConfigurationType</span></span>|<span data-ttu-id="c298e-116">Type qui implémente le transport.</span><span class="sxs-lookup"><span data-stu-id="c298e-116">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c298e-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c298e-117">Child Elements</span></span>  
  
|<span data-ttu-id="c298e-118">Élément</span><span class="sxs-lookup"><span data-stu-id="c298e-118">Element</span></span>|<span data-ttu-id="c298e-119">Description</span><span class="sxs-lookup"><span data-stu-id="c298e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c298e-120">\<add></span><span class="sxs-lookup"><span data-stu-id="c298e-120">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="c298e-121">Ajoute un élément de configuration identifiant le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="c298e-121">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c298e-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c298e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c298e-123">Élément</span><span class="sxs-lookup"><span data-stu-id="c298e-123">Element</span></span>|<span data-ttu-id="c298e-124">Description</span><span class="sxs-lookup"><span data-stu-id="c298e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c298e-125">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="c298e-125">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="c298e-126">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="c298e-126">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c298e-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c298e-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="c298e-128">Hébergement</span><span class="sxs-lookup"><span data-stu-id="c298e-128">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
