---
title: Hôte générique .NET
author: IEvangelist
description: En savoir plus sur l’hôte générique .NET, qui est responsable du démarrage et de la gestion de la durée de vie des applications.
ms.author: dapine
ms.date: 12/04/2020
ms.openlocfilehash: ddb71b70d15121b7f59899fba38b2bf861219878
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740096"
---
# <a name="net-generic-host"></a><span data-ttu-id="4b7f4-103">Hôte générique .NET</span><span class="sxs-lookup"><span data-stu-id="4b7f4-103">.NET Generic Host</span></span>

<span data-ttu-id="4b7f4-104">Les modèles de service Worker créent un hôte générique .NET, <xref:Microsoft.Extensions.Hosting.HostBuilder> .</span><span class="sxs-lookup"><span data-stu-id="4b7f4-104">The Worker Service templates create a .NET Generic Host, <xref:Microsoft.Extensions.Hosting.HostBuilder>.</span></span> <span data-ttu-id="4b7f4-105">L’hôte générique peut être utilisé avec d’autres types d’applications .NET, comme les applications console.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-105">The Generic Host can be used with other types of .NET applications, such as Console apps.</span></span>

<span data-ttu-id="4b7f4-106">Un *hôte* est un objet qui encapsule les ressources de l’application, telles que :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-106">A *host* is an object that encapsulates an app's resources, such as:</span></span>

- <span data-ttu-id="4b7f4-107">Injection de dépendances (DI)</span><span class="sxs-lookup"><span data-stu-id="4b7f4-107">Dependency injection (DI)</span></span>
- <span data-ttu-id="4b7f4-108">Journalisation</span><span class="sxs-lookup"><span data-stu-id="4b7f4-108">Logging</span></span>
- <span data-ttu-id="4b7f4-109">Configuration</span><span class="sxs-lookup"><span data-stu-id="4b7f4-109">Configuration</span></span>
- <span data-ttu-id="4b7f4-110">Implémentations de `IHostedService`</span><span class="sxs-lookup"><span data-stu-id="4b7f4-110">`IHostedService` implementations</span></span>

<span data-ttu-id="4b7f4-111">Lorsqu’un hôte démarre, il appelle <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> sur chaque implémentation de <xref:Microsoft.Extensions.Hosting.IHostedService> inscrite dans la collection de services hébergés du conteneur de services.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-111">When a host starts, it calls <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> on each implementation of <xref:Microsoft.Extensions.Hosting.IHostedService> registered in the service container's collection of hosted services.</span></span> <span data-ttu-id="4b7f4-112">Dans une application de service de travail, toutes les `IHostedService` implémentations qui contiennent des <xref:Microsoft.Extensions.Hosting.BackgroundService> instances ont leurs <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> méthodes appelées.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-112">In a worker service app, all `IHostedService` implementations that contain <xref:Microsoft.Extensions.Hosting.BackgroundService> instances have their <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> methods called.</span></span>

<span data-ttu-id="4b7f4-113">La principale raison d’inclure toutes les ressources interdépendantes de l’application dans un objet est la gestion de la durée de vie : contrôler le démarrage de l’application et l’arrêt approprié.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-113">The main reason for including all of the app's interdependent resources in one object is lifetime management: control over app startup and graceful shutdown.</span></span> <span data-ttu-id="4b7f4-114">Cela est possible avec le package NuGet [Microsoft. extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) .</span><span class="sxs-lookup"><span data-stu-id="4b7f4-114">This is achieved with the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package.</span></span>

## <a name="set-up-a-host"></a><span data-ttu-id="4b7f4-115">Configurer un hôte</span><span class="sxs-lookup"><span data-stu-id="4b7f4-115">Set up a host</span></span>

<span data-ttu-id="4b7f4-116">L’hôte est généralement configuré, généré et exécuté par du code dans la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-116">The host is typically configured, built, and run by code in the `Program` class.</span></span> <span data-ttu-id="4b7f4-117">La méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-117">The `Main` method:</span></span>

- <span data-ttu-id="4b7f4-118">Appelle une méthode <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> pour créer et configurer un objet builder.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-118">Calls a <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> method to create and configure a builder object.</span></span>
- <span data-ttu-id="4b7f4-119">Appelle <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> pour créer une <xref:Microsoft.Extensions.Hosting.IHost> instance.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-119">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> to create an <xref:Microsoft.Extensions.Hosting.IHost> instance.</span></span>
- <span data-ttu-id="4b7f4-120">Appelle <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> ou <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> méthode sur l’objet hôte.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-120">Calls <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> or <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> method on the host object.</span></span>

<span data-ttu-id="4b7f4-121">Les modèles de service de travail .NET génèrent le code suivant pour créer un hôte générique :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-121">The .NET Worker Service templates generate the following code to create a Generic Host:</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureServices((hostContext, services) =>
            {
                services.AddHostedService<Worker>();
            });
}
```

## <a name="default-builder-settings"></a><span data-ttu-id="4b7f4-122">Paramètres du générateur par défaut</span><span class="sxs-lookup"><span data-stu-id="4b7f4-122">Default builder settings</span></span>

<span data-ttu-id="4b7f4-123">La méthode <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-123">The <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> method:</span></span>

- <span data-ttu-id="4b7f4-124">Définit le chemin retourné par <xref:System.IO.Directory.GetCurrentDirectory> comme racine de contenu.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-124">Sets the content root to the path returned by <xref:System.IO.Directory.GetCurrentDirectory>.</span></span>
- <span data-ttu-id="4b7f4-125">Charge la [configuration de l’hôte](#host-configuration) à partir de :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-125">Loads [host configuration](#host-configuration) from:</span></span>
  - <span data-ttu-id="4b7f4-126">Les variables d’environnement précédées de `DOTNET_` .</span><span class="sxs-lookup"><span data-stu-id="4b7f4-126">Environment variables prefixed with `DOTNET_`.</span></span>
  - <span data-ttu-id="4b7f4-127">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="4b7f4-127">Command-line arguments.</span></span>
- <span data-ttu-id="4b7f4-128">Charge la configuration de l’application à partir de :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-128">Loads app configuration from:</span></span>
  - <span data-ttu-id="4b7f4-129">*appsettings.js*.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-129">*appsettings.json*.</span></span>
  - <span data-ttu-id="4b7f4-130">*appsettings.{Environment}.json*</span><span class="sxs-lookup"><span data-stu-id="4b7f4-130">*appsettings.{Environment}.json*.</span></span>
  - <span data-ttu-id="4b7f4-131">Secret Manager quand l’application s’exécute dans l’environnement `Development`.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-131">Secret Manager when the app runs in the `Development` environment.</span></span>
  - <span data-ttu-id="4b7f4-132">Variables d'environnement.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-132">Environment variables.</span></span>
  - <span data-ttu-id="4b7f4-133">Arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="4b7f4-133">Command-line arguments.</span></span>
- <span data-ttu-id="4b7f4-134">Ajoute les fournisseurs de journalisation suivants :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-134">Adds the following logging providers:</span></span>
  - <span data-ttu-id="4b7f4-135">Console</span><span class="sxs-lookup"><span data-stu-id="4b7f4-135">Console</span></span>
  - <span data-ttu-id="4b7f4-136">Débogage</span><span class="sxs-lookup"><span data-stu-id="4b7f4-136">Debug</span></span>
  - <span data-ttu-id="4b7f4-137">EventSource</span><span class="sxs-lookup"><span data-stu-id="4b7f4-137">EventSource</span></span>
  - <span data-ttu-id="4b7f4-138">EventLog (uniquement en cas d’exécution sur Windows)</span><span class="sxs-lookup"><span data-stu-id="4b7f4-138">EventLog (only when running on Windows)</span></span>
- <span data-ttu-id="4b7f4-139">Active la validation de l’étendue et la [validation des dépendances](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) lorsque l’environnement est `Development` .</span><span class="sxs-lookup"><span data-stu-id="4b7f4-139">Enables scope validation and [dependency validation](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) when the environment is `Development`.</span></span>

<span data-ttu-id="4b7f4-140">La `ConfigureServices` méthode expose la possibilité d’ajouter des services à l' <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-140">The `ConfigureServices` method exposes the ability to add services to the <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="4b7f4-141">Plus tard, ces services peuvent être mis à disposition à partir de l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-141">Later, these services can be made available from dependency injection.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="4b7f4-142">Services fournis par le framework</span><span class="sxs-lookup"><span data-stu-id="4b7f4-142">Framework-provided services</span></span>

<span data-ttu-id="4b7f4-143">Les services suivants sont inscrits automatiquement :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-143">The following services are registered automatically:</span></span>

- [<span data-ttu-id="4b7f4-144">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="4b7f4-144">IHostApplicationLifetime</span></span>](#ihostapplicationlifetime)
- [<span data-ttu-id="4b7f4-145">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="4b7f4-145">IHostLifetime</span></span>](#ihostlifetime)
- [<span data-ttu-id="4b7f4-146">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="4b7f4-146">IHostEnvironment</span></span>](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a><span data-ttu-id="4b7f4-147">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="4b7f4-147">IHostApplicationLifetime</span></span>

<span data-ttu-id="4b7f4-148">Injectez le <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> service dans n’importe quelle classe pour gérer les tâches de démarrage et d’arrêt gracieuses.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-148">Inject the <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> service into any class to handle post-startup and graceful shutdown tasks.</span></span> <span data-ttu-id="4b7f4-149">Trois propriétés de l’interface sont des jetons d’annulation utilisés pour inscrire les méthodes du gestionnaire d’événements de démarrage et d’arrêt d’application.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-149">Three properties on the interface are cancellation tokens used to register app start and app stop event handler methods.</span></span> <span data-ttu-id="4b7f4-150">L’interface inclut également une méthode <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication>.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-150">The interface also includes a <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> method.</span></span>

<span data-ttu-id="4b7f4-151">L’exemple suivant est une `IHostedService` implémentation qui inscrit des `IHostApplicationLifetime` événements :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-151">The following example is an `IHostedService` implementation that registers `IHostApplicationLifetime` events:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

<span data-ttu-id="4b7f4-152">Le modèle de service Worker peut être modifié pour ajouter l' `ExampleHostedService` implémentation :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-152">The Worker Service template could be modified to add the `ExampleHostedService` implementation:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

<span data-ttu-id="4b7f4-153">L’application écrirait l’exemple de sortie suivant :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-153">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a><span data-ttu-id="4b7f4-154">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="4b7f4-154">IHostLifetime</span></span>

<span data-ttu-id="4b7f4-155">L’implémentation de <xref:Microsoft.Extensions.Hosting.IHostLifetime> contrôle quand l’hôte démarre et quand il s’arrête.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-155">The <xref:Microsoft.Extensions.Hosting.IHostLifetime> implementation controls when the host starts and when it stops.</span></span> <span data-ttu-id="4b7f4-156">La dernière implémentation inscrite est utilisée.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-156">The last implementation registered is used.</span></span>

<span data-ttu-id="4b7f4-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` est l’implémentation de `IHostLifetime` par défaut.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` is the default `IHostLifetime` implementation.</span></span> <span data-ttu-id="4b7f4-158">`ConsoleLifetime`:</span><span class="sxs-lookup"><span data-stu-id="4b7f4-158">`ConsoleLifetime`:</span></span>

- <span data-ttu-id="4b7f4-159">Écoute la <kbd>combinaison de touches Ctrl</kbd> + <kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)ou [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) et appelle <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> pour démarrer le processus d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-159">Listens for <kbd>Ctrl</kbd>+<kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT), or [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) and calls <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> to start the shutdown process.</span></span>
- <span data-ttu-id="4b7f4-160">Débloque les extensions telles que `RunAsync` et `WaitForShutdownAsync` .</span><span class="sxs-lookup"><span data-stu-id="4b7f4-160">Unblocks extensions such as `RunAsync` and `WaitForShutdownAsync`.</span></span>

## <a name="ihostenvironment"></a><span data-ttu-id="4b7f4-161">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="4b7f4-161">IHostEnvironment</span></span>

<span data-ttu-id="4b7f4-162">Injectez le <xref:Microsoft.Extensions.Hosting.IHostEnvironment> service dans une classe pour obtenir des informations sur les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-162">Inject the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> service into a class to get information about the following settings:</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a><span data-ttu-id="4b7f4-163">Configuration de l’hôte</span><span class="sxs-lookup"><span data-stu-id="4b7f4-163">Host configuration</span></span>

<span data-ttu-id="4b7f4-164">La configuration de l’hôte est utilisée pour les propriétés de l’implémentation de <xref:Microsoft.Extensions.Hosting.IHostEnvironment>.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-164">Host configuration is used for the properties of the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> implementation.</span></span>

<span data-ttu-id="4b7f4-165">La configuration de l’hôte est disponible à partir de [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) dans <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-165">Host configuration is available from [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) inside <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>.</span></span> <span data-ttu-id="4b7f4-166">Après `ConfigureAppConfiguration`, `HostBuilderContext.Configuration` est remplacé par la configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-166">After `ConfigureAppConfiguration`, `HostBuilderContext.Configuration` is replaced with the app config.</span></span>

<span data-ttu-id="4b7f4-167">Pour ajouter la configuration d’hôte, appelez <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> sur `IHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-167">To add host configuration, call <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="4b7f4-168">`ConfigureHostConfiguration` peut être appelé plusieurs fois avec des résultats additifs.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-168">`ConfigureHostConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="4b7f4-169">L’hôte utilise l’option qui définit une valeur en dernier sur une clé donnée.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-169">The host uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="4b7f4-170">L’exemple suivant crée la configuration d’hôte :</span><span class="sxs-lookup"><span data-stu-id="4b7f4-170">The following example creates host configuration:</span></span>

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="19-25":::

## <a name="app-configuration"></a><span data-ttu-id="4b7f4-171">la configuration d’une application ;</span><span class="sxs-lookup"><span data-stu-id="4b7f4-171">App configuration</span></span>

<span data-ttu-id="4b7f4-172">La configuration d’application est créée en appelant <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> sur `IHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-172">App configuration is created by calling <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="4b7f4-173">`ConfigureAppConfiguration` peut être appelé plusieurs fois avec des résultats additifs.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-173">`ConfigureAppConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="4b7f4-174">L’application utilise l’option qui définit une valeur en dernier sur une clé donnée.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-174">The app uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="4b7f4-175">La configuration créée par `ConfigureAppConfiguration` est disponible dans [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) pour les opérations suivantes et en tant que service à partir de l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-175">The configuration created by `ConfigureAppConfiguration` is available at [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) for subsequent operations and as a service from DI.</span></span> <span data-ttu-id="4b7f4-176">La configuration d’hôte est également ajoutée à la configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="4b7f4-176">The host configuration is also added to the app configuration.</span></span>

<span data-ttu-id="4b7f4-177">Pour plus d’informations, consultez [configuration dans .net](configuration.md).</span><span class="sxs-lookup"><span data-stu-id="4b7f4-177">For more information, see [Configuration in .NET](configuration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4b7f4-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b7f4-178">See also</span></span>

- [<span data-ttu-id="4b7f4-179">Configuration dans .NET</span><span class="sxs-lookup"><span data-stu-id="4b7f4-179">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="4b7f4-180">Hôte web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4b7f4-180">ASP.NET Core Web Host</span></span>](/aspnet/core/fundamentals/host/web-host)
- <span data-ttu-id="4b7f4-181">Les bogues d’hôte générique doivent être créés dans [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) référentiel</span><span class="sxs-lookup"><span data-stu-id="4b7f4-181">Generic host bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
