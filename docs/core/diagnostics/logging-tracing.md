---
title: Journalisation et suivi-.NET Core
description: Présentation de la journalisation et du suivi de .NET Core.
ms.date: 10/12/2020
ms.openlocfilehash: a8c6d82ddb7bc3f8b4cc9eae9dd7aaf65732a0b8
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548393"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="98b37-103">Journalisation et suivi .NET Core</span><span class="sxs-lookup"><span data-stu-id="98b37-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="98b37-104">La journalisation et le suivi sont en fait deux noms pour la même technique.</span><span class="sxs-lookup"><span data-stu-id="98b37-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="98b37-105">La technique simple a été utilisée depuis les premiers jours d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="98b37-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="98b37-106">Cela implique simplement l’instrumentation d’une application pour écrire la sortie à consommer ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="98b37-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="98b37-107">Raisons pour utiliser la journalisation et le suivi</span><span class="sxs-lookup"><span data-stu-id="98b37-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="98b37-108">Cette technique simple est étonnamment puissante.</span><span class="sxs-lookup"><span data-stu-id="98b37-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="98b37-109">Il peut être utilisé dans les situations où un débogueur échoue :</span><span class="sxs-lookup"><span data-stu-id="98b37-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="98b37-110">Les problèmes survenant sur de longues périodes peuvent être difficiles à déboguer avec un débogueur traditionnel.</span><span class="sxs-lookup"><span data-stu-id="98b37-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="98b37-111">Les journaux permettent d’obtenir des informations détaillées sur de longues périodes.</span><span class="sxs-lookup"><span data-stu-id="98b37-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="98b37-112">En revanche, les débogueurs se limitent à une analyse en temps réel.</span><span class="sxs-lookup"><span data-stu-id="98b37-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="98b37-113">Les applications multithread et les applications distribuées sont souvent difficiles à déboguer.</span><span class="sxs-lookup"><span data-stu-id="98b37-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="98b37-114">Attacher un débogueur tend à modifier les comportements.</span><span class="sxs-lookup"><span data-stu-id="98b37-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="98b37-115">Les journaux détaillés peuvent être analysés en fonction des besoins pour comprendre les systèmes complexes.</span><span class="sxs-lookup"><span data-stu-id="98b37-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="98b37-116">Les problèmes dans les applications distribuées peuvent provenir d’une interaction complexe entre de nombreux composants, et il n’est pas judicieux de connecter un débogueur à chaque partie du système.</span><span class="sxs-lookup"><span data-stu-id="98b37-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="98b37-117">De nombreux services ne devraient pas être bloqués.</span><span class="sxs-lookup"><span data-stu-id="98b37-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="98b37-118">Attacher un débogueur provoque souvent des échecs de dépassement de délai.</span><span class="sxs-lookup"><span data-stu-id="98b37-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="98b37-119">Les problèmes ne sont pas toujours anticipés.</span><span class="sxs-lookup"><span data-stu-id="98b37-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="98b37-120">La journalisation et le suivi sont conçus pour entraîner une faible surcharge, afin que les programmes puissent toujours enregistrer les données en cas de problème.</span><span class="sxs-lookup"><span data-stu-id="98b37-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="98b37-121">API .NET Core</span><span class="sxs-lookup"><span data-stu-id="98b37-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="98b37-122">API de style d’impression</span><span class="sxs-lookup"><span data-stu-id="98b37-122">Print style APIs</span></span>

<span data-ttu-id="98b37-123">Les <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes, et <xref:System.Diagnostics.Debug?displayProperty=nameWithType> fournissent chacune des API de style d’impression similaires pratiques pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="98b37-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="98b37-124">Vous avez le choix de l’API de style d’impression à utiliser.</span><span class="sxs-lookup"><span data-stu-id="98b37-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="98b37-125">:</span><span class="sxs-lookup"><span data-stu-id="98b37-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="98b37-126">Toujours activé et toujours écrire dans la console.</span><span class="sxs-lookup"><span data-stu-id="98b37-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="98b37-127">C’est approche est utile pour les informations dont votre client peut avoir besoin lors de la mise en production.</span><span class="sxs-lookup"><span data-stu-id="98b37-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="98b37-128">Comme il s’agit de l’approche la plus simple, elle est souvent utilisée pour le débogage temporaire ad hoc.</span><span class="sxs-lookup"><span data-stu-id="98b37-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="98b37-129">Souvent, ce code de débogage n’est jamais archivé dans le contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="98b37-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="98b37-130">Activé uniquement lorsque `TRACE` est défini en ajoutant `#define TRACE` à votre source ou en spécifiant l’option lors de la `/d:TRACE` compilation.</span><span class="sxs-lookup"><span data-stu-id="98b37-130">Only enabled when `TRACE` is defined by adding `#define TRACE` to your source or specifying the option `/d:TRACE` when compiling.</span></span>
  - <span data-ttu-id="98b37-131">Écrit dans attaché <xref:System.Diagnostics.Trace.Listeners> , par défaut <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="98b37-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="98b37-132">Utilisez cette API lors de la création de journaux qui seront activés dans la plupart des builds.</span><span class="sxs-lookup"><span data-stu-id="98b37-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="98b37-133">Activé uniquement lorsque `DEBUG` est défini en ajoutant `#define DEBUG` à votre source ou en spécifiant l’option lors de la `/d:DEBUG` compilation.</span><span class="sxs-lookup"><span data-stu-id="98b37-133">Only enabled when `DEBUG` is defined by adding `#define DEBUG` to your source or specifying the option `/d:DEBUG` when compiling.</span></span>
  - <span data-ttu-id="98b37-134">Écrit dans un débogueur attaché.</span><span class="sxs-lookup"><span data-stu-id="98b37-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="98b37-135">Lors de l' `*nix` écriture dans stderr si `COMPlus_DebugWriteToStdErr` est défini.</span><span class="sxs-lookup"><span data-stu-id="98b37-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="98b37-136">Utilisez cette API lors de la création de journaux qui seront activés uniquement dans les builds de débogage.</span><span class="sxs-lookup"><span data-stu-id="98b37-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="98b37-137">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="98b37-137">Logging events</span></span>

<span data-ttu-id="98b37-138">Les API suivantes sont plus orientées événement.</span><span class="sxs-lookup"><span data-stu-id="98b37-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="98b37-139">Au lieu d’enregistrer des chaînes simples, elles consignent des objets d’événement.</span><span class="sxs-lookup"><span data-stu-id="98b37-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="98b37-140">EventSource est l’API principale de suivi .NET Core racine.</span><span class="sxs-lookup"><span data-stu-id="98b37-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="98b37-141">Disponible dans toutes les versions de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="98b37-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="98b37-142">Autorise uniquement le suivi des objets sérialisables.</span><span class="sxs-lookup"><span data-stu-id="98b37-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="98b37-143">Peut être consommé dans le processus via n’importe quelle instance [EventListener](xref:System.Diagnostics.Tracing.EventListener) configurée pour utiliser EventSource.</span><span class="sxs-lookup"><span data-stu-id="98b37-143">Can be consumed in-process via any [EventListener](xref:System.Diagnostics.Tracing.EventListener) instances configured to consume the EventSource.</span></span>
  - <span data-ttu-id="98b37-144">Peut être consommé hors processus via :</span><span class="sxs-lookup"><span data-stu-id="98b37-144">Can be consumed out-of-process via:</span></span>
    - <span data-ttu-id="98b37-145">[EventPipe de .net Core](./eventpipe.md) sur toutes les plateformes</span><span class="sxs-lookup"><span data-stu-id="98b37-145">[.NET Core's EventPipe](./eventpipe.md) on all platforms</span></span>
    - [<span data-ttu-id="98b37-146">Suivi d’événements pour Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="98b37-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="98b37-147">Infrastructure de suivi LTTng pour Linux</span><span class="sxs-lookup"><span data-stu-id="98b37-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)
      - <span data-ttu-id="98b37-148">Procédure pas à pas : [collecte d’une trace LTTng à l’aide de PerfCollect](trace-perfcollect-lttng.md).</span><span class="sxs-lookup"><span data-stu-id="98b37-148">Walkthrough: [Collect an LTTng trace using PerfCollect](trace-perfcollect-lttng.md).</span></span>

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="98b37-149">Inclus dans .NET Core et en tant que [package NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pour .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="98b37-149">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="98b37-150">Permet le suivi en cours des objets non sérialisables.</span><span class="sxs-lookup"><span data-stu-id="98b37-150">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="98b37-151">Comprend un pont pour permettre l’écriture de champs sélectionnés d’objets journalisés dans un <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="98b37-151">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="98b37-152">Fournit un moyen définitif d’identifier les messages du journal qui résultent d’une activité ou d’une transaction spécifique.</span><span class="sxs-lookup"><span data-stu-id="98b37-152">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="98b37-153">Cet objet peut être utilisé pour mettre en corrélation les journaux entre différents services.</span><span class="sxs-lookup"><span data-stu-id="98b37-153">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="98b37-154">Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="98b37-154">Windows only.</span></span>
  - <span data-ttu-id="98b37-155">Écrit des messages dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="98b37-155">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="98b37-156">Les administrateurs système attendent que des messages d’erreur d’application irrécupérables s’affichent dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="98b37-156">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="distributed-tracing"></a><span data-ttu-id="98b37-157">Suivi distribué</span><span class="sxs-lookup"><span data-stu-id="98b37-157">Distributed Tracing</span></span>

<span data-ttu-id="98b37-158">Le [traçage distribué](./distributed-tracing.md) permet de publier et d’observer les données de suivi dans un système distribué.</span><span class="sxs-lookup"><span data-stu-id="98b37-158">[Distributed Tracing](./distributed-tracing.md) is the way to publish and observe the tracing data in a distributed system.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="98b37-159">Frameworks ILogger et Logging</span><span class="sxs-lookup"><span data-stu-id="98b37-159">ILogger and logging frameworks</span></span>

<span data-ttu-id="98b37-160">Les API de bas niveau ne sont peut-être pas le bon choix pour vos besoins de journalisation.</span><span class="sxs-lookup"><span data-stu-id="98b37-160">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="98b37-161">Vous pouvez envisager d’utiliser un Framework de journalisation.</span><span class="sxs-lookup"><span data-stu-id="98b37-161">You may want to consider a logging framework.</span></span>

<span data-ttu-id="98b37-162">L' <xref:Microsoft.Extensions.Logging.ILogger> interface a été utilisée pour créer une interface de journalisation commune dans laquelle les enregistreurs d’événements peuvent être insérés via l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="98b37-162">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="98b37-163">Par exemple, pour vous permettre de choisir le meilleur choix pour votre application, .NET offre une prise en charge pour une sélection de frameworks intégrés et tiers :</span><span class="sxs-lookup"><span data-stu-id="98b37-163">For instance, to allow you to make the best choice for your application .NET offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="98b37-164">Fournisseurs de journalisation intégrés .NET</span><span class="sxs-lookup"><span data-stu-id="98b37-164">.NET Built-in logging providers</span></span>](../extensions/logging-providers.md#built-in-logging-providers)
- [<span data-ttu-id="98b37-165">Fournisseurs de journalisation tiers .NET</span><span class="sxs-lookup"><span data-stu-id="98b37-165">.NET Third-party logging providers</span></span>](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="98b37-166">Références associées à la journalisation</span><span class="sxs-lookup"><span data-stu-id="98b37-166">Logging related references</span></span>

- [<span data-ttu-id="98b37-167">Procédure : Effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="98b37-167">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="98b37-168">Procédure : Ajouter des instructions de trace dans le code d’une application</span><span class="sxs-lookup"><span data-stu-id="98b37-168">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="98b37-169">La [journalisation dans .net](../extensions/logging.md) fournit une vue d’ensemble des techniques de journalisation qu’il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="98b37-169">[Logging in .NET](../extensions/logging.md) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="98b37-170">L' [interpolation de chaîne C#](../../csharp/language-reference/tokens/interpolated.md) peut simplifier l’écriture d’un code de journalisation.</span><span class="sxs-lookup"><span data-stu-id="98b37-170">[C# string interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- [<span data-ttu-id="98b37-171">Liste des événements du fournisseur de Runtime</span><span class="sxs-lookup"><span data-stu-id="98b37-171">Runtime Provider Event List</span></span>](../../fundamentals/diagnostics/runtime-events.md)

- [<span data-ttu-id="98b37-172">Fournisseurs d’événements connus dans .NET</span><span class="sxs-lookup"><span data-stu-id="98b37-172">Well-known Event Providers in .NET</span></span>](well-known-event-providers.md)

- <span data-ttu-id="98b37-173">La <xref:System.Exception.Message?displayProperty=nameWithType> propriété est utile pour la journalisation des exceptions.</span><span class="sxs-lookup"><span data-stu-id="98b37-173">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="98b37-174">La <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe peut être utile pour fournir des informations de pile dans vos journaux.</span><span class="sxs-lookup"><span data-stu-id="98b37-174">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="98b37-175">Considérations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="98b37-175">Performance considerations</span></span>

<span data-ttu-id="98b37-176">La mise en forme des chaînes peut prendre un temps de traitement de l’UC notable.</span><span class="sxs-lookup"><span data-stu-id="98b37-176">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="98b37-177">Dans les applications critiques pour les performances, il est recommandé de :</span><span class="sxs-lookup"><span data-stu-id="98b37-177">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="98b37-178">Évitez un grand nombre de journaux quand aucun n’est à l’écoute.</span><span class="sxs-lookup"><span data-stu-id="98b37-178">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="98b37-179">Évitez de créer des messages de journalisation coûteux en vérifiant si la journalisation est activée en premier.</span><span class="sxs-lookup"><span data-stu-id="98b37-179">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="98b37-180">Consignez uniquement ce qui est utile.</span><span class="sxs-lookup"><span data-stu-id="98b37-180">Only log what's useful.</span></span>
- <span data-ttu-id="98b37-181">Différer la mise en forme complète à l’étape d’analyse.</span><span class="sxs-lookup"><span data-stu-id="98b37-181">Defer fancy formatting to the analysis stage.</span></span>
