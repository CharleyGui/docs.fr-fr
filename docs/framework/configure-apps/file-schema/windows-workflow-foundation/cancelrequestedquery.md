---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: a50e9965a595fce64c383313091334e883dcfbfa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189485"
---
# \<cancelRequestedQuery>

<span data-ttu-id="88fbb-101">Représente une requête qui permet d'effectuer le suivi des demande d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="88fbb-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="88fbb-102">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="88fbb-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="88fbb-103">Pour plus d’informations sur le suivi des requêtes de profils, consultez [suivi des profils](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="88fbb-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="88fbb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88fbb-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88fbb-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="88fbb-105">Attributes and Elements</span></span>  

 <span data-ttu-id="88fbb-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="88fbb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88fbb-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="88fbb-107">Attributes</span></span>  
  
|<span data-ttu-id="88fbb-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="88fbb-108">Attribute</span></span>|<span data-ttu-id="88fbb-109">Description</span><span class="sxs-lookup"><span data-stu-id="88fbb-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88fbb-110">activityName</span><span class="sxs-lookup"><span data-stu-id="88fbb-110">activityName</span></span>|<span data-ttu-id="88fbb-111">Chaîne qui spécifie le nom de l'activité demandant l'annulation.</span><span class="sxs-lookup"><span data-stu-id="88fbb-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="88fbb-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="88fbb-112">childActivityName</span></span>|<span data-ttu-id="88fbb-113">Chaîne qui spécifie le nom de l'activité enfant pour laquelle l'annulation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="88fbb-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88fbb-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="88fbb-114">Child Elements</span></span>  

 <span data-ttu-id="88fbb-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="88fbb-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88fbb-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="88fbb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="88fbb-117">Élément</span><span class="sxs-lookup"><span data-stu-id="88fbb-117">Element</span></span>|<span data-ttu-id="88fbb-118">Description</span><span class="sxs-lookup"><span data-stu-id="88fbb-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="88fbb-119">Représente une liste d'éléments de configuration qui permettent d'effectuer le suivi des demandes d'annulation d'une activité enfant par l'activité parent.</span><span class="sxs-lookup"><span data-stu-id="88fbb-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="88fbb-120">La requête est nécessaire pour qu'un participant au suivi puisse s'abonner à des objets d'enregistrement de demande d'annulation.</span><span class="sxs-lookup"><span data-stu-id="88fbb-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88fbb-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88fbb-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="88fbb-122">Suivi et traçage de workflow</span><span class="sxs-lookup"><span data-stu-id="88fbb-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="88fbb-123">Modèles de suivi</span><span class="sxs-lookup"><span data-stu-id="88fbb-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
