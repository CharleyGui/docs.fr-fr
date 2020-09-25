---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 940bf28958251e7257b2cc19a9c5ff0059411bcd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201549"
---
# \<backupLists>

<span data-ttu-id="f37dd-101">Représente une section de configuration pour la définition d'un ensemble de services de sauvegarde utilisés dans la gestion des erreurs.</span><span class="sxs-lookup"><span data-stu-id="f37dd-101">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="f37dd-102">Chaque élément enfant est une liste de sauvegarde qui énumère un ensemble de points de terminaison à utiliser par le service de routage s'il est impossible d'atteindre le point de terminaison primaire.</span><span class="sxs-lookup"><span data-stu-id="f37dd-102">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="f37dd-103">Si le premier point de terminaison de la liste est inactif, le service de routage bascule automatiquement sur le suivant dans la liste.</span><span class="sxs-lookup"><span data-stu-id="f37dd-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="f37dd-104">Vous disposez ainsi d’une méthode rapide pour renforcer la fiabilité de votre application sans avoir à apprendre à votre application cliente à gérer des modèles complexes ou à rechercher l’emplacement de tous vos services déployés.</span><span class="sxs-lookup"><span data-stu-id="f37dd-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="f37dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f37dd-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f37dd-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f37dd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f37dd-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f37dd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f37dd-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="f37dd-108">Attributes</span></span>  

 <span data-ttu-id="f37dd-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f37dd-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f37dd-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f37dd-110">Child Elements</span></span>  
  
|<span data-ttu-id="f37dd-111">Élément</span><span class="sxs-lookup"><span data-stu-id="f37dd-111">Element</span></span>|<span data-ttu-id="f37dd-112">Description</span><span class="sxs-lookup"><span data-stu-id="f37dd-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="f37dd-113">Contient une liste de points de terminaison à utiliser par le service de routage au cas où il est impossible d'atteindre le point de terminaison primaire.</span><span class="sxs-lookup"><span data-stu-id="f37dd-113">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="f37dd-114">.</span><span class="sxs-lookup"><span data-stu-id="f37dd-114">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f37dd-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f37dd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f37dd-116">Élément</span><span class="sxs-lookup"><span data-stu-id="f37dd-116">Element</span></span>|<span data-ttu-id="f37dd-117">Description</span><span class="sxs-lookup"><span data-stu-id="f37dd-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="f37dd-118">Représente une section de configuration permettant de définir un jeu de filtres de routage, qui détermine le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="f37dd-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f37dd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f37dd-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
