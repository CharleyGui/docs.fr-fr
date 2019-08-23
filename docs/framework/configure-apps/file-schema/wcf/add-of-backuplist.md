---
title: <add> de <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: c590dbd671807b32e08ad5d871d376a0dc51e611
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926875"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="7afd3-102">\<Ajouter > de \<la > backupList</span><span class="sxs-lookup"><span data-stu-id="7afd3-102">\<add> of \<backupList></span></span>
<span data-ttu-id="7afd3-103">Représente un élément de configuration qui définit un élément de point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="7afd3-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="7afd3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7afd3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7afd3-105">\<routing></span><span class="sxs-lookup"><span data-stu-id="7afd3-105">\<routing></span></span>  
<span data-ttu-id="7afd3-106">\<backupLists></span><span class="sxs-lookup"><span data-stu-id="7afd3-106">\<backupLists></span></span>  
<span data-ttu-id="7afd3-107">\<backupList></span><span class="sxs-lookup"><span data-stu-id="7afd3-107">\<backupList></span></span>  
<span data-ttu-id="7afd3-108">\<add></span><span class="sxs-lookup"><span data-stu-id="7afd3-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7afd3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7afd3-109">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7afd3-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7afd3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7afd3-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7afd3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7afd3-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="7afd3-112">Attributes</span></span>  
  
|<span data-ttu-id="7afd3-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="7afd3-113">Attribute</span></span>|<span data-ttu-id="7afd3-114">Description</span><span class="sxs-lookup"><span data-stu-id="7afd3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7afd3-115">name</span><span class="sxs-lookup"><span data-stu-id="7afd3-115">name</span></span>|<span data-ttu-id="7afd3-116">Chaîne qui spécifie le nom du point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="7afd3-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7afd3-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7afd3-117">Child Elements</span></span>  
 <span data-ttu-id="7afd3-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7afd3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7afd3-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7afd3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7afd3-120">Élément</span><span class="sxs-lookup"><span data-stu-id="7afd3-120">Element</span></span>|<span data-ttu-id="7afd3-121">Description</span><span class="sxs-lookup"><span data-stu-id="7afd3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7afd3-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="7afd3-122">\<routing></span></span>](routing.md)|<span data-ttu-id="7afd3-123">Contient une liste de points de terminaison que vous souhaitez que le service de routage utilise si le point de terminaison principal n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="7afd3-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7afd3-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7afd3-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
