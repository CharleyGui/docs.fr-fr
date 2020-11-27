---
title: Liste des types de suivis
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: e8d222d6f093f5db3bd620194bfde7edd4b998a8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259243"
---
# <a name="trace-type-summary"></a><span data-ttu-id="bec8a-102">Liste des types de suivis</span><span class="sxs-lookup"><span data-stu-id="bec8a-102">Trace Type Summary</span></span>

<span data-ttu-id="bec8a-103">Les [niveaux source](xref:System.Diagnostics.SourceLevels) définissent différents niveaux de suivi : critique, erreur, avertissement, informations et commentaires. ils fournissent également une description de l' `ActivityTracing` indicateur, qui bascule la sortie des événements de limite de suivi et de transfert d’activité.</span><span class="sxs-lookup"><span data-stu-id="bec8a-103">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="bec8a-104">Vous pouvez également passer en revue <xref:System.Diagnostics.TraceEventType> les types de traces qui peuvent être émis à partir de <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="bec8a-104">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="bec8a-105">Le tableau suivant répertorie les plus importants.</span><span class="sxs-lookup"><span data-stu-id="bec8a-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="bec8a-106">Type de suivi</span><span class="sxs-lookup"><span data-stu-id="bec8a-106">Trace Type</span></span>|<span data-ttu-id="bec8a-107">Description</span><span class="sxs-lookup"><span data-stu-id="bec8a-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="bec8a-108">Critique</span><span class="sxs-lookup"><span data-stu-id="bec8a-108">Critical</span></span>|<span data-ttu-id="bec8a-109">Erreur irrécupérable ou panne d'application.</span><span class="sxs-lookup"><span data-stu-id="bec8a-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="bec8a-110">Error</span><span class="sxs-lookup"><span data-stu-id="bec8a-110">Error</span></span>|<span data-ttu-id="bec8a-111">Erreur récupérable.</span><span class="sxs-lookup"><span data-stu-id="bec8a-111">Recoverable error.</span></span>|  
|<span data-ttu-id="bec8a-112">Avertissement</span><span class="sxs-lookup"><span data-stu-id="bec8a-112">Warning</span></span>|<span data-ttu-id="bec8a-113">Message d’information.</span><span class="sxs-lookup"><span data-stu-id="bec8a-113">Informational message.</span></span>|  
|<span data-ttu-id="bec8a-114">Informations</span><span class="sxs-lookup"><span data-stu-id="bec8a-114">Information</span></span>|<span data-ttu-id="bec8a-115">Problème non critique.</span><span class="sxs-lookup"><span data-stu-id="bec8a-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="bec8a-116">Commentaires</span><span class="sxs-lookup"><span data-stu-id="bec8a-116">Verbose</span></span>|<span data-ttu-id="bec8a-117">Suivi de débogage.</span><span class="sxs-lookup"><span data-stu-id="bec8a-117">Debugging trace.</span></span>|  
|<span data-ttu-id="bec8a-118">Démarrer</span><span class="sxs-lookup"><span data-stu-id="bec8a-118">Start</span></span>|<span data-ttu-id="bec8a-119">Démarrage d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="bec8a-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="bec8a-120">Interrompre</span><span class="sxs-lookup"><span data-stu-id="bec8a-120">Suspend</span></span>|<span data-ttu-id="bec8a-121">Interruption d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="bec8a-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="bec8a-122">Reprendre</span><span class="sxs-lookup"><span data-stu-id="bec8a-122">Resume</span></span>|<span data-ttu-id="bec8a-123">Reprise d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="bec8a-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="bec8a-124">Arrêter</span><span class="sxs-lookup"><span data-stu-id="bec8a-124">Stop</span></span>|<span data-ttu-id="bec8a-125">Arrêt d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="bec8a-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="bec8a-126">Transférer</span><span class="sxs-lookup"><span data-stu-id="bec8a-126">Transfer</span></span>|<span data-ttu-id="bec8a-127">Changement d'identité de corrélation.</span><span class="sxs-lookup"><span data-stu-id="bec8a-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="bec8a-128">Une activité est définie comme une combinaison des types de suivi ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="bec8a-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="bec8a-129">Le code suivant est une expression régulière qui définit une activité idéale dans une étendue locale (source de suivi).</span><span class="sxs-lookup"><span data-stu-id="bec8a-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="bec8a-130">Cela signifie qu'une activité doit remplir les conditions suivantes.</span><span class="sxs-lookup"><span data-stu-id="bec8a-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="bec8a-131">Elle doit respectivement démarrer et s'arrêter avec les suivis Démarrer et Arrêter.</span><span class="sxs-lookup"><span data-stu-id="bec8a-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="bec8a-132">Elle doit contenir un suivi Transfert immédiatement avant un suivi Interrompre ou Reprendre.</span><span class="sxs-lookup"><span data-stu-id="bec8a-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="bec8a-133">Elle ne doit pas contenir de suivi entre les suivis Interrompre et Reprendre, s'ils existent.</span><span class="sxs-lookup"><span data-stu-id="bec8a-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="bec8a-134">Elle peut contenir n'importe quel type de suivi Critique/Avertissement/Informations/Commentaires/Transfert, en nombre illimité, tant que les conditions précédentes sont observées.</span><span class="sxs-lookup"><span data-stu-id="bec8a-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="bec8a-135">Le code suivant est une expression régulière qui définit une activité idéale dans la portée globale,</span><span class="sxs-lookup"><span data-stu-id="bec8a-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="bec8a-136">R étant l'expression régulière d'une activité dans l'étendue locale.</span><span class="sxs-lookup"><span data-stu-id="bec8a-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="bec8a-137">Cela se traduit par :</span><span class="sxs-lookup"><span data-stu-id="bec8a-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
