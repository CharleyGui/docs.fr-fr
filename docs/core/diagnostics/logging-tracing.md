---
title: Enregistrement et traçage - .NET Core
description: Une introduction à l’enregistrement et au traçage de base de .NET.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714424"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="d0bfb-103">.NET Core logging and tracing</span><span class="sxs-lookup"><span data-stu-id="d0bfb-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="d0bfb-104">L’exploitation forestière et le traçage sont vraiment deux noms pour la même technique.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="d0bfb-105">La technique simple a été utilisée depuis les premiers jours des ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="d0bfb-106">Il s’agit simplement d’instrumenter une application pour écrire la sortie à consommer plus tard.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="d0bfb-107">Raisons d’utiliser l’enregistrement et le traçage</span><span class="sxs-lookup"><span data-stu-id="d0bfb-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="d0bfb-108">Cette technique simple est étonnamment puissante.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="d0bfb-109">Il peut être utilisé dans les situations où un débbuggeur échoue :</span><span class="sxs-lookup"><span data-stu-id="d0bfb-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="d0bfb-110">Les problèmes qui se produisent sur de longues périodes de temps, peuvent être difficiles à déboquer avec un débbugger traditionnel.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="d0bfb-111">Les journaux permettent un examen post-mortem détaillé couvrant de longues périodes de temps.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="d0bfb-112">En revanche, les débbuggeurs sont limités à l’analyse en temps réel.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="d0bfb-113">Les applications multi-threaded et les applications distribuées sont souvent difficiles à déboiffer.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="d0bfb-114">L’attachement d’un débbuggeur tend à modifier les comportements.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="d0bfb-115">Les journaux détaillés peuvent être analysés au besoin pour comprendre les systèmes complexes.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="d0bfb-116">Les problèmes dans les applications distribuées peuvent résulter d’une interaction complexe entre de nombreux composants et il peut ne pas être raisonnable de connecter un débbugger à chaque partie du système.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="d0bfb-117">De nombreux services ne devraient pas être bloqués.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="d0bfb-118">L’attachement d’un débogueur provoque souvent des échecs de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="d0bfb-119">Les problèmes ne sont pas toujours prévus.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="d0bfb-120">L’enregistrement et le traçage sont conçus pour les frais généraux faibles afin que les programmes puissent toujours être consigné en cas de problème.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="d0bfb-121">.NET Core API</span><span class="sxs-lookup"><span data-stu-id="d0bfb-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="d0bfb-122">API de style d’impression</span><span class="sxs-lookup"><span data-stu-id="d0bfb-122">Print style APIs</span></span>

<span data-ttu-id="d0bfb-123">Les <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType> , et les classes fournissent chacune des API de style d’impression similaires pratique pour l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="d0bfb-124">Le choix de l’API de style d’impression à utiliser est à vous.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="d0bfb-125">:</span><span class="sxs-lookup"><span data-stu-id="d0bfb-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="d0bfb-126">Toujours activé et écrit toujours à la console.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="d0bfb-127">Utile pour les informations que votre client peut avoir besoin de voir dans la version.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="d0bfb-128">Parce que c’est l’approche la plus simple, elle est souvent utilisée pour le débogage temporaire ad hoc.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="d0bfb-129">Ce code de débaillement n’est souvent jamais enregistré au contrôle de source.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="d0bfb-130">Activé uniquement `TRACE` lorsque vous êtes défini.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-130">Only enabled when `TRACE` is defined.</span></span>
  - <span data-ttu-id="d0bfb-131">Écrit à <xref:System.Diagnostics.Trace.Listeners>ci-joint <xref:System.Diagnostics.DefaultTraceListener>, par défaut le .</span><span class="sxs-lookup"><span data-stu-id="d0bfb-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="d0bfb-132">Utilisez cette API lors de la création de journaux qui seront activés dans la plupart des versions.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="d0bfb-133">Activé uniquement `DEBUG` lorsque vous êtes défini.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-133">Only enabled when `DEBUG` is defined.</span></span>
  - <span data-ttu-id="d0bfb-134">Écrit à un débbuggeur attaché.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="d0bfb-135">Sur `*nix` écrit à stderr si `COMPlus_DebugWriteToStdErr` est réglé.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="d0bfb-136">Utilisez cette API lors de la création de journaux qui ne seront activés que dans les constructions de débogé.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="d0bfb-137">Événements d’exploitation forestière</span><span class="sxs-lookup"><span data-stu-id="d0bfb-137">Logging events</span></span>

<span data-ttu-id="d0bfb-138">Les API suivantes sont plus orientées vers l’événement.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="d0bfb-139">Plutôt que d’enregistrer des chaînes simples, ils enregistrent des objets d’événement.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="d0bfb-140">EventSource est la principale racine .NET Core traçant API.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="d0bfb-141">Disponible dans toutes les versions .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="d0bfb-142">Permet seulement de retracer des objets sérialisables.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="d0bfb-143">Écrit aux [auditeurs de l’événement ci-joint](xref:System.Diagnostics.Tracing.EventListener).</span><span class="sxs-lookup"><span data-stu-id="d0bfb-143">Writes to the attached [event listeners](xref:System.Diagnostics.Tracing.EventListener).</span></span>
  - <span data-ttu-id="d0bfb-144">.NET Core fournit aux auditeurs pour :</span><span class="sxs-lookup"><span data-stu-id="d0bfb-144">.NET Core provides listeners for:</span></span>
    - <span data-ttu-id="d0bfb-145">.NET Core’s EventPipe sur toutes les plateformes</span><span class="sxs-lookup"><span data-stu-id="d0bfb-145">.NET Core's EventPipe on all platforms</span></span>
    - [<span data-ttu-id="d0bfb-146">Suivi d'événements pour Windows (ETW)</span><span class="sxs-lookup"><span data-stu-id="d0bfb-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="d0bfb-147">Cadre de traçage LTTng pour Linux</span><span class="sxs-lookup"><span data-stu-id="d0bfb-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="d0bfb-148">Inclus dans .NET Core et comme un [paquet NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pour .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-148">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="d0bfb-149">Permet le traçage en cours d’objets non sérialisables.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-149">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="d0bfb-150">Inclut un pont pour permettre l’écriture de <xref:System.Diagnostics.Tracing.EventSource>certains champs d’objets enregistrés à un .</span><span class="sxs-lookup"><span data-stu-id="d0bfb-150">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="d0bfb-151">Fournit un moyen définitif d’identifier les messages journalaux résultant d’une activité ou d’une transaction spécifique.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-151">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="d0bfb-152">Cet objet peut être utilisé pour corréler les journaux entre différents services.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-152">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="d0bfb-153">Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-153">Windows only.</span></span>
  - <span data-ttu-id="d0bfb-154">Écrit des messages au journal d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-154">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="d0bfb-155">Les administrateurs système s’attendent à ce que les messages d’erreur d’application mortels apparaissent dans le journal d’événements Windows.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-155">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="d0bfb-156">Cadres ILogger et exploitation forestière</span><span class="sxs-lookup"><span data-stu-id="d0bfb-156">ILogger and logging frameworks</span></span>

<span data-ttu-id="d0bfb-157">Les API de bas niveau peuvent ne pas être le bon choix pour vos besoins d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-157">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="d0bfb-158">Vous voudrez peut-être envisager un cadre d’exploitation forestière.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-158">You may want to consider a logging framework.</span></span>

<span data-ttu-id="d0bfb-159">L’interface <xref:Microsoft.Extensions.Logging.ILogger> a été utilisée pour créer une interface d’enregistrement commune où les enregistreurs peuvent être insérés par injection de dépendance.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-159">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="d0bfb-160">Par exemple, vous permettre de faire le `ASP.NET` meilleur choix pour votre application offre un support pour une sélection de cadres intégrés et tiers:</span><span class="sxs-lookup"><span data-stu-id="d0bfb-160">For instance, to allow you to make the best choice for your application `ASP.NET` offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="d0bfb-161">ASP.NET construit dans les fournisseurs d’exploitation forestière</span><span class="sxs-lookup"><span data-stu-id="d0bfb-161">ASP.NET built in logging providers</span></span>](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [<span data-ttu-id="d0bfb-162">ASP.NET fournisseurs d’exploitation forestière tiers</span><span class="sxs-lookup"><span data-stu-id="d0bfb-162">ASP.NET Third-party logging providers</span></span>](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="d0bfb-163">Références liées à l’exploitation forestière</span><span class="sxs-lookup"><span data-stu-id="d0bfb-163">Logging related references</span></span>

- [<span data-ttu-id="d0bfb-164">Comment : effectuer une compilation conditionnelle avec Trace et Debug</span><span class="sxs-lookup"><span data-stu-id="d0bfb-164">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="d0bfb-165">Comment : ajouter des instructions de traçage dans le code d'une application</span><span class="sxs-lookup"><span data-stu-id="d0bfb-165">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="d0bfb-166">[ASP.NET l’exploitation forestière](/aspnet/core/fundamentals/logging) donne un aperçu des techniques d’exploitation forestière qu’il prend en charge.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-166">[ASP.NET Logging](/aspnet/core/fundamentals/logging) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="d0bfb-167">[L’interpolation des chaînes de CMD](../../csharp/language-reference/tokens/interpolated.md) peut simplifier l’écriture de code d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-167">[C# String Interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- <span data-ttu-id="d0bfb-168">La <xref:System.Exception.Message?displayProperty=nameWithType> propriété est utile pour les exceptions d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-168">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="d0bfb-169">La <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe peut être utile pour fournir des informations de pile dans vos journaux.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-169">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="d0bfb-170">Considérations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="d0bfb-170">Performance considerations</span></span>

<span data-ttu-id="d0bfb-171">La mise en forme des cordes peut prendre un temps de traitement CPU notable.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-171">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="d0bfb-172">Dans les applications critiques de performance, il est recommandé que vous :</span><span class="sxs-lookup"><span data-stu-id="d0bfb-172">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="d0bfb-173">Évitez beaucoup de connexion lorsque personne n’écoute.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-173">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="d0bfb-174">Évitez de construire des messages d’enregistrement coûteux en vérifiant si l’enregistrement est activé en premier.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-174">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="d0bfb-175">Enregistrez seulement ce qui est utile.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-175">Only log what's useful.</span></span>
- <span data-ttu-id="d0bfb-176">Reportez le formatage de fantaisie à l’étape de l’analyse.</span><span class="sxs-lookup"><span data-stu-id="d0bfb-176">Defer fancy formatting to the analysis stage.</span></span>
