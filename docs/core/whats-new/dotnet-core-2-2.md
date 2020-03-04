---
title: Nouveautés de .NET Core 2.2
description: Découvrez les nouvelles fonctionnalités de .NET Core 2.2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: e045c39240c99777d05ca86ee0a8cd1fa4309c4f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156580"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="2f3dc-103">Nouveautés de .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2f3dc-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="2f3dc-104">.NET Core 2.2 comporte des améliorations dans plusieurs domaines : déploiement d’applications, gestion des événements pour les services de runtime, authentification auprès des bases de données SQL Azure, performances du compilateur JIT et injection de code avant l’exécution de la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="2f3dc-105">Nouveau mode de déploiement</span><span class="sxs-lookup"><span data-stu-id="2f3dc-105">New deployment mode</span></span>

<span data-ttu-id="2f3dc-106">À partir de .NET Core 2.2, vous pouvez déployer des [exécutables dépendants du framework](../deploying/index.md#publish-runtime-dependent), qui sont des fichiers **.exe** au lieu de fichiers **.dll**.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#publish-runtime-dependent), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="2f3dc-107">Comme les déploiements dépendants du framework, les exécutables dépendants du framework dépendent toujours de la présence d’une version de .NET Core partagée à l’échelle du système pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="2f3dc-108">Votre application ne comporte que votre code et les éventuelles dépendances tierces.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="2f3dc-109">Contrairement aux déploiements dépendants du framework, les exécutables dépendants du framework sont propres à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="2f3dc-110">Ce nouveau mode de déploiement présente le net avantage de créer un exécutable au lieu d’une bibliothèque, ce qui permet d’exécuter directement l’application, sans appeler `dotnet` au préalable.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="2f3dc-111">Core</span><span class="sxs-lookup"><span data-stu-id="2f3dc-111">Core</span></span>

<span data-ttu-id="2f3dc-112">**Gérer les événements dans les services de runtime**</span><span class="sxs-lookup"><span data-stu-id="2f3dc-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="2f3dc-113">Supposons que vous souhaitiez surveiller l’utilisation des services de runtime (par exemple, GC, JIT ou ThreadPool) par votre application, pour comprendre leur impact sur votre application.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="2f3dc-114">Sur les systèmes Windows, cette opération est généralement effectuée en surveillant les événements ETW du processus en cours.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="2f3dc-115">Bien que cette opération continue de fonctionner correctement, il n’est pas toujours possible d’utiliser ETW si vous exécutez dans un environnement à faibles privilèges ou sur Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span>

<span data-ttu-id="2f3dc-116">À partir de .NET Core 2.2, la classe <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> peut consommer des événements CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2f3dc-117">Ces événements décrivent le comportement de ces services de runtime, comme GC, JIT, ThreadPool et Interop.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="2f3dc-118">Ce sont les mêmes que dans le fournisseur ETW CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="2f3dc-119">Cela permet aux applications de consommer ces événements ou d’utiliser un mécanisme de transport pour les envoyer à un service d’agrégation de télémétrie.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="2f3dc-120">L’exemple de code suivant montre comment s’abonner aux événements :</span><span class="sxs-lookup"><span data-stu-id="2f3dc-120">You can see how to subscribe to events in the following code sample:</span></span>

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

<span data-ttu-id="2f3dc-121">Par ailleurs, .NET Core 2.2 ajoute les deux propriétés suivantes à la classe <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> pour fournir des informations supplémentaires sur les événements ETW :</span><span class="sxs-lookup"><span data-stu-id="2f3dc-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="2f3dc-122">Données</span><span class="sxs-lookup"><span data-stu-id="2f3dc-122">Data</span></span>

<span data-ttu-id="2f3dc-123">**Authentification AAD à des bases de données SQL Azure avec la propriété SqlConnection.AccessToken**</span><span class="sxs-lookup"><span data-stu-id="2f3dc-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="2f3dc-124">À partir de .NET Core 2.2, il est possible d’utiliser un jeton d’accès émis par Azure Active Directory pour s’authentifier auprès d’une base de données SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="2f3dc-125">Pour prendre en charge les jetons d’accès, la propriété <xref:System.Data.SqlClient.SqlConnection.AccessToken> a été ajoutée à la classe <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="2f3dc-126">Téléchargez la version 4.6 du package NuGet System.Data.SqlClient afin de tirer parti de l’authentification AAD.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="2f3dc-127">Pour pouvoir utiliser la fonctionnalité, récupérez la valeur du jeton d’accès à l’aide de la [Bibliothèque d'authentification Active Directory pour .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contenue dans le package NuGet [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).</span><span class="sxs-lookup"><span data-stu-id="2f3dc-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="2f3dc-128">Améliorations du compilateur JIT</span><span class="sxs-lookup"><span data-stu-id="2f3dc-128">JIT compiler improvements</span></span>

<span data-ttu-id="2f3dc-129">**La compilation hiérarchisée reste une fonctionnalité sur option**</span><span class="sxs-lookup"><span data-stu-id="2f3dc-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="2f3dc-130">Dans .NET Core 2.1, le compilateur JIT a implémenté une nouvelle technologie, la *compilation hiérarchisée*, que l’on peut choisir d’activer ou non.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="2f3dc-131">L’objectif de la compilation hiérarchisée est d’améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="2f3dc-132">Une des tâches importantes effectuées par le compilateur JIT est l’optimisation de l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="2f3dc-133">Pour les chemins de code peu utilisés cependant, le compilateur risque de passer plus de temps à optimiser le code que le runtime à exécuter du code non optimisé.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="2f3dc-134">La compilation à plusieurs niveaux ajoute deux étapes à la compilation JIT :</span><span class="sxs-lookup"><span data-stu-id="2f3dc-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="2f3dc-135">Un **premier niveau**, qui génère du code aussi rapidement que possible.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="2f3dc-136">Un **second niveau**, qui génère un code optimisé pour les méthodes fréquemment exécutées.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="2f3dc-137">Le second niveau de compilation est effectué en parallèle pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="2f3dc-138">Pour plus d’informations sur l’amélioration des performances offerte par la compilation hiérarchisée, voir [Annonce de .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="2f3dc-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="2f3dc-139">Dans .NET Core 2.2 Preview 2, la compilation hiérarchisée était activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="2f3dc-140">Toutefois, nous avons décidé que nous ne sommes pas encore prêts à l’activer par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="2f3dc-141">C’est pourquoi, dans .NET Core 2.2, elle reste une fonctionnalité sur option.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="2f3dc-142">Pour plus d’informations sur le choix de la compilation hiérarchisée, voir [Amélioration du compilateur JIT](dotnet-core-2-1.md#jit-compiler-improvements) dans [Nouveautés de .NET Core 2.1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="2f3dc-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="2f3dc-143">Runtime</span><span class="sxs-lookup"><span data-stu-id="2f3dc-143">Runtime</span></span>

<span data-ttu-id="2f3dc-144">**Injecter du code avant d’exécuter la méthode Main**</span><span class="sxs-lookup"><span data-stu-id="2f3dc-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="2f3dc-145">À partir de .NET Core 2.2, vous pouvez utiliser un hook de démarrage pour injecter du code avant d’exécuter la méthode Main d’une application.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="2f3dc-146">Les hooks de démarrage permettent à un hôte de personnaliser le comportement des applications une fois déployées, sans avoir à les recompiler ou à les modifier.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="2f3dc-147">Nous attendons des fournisseurs d’hébergement qu’ils définissent la stratégie et la configuration personnalisées, y compris les paramètres susceptibles d’influencer le comportement du point d’entrée principal, et notamment le comportement de  <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2f3dc-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="2f3dc-148">Le hook peut être utilisé pour configurer l’injection de données de télémétrie ou de suivi, pour mettre en place des rappels à des fins de gestion ou pour définir un autre comportement dépendant de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="2f3dc-149">Il est distinct du point d’entrée, ce qui évite d’avoir à modifier le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f3dc-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="2f3dc-150">Pour plus d’informations, voir [Hook de démarrage hôte](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md).</span><span class="sxs-lookup"><span data-stu-id="2f3dc-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f3dc-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f3dc-151">See also</span></span>

- [<span data-ttu-id="2f3dc-152">Nouveautés de .NET Core</span><span class="sxs-lookup"><span data-stu-id="2f3dc-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="2f3dc-153">Nouveautés d’ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2f3dc-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="2f3dc-154">Nouvelles fonctionnalités d’EF Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2f3dc-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
