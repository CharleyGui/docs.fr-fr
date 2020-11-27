---
title: Configuration de la validation d'activité
ms.date: 03/30/2017
ms.assetid: 25a4eccb-b8fc-4857-a01d-2683b6341219
ms.openlocfilehash: c3e10fc096b16ef2cf7a6c7533ac9bad8c5ec205
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288955"
---
# <a name="configuring-activity-validation"></a><span data-ttu-id="24983-102">Configuration de la validation d'activité</span><span class="sxs-lookup"><span data-stu-id="24983-102">Configuring Activity Validation</span></span>

<span data-ttu-id="24983-103">La validation d'activité permet aux auteurs et aux utilisateurs d'activités d'identifier et de signaler des erreurs dans la configuration de toute activité, avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="24983-103">Activity validation enables activity authors and users to identify and report errors in an activity’s configuration prior to its execution.</span></span> <span data-ttu-id="24983-104">Windows Workflow Foundation (WF) fournit les trois types de validation d’activité suivants :</span><span class="sxs-lookup"><span data-stu-id="24983-104">Windows Workflow Foundation (WF) provides the following three types of activity validation:</span></span>  
  
- <span data-ttu-id="24983-105">attributs `RequiredArgument` et `OverloadGroup` ;</span><span class="sxs-lookup"><span data-stu-id="24983-105">`RequiredArgument` and `OverloadGroup` attributes.</span></span>  
  
- <span data-ttu-id="24983-106">validation basée sur le code impératif ;</span><span class="sxs-lookup"><span data-stu-id="24983-106">Imperative code-based validation.</span></span>  
  
- <span data-ttu-id="24983-107">contraintes déclaratives.</span><span class="sxs-lookup"><span data-stu-id="24983-107">Declarative constraints.</span></span>  
  
 <span data-ttu-id="24983-108">Les attributs `RequiredArgument` et `OverloadGroup` indiquent que certains arguments d'une activité sont requis.</span><span class="sxs-lookup"><span data-stu-id="24983-108">`RequiredArgument` and `OverloadGroup` attributes indicate that certain arguments on an activity are required.</span></span> <span data-ttu-id="24983-109">La validation basée sur le code impératif permet à une activité de fournir facilement sa propre validation. Quant aux contraintes déclaratives, elle permettent la validation de l’activité et de sa relation avec le flux de travail conteneur.</span><span class="sxs-lookup"><span data-stu-id="24983-109">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and declarative constraints enable validation about the activity and its relationship with the containing workflow.</span></span> <span data-ttu-id="24983-110">Si une activité n’est pas configurée selon les exigences de validation, des erreurs et avertissements de validation sont retournés.</span><span class="sxs-lookup"><span data-stu-id="24983-110">If an activity is not configured properly according to the validation requirements, validation errors and warnings are returned.</span></span> <span data-ttu-id="24983-111">Si le flux de travail conteneur est créé à l’aide du Workflow Designer, l’ensemble des erreurs et avertissements de validation s’affichent dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="24983-111">If the containing workflow is created using the workflow designer, any validation errors and warnings are displayed in the designer.</span></span> <span data-ttu-id="24983-112">Si le flux de travail est créé en dehors du Workflow Designer, toutes les erreurs de validation sont retournées lors de l’appel du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="24983-112">If the workflow is created outside of the workflow designer any validation errors are returned when the workflow is invoked.</span></span> <span data-ttu-id="24983-113">Quelle que soit sa méthode de création, un flux de travail contenant des erreurs de validation n'est jamais autorisé à s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="24983-113">Regardless of how the workflow was created, a workflow with validation errors is never allowed to execute.</span></span> <span data-ttu-id="24983-114">Cette section offre une vue d’ensemble de ces types de validation d’activité et de la façon dont la validation d’activité est appelée.</span><span class="sxs-lookup"><span data-stu-id="24983-114">This section provides an overview of these types of activity validation and how activity validation is invoked.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24983-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="24983-115">In This Section</span></span>  

 [<span data-ttu-id="24983-116">Arguments obligatoires et groupes surchargés</span><span class="sxs-lookup"><span data-stu-id="24983-116">Required Arguments and Overload Groups</span></span>](required-arguments-and-overload-groups.md)  
 <span data-ttu-id="24983-117">Explique comment utiliser les attributs `RequiredArgument` et `OverloadGroup` pour fournir la validation.</span><span class="sxs-lookup"><span data-stu-id="24983-117">Describes how to use the `RequiredArgument` and `OverloadGroup` attributes to provide validation.</span></span>  
  
 [<span data-ttu-id="24983-118">Validation basée sur le code impératif</span><span class="sxs-lookup"><span data-stu-id="24983-118">Imperative Code-Based Validation</span></span>](imperative-code-based-validation.md)  
 <span data-ttu-id="24983-119">Explique comment utiliser la validation basée sur code pour les activités basées sur les objets <xref:System.Activities.CodeActivity> et <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="24983-119">Describes how to use code-based validation for <xref:System.Activities.CodeActivity> and <xref:System.Activities.NativeActivity> based activities.</span></span>  
  
 [<span data-ttu-id="24983-120">Contraintes déclaratives</span><span class="sxs-lookup"><span data-stu-id="24983-120">Declarative Constraints</span></span>](declarative-constraints.md)  
 <span data-ttu-id="24983-121">Explique comment utiliser les contraintes déclaratives pour fournir la validation des activités complexes.</span><span class="sxs-lookup"><span data-stu-id="24983-121">Describes how to use declarative constraints to provide complex activity validation.</span></span>  
  
 [<span data-ttu-id="24983-122">Appel de la validation d'activité</span><span class="sxs-lookup"><span data-stu-id="24983-122">Invoking Activity Validation</span></span>](invoking-activity-validation.md)  
 <span data-ttu-id="24983-123">Explique dans quels cas la validation d’activité est appelée automatiquement et comment appeler explicitement la validation.</span><span class="sxs-lookup"><span data-stu-id="24983-123">Discusses when activity validation is invoked automatically and how to explicitly invoke validation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="24983-124">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="24983-124">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="24983-125">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="24983-125">Related Sections</span></span>
