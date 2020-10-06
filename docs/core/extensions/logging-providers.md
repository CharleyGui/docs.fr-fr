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
# <a name="logging-providers-in-net"></a>Fournisseurs de journalisation dans .NET

Les fournisseurs de journalisation conservent les journaux, à l’exception du `Console` fournisseur qui affiche uniquement les journaux en tant que sortie standard. Par exemple, le fournisseur Azure Application Insights stocke les journaux dans Azure Application Insights. Plusieurs fournisseurs peuvent être activés.

Les modèles d’application de travail .NET par défaut :

- Utilisez l' [hôte générique](generic-host.md).
- Appelez <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> , qui ajoute les fournisseurs de journalisation suivants :
  - [Console](#console)
  - [Déboguer](#debug)
  - [EventSource](#event-source)
  - [EventLog](#windows-eventlog): Windows uniquement

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

Le code précédent montre la `Program` classe créée avec les modèles d’application de travail .net. Les sections suivantes fournissent des exemples basés sur les modèles d’application de travail .NET, qui utilisent l’hôte générique.

Pour remplacer l’ensemble par défaut des fournisseurs de journalisation ajoutés par `Host.CreateDefaultBuilder` , appelez `ClearProviders` et ajoutez les fournisseurs de journalisation souhaités. Par exemple, le code suivant :

- Appelle <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> pour supprimer toutes les <xref:Microsoft.Extensions.Logging.ILoggerProvider> instances du générateur.
- Ajoute le fournisseur de journalisation de la [console](#console) .

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

Pour obtenir des fournisseurs supplémentaires, consultez :

- [Fournisseurs de journalisation intégrés](#built-in-logging-providers).
- [Fournisseurs de journalisation tiers](#third-party-logging-providers).

## <a name="configure-a-service-that-depends-on-ilogger"></a>Configurer un service qui dépend de ILogger

Pour configurer un service qui dépend de `ILogger<T>` , utilisez l’injection de constructeur ou fournissez une méthode de fabrique. L’approche de la méthode de fabrique est recommandée uniquement s’il n’y a aucune autre option. Par exemple, considérez un service qui a besoin d’une `ILogger<T>` instance fournie par di :

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

Le code précédent est un [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) qui s’exécute la première fois que le conteneur di doit construire une instance de `IExampleService` . Vous pouvez accéder à tous les services inscrits de cette manière.

## <a name="built-in-logging-providers"></a>Fournisseurs de journalisation intégrés

Les extensions Microsoft incluent les fournisseurs de journalisation suivants dans le cadre des bibliothèques Runtime :

- [Console](#console)
- [Déboguer](#debug)
- [EventSource](#event-source)
- [EventLog](#windows-eventlog)

Les fournisseurs de journalisation suivants sont fournis par Microsoft, mais pas dans le cadre des bibliothèques Runtime. Ils doivent être installés en tant que packages NuGet supplémentaires.

- [AzureAppServicesFile et AzureAppServicesBlob](#azure-app-service)
- [ApplicationInsights](#azure-application-insights)

### <a name="console"></a>Console

Le `Console` fournisseur journalise la sortie dans la console.

### <a name="debug"></a>Débogage

Le `Debug` fournisseur écrit la sortie du journal à l’aide de la classe [System. Diagnostics. Debug](/dotnet/api/system.diagnostics.debug) . Appelle pour `System.Diagnostics.Debug.WriteLine` écrire dans le `Debug` fournisseur.

Sur Linux, l' `Debug` emplacement du journal du fournisseur est dépendant de la distribution et peut être l’un des suivants :

- */var/log/message*
- */var/log/syslog*

### <a name="event-source"></a>Source de l’événement

Le `EventSource` fournisseur écrit dans une source d’événements multiplateforme portant le nom `Microsoft-Extensions-Logging` . Sur Windows, le fournisseur utilise [ETW](/windows/win32/etw/event-tracing-portal).

#### <a name="dotnet-trace-tooling"></a>outils de trace dotnet

L’outil [dotnet-trace](../diagnostics/dotnet-trace.md) est un outil global de l’interface CLI multiplateforme qui permet la collecte des traces .net core d’un processus en cours d’exécution. L’outil collecte les <xref:Microsoft.Extensions.Logging.EventSource> données du fournisseur à l’aide d’un <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> .

Consultez [dotnet-trace](../diagnostics/dotnet-trace.md) pour obtenir des instructions d’installation. Pour obtenir un didacticiel de diagnostic utilisant `dotnet-trace` , consultez [déboguer l’utilisation élevée du processeur dans .net Core](/../diagnostics/debug-highcpu.md).

### <a name="windows-eventlog"></a>Journal des événements Windows

Le `EventLog` fournisseur envoie la sortie de journal dans le journal des événements Windows. Contrairement aux autres fournisseurs, le `EventLog` fournisseur n’hérite ***pas*** des paramètres non-fournisseur par défaut. Si `EventLog` les paramètres du journal ne sont pas spécifiés, leur valeur par défaut est `LogLevel.Warning` .

Pour consigner les événements inférieurs à <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> , définissez explicitement le niveau de journalisation. L’exemple suivant définit le niveau de journalisation par défaut du journal des événements sur <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> :

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

Les [surcharges AddEventLog](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) peuvent passer <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> . Si `null` ou n’est pas spécifié, les paramètres par défaut suivants sont utilisés :

- `LogName`: « Application »
- `SourceName`: « .NET Runtime »
- `MachineName`: Le nom de l’ordinateur local est utilisé.

Le code suivant remplace la `SourceName` valeur par défaut de par `".NET Runtime"` `CustomLogs` :

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

### <a name="azure-app-service"></a>Azure App Service

Le package de fournisseur [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) écrit les enregistrements de journal dans des fichiers texte dans le système de fichiers d’une application Azure App Service, et dans un [stockage Blob](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) dans un compte de stockage Azure.

Le package du fournisseur n’est pas inclus dans les bibliothèques Runtime. Pour utiliser le fournisseur, ajoutez le package du fournisseur au projet.

Pour configurer les paramètres du fournisseur, utilisez <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> et <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, comme illustré dans l’exemple suivant :

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

Lors du déploiement sur Azure App Service, l’application utilise les paramètres de la section [app service les journaux](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) de la page **app service** du portail Azure. Quand les paramètres suivants sont mis à jour, les changements prennent effet immédiatement sans avoir besoin de redémarrer ou redéployer l’application.

- **Journalisation des applications (système de fichiers)**
- **Journalisation des applications (objet blob)**

L’emplacement par défaut des fichiers journaux est le dossier *D:\\racine\\LogFiles\\Application*, et le nom de fichier par défaut est *diagnostics-aaaammjj.txt*. La limite de taille de fichier par défaut est de 10 Mo, et le nombre maximal de fichiers conservés par défaut est de 2. Le nom par défaut du blob est *{app-name}{timestamp}/aaaa/mm/jj/hh/{guid}-applicationLog.txt*.

Ce fournisseur se connecte uniquement lorsque le projet s’exécute dans l’environnement Azure.

#### <a name="azure-log-streaming"></a>Streaming des journaux Azure

Azure log streaming prend en charge l’affichage de l’activité des journaux en temps réel à partir de :

- Serveur d'applications
- Serveur web
- Suivi des demandes ayant échoué

Pour configurer le streaming des journaux Azure :

- Accédez à la page **journaux App service** à partir de la page du portail de l’application.
- Définissez **Journal des applications (Système de fichiers)** sur **Activé**.
- Choisissez le **niveau** du journal. Ce paramètre s’applique uniquement à la diffusion en continu de journaux Azure.

Accédez à la page **flux de journal** pour afficher les journaux. Les messages journalisés sont enregistrés avec l' `ILogger` interface.

### <a name="azure-application-insights"></a>Azure Application Insights

Le package du fournisseur [Microsoft. extensions. Logging. ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) écrit les journaux dans [Azure application Insights](/azure/azure-monitor/app/cloudservices). Application Insights est un service qui surveille une application web et fournit des outils pour interroger et analyser les données de télémétrie. Si vous utilisez ce fournisseur, vous pouvez interroger et analyser vos journaux à l’aide des outils Application Insights.

Pour plus d’informations, consultez les ressources suivantes :

- [Vue d’ensemble d’Application Insights](/azure/application-insights/app-insights-overview)
- [Journaux ApplicationInsightsLoggerProvider pour .NET Core ILogger](/azure/azure-monitor/app/ilogger) : commencez ici si vous souhaitez implémenter le fournisseur de journalisation sans le reste des données de télémétrie Application Insights.
- [Adaptateurs de journalisation Application Insights](/azure/azure-monitor/app/asp-net-trace-logs).
- [Installer, configurer et initialiser le kit de développement logiciel (SDK) Application Insights](/learn/modules/instrument-web-app-code-with-application-insights) : tutoriel interactif sur le site Microsoft Learn.

## <a name="third-party-logging-providers"></a>Fournisseurs de journalisation tiers

Voici quelques frameworks de journalisation tiers qui fonctionnent avec différentes charges de travail .NET :

- [elmah.io](https://elmah.io) ([dépôt GitHub](https://github.com/elmahio/Elmah.Io.Extensions.Logging))
- [Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([Dépôt GitHub](https://github.com/mattwcole/gelf-extensions-logging))
- [JSNLog](http://jsnlog.com) ([dépôt GitHub](https://github.com/mperdeck/jsnlog))
- [KissLog.net](https://kisslog.net) ([référentiel GitHub](https://github.com/catalingavan/KissLog-net))
- [Log4net](https://logging.apache.org/log4net) ([GitHub référentiel](https://github.com/apache/logging-log4net))
- [Loggr](https://loggr.net) ([dépôt GitHub](https://github.com/imobile3/Loggr.Extensions.Logging))
- [NLog](https://nlog-project.org) ([dépôt GitHub](https://github.com/NLog/NLog.Extensions.Logging))
- [Sentry](https://sentry.io/welcome) ([dépôt GitHub](https://github.com/getsentry/sentry-dotnet))
- [Serilog](https://serilog.net) ([dépôt GitHub](https://github.com/serilog/serilog-sinks-console))
- [Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub référentiel](https://github.com/googleapis/google-cloud-dotnet))

Certains frameworks tiers prennent en charge la [journalisation sémantique, également appelée journalisation structurée](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).

L’utilisation d’un framework tiers est semblable à l’utilisation des fournisseurs intégrés :

1. Ajoutez un package NuGet à votre projet.
1. Appeler une `ILoggerFactory` `ILoggingBuilder` méthode d’extension ou fournie par le Framework de journalisation.

Pour plus d’informations, consultez la documentation de chaque fournisseur. Les fournisseurs de journalisation tiers ne sont pas pris en charge par Microsoft.

## <a name="see-also"></a>Voir aussi

- [Journalisation dans .net](logging.md).
- [Implémentez un fournisseur de journalisation personnalisé dans .net](custom-logging-provider.md).
- [Journalisation hautes performances dans .net](high-performance-logging.md).
