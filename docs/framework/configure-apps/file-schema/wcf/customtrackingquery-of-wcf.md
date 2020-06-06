---
title: <customTrackingQuery>de WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855422"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="29f28-102">\<customTrackingQuery>de WCF</span><span class="sxs-lookup"><span data-stu-id="29f28-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="29f28-103">Représente une requête utilisée pour suivre les événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="29f28-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="29f28-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="29f28-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="29f28-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez modèles de [suivi](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="29f28-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="29f28-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f28-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29f28-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="29f28-107">Attributes and elements</span></span>  

<span data-ttu-id="29f28-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="29f28-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29f28-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="29f28-109">Attributes</span></span>  
  
|<span data-ttu-id="29f28-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="29f28-110">Attribute</span></span>|<span data-ttu-id="29f28-111">Description</span><span class="sxs-lookup"><span data-stu-id="29f28-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="29f28-112">Chaîne qui spécifie le nom de l'activité ayant généré l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="29f28-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="29f28-113">Chaîne qui spécifie le nom de l'enregistrement de suivi personnalisé émis.</span><span class="sxs-lookup"><span data-stu-id="29f28-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29f28-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="29f28-114">Child elements</span></span>

<span data-ttu-id="29f28-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="29f28-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29f28-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="29f28-116">Parent elements</span></span>

|<span data-ttu-id="29f28-117">Élément</span><span class="sxs-lookup"><span data-stu-id="29f28-117">Element</span></span>|<span data-ttu-id="29f28-118">Description</span><span class="sxs-lookup"><span data-stu-id="29f28-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="29f28-119">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="29f28-119">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="29f28-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29f28-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="29f28-121">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="29f28-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="29f28-122">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="29f28-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
