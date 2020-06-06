---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854962"
---
# \<timeOuts>
<span data-ttu-id="e494a-101">Représente un élément de configuration qui spécifie l'intervalle de temps pendant lequel l'ouverture ou la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="e494a-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="e494a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e494a-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e494a-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e494a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e494a-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e494a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e494a-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="e494a-105">Attributes</span></span>  
  
|<span data-ttu-id="e494a-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="e494a-106">Attribute</span></span>|<span data-ttu-id="e494a-107">Description</span><span class="sxs-lookup"><span data-stu-id="e494a-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e494a-108">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="e494a-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="e494a-109">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel l'ouverture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="e494a-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e494a-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e494a-110">Child Elements</span></span>  
 <span data-ttu-id="e494a-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e494a-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e494a-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e494a-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e494a-113">Élément</span><span class="sxs-lookup"><span data-stu-id="e494a-113">Element</span></span>|<span data-ttu-id="e494a-114">Description</span><span class="sxs-lookup"><span data-stu-id="e494a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="e494a-115">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="e494a-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e494a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e494a-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="e494a-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="e494a-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
