---
title: Fournisseurs de journalisation dans .NET
description: Découvrez comment l’API du fournisseur de journalisation est utilisée dans les applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.openlocfilehash: 96a5ece10068e39c991e67a36f22e725d6380af5
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91755886"
---
# <a name="logging-providers-in-net"></a><span data-ttu-id="cb6cf-103">Fournisseurs de journalisation dans .NET</span><span class="sxs-lookup"><span data-stu-id="cb6cf-103">Logging providers in .NET</span></span>

<span data-ttu-id="cb6cf-104">Les fournisseurs de journalisation conservent les journaux, à l’exception du `Console` fournisseur qui affiche uniquement les journaux en tant que sortie standard.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-104">Logging providers persist logs, except for the `Console` provider, which only displays logs as standard output.</span></span> <span data-ttu-id="cb6cf-105">Par exemple, le fournisseur Azure Application Insights stocke les journaux dans Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-105">For example, the Azure Application Insights provider stores logs in Azure Application Insights.</span></span> <span data-ttu-id="cb6cf-106">Plusieurs fournisseurs peuvent être activés.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-106">Multiple providers can be enabled.</span></span>

<span data-ttu-id="cb6cf-107">Les modèles d’application de travail .NET par défaut :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-107">The default .NET Worker app templates:</span></span>

- <span data-ttu-id="cb6cf-108">Utilisez l' [hôte générique](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-108">Use the [Generic Host](generic-host.md).</span></span>
- <span data-ttu-id="cb6cf-109">Appelez <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> , qui ajoute les fournisseurs de journalisation suivants :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-109">Call <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>, which adds the following logging providers:</span></span>
  - [<span data-ttu-id="cb6cf-110">Console</span><span class="sxs-lookup"><span data-stu-id="cb6cf-110">Console</span></span>](#console)
  - [<span data-ttu-id="cb6cf-111">Déboguer</span><span class="sxs-lookup"><span data-stu-id="cb6cf-111">Debug</span></span>](#debug)
  - [<span data-ttu-id="cb6cf-112">EventSource</span><span class="sxs-lookup"><span data-stu-id="cb6cf-112">EventSource</span></span>](#event-source)
  - <span data-ttu-id="cb6cf-113">[EventLog](#windows-eventlog): Windows uniquement</span><span class="sxs-lookup"><span data-stu-id="cb6cf-113">[EventLog](#windows-eventlog): Windows only</span></span>

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

<span data-ttu-id="cb6cf-114">Le code précédent montre la `Program` classe créée avec les modèles d’application de travail .net.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-114">The preceding code shows the `Program` class created with the .NET Worker app templates.</span></span> <span data-ttu-id="cb6cf-115">Les sections suivantes fournissent des exemples basés sur les modèles d’application de travail .NET, qui utilisent l’hôte générique.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-115">The next several sections provide samples based on the .NET Worker app templates, which use the Generic Host.</span></span>

<span data-ttu-id="cb6cf-116">Pour remplacer l’ensemble par défaut des fournisseurs de journalisation ajoutés par `Host.CreateDefaultBuilder` , appelez `ClearProviders` et ajoutez les fournisseurs de journalisation souhaités.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-116">To override the default set of logging providers added by `Host.CreateDefaultBuilder`, call `ClearProviders` and add the logging providers you want.</span></span> <span data-ttu-id="cb6cf-117">Par exemple, le code suivant :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-117">For example, the following code:</span></span>

- <span data-ttu-id="cb6cf-118">Appelle <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> pour supprimer toutes les <xref:Microsoft.Extensions.Logging.ILoggerProvider> instances du générateur.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-118">Calls <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> to remove all the <xref:Microsoft.Extensions.Logging.ILoggerProvider> instances from the builder.</span></span>
- <span data-ttu-id="cb6cf-119">Ajoute le fournisseur de journalisation de la [console](#console) .</span><span class="sxs-lookup"><span data-stu-id="cb6cf-119">Adds the [Console](#console) logging provider.</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

<span data-ttu-id="cb6cf-120">Pour obtenir des fournisseurs supplémentaires, consultez :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-120">For additional providers, see:</span></span>

- <span data-ttu-id="cb6cf-121">[Fournisseurs de journalisation intégrés](#built-in-logging-providers).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-121">[Built-in logging providers](#built-in-logging-providers).</span></span>
- <span data-ttu-id="cb6cf-122">[Fournisseurs de journalisation tiers](#third-party-logging-providers).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-122">[Third-party logging providers](#third-party-logging-providers).</span></span>

## <a name="configure-a-service-that-depends-on-ilogger"></a><span data-ttu-id="cb6cf-123">Configurer un service qui dépend de ILogger</span><span class="sxs-lookup"><span data-stu-id="cb6cf-123">Configure a service that depends on ILogger</span></span>

<span data-ttu-id="cb6cf-124">Pour configurer un service qui dépend de `ILogger<T>` , utilisez l’injection de constructeur ou fournissez une méthode de fabrique.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-124">To configure a service that depends on `ILogger<T>`, use constructor injection or provide a factory method.</span></span> <span data-ttu-id="cb6cf-125">L’approche de la méthode de fabrique est recommandée uniquement s’il n’y a aucune autre option.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-125">The factory method approach is recommended only if there is no other option.</span></span> <span data-ttu-id="cb6cf-126">Par exemple, considérez un service qui a besoin d’une `ILogger<T>` instance fournie par di :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-126">For example, consider a service that needs an `ILogger<T>` instance provided by DI:</span></span>

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

<span data-ttu-id="cb6cf-127">Le code précédent est un [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) qui s’exécute la première fois que le conteneur di doit construire une instance de `IExampleService` .</span><span class="sxs-lookup"><span data-stu-id="cb6cf-127">The preceding code is a [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) that runs the first time the DI container needs to construct an instance of `IExampleService`.</span></span> <span data-ttu-id="cb6cf-128">Vous pouvez accéder à tous les services inscrits de cette manière.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-128">You can access any of the registered services in this way.</span></span>

## <a name="built-in-logging-providers"></a><span data-ttu-id="cb6cf-129">Fournisseurs de journalisation intégrés</span><span class="sxs-lookup"><span data-stu-id="cb6cf-129">Built-in logging providers</span></span>

<span data-ttu-id="cb6cf-130">Les extensions Microsoft incluent les fournisseurs de journalisation suivants dans le cadre des bibliothèques Runtime :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-130">Microsoft Extensions include the following logging providers as part of the runtime libraries:</span></span>

- [<span data-ttu-id="cb6cf-131">Console</span><span class="sxs-lookup"><span data-stu-id="cb6cf-131">Console</span></span>](#console)
- [<span data-ttu-id="cb6cf-132">Déboguer</span><span class="sxs-lookup"><span data-stu-id="cb6cf-132">Debug</span></span>](#debug)
- [<span data-ttu-id="cb6cf-133">EventSource</span><span class="sxs-lookup"><span data-stu-id="cb6cf-133">EventSource</span></span>](#event-source)
- [<span data-ttu-id="cb6cf-134">EventLog</span><span class="sxs-lookup"><span data-stu-id="cb6cf-134">EventLog</span></span>](#windows-eventlog)

<span data-ttu-id="cb6cf-135">Les fournisseurs de journalisation suivants sont fournis par Microsoft, mais pas dans le cadre des bibliothèques Runtime.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-135">The following logging providers are shipped by Microsoft, but not as part of the runtime libraries.</span></span> <span data-ttu-id="cb6cf-136">Ils doivent être installés en tant que packages NuGet supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-136">They must be installed as additional NuGet packages.</span></span>

- [<span data-ttu-id="cb6cf-137">AzureAppServicesFile et AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="cb6cf-137">AzureAppServicesFile and AzureAppServicesBlob</span></span>](#azure-app-service)
- [<span data-ttu-id="cb6cf-138">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="cb6cf-138">ApplicationInsights</span></span>](#azure-application-insights)

### <a name="console"></a><span data-ttu-id="cb6cf-139">Console</span><span class="sxs-lookup"><span data-stu-id="cb6cf-139">Console</span></span>

<span data-ttu-id="cb6cf-140">Le `Console` fournisseur journalise la sortie dans la console.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-140">The `Console` provider logs output to the console.</span></span>

### <a name="debug"></a><span data-ttu-id="cb6cf-141">Débogage</span><span class="sxs-lookup"><span data-stu-id="cb6cf-141">Debug</span></span>

<span data-ttu-id="cb6cf-142">Le `Debug` fournisseur écrit la sortie du journal à l’aide de la classe [System. Diagnostics. Debug](/dotnet/api/system.diagnostics.debug) .</span><span class="sxs-lookup"><span data-stu-id="cb6cf-142">The `Debug` provider writes log output by using the [System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug) class.</span></span> <span data-ttu-id="cb6cf-143">Appelle pour `System.Diagnostics.Debug.WriteLine` écrire dans le `Debug` fournisseur.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-143">Calls to `System.Diagnostics.Debug.WriteLine` write to the `Debug` provider.</span></span>

<span data-ttu-id="cb6cf-144">Sur Linux, l' `Debug` emplacement du journal du fournisseur est dépendant de la distribution et peut être l’un des suivants :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-144">On Linux, the `Debug` provider log location is distribution-dependent and may be one of the following:</span></span>

- <span data-ttu-id="cb6cf-145">*/var/log/message*</span><span class="sxs-lookup"><span data-stu-id="cb6cf-145">*/var/log/message*</span></span>
- <span data-ttu-id="cb6cf-146">*/var/log/syslog*</span><span class="sxs-lookup"><span data-stu-id="cb6cf-146">*/var/log/syslog*</span></span>

### <a name="event-source"></a><span data-ttu-id="cb6cf-147">Source de l’événement</span><span class="sxs-lookup"><span data-stu-id="cb6cf-147">Event Source</span></span>

<span data-ttu-id="cb6cf-148">Le `EventSource` fournisseur écrit dans une source d’événements multiplateforme portant le nom `Microsoft-Extensions-Logging` .</span><span class="sxs-lookup"><span data-stu-id="cb6cf-148">The `EventSource` provider writes to a cross-platform event source with the name `Microsoft-Extensions-Logging`.</span></span> <span data-ttu-id="cb6cf-149">Sur Windows, le fournisseur utilise [ETW](/windows/win32/etw/event-tracing-portal).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-149">On Windows, the provider uses [ETW](/windows/win32/etw/event-tracing-portal).</span></span>

#### <a name="dotnet-trace-tooling"></a><span data-ttu-id="cb6cf-150">outils de trace dotnet</span><span class="sxs-lookup"><span data-stu-id="cb6cf-150">dotnet trace tooling</span></span>

<span data-ttu-id="cb6cf-151">L’outil [dotnet-trace](../diagnostics/dotnet-trace.md) est un outil global de l’interface CLI multiplateforme qui permet la collecte des traces .net core d’un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-151">The [dotnet-trace](../diagnostics/dotnet-trace.md) tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process.</span></span> <span data-ttu-id="cb6cf-152">L’outil collecte les <xref:Microsoft.Extensions.Logging.EventSource> données du fournisseur à l’aide d’un <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> .</span><span class="sxs-lookup"><span data-stu-id="cb6cf-152">The tool collects <xref:Microsoft.Extensions.Logging.EventSource> provider data using a <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource>.</span></span>

<span data-ttu-id="cb6cf-153">Consultez [dotnet-trace](../diagnostics/dotnet-trace.md) pour obtenir des instructions d’installation.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-153">See [dotnet-trace](../diagnostics/dotnet-trace.md) for installation instructions.</span></span> <span data-ttu-id="cb6cf-154">Pour obtenir un didacticiel de diagnostic utilisant `dotnet-trace` , consultez [déboguer l’utilisation élevée du processeur dans .net Core](/../diagnostics/debug-highcpu.md).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-154">For a diagnostic tutorial using `dotnet-trace`, see [Debug high CPU usage in .NET Core](/../diagnostics/debug-highcpu.md).</span></span>

### <a name="windows-eventlog"></a><span data-ttu-id="cb6cf-155">Journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="cb6cf-155">Windows EventLog</span></span>

<span data-ttu-id="cb6cf-156">Le `EventLog` fournisseur envoie la sortie de journal dans le journal des événements Windows.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-156">The `EventLog` provider sends log output to the Windows Event Log.</span></span> <span data-ttu-id="cb6cf-157">Contrairement aux autres fournisseurs, le `EventLog` fournisseur n’hérite ***pas*** des paramètres non-fournisseur par défaut.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-157">Unlike the other providers, the `EventLog` provider does ***not*** inherit the default non-provider settings.</span></span> <span data-ttu-id="cb6cf-158">Si `EventLog` les paramètres du journal ne sont pas spécifiés, leur valeur par défaut est `LogLevel.Warning` .</span><span class="sxs-lookup"><span data-stu-id="cb6cf-158">If `EventLog` log settings aren't specified, they default to `LogLevel.Warning`.</span></span>

<span data-ttu-id="cb6cf-159">Pour consigner les événements inférieurs à <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> , définissez explicitement le niveau de journalisation.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-159">To log events lower than <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType>, explicitly set the log level.</span></span> <span data-ttu-id="cb6cf-160">L’exemple suivant définit le niveau de journalisation par défaut du journal des événements sur <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-160">The following example sets the Event Log default log level to <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType>:</span></span>

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

<span data-ttu-id="cb6cf-161">Les [surcharges AddEventLog](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) peuvent passer <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> .</span><span class="sxs-lookup"><span data-stu-id="cb6cf-161">[AddEventLog overloads](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) can pass in <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings>.</span></span> <span data-ttu-id="cb6cf-162">Si `null` ou n’est pas spécifié, les paramètres par défaut suivants sont utilisés :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-162">If `null` or not specified, the following default settings are used:</span></span>

- <span data-ttu-id="cb6cf-163">`LogName`: « Application »</span><span class="sxs-lookup"><span data-stu-id="cb6cf-163">`LogName`: "Application"</span></span>
- <span data-ttu-id="cb6cf-164">`SourceName`: « .NET Runtime »</span><span class="sxs-lookup"><span data-stu-id="cb6cf-164">`SourceName`: ".NET Runtime"</span></span>
- <span data-ttu-id="cb6cf-165">`MachineName`: Le nom de l’ordinateur local est utilisé.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-165">`MachineName`: The local machine name is used.</span></span>

<span data-ttu-id="cb6cf-166">Le code suivant remplace la `SourceName` valeur par défaut de par `".NET Runtime"` `CustomLogs` :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-166">The following code changes the `SourceName` from the default value of `".NET Runtime"` to `CustomLogs`:</span></span>

```csharp
public class Program
{
    public static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddEventLog(configuration =>
                    configuration.SourceName = "CustomLogs"));
}
```

### <a name="azure-app-service"></a><span data-ttu-id="cb6cf-167">Azure App Service</span><span class="sxs-lookup"><span data-stu-id="cb6cf-167">Azure App Service</span></span>

<span data-ttu-id="cb6cf-168">Le package de fournisseur [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) écrit les enregistrements de journal dans des fichiers texte dans le système de fichiers d’une application Azure App Service, et dans un [stockage Blob](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) dans un compte de stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-168">The [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) provider package writes logs to text files in an Azure App Service app's file system and to [blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) in an Azure Storage account.</span></span>

<span data-ttu-id="cb6cf-169">Le package du fournisseur n’est pas inclus dans les bibliothèques Runtime.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-169">The provider package isn't included in the runtime libraries.</span></span> <span data-ttu-id="cb6cf-170">Pour utiliser le fournisseur, ajoutez le package du fournisseur au projet.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-170">To use the provider, add the provider package to the project.</span></span>

<span data-ttu-id="cb6cf-171">Pour configurer les paramètres du fournisseur, utilisez <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> et <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, comme illustré dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-171">To configure provider settings, use <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> and <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, as shown in the following example:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddAzureWebAppDiagnostics())
            .ConfigureServices(services =>
                services.Configure<AzureFileLoggerOptions>(options =>
                {
                    options.FileName = "azure-diagnostics-";
                    options.FileSizeLimit = 50 * 1024;
                    options.RetainedFileCountLimit = 5;
                })
                .Configure<AzureBlobLoggerOptions>(options =>
                {
                    options.BlobName = "log.txt";
                }));
}
```

<span data-ttu-id="cb6cf-172">Lors du déploiement sur Azure App Service, l’application utilise les paramètres de la section [app service les journaux](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) de la page **app service** du portail Azure.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-172">When deployed to Azure App Service, the app uses the settings in the [App Service logs](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) section of the **App Service** page of the Azure portal.</span></span> <span data-ttu-id="cb6cf-173">Quand les paramètres suivants sont mis à jour, les changements prennent effet immédiatement sans avoir besoin de redémarrer ou redéployer l’application.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-173">When the following settings are updated, the changes take effect immediately without requiring a restart or redeployment of the app.</span></span>

- <span data-ttu-id="cb6cf-174">**Journalisation des applications (système de fichiers)**</span><span class="sxs-lookup"><span data-stu-id="cb6cf-174">**Application Logging (Filesystem)**</span></span>
- <span data-ttu-id="cb6cf-175">**Journalisation des applications (objet blob)**</span><span class="sxs-lookup"><span data-stu-id="cb6cf-175">**Application Logging (Blob)**</span></span>

<span data-ttu-id="cb6cf-176">L’emplacement par défaut des fichiers journaux est le dossier *D:\\racine\\LogFiles\\Application*, et le nom de fichier par défaut est *diagnostics-aaaammjj.txt*.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-176">The default location for log files is in the *D:\\home\\LogFiles\\Application* folder, and the default file name is *diagnostics-yyyymmdd.txt*.</span></span> <span data-ttu-id="cb6cf-177">La limite de taille de fichier par défaut est de 10 Mo, et le nombre maximal de fichiers conservés par défaut est de 2.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-177">The default file size limit is 10 MB, and the default maximum number of files retained is 2.</span></span> <span data-ttu-id="cb6cf-178">Le nom par défaut du blob est *{app-name}{timestamp}/aaaa/mm/jj/hh/{guid}-applicationLog.txt*.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-178">The default blob name is *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*.</span></span>

<span data-ttu-id="cb6cf-179">Ce fournisseur se connecte uniquement lorsque le projet s’exécute dans l’environnement Azure.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-179">This provider only logs when the project runs in the Azure environment.</span></span>

#### <a name="azure-log-streaming"></a><span data-ttu-id="cb6cf-180">Streaming des journaux Azure</span><span class="sxs-lookup"><span data-stu-id="cb6cf-180">Azure log streaming</span></span>

<span data-ttu-id="cb6cf-181">Azure log streaming prend en charge l’affichage de l’activité des journaux en temps réel à partir de :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-181">Azure log streaming supports viewing log activity in real time from:</span></span>

- <span data-ttu-id="cb6cf-182">Serveur d'applications</span><span class="sxs-lookup"><span data-stu-id="cb6cf-182">The app server</span></span>
- <span data-ttu-id="cb6cf-183">Serveur web</span><span class="sxs-lookup"><span data-stu-id="cb6cf-183">The web server</span></span>
- <span data-ttu-id="cb6cf-184">Suivi des demandes ayant échoué</span><span class="sxs-lookup"><span data-stu-id="cb6cf-184">Failed request tracing</span></span>

<span data-ttu-id="cb6cf-185">Pour configurer le streaming des journaux Azure :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-185">To configure Azure log streaming:</span></span>

- <span data-ttu-id="cb6cf-186">Accédez à la page **journaux App service** à partir de la page du portail de l’application.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-186">Navigate to the **App Service logs** page from the app's portal page.</span></span>
- <span data-ttu-id="cb6cf-187">Définissez **Journal des applications (Système de fichiers)** sur **Activé**.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-187">Set **Application Logging (Filesystem)** to **On**.</span></span>
- <span data-ttu-id="cb6cf-188">Choisissez le **niveau** du journal.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-188">Choose the log **Level**.</span></span> <span data-ttu-id="cb6cf-189">Ce paramètre s’applique uniquement à la diffusion en continu de journaux Azure.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-189">This setting only applies to Azure log streaming.</span></span>

<span data-ttu-id="cb6cf-190">Accédez à la page **flux de journal** pour afficher les journaux.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-190">Navigate to the **Log Stream** page to view logs.</span></span> <span data-ttu-id="cb6cf-191">Les messages journalisés sont enregistrés avec l' `ILogger` interface.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-191">The logged messages are logged with the `ILogger` interface.</span></span>

### <a name="azure-application-insights"></a><span data-ttu-id="cb6cf-192">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="cb6cf-192">Azure Application Insights</span></span>

<span data-ttu-id="cb6cf-193">Le package du fournisseur [Microsoft. extensions. Logging. ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) écrit les journaux dans [Azure application Insights](/azure/azure-monitor/app/cloudservices).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-193">The [Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) provider package writes logs to [Azure Application Insights](/azure/azure-monitor/app/cloudservices).</span></span> <span data-ttu-id="cb6cf-194">Application Insights est un service qui surveille une application web et fournit des outils pour interroger et analyser les données de télémétrie.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-194">Application Insights is a service that monitors a web app and provides tools for querying and analyzing the telemetry data.</span></span> <span data-ttu-id="cb6cf-195">Si vous utilisez ce fournisseur, vous pouvez interroger et analyser vos journaux à l’aide des outils Application Insights.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-195">If you use this provider, you can query and analyze your logs by using the Application Insights tools.</span></span>

<span data-ttu-id="cb6cf-196">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-196">For more information, see the following resources:</span></span>

- [<span data-ttu-id="cb6cf-197">Vue d’ensemble d’Application Insights</span><span class="sxs-lookup"><span data-stu-id="cb6cf-197">Application Insights overview</span></span>](/azure/application-insights/app-insights-overview)
- <span data-ttu-id="cb6cf-198">[Journaux ApplicationInsightsLoggerProvider pour .NET Core ILogger](/azure/azure-monitor/app/ilogger) : commencez ici si vous souhaitez implémenter le fournisseur de journalisation sans le reste des données de télémétrie Application Insights.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-198">[ApplicationInsightsLoggerProvider for .NET Core ILogger logs](/azure/azure-monitor/app/ilogger) - Start here if you want to implement the logging provider without the rest of Application Insights telemetry.</span></span>
- <span data-ttu-id="cb6cf-199">[Adaptateurs de journalisation Application Insights](/azure/azure-monitor/app/asp-net-trace-logs).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-199">[Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs).</span></span>
- <span data-ttu-id="cb6cf-200">[Installer, configurer et initialiser le kit de développement logiciel (SDK) Application Insights](/learn/modules/instrument-web-app-code-with-application-insights) : tutoriel interactif sur le site Microsoft Learn.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-200">[Install, configure, and initialize the Application Insights SDK](/learn/modules/instrument-web-app-code-with-application-insights) - Interactive tutorial on the Microsoft Learn site.</span></span>

## <a name="third-party-logging-providers"></a><span data-ttu-id="cb6cf-201">Fournisseurs de journalisation tiers</span><span class="sxs-lookup"><span data-stu-id="cb6cf-201">Third-party logging providers</span></span>

<span data-ttu-id="cb6cf-202">Voici quelques frameworks de journalisation tiers qui fonctionnent avec différentes charges de travail .NET :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-202">Here are some third-party logging frameworks that work with various .NET workloads:</span></span>

- <span data-ttu-id="cb6cf-203">[elmah.io](https://elmah.io) ([dépôt GitHub](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-203">[elmah.io](https://elmah.io) ([GitHub repo](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span></span>
- <span data-ttu-id="cb6cf-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([Dépôt GitHub](https://github.com/mattwcole/gelf-extensions-logging))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub repo](https://github.com/mattwcole/gelf-extensions-logging))</span></span>
- <span data-ttu-id="cb6cf-205">[JSNLog](http://jsnlog.com) ([dépôt GitHub](https://github.com/mperdeck/jsnlog))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-205">[JSNLog](http://jsnlog.com) ([GitHub repo](https://github.com/mperdeck/jsnlog))</span></span>
- <span data-ttu-id="cb6cf-206">[KissLog.net](https://kisslog.net) ([référentiel GitHub](https://github.com/catalingavan/KissLog-net))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-206">[KissLog.net](https://kisslog.net) ([GitHub repo](https://github.com/catalingavan/KissLog-net))</span></span>
- <span data-ttu-id="cb6cf-207">[Log4net](https://logging.apache.org/log4net) ([GitHub référentiel](https://github.com/apache/logging-log4net))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-207">[Log4Net](https://logging.apache.org/log4net) ([GitHub repo](https://github.com/apache/logging-log4net))</span></span>
- <span data-ttu-id="cb6cf-208">[Loggr](https://loggr.net) ([dépôt GitHub](https://github.com/imobile3/Loggr.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-208">[Loggr](https://loggr.net) ([GitHub repo](https://github.com/imobile3/Loggr.Extensions.Logging))</span></span>
- <span data-ttu-id="cb6cf-209">[NLog](https://nlog-project.org) ([dépôt GitHub](https://github.com/NLog/NLog.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-209">[NLog](https://nlog-project.org) ([GitHub repo](https://github.com/NLog/NLog.Extensions.Logging))</span></span>
- <span data-ttu-id="cb6cf-210">[Sentry](https://sentry.io/welcome) ([dépôt GitHub](https://github.com/getsentry/sentry-dotnet))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-210">[Sentry](https://sentry.io/welcome) ([GitHub repo](https://github.com/getsentry/sentry-dotnet))</span></span>
- <span data-ttu-id="cb6cf-211">[Serilog](https://serilog.net) ([dépôt GitHub](https://github.com/serilog/serilog-sinks-console))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-211">[Serilog](https://serilog.net) ([GitHub repo](https://github.com/serilog/serilog-sinks-console))</span></span>
- <span data-ttu-id="cb6cf-212">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub référentiel](https://github.com/googleapis/google-cloud-dotnet))</span><span class="sxs-lookup"><span data-stu-id="cb6cf-212">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub repo](https://github.com/googleapis/google-cloud-dotnet))</span></span>

<span data-ttu-id="cb6cf-213">Certains frameworks tiers prennent en charge la [journalisation sémantique, également appelée journalisation structurée](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-213">Some third-party frameworks can perform [semantic logging, also known as structured logging](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span></span>

<span data-ttu-id="cb6cf-214">L’utilisation d’un framework tiers est semblable à l’utilisation des fournisseurs intégrés :</span><span class="sxs-lookup"><span data-stu-id="cb6cf-214">Using a third-party framework is similar to using one of the built-in providers:</span></span>

1. <span data-ttu-id="cb6cf-215">Ajoutez un package NuGet à votre projet.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-215">Add a NuGet package to your project.</span></span>
1. <span data-ttu-id="cb6cf-216">Appeler une `ILoggerFactory` `ILoggingBuilder` méthode d’extension ou fournie par le Framework de journalisation.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-216">Call an `ILoggerFactory` or `ILoggingBuilder` extension method provided by the logging framework.</span></span>

<span data-ttu-id="cb6cf-217">Pour plus d’informations, consultez la documentation de chaque fournisseur.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-217">For more information, see each provider's documentation.</span></span> <span data-ttu-id="cb6cf-218">Les fournisseurs de journalisation tiers ne sont pas pris en charge par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cb6cf-218">Third-party logging providers aren't supported by Microsoft.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb6cf-219">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb6cf-219">See also</span></span>

- <span data-ttu-id="cb6cf-220">[Journalisation dans .net](logging.md).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-220">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="cb6cf-221">[Implémentez un fournisseur de journalisation personnalisé dans .net](custom-logging-provider.md).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-221">[Implement a custom logging provider in .NET](custom-logging-provider.md).</span></span>
- <span data-ttu-id="cb6cf-222">[Journalisation hautes performances dans .net](high-performance-logging.md).</span><span class="sxs-lookup"><span data-stu-id="cb6cf-222">[High-performance logging in .NET](high-performance-logging.md).</span></span>
