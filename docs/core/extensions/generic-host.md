---
title: Hôte générique .NET
author: IEvangelist
description: En savoir plus sur l’hôte générique .NET, qui est responsable du démarrage et de la gestion de la durée de vie des applications.
ms.author: dapine
ms.date: 12/18/2020
ms.openlocfilehash: bf6d5ad624bbed46994633abace0af64712757f3
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700733"
---
# <a name="net-generic-host"></a>Hôte générique .NET

Les modèles de service Worker créent un hôte générique .NET, <xref:Microsoft.Extensions.Hosting.HostBuilder> . L’hôte générique peut être utilisé avec d’autres types d’applications .NET, comme les applications console.

Un *hôte* est un objet qui encapsule les ressources de l’application, telles que :

- Injection de dépendances (DI)
- Journalisation
- Configuration
- Implémentations de `IHostedService`

Lorsqu’un hôte démarre, il appelle <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> sur chaque implémentation de <xref:Microsoft.Extensions.Hosting.IHostedService> inscrite dans la collection de services hébergés du conteneur de services. Dans une application de service de travail, toutes les `IHostedService` implémentations qui contiennent des <xref:Microsoft.Extensions.Hosting.BackgroundService> instances ont leurs <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> méthodes appelées.

La principale raison d’inclure toutes les ressources interdépendantes de l’application dans un objet est la gestion de la durée de vie : contrôler le démarrage de l’application et l’arrêt approprié. Cela est possible avec le package NuGet [Microsoft. extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) .

## <a name="set-up-a-host"></a>Configurer un hôte

L’hôte est généralement configuré, généré et exécuté par du code dans la classe `Program`. La méthode `Main` :

- Appelle une méthode <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> pour créer et configurer un objet builder.
- Appelle <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> pour créer une <xref:Microsoft.Extensions.Hosting.IHost> instance.
- Appelle <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> ou <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> méthode sur l’objet hôte.

Les modèles de service de travail .NET génèrent le code suivant pour créer un hôte générique :

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

## <a name="default-builder-settings"></a>Paramètres du générateur par défaut

La méthode <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> :

- Définit le chemin retourné par <xref:System.IO.Directory.GetCurrentDirectory> comme racine de contenu.
- Charge la [configuration de l’hôte](#host-configuration) à partir de :
  - Les variables d’environnement précédées de `DOTNET_` .
  - Arguments de ligne de commande
- Charge la configuration de l’application à partir de :
  - *appsettings.js*.
  - *appsettings.{Environment}.json*
  - Secret Manager quand l’application s’exécute dans l’environnement `Development`.
  - Variables d'environnement.
  - Arguments de ligne de commande
- Ajoute les fournisseurs de journalisation suivants :
  - Console
  - Débogage
  - EventSource
  - EventLog (uniquement en cas d’exécution sur Windows)
- Active la validation de l’étendue et la [validation des dépendances](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) lorsque l’environnement est `Development` .

La `ConfigureServices` méthode expose la possibilité d’ajouter des services à l' <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instance. Plus tard, ces services peuvent être mis à disposition à partir de l’injection de dépendances.

## <a name="framework-provided-services"></a>Services fournis par le framework

Les services suivants sont inscrits automatiquement :

- [IHostApplicationLifetime](#ihostapplicationlifetime)
- [IHostLifetime](#ihostlifetime)
- [IHostEnvironment](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a>IHostApplicationLifetime

Injectez le <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> service dans n’importe quelle classe pour gérer les tâches de démarrage et d’arrêt gracieuses. Trois propriétés de l’interface sont des jetons d’annulation utilisés pour inscrire les méthodes du gestionnaire d’événements de démarrage et d’arrêt d’application. L’interface inclut également une méthode <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication>.

L’exemple suivant est une `IHostedService` implémentation qui inscrit des `IHostApplicationLifetime` événements :

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

Le modèle de service Worker peut être modifié pour ajouter l' `ExampleHostedService` implémentation :

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

L’application écrirait l’exemple de sortie suivant :

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a>IHostLifetime

L’implémentation de <xref:Microsoft.Extensions.Hosting.IHostLifetime> contrôle quand l’hôte démarre et quand il s’arrête. La dernière implémentation inscrite est utilisée.

`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` est l’implémentation de `IHostLifetime` par défaut. `ConsoleLifetime`:

- Écoute la <kbd>combinaison de touches Ctrl</kbd> + <kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)ou [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) et appelle <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> pour démarrer le processus d’arrêt.
- Débloque les extensions telles que `RunAsync` et `WaitForShutdownAsync` .

## <a name="ihostenvironment"></a>IHostEnvironment

Injectez le <xref:Microsoft.Extensions.Hosting.IHostEnvironment> service dans une classe pour obtenir des informations sur les paramètres suivants :

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a>Configuration de l’hôte

La configuration d’hôte est utilisée pour configurer les propriétés de l’implémentation de [IHostEnvironment](#ihostenvironment) .

La configuration d’hôte est disponible dans [HostBuilderContext.Configfiguration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) dans la <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> méthode. Lors de l’appel de la `ConfigureAppConfiguration` méthode, `HostBuilderContext` et `IConfigurationBuilder` sont passés dans le `configureDelegate` . Le `configureDelegate` est défini en tant que `Action<HostBuilderContext, IConfigurationBuilder>` . Le contexte du générateur d’ordinateur hôte expose la `.Configuration` propriété, qui est une instance de `IConfiguration` . Il représente la configuration générée à partir de l’hôte, tandis que le `IConfigurationBuilder` est l’objet générateur utilisé pour configurer l’application.

> [!TIP]
> Une fois `ConfigureAppConfiguration` appelé `HostBuilderContext.Configuration` , est remplacé par la [configuration](#app-configuration)de l’application.

Pour ajouter la configuration d’hôte, appelez <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> sur `IHostBuilder`. `ConfigureHostConfiguration` peut être appelé plusieurs fois avec des résultats additifs. L’hôte utilise l’option qui définit une valeur en dernier sur une clé donnée.

L’exemple suivant crée la configuration d’hôte :

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="19-25":::

## <a name="app-configuration"></a>la configuration d’une application ;

La configuration d’application est créée en appelant <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> sur `IHostBuilder`. `ConfigureAppConfiguration` peut être appelé plusieurs fois avec des résultats additifs. L’application utilise l’option qui définit une valeur en dernier sur une clé donnée.

La configuration créée par `ConfigureAppConfiguration` est disponible dans [HostBuilderContext.Configfiguration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) pour les opérations suivantes et en tant que service à partir de di. La configuration d’hôte est également ajoutée à la configuration d’application.

Pour plus d’informations, consultez [configuration dans .net](configuration.md).

## <a name="see-also"></a>Voir aussi

- [Configuration dans .NET](configuration.md)
- [Hôte web ASP.NET Core](/aspnet/core/fundamentals/host/web-host)
- Les bogues d’hôte générique doivent être créés dans [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) référentiel
