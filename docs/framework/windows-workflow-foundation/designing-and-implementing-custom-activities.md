---
title: Conception et implémentation d'activités personnalisées
description: Cet article fournit des ressources pour créer des activités personnalisées dans Workflow Foundation en créant des activités composites ou en créant de nouveaux types d’activités.
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 9c184bff9518bb5581f3bf4cd408db224736192b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419991"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="5820b-103">Conception et implémentation d'activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="5820b-103">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="5820b-104">Dans [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)], les activités personnalisées sont créées soit en assemblant des activités fournies par le système dans des activités composites, soit en créant de nouveaux types qui dérivent des objets <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ou <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="5820b-104">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="5820b-105">Cette section décrit la procédure de création des activités personnalisées avec l'une ou l'autre de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="5820b-105">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5820b-106">Les activités personnalisées s'affichent par défaut dans le concepteur de workflow comme un rectangle simple avec le nom d'activité.</span><span class="sxs-lookup"><span data-stu-id="5820b-106">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="5820b-107">Pour fournir une représentation visuelle personnalisée de votre activité dans le concepteur de workflow, vous devez également créer un concepteur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5820b-107">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="5820b-108">Pour plus d’informations, consultez [utilisation des concepteurs et des modèles d’activités personnalisées](using-custom-activity-designers-and-templates.md).</span><span class="sxs-lookup"><span data-stu-id="5820b-108">For more information, see [Using Custom Activity Designers and Templates](using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5820b-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5820b-109">In This Section</span></span>  
 [<span data-ttu-id="5820b-110">Options de création d’activités</span><span class="sxs-lookup"><span data-stu-id="5820b-110">Activity Authoring Options</span></span>](activity-authoring-options-in-wf.md)  
 <span data-ttu-id="5820b-111">Traite des styles de création disponibles dans [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5820b-111">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="5820b-112">Utilisation d’une activité personnalisée</span><span class="sxs-lookup"><span data-stu-id="5820b-112">Using a custom activity</span></span>](using-a-custom-activity.md)  
 <span data-ttu-id="5820b-113">Décrit comment ajouter une activité personnalisée à un projet de workflow.</span><span class="sxs-lookup"><span data-stu-id="5820b-113">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="5820b-114">Création d'activités asynchrones</span><span class="sxs-lookup"><span data-stu-id="5820b-114">Creating Asynchronous Activities</span></span>](creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="5820b-115">Décrit comment créer des activités asynchrones.</span><span class="sxs-lookup"><span data-stu-id="5820b-115">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="5820b-116">Configuration de la validation d’activité</span><span class="sxs-lookup"><span data-stu-id="5820b-116">Configuring Activity Validation</span></span>](configuring-activity-validation.md)  
 <span data-ttu-id="5820b-117">Décrit comment utiliser la validation d'activité pour identifier et signaler des erreurs dans la configuration d'une activité, avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="5820b-117">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="5820b-118">Création d’une activité en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="5820b-118">Creating an Activity at Runtime</span></span>](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="5820b-119">Explique comment créer des activités au moment de l'exécution en utilisant <xref:System.Activities.DynamicActivity>.</span><span class="sxs-lookup"><span data-stu-id="5820b-119">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="5820b-120">Propriétés d’exécution de workflow</span><span class="sxs-lookup"><span data-stu-id="5820b-120">Workflow Execution Properties</span></span>](workflow-execution-properties.md)  
 <span data-ttu-id="5820b-121">Décrit comment utiliser les propriétés d'exécution de workflow pour ajouter des propriétés spécifiques au contexte à l'environnement d'une activité.</span><span class="sxs-lookup"><span data-stu-id="5820b-121">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="5820b-122">Utilisation de délégués d’activité</span><span class="sxs-lookup"><span data-stu-id="5820b-122">Using Activity Delegates</span></span>](using-activity-delegates.md)  
 <span data-ttu-id="5820b-123">Explique comment créer et utiliser des activités qui contiennent des délégués d'activité.</span><span class="sxs-lookup"><span data-stu-id="5820b-123">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="5820b-124">Utilisation d’extensions d’activité</span><span class="sxs-lookup"><span data-stu-id="5820b-124">Using Activity Extensions</span></span>](using-activity-extensions.md)  
 <span data-ttu-id="5820b-125">Décrit comment créer et utiliser des extensions d'activité.</span><span class="sxs-lookup"><span data-stu-id="5820b-125">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="5820b-126">Consommation de flux OData à partir d’un workflow</span><span class="sxs-lookup"><span data-stu-id="5820b-126">Consuming OData Feeds from a Workflow</span></span>](consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="5820b-127">Décrit plusieurs méthodes pour appeler un service de données WCF à partir d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="5820b-127">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="5820b-128">Portée et visibilité de la définition de l’activité</span><span class="sxs-lookup"><span data-stu-id="5820b-128">Activity Definition Scoping and Visibility</span></span>](activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="5820b-129">Décrit les options et les règles pour définir la portée des données et la visibilité des membres pour les activités.</span><span class="sxs-lookup"><span data-stu-id="5820b-129">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
