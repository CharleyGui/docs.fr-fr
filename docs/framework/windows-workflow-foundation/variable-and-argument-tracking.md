---
title: Suivi de variables et arguments
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 75ec8124200b146965214d161d0e6f246888542c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640979"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="d7970-102">Suivi de variables et arguments</span><span class="sxs-lookup"><span data-stu-id="d7970-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="d7970-103">Lors du suivi de l'exécution d'un workflow, il est souvent utile d'extraire des données.</span><span class="sxs-lookup"><span data-stu-id="d7970-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="d7970-104">Vous obtenez ainsi un contexte supplémentaire lors de l'accès à une post-exécution d'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="d7970-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="d7970-105">Dans [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], vous pouvez extraire toute variable ou argument visible dans l’étendue de toute activité d’un flux de travail utilisant le suivi.</span><span class="sxs-lookup"><span data-stu-id="d7970-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="d7970-106">Les profils de suivi facilitent l'extraction de données.</span><span class="sxs-lookup"><span data-stu-id="d7970-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="d7970-107">Variables et arguments</span><span class="sxs-lookup"><span data-stu-id="d7970-107">Variables and Arguments</span></span>  
 <span data-ttu-id="d7970-108">Les variables et arguments sont extraits lorsqu'une activité émet un objet ActivityStateRecord.</span><span class="sxs-lookup"><span data-stu-id="d7970-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="d7970-109">Une variable est disponible pour l'extraction, seulement si elle se trouve dans l'étendue de l'activité.</span><span class="sxs-lookup"><span data-stu-id="d7970-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="d7970-110">Une variable à extraire dans une activité est spécifiée comme suit :</span><span class="sxs-lookup"><span data-stu-id="d7970-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
- <span data-ttu-id="d7970-111">Si une variable est spécifiée par son nom, le suivi recherche la variable dans l'activité en cours de suivi et dans les activités parentes.</span><span class="sxs-lookup"><span data-stu-id="d7970-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="d7970-112">Elle est recherchée dans l'étendue de l'activité en cours et dans l'étendue parente.</span><span class="sxs-lookup"><span data-stu-id="d7970-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
- <span data-ttu-id="d7970-113">Si les variables à extraire sont spécifiées à l’aide du nom = « \* », toutes les variables dans l’activité en cours de suivi sont extraites.</span><span class="sxs-lookup"><span data-stu-id="d7970-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="d7970-114">Dans ce cas, les variables qui sont dans l'étendue, mais définies dans les activités parentes ne sont pas extraites.</span><span class="sxs-lookup"><span data-stu-id="d7970-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="d7970-115">Lors de l’extraction d’arguments, les arguments extraits dépendent de l’état de l’activité.</span><span class="sxs-lookup"><span data-stu-id="d7970-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="d7970-116">Lorsque l'état d'une activité est Exécution, seuls les `InArguments` sont disponibles pour l'extraction.</span><span class="sxs-lookup"><span data-stu-id="d7970-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="d7970-117">Pour tout autre état d’activité (Closed, Faulted, Canceled), tous les arguments, InArguments et OutArguments, sont disponibles pour l’extraction.</span><span class="sxs-lookup"><span data-stu-id="d7970-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="d7970-118">L’exemple suivant illustre une requête d’état d’activité qui extrait des variables et arguments lorsque l’enregistrement de suivi `Closed` de l’activité est émis.</span><span class="sxs-lookup"><span data-stu-id="d7970-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d7970-119">Les variables et arguments peuvent être extraits uniquement avec un objet <xref:System.Activities.Tracking.ActivityStateRecord> et l’abonnement à ces derniers se fait donc à partir d’un modèle de suivi à l’aide de l’objet <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="d7970-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="d7970-120">Protection des informations stockées dans les variables et arguments</span><span class="sxs-lookup"><span data-stu-id="d7970-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="d7970-121">Par défaut, une variable ou un argument suivi est rendu visible par le runtime WF.</span><span class="sxs-lookup"><span data-stu-id="d7970-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="d7970-122">Un développeur de workflow peut les protéger contre tout accès en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="d7970-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1. <span data-ttu-id="d7970-123">Chiffrez la valeur d'une variable.</span><span class="sxs-lookup"><span data-stu-id="d7970-123">Encrypt the value of a variable.</span></span>  
  
2. <span data-ttu-id="d7970-124">Contrôlez la création d’un modèle de suivi pour éviter l’extraction de variable ou d’argument.</span><span class="sxs-lookup"><span data-stu-id="d7970-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3. <span data-ttu-id="d7970-125">Pour les participants au suivi personnalisé, vérifiez que le code WF ne divulgue pas les informations sensibles stockées dans les variables ou les arguments.</span><span class="sxs-lookup"><span data-stu-id="d7970-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7970-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7970-126">See also</span></span>

- [<span data-ttu-id="d7970-127">Surveillance de Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="d7970-127">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="d7970-128">Surveillance des Applications avec App Fabric</span><span class="sxs-lookup"><span data-stu-id="d7970-128">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
