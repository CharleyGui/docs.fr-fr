---
title: <add> de <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 80726cc22cb56013c85c7704c28579b1337666c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850543"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="db622-102">\<add> de \<backupList></span><span class="sxs-lookup"><span data-stu-id="db622-102">\<add> of \<backupList></span></span>
<span data-ttu-id="db622-103">Représente un élément de configuration qui définit un élément de point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="db622-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="db622-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db622-104">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db622-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="db622-105">Attributes and Elements</span></span>  
 <span data-ttu-id="db622-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="db622-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db622-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="db622-107">Attributes</span></span>  
  
|<span data-ttu-id="db622-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="db622-108">Attribute</span></span>|<span data-ttu-id="db622-109">Description</span><span class="sxs-lookup"><span data-stu-id="db622-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db622-110">name</span><span class="sxs-lookup"><span data-stu-id="db622-110">name</span></span>|<span data-ttu-id="db622-111">Chaîne qui spécifie le nom du point de terminaison de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="db622-111">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db622-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="db622-112">Child Elements</span></span>  
 <span data-ttu-id="db622-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="db622-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db622-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="db622-114">Parent Elements</span></span>  
  
|<span data-ttu-id="db622-115">Élément</span><span class="sxs-lookup"><span data-stu-id="db622-115">Element</span></span>|<span data-ttu-id="db622-116">Description</span><span class="sxs-lookup"><span data-stu-id="db622-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="db622-117">Contient une liste de points de terminaison à utiliser par le service de routage au cas où il est impossible d'atteindre le point de terminaison primaire.</span><span class="sxs-lookup"><span data-stu-id="db622-117">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="db622-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db622-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
