---
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 4be08f780c1095b0016bd130b5719a2a7307d019
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854926"
---
# <a name="transportconfigurationtypes"></a><span data-ttu-id="7aee3-101">\<transportConfigurationTypes></span><span class="sxs-lookup"><span data-stu-id="7aee3-101">\<transportConfigurationTypes></span></span>
<span data-ttu-id="7aee3-102">Représente une collection d’éléments de configuration identifiant le type d’un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="7aee3-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="7aee3-103">Peut être utilisé pour ajouter des protocoles WAS personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7aee3-103">This can be used to add custom WAS protocols.</span></span>  
  
<span data-ttu-id="7aee3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7aee3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7aee3-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7aee3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7aee3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceHostingEnvironment >** ](servicehostingenvironment.md)</span><span class="sxs-lookup"><span data-stu-id="7aee3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)</span></span>\
<span data-ttu-id="7aee3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transportConfigurationTypes >**</span><span class="sxs-lookup"><span data-stu-id="7aee3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aee3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7aee3-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7aee3-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7aee3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7aee3-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7aee3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7aee3-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="7aee3-111">Attributes</span></span>  
  
|<span data-ttu-id="7aee3-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="7aee3-112">Attribute</span></span>|<span data-ttu-id="7aee3-113">Description</span><span class="sxs-lookup"><span data-stu-id="7aee3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7aee3-114">name</span><span class="sxs-lookup"><span data-stu-id="7aee3-114">name</span></span>|<span data-ttu-id="7aee3-115">Nom du transport.</span><span class="sxs-lookup"><span data-stu-id="7aee3-115">The name of the transport</span></span>|  
|<span data-ttu-id="7aee3-116">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="7aee3-116">transportConfigurationType</span></span>|<span data-ttu-id="7aee3-117">Type qui implémente le transport.</span><span class="sxs-lookup"><span data-stu-id="7aee3-117">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7aee3-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7aee3-118">Child Elements</span></span>  
  
|<span data-ttu-id="7aee3-119">Élément</span><span class="sxs-lookup"><span data-stu-id="7aee3-119">Element</span></span>|<span data-ttu-id="7aee3-120">Description</span><span class="sxs-lookup"><span data-stu-id="7aee3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7aee3-121">\<add></span><span class="sxs-lookup"><span data-stu-id="7aee3-121">\<add></span></span>](add-of-transportconfigurationtype.md)|<span data-ttu-id="7aee3-122">Ajoute un élément de configuration identifiant le type d'un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="7aee3-122">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7aee3-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7aee3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7aee3-124">Élément</span><span class="sxs-lookup"><span data-stu-id="7aee3-124">Element</span></span>|<span data-ttu-id="7aee3-125">Description</span><span class="sxs-lookup"><span data-stu-id="7aee3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7aee3-126">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="7aee3-126">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="7aee3-127">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="7aee3-127">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7aee3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aee3-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="7aee3-129">Hébergement</span><span class="sxs-lookup"><span data-stu-id="7aee3-129">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
