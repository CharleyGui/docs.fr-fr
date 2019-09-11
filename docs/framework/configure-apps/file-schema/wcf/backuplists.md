---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850259"
---
# <a name="backuplists"></a><span data-ttu-id="f97c7-101">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="f97c7-101">\<backupLists></span></span>
<span data-ttu-id="f97c7-102">Représente une section de configuration pour la définition d'un ensemble de services de sauvegarde utilisés dans la gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="f97c7-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="f97c7-103">Chaque élément enfant est une liste de sauvegarde qui énumère un ensemble de points de terminaison que vous souhaitez que le service de routage utilise si le point de terminaison principal est inaccessible.</span><span class="sxs-lookup"><span data-stu-id="f97c7-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="f97c7-104">Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste.</span><span class="sxs-lookup"><span data-stu-id="f97c7-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="f97c7-105">Vous disposez ainsi d’une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l’emplacement de tous vos services déployés.</span><span class="sxs-lookup"><span data-stu-id="f97c7-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
<span data-ttu-id="f97c7-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f97c7-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f97c7-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f97c7-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f97c7-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="f97c7-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="f97c7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<backupLists >**</span><span class="sxs-lookup"><span data-stu-id="f97c7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f97c7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f97c7-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f97c7-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f97c7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f97c7-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f97c7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f97c7-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="f97c7-113">Attributes</span></span>  
 <span data-ttu-id="f97c7-114">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f97c7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f97c7-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f97c7-115">Child Elements</span></span>  
  
|<span data-ttu-id="f97c7-116">Élément</span><span class="sxs-lookup"><span data-stu-id="f97c7-116">Element</span></span>|<span data-ttu-id="f97c7-117">Description</span><span class="sxs-lookup"><span data-stu-id="f97c7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f97c7-118">\<filter></span><span class="sxs-lookup"><span data-stu-id="f97c7-118">\<filter></span></span>](filter.md)|<span data-ttu-id="f97c7-119">Contient une liste de points de terminaison que vous souhaitez que le service de routage utilise si le point de terminaison principal n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="f97c7-119">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="f97c7-120">.</span><span class="sxs-lookup"><span data-stu-id="f97c7-120">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f97c7-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f97c7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f97c7-122">Élément</span><span class="sxs-lookup"><span data-stu-id="f97c7-122">Element</span></span>|<span data-ttu-id="f97c7-123">Description</span><span class="sxs-lookup"><span data-stu-id="f97c7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f97c7-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="f97c7-124">\<routing></span></span>](routing.md)|<span data-ttu-id="f97c7-125">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles Envoyer des messages à lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="f97c7-125">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f97c7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f97c7-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
