---
title: Liste des types de suivis
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674839"
---
# <a name="trace-type-summary"></a><span data-ttu-id="9d4d9-102">Liste des types de suivis</span><span class="sxs-lookup"><span data-stu-id="9d4d9-102">Trace Type Summary</span></span>
<span data-ttu-id="9d4d9-103">[Les niveaux de source](xref:System.Diagnostics.SourceLevels) définissent divers niveaux de trace : critiques, erreurs, avertissement, `ActivityTracing` information et Verbose, ainsi qu’une description du drapeau, qui bascule la sortie des événements de limite de trace et de transfert d’activité.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-103">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="9d4d9-104">Vous pouvez <xref:System.Diagnostics.TraceEventType> également passer en revue pour les <xref:System.Diagnostics>types de traces qui peuvent être émises à partir de .</span><span class="sxs-lookup"><span data-stu-id="9d4d9-104">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="9d4d9-105">Le tableau suivant répertorie les plus importants.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="9d4d9-106">Type de suivi</span><span class="sxs-lookup"><span data-stu-id="9d4d9-106">Trace Type</span></span>|<span data-ttu-id="9d4d9-107">Description</span><span class="sxs-lookup"><span data-stu-id="9d4d9-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="9d4d9-108">Critique</span><span class="sxs-lookup"><span data-stu-id="9d4d9-108">Critical</span></span>|<span data-ttu-id="9d4d9-109">Erreur irrécupérable ou panne d'application.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="9d4d9-110">Error</span><span class="sxs-lookup"><span data-stu-id="9d4d9-110">Error</span></span>|<span data-ttu-id="9d4d9-111">Erreur récupérable.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-111">Recoverable error.</span></span>|  
|<span data-ttu-id="9d4d9-112">Avertissement</span><span class="sxs-lookup"><span data-stu-id="9d4d9-112">Warning</span></span>|<span data-ttu-id="9d4d9-113">Message d’information.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-113">Informational message.</span></span>|  
|<span data-ttu-id="9d4d9-114">Information</span><span class="sxs-lookup"><span data-stu-id="9d4d9-114">Information</span></span>|<span data-ttu-id="9d4d9-115">Problème non critique.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="9d4d9-116">Commentaires</span><span class="sxs-lookup"><span data-stu-id="9d4d9-116">Verbose</span></span>|<span data-ttu-id="9d4d9-117">Suivi de débogage.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-117">Debugging trace.</span></span>|  
|<span data-ttu-id="9d4d9-118">Démarrer</span><span class="sxs-lookup"><span data-stu-id="9d4d9-118">Start</span></span>|<span data-ttu-id="9d4d9-119">Démarrage d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9d4d9-120">Interrompre</span><span class="sxs-lookup"><span data-stu-id="9d4d9-120">Suspend</span></span>|<span data-ttu-id="9d4d9-121">Interruption d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9d4d9-122">Reprendre</span><span class="sxs-lookup"><span data-stu-id="9d4d9-122">Resume</span></span>|<span data-ttu-id="9d4d9-123">Reprise d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9d4d9-124">Arrêter</span><span class="sxs-lookup"><span data-stu-id="9d4d9-124">Stop</span></span>|<span data-ttu-id="9d4d9-125">Arrêt d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="9d4d9-126">Transférer</span><span class="sxs-lookup"><span data-stu-id="9d4d9-126">Transfer</span></span>|<span data-ttu-id="9d4d9-127">Changement d'identité de corrélation.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="9d4d9-128">Une activité est définie comme une combinaison des types de suivi ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="9d4d9-129">Le code suivant est une expression régulière qui définit une activité idéale dans une étendue locale (source de suivi).</span><span class="sxs-lookup"><span data-stu-id="9d4d9-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="9d4d9-130">Cela signifie qu'une activité doit remplir les conditions suivantes.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="9d4d9-131">Elle doit respectivement démarrer et s'arrêter avec les suivis Démarrer et Arrêter.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="9d4d9-132">Elle doit contenir un suivi Transfert immédiatement avant un suivi Interrompre ou Reprendre.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="9d4d9-133">Elle ne doit pas contenir de suivi entre les suivis Interrompre et Reprendre, s'ils existent.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="9d4d9-134">Elle peut contenir n'importe quel type de suivi Critique/Avertissement/Informations/Commentaires/Transfert, en nombre illimité, tant que les conditions précédentes sont observées.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="9d4d9-135">Le code suivant est une expression régulière qui définit une activité idéale dans la portée globale,</span><span class="sxs-lookup"><span data-stu-id="9d4d9-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="9d4d9-136">R étant l'expression régulière d'une activité dans l'étendue locale.</span><span class="sxs-lookup"><span data-stu-id="9d4d9-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="9d4d9-137">Cela se traduit par :</span><span class="sxs-lookup"><span data-stu-id="9d4d9-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
