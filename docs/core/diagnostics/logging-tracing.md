---
title: Journalisation et suivi-.NET Core
description: Présentation de la journalisation et du suivi de .NET Core.
ms.date: 10/12/2020
ms.openlocfilehash: 33c78ecc839b552267ad43dd00b7d627e756a939
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997696"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="86b85-103">Journalisation et suivi .NET Core</span><span class="sxs-lookup"><span data-stu-id="86b85-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="86b85-104">La journalisation et le suivi sont en fait deux noms pour la même technique.</span><span class="sxs-lookup"><span data-stu-id="86b85-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="86b85-105">La technique simple a été utilisée depuis les premiers jours d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="86b85-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="86b85-106">Cela implique simplement l’instrumentation d’une application pour écrire la sortie à consommer ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="86b85-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="86b85-107">Raisons pour utiliser la journalisation et le suivi</span><span class="sxs-lookup"><span data-stu-id="86b85-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="86b85-108">Cette technique simple est étonnamment puissante.</span><span class="sxs-lookup"><span data-stu-id="86b85-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="86b85-109">Il peut être utilisé dans les situations où un débogueur échoue :</span><span class="sxs-lookup"><span data-stu-id="86b85-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="86b85-110">Les problèmes survenant sur de longues périodes de temps peuvent être difficiles à déboguer avec un débogueur traditionnel.</span><span class="sxs-lookup"><span data-stu-id="86b85-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="86b85-111">Les journaux permettent d’obtenir des informations détaillées sur de longues périodes de temps.</span><span class="sxs-lookup"><span data-stu-id="86b85-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="86b85-112">En revanche, les débogueurs sont limités à l’analyse en temps réel.</span><span class="sxs-lookup"><span data-stu-id="86b85-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="86b85-113">Les applications multithread et les applications distribuées sont souvent difficiles à déboguer.</span><span class="sxs-lookup"><span data-stu-id="86b85-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="86b85-114">L’attachement d’un débogueur tend à modifier les comportements.</span><span class="sxs-lookup"><span data-stu-id="86b85-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="86b85-115">Les journaux détaillés peuvent être analysés en fonction des besoins pour comprendre les systèmes complexes.</span><span class="sxs-lookup"><span data-stu-id="86b85-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="86b85-116">Les problèmes dans les applications distribuées peuvent provenir d’une interaction complexe entre de nombreux composants et il n’est pas judicieux de connecter un débogueur à chaque partie du système.</span><span class="sxs-lookup"><span data-stu-id="86b85-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="86b85-117">De nombreux services ne doivent pas être bloqués.</span><span class="sxs-lookup"><span data-stu-id="86b85-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="86b85-118">L’attachement d’un débogueur provoque souvent des échecs de dépassement de délai.</span><span class="sxs-lookup"><span data-stu-id="86b85-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="86b85-119">Les problèmes ne sont pas toujours prévus.</span><span class="sxs-lookup"><span data-stu-id="86b85-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="86b85-120">La journalisation et le suivi sont conçus pour une faible surcharge, afin que les programmes puissent toujours être enregistrées en cas de problème.</span><span class="sxs-lookup"><span data-stu-id="86b85-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="86b85-121">API .NET Core</span><span class="sxs-lookup"><span data-stu-id="86b85-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="86b85-122">API de style d’impression</span><span class="sxs-lookup"><span data-stu-id="86b85-122">Print style APIs</span></span>

<span data-ttu-id="86b85-123">Les <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes, et <xref:System.Diagnostics.Debug?displayProperty=nameWithType> fournissent chacune des API de style d’impression similaires pratiques pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="86b85-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="86b85-124">Vous avez le choix de l’API de style d’impression à utiliser.</span><span class="sxs-lookup"><span data-stu-id="86b85-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="86b85-125">:</span><span class="sxs-lookup"><span data-stu-id="86b85-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="86b85-126">Toujours activé et écrit toujours sur la console.</span><span class="sxs-lookup"><span data-stu-id="86b85-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="86b85-127">Utile pour les informations que votre client peut avoir besoin de voir dans la version.</span><span class="sxs-lookup"><span data-stu-id="86b85-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="86b85-128">Étant donné qu’il s’agit de l’approche la plus simple, elle est souvent utilisée pour le débogage temporaire ad hoc.</span><span class="sxs-lookup"><span data-stu-id="86b85-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="86b85-129">Ce code de débogage n’est souvent jamais archivé dans le contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="86b85-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="86b85-130">Activé uniquement lorsque `TRACE` est défini.</span><span class="sxs-lookup"><span data-stu-id="86b85-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="86b85-131">Écrit dans attaché <xref:System.Diagnostics.Trace.Listeners> , par défaut <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="86b85-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="86b85-132">Utilisez cette API lors de la création de journaux qui seront activés dans la plupart des builds.</span><span class="sxs-lookup"><span data-stu-id="86b85-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="86b85-133">Activé uniquement lorsque `DEBUG` est défini.</span><span class="sxs-lookup"><span data-stu-id="86b85-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="86b85-134">Écrit dans un débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="86b85-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="86b85-135">Lors de l' `*nix` écriture dans stderr si `COMPlus_DebugWriteToStdErr` est défini.</span><span class="sxs-lookup"><span data-stu-id="86b85-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="86b85-136">Utilisez cette API lors de la création de journaux qui seront activés uniquement dans les versions Debug.</span><span class="sxs-lookup"><span data-stu-id="86b85-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="86b85-137">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="86b85-137">Logging events</span></span>

<span data-ttu-id="86b85-138">Les API suivantes sont plus orientées événement.</span><span class="sxs-lookup"><span data-stu-id="86b85-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="86b85-139">Au lieu d’enregistrer des chaînes simples, elles consignent des objets d’événement.</span><span class="sxs-lookup"><span data-stu-id="86b85-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="86b85-140">EventSource est l’API principale de suivi .NET Core racine.</span><span class="sxs-lookup"><span data-stu-id="86b85-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="86b85-141">Disponible dans toutes les versions de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="86b85-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="86b85-142">Autorise uniquement le suivi des objets sérialisables.</span><span class="sxs-lookup"><span data-stu-id="86b85-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="86b85-143">Écrit dans les [écouteurs d’événements](xref:System.Diagnostics.Tracing.EventListener)attachés.</span><span class="sxs-lookup"><span data-stu-id="86b85-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="86b85-144">.NET Core fournit des écouteurs pour :</span><span class="sxs-lookup"><span data-stu-id="86b85-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="86b85-145">EventPipe de .NET Core sur toutes les plateformes</span><span class="sxs-lookup"><span data-stu-id="86b85-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="86b85-146">Suivi d’événements pour Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="86b85-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="86b85-147">Infrastructure de suivi LTTng pour Linux</span><span class="sxs-lookup"><span data-stu-id="86b85-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="86b85-148">Inclus dans .NET Core et en tant que [package NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pour .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86b85-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="86b85-149">Permet le suivi en cours des objets non sérialisables.</span><span class="sxs-lookup"><span data-stu-id="86b85-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="86b85-150">Comprend un pont pour permettre l’écriture de champs sélectionnés d’objets journalisés dans un <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="86b85-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="86b85-151">Fournit un moyen définitif d’identifier les messages du journal qui résultent d’une activité ou d’une transaction spécifique.</span><span class="sxs-lookup"><span data-stu-id="86b85-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="86b85-152">Cet objet peut être utilisé pour mettre en corrélation les journaux entre différents services.</span><span class="sxs-lookup"><span data-stu-id="86b85-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="86b85-153">Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="86b85-153">Windows only.</span></span>
  - <span data-ttu-id="86b85-154">Écrit des messages dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="86b85-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="86b85-155">Les administrateurs système attendent que des messages d’erreur d’application irrécupérables s’affichent dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="86b85-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="86b85-156">Frameworks ILogger et Logging</span><span class="sxs-lookup"><span data-stu-id="86b85-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="86b85-157">Les API de bas niveau ne sont peut-être pas le bon choix pour vos besoins de journalisation.</span><span class="sxs-lookup"><span data-stu-id="86b85-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="86b85-158">Vous pouvez envisager d’utiliser un Framework de journalisation.</span><span class="sxs-lookup"><span data-stu-id="86b85-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="86b85-159">L' <xref:Microsoft.Extensions.Logging.ILogger> interface a été utilisée pour créer une interface de journalisation commune dans laquelle les enregistreurs d’événements peuvent être insérés via l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="86b85-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="86b85-160">Par exemple, pour vous permettre de choisir le meilleur choix pour votre application, .NET offre une prise en charge pour une sélection de frameworks intégrés et tiers :</span><span class="sxs-lookup"><span data-stu-id="86b85-160">For instance, to allow you to make the best choice for your application .NET offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="86b85-161">Fournisseurs de journalisation intégrés .NET</span><span class="sxs-lookup"><span data-stu-id="86b85-161">.NET Built-in logging providers</span></span>](../extensions/logging-providers.md#built-in-logging-providers)
- [<span data-ttu-id="86b85-162">Fournisseurs de journalisation tiers .NET</span><span class="sxs-lookup"><span data-stu-id="86b85-162">.NET Third-party logging providers</span></span>](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="86b85-163">Références associées à la journalisation</span><span class="sxs-lookup"><span data-stu-id="86b85-163">Logging related references</span></span>

- [<span data-ttu-id="86b85-164">Procédure : Effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="86b85-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="86b85-165">Procédure : Ajouter des instructions de trace dans le code d’une application</span><span class="sxs-lookup"><span data-stu-id="86b85-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="86b85-166">La [journalisation dans .net](../extensions/logging.md) fournit une vue d’ensemble des techniques de journalisation qu’il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="86b85-166">[Logging in .NET](../extensions/logging.md) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="86b85-167">L' [interpolation de chaîne C#](../../csharp/language-reference/tokens/interpolated.md) peut simplifier l’écriture d’un code de journalisation.</span><span class="sxs-lookup"><span data-stu-id="86b85-167">[C# string interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="86b85-168">La <xref:System.Exception.Message?displayProperty=nameWithType> propriété est utile pour la journalisation des exceptions.</span><span class="sxs-lookup"><span data-stu-id="86b85-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="86b85-169">La <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe peut être utile pour fournir des informations de pile dans vos journaux.</span><span class="sxs-lookup"><span data-stu-id="86b85-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="86b85-170">Considérations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="86b85-170">Performance considerations</span></span>

<span data-ttu-id="86b85-171">La mise en forme des chaînes peut prendre un temps de traitement de l’UC notable.</span><span class="sxs-lookup"><span data-stu-id="86b85-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="86b85-172">Dans les applications critiques pour les performances, il est recommandé de :</span><span class="sxs-lookup"><span data-stu-id="86b85-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="86b85-173">Évitez un grand nombre de journaux quand aucun n’est à l’écoute.</span><span class="sxs-lookup"><span data-stu-id="86b85-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="86b85-174">Évitez de créer des messages de journalisation coûteux en vérifiant si la journalisation est activée en premier.</span><span class="sxs-lookup"><span data-stu-id="86b85-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="86b85-175">Consignez uniquement ce qui est utile.</span><span class="sxs-lookup"><span data-stu-id="86b85-175">Only log what's useful.</span></span>
- <span data-ttu-id="86b85-176">Différer la mise en forme complète à l’étape d’analyse.</span><span class="sxs-lookup"><span data-stu-id="86b85-176">Defer fancy formatting to the analysis stage.</span></span>
