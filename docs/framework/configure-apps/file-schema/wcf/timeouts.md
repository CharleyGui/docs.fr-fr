---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854962"
---
# <a name="timeouts"></a><span data-ttu-id="912c7-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="912c7-101">\<timeOuts></span></span>
<span data-ttu-id="912c7-102">Représente un élément de configuration qui spécifie l'intervalle de temps pendant lequel l'ouverture ou la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="912c7-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
<span data-ttu-id="912c7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="912c7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="912c7-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="912c7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="912c7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<services >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="912c7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="912c7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de service**](service.md)</span><span class="sxs-lookup"><span data-stu-id="912c7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="912c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> d’hôte**](host.md)</span><span class="sxs-lookup"><span data-stu-id="912c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="912c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Délais d’expiration >**</span><span class="sxs-lookup"><span data-stu-id="912c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912c7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="912c7-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="912c7-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="912c7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="912c7-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="912c7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="912c7-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="912c7-112">Attributes</span></span>  
  
|<span data-ttu-id="912c7-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="912c7-113">Attribute</span></span>|<span data-ttu-id="912c7-114">Description</span><span class="sxs-lookup"><span data-stu-id="912c7-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="912c7-115">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="912c7-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="912c7-116">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel l'ouverture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="912c7-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="912c7-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="912c7-117">Child Elements</span></span>  
 <span data-ttu-id="912c7-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="912c7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="912c7-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="912c7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="912c7-120">Élément</span><span class="sxs-lookup"><span data-stu-id="912c7-120">Element</span></span>|<span data-ttu-id="912c7-121">Description</span><span class="sxs-lookup"><span data-stu-id="912c7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="912c7-122">\<host></span><span class="sxs-lookup"><span data-stu-id="912c7-122">\<host></span></span>](host.md)|<span data-ttu-id="912c7-123">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="912c7-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="912c7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="912c7-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="912c7-125">Hébergement</span><span class="sxs-lookup"><span data-stu-id="912c7-125">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
