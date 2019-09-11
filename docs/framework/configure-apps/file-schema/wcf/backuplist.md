---
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 478211755b9131c03b72777ee95ff7223b9092c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850275"
---
# <a name="backuplist"></a><span data-ttu-id="bd916-101">\<backupList></span><span class="sxs-lookup"><span data-stu-id="bd916-101">\<backupList></span></span>
<span data-ttu-id="bd916-102">Représente une section de configuration pour la définition d’une liste de sauvegarde qui énumère un ensemble de points de terminaison que vous souhaitez que le service de routage utilise si le point de terminaison principal est inaccessible.</span><span class="sxs-lookup"><span data-stu-id="bd916-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="bd916-103">Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste.</span><span class="sxs-lookup"><span data-stu-id="bd916-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="bd916-104">Vous disposez ainsi d’une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l’emplacement de tous vos services déployés.</span><span class="sxs-lookup"><span data-stu-id="bd916-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="bd916-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd916-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd916-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bd916-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bd916-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="bd916-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="bd916-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="bd916-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="bd916-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupList >**</span><span class="sxs-lookup"><span data-stu-id="bd916-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd916-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd916-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd916-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bd916-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bd916-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bd916-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd916-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="bd916-113">Attributes</span></span>  
  
|<span data-ttu-id="bd916-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="bd916-114">Attribute</span></span>|<span data-ttu-id="bd916-115">Description</span><span class="sxs-lookup"><span data-stu-id="bd916-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd916-116">name</span><span class="sxs-lookup"><span data-stu-id="bd916-116">name</span></span>|<span data-ttu-id="bd916-117">Chaîne qui spécifie le nom permettant d'identifier la liste de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="bd916-117">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd916-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bd916-118">Child Elements</span></span>  
  
|<span data-ttu-id="bd916-119">Élément</span><span class="sxs-lookup"><span data-stu-id="bd916-119">Element</span></span>|<span data-ttu-id="bd916-120">Description</span><span class="sxs-lookup"><span data-stu-id="bd916-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd916-121">\<filter></span><span class="sxs-lookup"><span data-stu-id="bd916-121">\<filter></span></span>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="bd916-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bd916-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bd916-123">Élément</span><span class="sxs-lookup"><span data-stu-id="bd916-123">Element</span></span>|<span data-ttu-id="bd916-124">Description</span><span class="sxs-lookup"><span data-stu-id="bd916-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd916-125">\<routing></span><span class="sxs-lookup"><span data-stu-id="bd916-125">\<routing></span></span>](routing.md)|<span data-ttu-id="bd916-126">Liste de points de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="bd916-126">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd916-127">Notes</span><span class="sxs-lookup"><span data-stu-id="bd916-127">Remarks</span></span>  
 <span data-ttu-id="bd916-128">Cette section contient une collection ordonnée de points de terminaison auxquels un message sera transmis si une exception de communication se produit lors de l'envoi au point de terminaison primaire.</span><span class="sxs-lookup"><span data-stu-id="bd916-128">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="bd916-129">Si un envoi au point de terminaison principal listé dans `endpointName` l’attribut de [ \<Add >](add-of-entries.md) échoue avec une exception de communication, le service de routage tente d’envoyer le message au premier point de terminaison de cette section de configuration.</span><span class="sxs-lookup"><span data-stu-id="bd916-129">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="bd916-130">Si l’opération échoue également avec une exception de communication, le service de routage essaie d’envoyer le message au point de terminaison suivant contenu dans cette section jusqu’à ce que la tentative d’envoi aboutisse, retourne une erreur autre qu’une exception de communication, ou que tous les points de terminaison de la collection retournent une erreur.</span><span class="sxs-lookup"><span data-stu-id="bd916-130">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="bd916-131">Dans l’exemple suivant, si un envoi au point de terminaison principal nommé « destination » retourne une exception de communication, le service tente d’envoyer le message à « alternateServiceQueue ».</span><span class="sxs-lookup"><span data-stu-id="bd916-131">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="bd916-132">Si cette tentative retourne également une exception de communication, le service de routage essaiera d’envoyer le message au point de terminaison suivant dans la collection.</span><span class="sxs-lookup"><span data-stu-id="bd916-132">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="bd916-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd916-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
