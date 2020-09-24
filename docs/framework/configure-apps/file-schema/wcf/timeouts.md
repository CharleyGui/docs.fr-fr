---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: f7e513bb5c486fa5f7c39c9b2e3cfcd26bd7c219
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157094"
---
# \<timeOuts>

<span data-ttu-id="89687-101">Représente un élément de configuration qui spécifie l'intervalle de temps pendant lequel l'ouverture ou la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="89687-101">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="89687-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89687-102">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89687-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="89687-103">Attributes and Elements</span></span>  

 <span data-ttu-id="89687-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="89687-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89687-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="89687-105">Attributes</span></span>  
  
|<span data-ttu-id="89687-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="89687-106">Attribute</span></span>|<span data-ttu-id="89687-107">Description</span><span class="sxs-lookup"><span data-stu-id="89687-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="89687-108">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel la fermeture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="89687-108">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="89687-109">Valeur de type <xref:System.TimeSpan> qui spécifie l'intervalle de temps pendant lequel l'ouverture de l'hôte de service est autorisée.</span><span class="sxs-lookup"><span data-stu-id="89687-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89687-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="89687-110">Child Elements</span></span>  

 <span data-ttu-id="89687-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="89687-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89687-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="89687-112">Parent Elements</span></span>  
  
|<span data-ttu-id="89687-113">Élément</span><span class="sxs-lookup"><span data-stu-id="89687-113">Element</span></span>|<span data-ttu-id="89687-114">Description</span><span class="sxs-lookup"><span data-stu-id="89687-114">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="89687-115">Élément de configuration qui spécifie des paramètres pour un hôte de service.</span><span class="sxs-lookup"><span data-stu-id="89687-115">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="89687-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89687-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="89687-117">Hosting</span><span class="sxs-lookup"><span data-stu-id="89687-117">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
