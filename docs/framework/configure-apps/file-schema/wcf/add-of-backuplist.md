---
title: <add> de <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850543"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="065b6-102">\<Ajouter > de \<la > backupList</span><span class="sxs-lookup"><span data-stu-id="065b6-102">\<add> of \<backupList></span></span>
<span data-ttu-id="065b6-103">Représente un élément de configuration qui définit un élément de point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="065b6-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
<span data-ttu-id="065b6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="065b6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="065b6-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="065b6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="065b6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de routage**](routing.md)</span><span class="sxs-lookup"><span data-stu-id="065b6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="065b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupLists >** ](backuplists.md)</span><span class="sxs-lookup"><span data-stu-id="065b6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)</span></span>\
<span data-ttu-id="065b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<backupList >** ](backuplist.md)</span><span class="sxs-lookup"><span data-stu-id="065b6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)</span></span>\
<span data-ttu-id="065b6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ajouter >**</span><span class="sxs-lookup"><span data-stu-id="065b6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="065b6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="065b6-110">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="065b6-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="065b6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="065b6-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="065b6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="065b6-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="065b6-113">Attributes</span></span>  
  
|<span data-ttu-id="065b6-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="065b6-114">Attribute</span></span>|<span data-ttu-id="065b6-115">Description</span><span class="sxs-lookup"><span data-stu-id="065b6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="065b6-116">name</span><span class="sxs-lookup"><span data-stu-id="065b6-116">name</span></span>|<span data-ttu-id="065b6-117">Chaîne qui spécifie le nom du point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="065b6-117">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="065b6-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="065b6-118">Child Elements</span></span>  
 <span data-ttu-id="065b6-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="065b6-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="065b6-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="065b6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="065b6-121">Élément</span><span class="sxs-lookup"><span data-stu-id="065b6-121">Element</span></span>|<span data-ttu-id="065b6-122">Description</span><span class="sxs-lookup"><span data-stu-id="065b6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="065b6-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="065b6-123">\<routing></span></span>](routing.md)|<span data-ttu-id="065b6-124">Contient une liste de points de terminaison que vous souhaitez que le service de routage utilise si le point de terminaison principal n’est pas accessible.</span><span class="sxs-lookup"><span data-stu-id="065b6-124">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="065b6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="065b6-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
