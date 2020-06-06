---
title: <customTrackingQueries>de WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855432"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="1cbd0-102">\<customTrackingQueries>de WCF</span><span class="sxs-lookup"><span data-stu-id="1cbd0-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="1cbd0-103">Représente une collection de requêtes permettant d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="1cbd0-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="1cbd0-104">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des enregistrements de suivi personnalisés.</span><span class="sxs-lookup"><span data-stu-id="1cbd0-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="1cbd0-105">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1cbd0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="1cbd0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cbd0-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cbd0-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1cbd0-107">Attributes and elements</span></span>

<span data-ttu-id="1cbd0-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1cbd0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cbd0-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1cbd0-109">Attributes</span></span>

<span data-ttu-id="1cbd0-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1cbd0-110">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="1cbd0-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1cbd0-111">Child elements</span></span>
  
|<span data-ttu-id="1cbd0-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1cbd0-112">Element</span></span>|<span data-ttu-id="1cbd0-113">Description</span><span class="sxs-lookup"><span data-stu-id="1cbd0-113">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="1cbd0-114">Requête qui permet d'effectuer le suivi des événements que vous définissez dans vos activités de code.</span><span class="sxs-lookup"><span data-stu-id="1cbd0-114">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1cbd0-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1cbd0-115">Parent elements</span></span>  
  
|<span data-ttu-id="1cbd0-116">Élément</span><span class="sxs-lookup"><span data-stu-id="1cbd0-116">Element</span></span>|<span data-ttu-id="1cbd0-117">Description</span><span class="sxs-lookup"><span data-stu-id="1cbd0-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="1cbd0-118">Élément de configuration qui contient toutes les requêtes d'un flux de travail spécifique identifié par la propriété `activityDefinitionId`.</span><span class="sxs-lookup"><span data-stu-id="1cbd0-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cbd0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cbd0-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1cbd0-120">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="1cbd0-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1cbd0-121">Profils de suivi</span><span class="sxs-lookup"><span data-stu-id="1cbd0-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
