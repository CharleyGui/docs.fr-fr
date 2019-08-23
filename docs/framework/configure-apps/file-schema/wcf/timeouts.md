---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b159488efa2a80a9dea625e4c6dfe2f215dfc457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939188"
---
# <a name="timeouts"></a><span data-ttu-id="410d7-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="410d7-101">\<timeOuts></span></span>
<span data-ttu-id="410d7-102">Représente un élément de configuration qui spécifie l'intervalle de temps pendant lequel l'ouverture ou la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="410d7-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="410d7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="410d7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="410d7-104">\<client></span><span class="sxs-lookup"><span data-stu-id="410d7-104">\<client></span></span>  
<span data-ttu-id="410d7-105">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="410d7-105">\<endpoint></span></span>  
<span data-ttu-id="410d7-106">\<host></span><span class="sxs-lookup"><span data-stu-id="410d7-106">\<host></span></span>  
<span data-ttu-id="410d7-107">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="410d7-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410d7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="410d7-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="410d7-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="410d7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="410d7-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="410d7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="410d7-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="410d7-111">Attributes</span></span>  
  
|<span data-ttu-id="410d7-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="410d7-112">Attribute</span></span>|<span data-ttu-id="410d7-113">Description</span><span class="sxs-lookup"><span data-stu-id="410d7-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="410d7-114">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="410d7-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="410d7-115">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel l'ouverture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="410d7-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="410d7-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="410d7-116">Child Elements</span></span>  
 <span data-ttu-id="410d7-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="410d7-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="410d7-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="410d7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="410d7-119">Élément</span><span class="sxs-lookup"><span data-stu-id="410d7-119">Element</span></span>|<span data-ttu-id="410d7-120">Description</span><span class="sxs-lookup"><span data-stu-id="410d7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="410d7-121">\<host></span><span class="sxs-lookup"><span data-stu-id="410d7-121">\<host></span></span>](host.md)|<span data-ttu-id="410d7-122">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="410d7-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="410d7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="410d7-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="410d7-124">Hébergement</span><span class="sxs-lookup"><span data-stu-id="410d7-124">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
