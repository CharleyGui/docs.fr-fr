---
title: Journalisation dans .NET
author: IEvangelist
description: Découvrez comment utiliser le framework de journalisation fourni par le package NuGet Microsoft.Extensions.Logging.
ms.author: dapine
ms.date: 09/30/2020
ms.openlocfilehash: 5a4d333368082389c4dfc134bb6a9a2e618d47e9
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982319"
---
# <a name="logging-in-net"></a>Journalisation dans .NET

.NET prend en charge une API de journalisation qui fonctionne avec un large éventail de fournisseurs de journalisation intégrés et tiers. Cet article explique comment utiliser cette API de journalisation avec les fournisseurs de journalisation intégrés. La plupart des exemples de code présentés dans cet article s’appliquent à toutes les applications .NET qui utilisent l' [hôte générique](generic-host.md). Pour les applications qui n’utilisent pas l’hôte générique, consultez [application console non-hôte](#non-host-console-app).

## <a name="create-logs"></a>Créer des journaux

Pour créer des journaux, utilisez un <xref:Microsoft.Extensions.Logging.ILogger%601> objet à partir de l' [injection de dépendances (di)](dependency-injection.md).

L’exemple suivant :

- Crée un enregistreur d’événements, `ILogger<Worker>` , qui utilise une *catégorie* de journal du nom qualifié complet du type `Worker` . La catégorie du journal est une chaîne associée à chaque journal.
- Appels <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> à consigner au `Information` niveau. Le *niveau* du journal indique la gravité de l’événement consigné.

:::code language="csharp" source="snippets/configuration/worker-service/Worker.cs" range="9-24" highlight="12":::

Les [niveaux](#log-level) et les [catégories](#log-category) sont expliqués plus en détail plus loin dans cet article.

## <a name="configure-logging"></a>Configuration de la journalisation

La configuration de la journalisation est généralement fournie par la `Logging` section de *appSettings*. `{Environment}` fichiers *. JSON* . Leappsettings.Development.jssuivant sur le fichier est généré par les modèles *de service de* travail .net :

:::code language="json" source="snippets/configuration/worker-service/appsettings.Development.json":::

Dans le code JSON précédent :

- Les `"Default"` `"Microsoft"` catégories, et `"Microsoft.Hosting.Lifetime"` sont spécifiées.
- La `"Microsoft"` catégorie s’applique à toutes les catégories qui commencent par `"Microsoft"` .
- La `"Microsoft"` catégorie enregistre les journaux au niveau du journal et au niveau `Warning` supérieur.
- La catégorie `"Microsoft.Hosting.Lifetime"` est plus spécifique que la catégorie `"Microsoft"` , de sorte que la `"Microsoft.Hosting.Lifetime"` catégorie enregistre les journaux au niveau du journal « information » et supérieur.
- Un module fournisseur d’informations spécifique n’étant pas spécifié, `LogLevel` s’applique à tous les fournisseurs de journalisation activés, à l’exception du journal des [événements Windows](logging-providers.md#windows-eventlog).

La `Logging` propriété peut avoir <xref:Microsoft.Extensions.Logging.LogLevel> et enregistrer les propriétés du fournisseur. `LogLevel`Spécifie le [niveau](#log-level) minimal à enregistrer pour les catégories sélectionnées. Dans le code JSON précédent, les `Information` `Warning` niveaux de journalisation sont spécifiés. `LogLevel` indique la gravité du journal et les plages de 0 à 6 :

`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5 et `None` = 6.

Lorsqu’un `LogLevel` est spécifié, la journalisation est activée pour les messages au niveau spécifié et supérieur. Dans le code JSON précédent, la `Default` catégorie est journalisée pour `Information` et les versions ultérieures. Par exemple, les messages,, `Information` `Warning` `Error` et `Critical` sont journalisés. Si aucun `LogLevel` n’est spécifié, la journalisation est définie par défaut sur le `Information` niveau. Pour plus d’informations, consultez [niveaux de journalisation](#log-level).

Une propriété de fournisseur peut spécifier une `LogLevel` propriété. `LogLevel` sous un fournisseur spécifie les niveaux de journalisation pour ce fournisseur, et remplace les paramètres du journal non fournisseur. Prenez en compte les *appsettings.jssuivantes sur* le fichier :

:::code language="json" source="snippets/configuration/worker-service/appsettings.Staging.json":::

Paramètres dans les `Logging.{ProviderName}.LogLevel` paramètres de remplacement dans `Logging.LogLevel` . Dans le code JSON précédent, le `Debug` niveau de journalisation par défaut du fournisseur est défini sur `Information` :

`Logging:Debug:LogLevel:Default:Information`

Le paramètre précédent spécifie le `Information` niveau de journalisation pour chaque `Logging:Debug:` catégorie, à l’exception de `Microsoft.Hosting` . Quand une catégorie spécifique est indiquée, la catégorie spécifique remplace la catégorie par défaut. Dans le JSON précédent, les `Logging:Debug:LogLevel` catégories `"Microsoft.Hosting"` et `"Default"` remplacent les paramètres dans `Logging:LogLevel`

Le niveau de journal minimal peut être spécifié pour l’un des éléments suivants :

- Fournisseurs spécifiques : par exemple, `Logging:EventSource:LogLevel:Default:Information`
- Catégories spécifiques : par exemple, `Logging:LogLevel:Microsoft:Warning`
- Tous les fournisseurs et toutes les catégories : `Logging:LogLevel:Default:Warning`

Tous les journaux situés en dessous du niveau minimal sont ***not** _ :

- Passé au fournisseur.
- Consigné ou affiché.

Pour supprimer tous les journaux, spécifiez [LogLevel. None](xref:Microsoft.Extensions.Logging.LogLevel). `LogLevel.None` a une valeur de 6, qui est supérieure à `LogLevel.Critical` (5).

Si un fournisseur prend en charge les [étendues de journal](#log-scopes), `IncludeScopes` indique s’ils sont activés. Pour plus d’informations, consultez [étendues de journaux](#log-scopes)

Le _appsettings.jssuivant sur le fichier * contient les paramètres de tous les fournisseurs intégrés :

:::code language="json" source="snippets/configuration/worker-service/appsettings.Production.json":::

Dans l’exemple précédent :

- Les catégories et les niveaux ne sont pas des valeurs suggérées. L’exemple est fourni pour afficher tous les fournisseurs par défaut.
- Paramètres dans les `Logging.{ProviderName}.LogLevel` paramètres de remplacement dans `Logging.LogLevel` . Par exemple, le niveau dans `Debug.LogLevel.Default` remplace le niveau dans `LogLevel.Default` .
- L' *alias* de chaque fournisseur est utilisé. Chaque fournisseur définit un *alias* qui peut être utilisé dans la configuration à la place du nom de type complet. Les alias des fournisseurs intégrés sont les suivants :
  - Console
  - Débogage
  - EventSource
  - EventLog
  - AzureAppServicesFile
  - AzureAppServicesBlob
  - ApplicationInsights

### <a name="set-log-level-by-command-line-environment-variables-and-other-configuration"></a>Définir le niveau de journalisation à l’aide d’une ligne de commande, de variables d’environnement et d’autres configurations

Le niveau de journal peut être défini par l’un des [fournisseurs de configuration](configuration-providers.md).

Les commandes suivantes :

- Affectez à la clé d’environnement la `Logging:LogLevel:Microsoft` valeur `Information` sur Windows.
- Testez les paramètres lors de l’utilisation d’une application créée avec les modèles de service de travail .NET. La `dotnet run` commande doit être exécutée dans le répertoire du projet après l’utilisation de `set` .

```cmd
set Logging__LogLevel__Microsoft=Information
dotnet run
```

Le paramètre d’environnement précédent :

- Est défini uniquement dans les processus lancés à partir de la fenêtre de commande dans laquelle ils ont été définis.
- N’est pas lu par les applications lancées avec Visual Studio.

La commande [setx](/windows-server/administration/windows-commands/setx) suivante définit également la clé et la valeur de l’environnement sur Windows. Contrairement à `set` , `setx` les paramètres sont conservés. Le `/M` commutateur définit la variable dans l’environnement système. Si `/M` n’est pas utilisé, une variable d’environnement utilisateur est définie.

```cmd
setx Logging__LogLevel__Microsoft=Information /M
```

Dans [Azure App service](https://azure.microsoft.com/services/app-service/), sélectionnez **nouveau paramètre d’application** dans la page **paramètres > configuration** . Azure App Service paramètres de l’application sont les suivants :

- Chiffré au repos et transmis sur un canal chiffré.
- Exposés en tant que variables d’environnement.

Pour plus d’informations sur la définition des valeurs de configuration .NET à l’aide de variables d’environnement, consultez [variables d’environnement](configuration-providers.md#environment-variable-configuration-provider).

## <a name="how-filtering-rules-are-applied"></a>Mode d’application des règles de filtre

À la création d’un objet <xref:Microsoft.Extensions.Logging.ILogger%601>, l’objet <xref:Microsoft.Extensions.Logging.ILoggerFactory> sélectionne une seule règle à appliquer à cet enregistrement d’événements par fournisseur. Tous les messages écrits par une instance `ILogger` sont filtrés selon les règles sélectionnées. La règle la plus spécifique pour chaque paire fournisseur et catégorie est sélectionnée parmi les règles disponibles.

L’algorithme suivant est utilisé pour chaque fournisseur quand un objet `ILogger` est créé pour une catégorie donnée :

- Sélectionnez toutes les règles qui correspondent au fournisseur ou à son alias. Si aucune correspondance n’est trouvée, sélectionnez toutes les règles avec un fournisseur vide.
- À partir du résultat de l’étape précédente, sélectionnez les règles ayant le plus long préfixe de catégorie correspondant. Si aucune correspondance n’est trouvée, sélectionnez toutes les règles qui ne spécifient pas de catégorie.
- Si plusieurs règles sont sélectionnées, prenez la **dernière**.
- Si aucune règle n’est sélectionnée, utilisez <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> pour spécifier le niveau de journalisation minimale.

## <a name="log-category"></a>Catégorie de journal

Lorsqu’un `ILogger` objet est créé, une *catégorie* est spécifiée. Cette catégorie est incluse dans tous les messages de journal créés par cette instance de `ILogger`. La chaîne de catégorie est arbitraire, mais la Convention consiste à utiliser le nom de la classe. Par exemple, dans une application avec un service défini comme l’objet suivant, la catégorie peut être `"Example.DefaultService"` :

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger<DefaultService> _logger;

        public DefaultService(ILogger<DefaultService> logger) =>
            _logger = logger;

        // ...
    }
}
```

Pour spécifier explicitement la catégorie, appelez <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType> :

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger _logger;

        public DefaultService(ILoggerFactory loggerFactory) =>
            _logger = logger.CreateLogger("CustomCategory");

        // ...
    }
}
```

L’appel de `CreateLogger` avec un nom fixe peut être utile lorsqu’il est utilisé dans plusieurs méthodes afin que les événements puissent être organisés par catégorie.

`ILogger<T>` équivaut à appeler `CreateLogger` avec le nom de type complet `T`.

## <a name="log-level"></a>Log level

Le tableau suivant répertorie les <xref:Microsoft.Extensions.Logging.LogLevel> valeurs, la `Log{LogLevel}` méthode d’extension de commodité et l’utilisation suggérée :

| LogLevel | Valeur | Méthode | Description |
|--|--|--|--|
| [Trace](xref:Microsoft.Extensions.Logging.LogLevel) | 0 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogTrace%2A> | Contiennent les messages les plus détaillés. Ces messages peuvent contenir des données d’application sensibles. Ces messages sont désactivés par défaut et ne doivent **pas** être activés en production. |
| [Déboguer](xref:Microsoft.Extensions.Logging.LogLevel) | 1 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> | Pour le débogage et le développement. Utilisez avec précaution en production en raison du volume élevé. |
| [Informations](xref:Microsoft.Extensions.Logging.LogLevel) | 2 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> | Effectue le suivi du déroulement général de l’application. Peut avoir une valeur à long terme. |
| [Avertissement](xref:Microsoft.Extensions.Logging.LogLevel) | 3 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogWarning%2A> | Pour les événements anormaux ou inattendus. Comprend généralement des erreurs ou des conditions qui ne provoquent pas l’échec de l’application. |
| [Error](xref:Microsoft.Extensions.Logging.LogLevel) | 4 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogError%2A> | Fournit des informations sur des erreurs et des exceptions qui ne peuvent pas être gérées. Ces messages indiquent un échec dans l’opération ou la demande en cours, et non dans l’ensemble de l’application. |
| [Critique](xref:Microsoft.Extensions.Logging.LogLevel) | 5 | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogCritical%2A> | Fournit des informations sur des échecs qui nécessitent un examen immédiat. Exemples : perte de données, espace disque insuffisant. |
| [Aucun](xref:Microsoft.Extensions.Logging.LogLevel) | 6 |  | Spécifie qu’aucun message ne doit être écrit. |

Dans le tableau précédent, la `LogLevel` est indiquée du niveau de gravité le plus bas au plus élevé.

Le premier paramètre de la méthode de [journalisation](xref:Microsoft.Extensions.Logging.LoggerExtensions) , <xref:Microsoft.Extensions.Logging.LogLevel> , indique la gravité du journal. Au lieu d’appeler `Log(LogLevel, ...)` , la plupart des développeurs appellent les méthodes d’extension [log {LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions) . Les `Log{LogLevel}` méthodes d’extension [appellent la méthode log et spécifient LogLevel](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs). Par exemple, les deux appels de journalisation suivants sont fonctionnellement équivalents et produisent le même journal :

```csharp
public void LogDetails()
{
    var logMessage = "Details for log.";

    _logger.Log(LogLevel.Information, AppLogEvents.Details, logMessage);
    _logger.LogInformation(AppLogEvents.Details, logMessage);
}
```

`AppLogEvents.Details` est l’ID d’événement et est implicitement représenté par une valeur de constante <xref:System.Int32> . `AppLogEvents` est une classe qui expose différentes constantes d’identificateur nommées et qui est affichée dans la section de l' [ID d’événement de journal](#log-event-id) .

Le code suivant crée des journaux `Information` et `Warning` :

```csharp
public async Task<T> GetAsync<T>(string id)
{
    _logger.LogInformation(AppLogEvents.Read, "Reading value for {Id}", id);

    var result = await _repository.GetAsync(id);
    if (result is null)
    {
        _logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
    }

    return result;
}
```

Dans le code précédent, le premier `Log{LogLevel}` paramètre, `AppLogEvents.Read` , est l' [ID d’événement du journal](#log-event-id). Le deuxième paramètre est un modèle de message contenant des espaces réservés pour les valeurs d’argument fournies par les autres paramètres de méthode. Les paramètres de méthode sont expliqués dans la section [modèle de message](#log-message-template) plus loin dans cet article.

Configurez le niveau de journalisation approprié et appelez les `Log{LogLevel}` méthodes appropriées pour contrôler la quantité de sortie de journal écrite sur un support de stockage particulier. Par exemple :

- En production :
  - La journalisation au `Trace` niveau des ou de `Information` génère un volume important de messages journaux détaillés. Pour contrôler les coûts et ne pas dépasser les limites de stockage des données, `Trace` `Information` les messages de journal et de niveau dans un magasin de données volumineux et à faible coût. Envisagez `Trace` de limiter et `Information` à des catégories spécifiques.
  - La journalisation au `Warning` `Critical` niveau des niveaux doit produire peu de messages de journal.
    - Les coûts et les limites de stockage ne sont généralement pas un problème.
    - Certains journaux offrent davantage de flexibilité dans les choix de magasins de données.
- En cours de développement :
  - Défini sur `Warning`.
  - Ajoutez `Trace` `Information` des messages ou lors de la résolution des problèmes. Pour limiter la sortie, `Trace` la définition ou `Information` uniquement pour les catégories en cours d’investigation.

Le code JSON suivant définit `Logging:Console:LogLevel:Microsoft:Information` :

:::code language="json" source="snippets/configuration/worker-service/appsettings.MSFT.json":::

## <a name="log-event-id"></a>ID d’événement de log

Chaque journal peut spécifier un identificateur de _event *, <xref:Microsoft.Extensions.Logging.EventId> est une structure avec un `Id` et des `Name` propriétés ReadOnly facultatives. L’exemple de code source utilise la `AppLogEvents` classe pour définir les ID d’événement :

```csharp
internal static class AppLogEvents
{
    internal const int Create = 1000;
    internal const int Read = 1001;
    internal const int Update = 1002;
    internal const int Delete = 1003;

    internal const int Details = 3000;
    internal const int Error = 3001;

    internal const int ReadNotFound = 4000;
    internal const int UpdateNotFound = 4001;

    // ...
}
```

Un ID d’événement associe un jeu d’événements. Par exemple, tous les journaux liés à la lecture des valeurs d’un référentiel peuvent être `1001` .

Le fournisseur de journalisation peut enregistrer l’ID d’événement dans un champ ID, dans le message de journalisation, ou pas du tout. Le fournisseur Debug n’affiche pas les ID d’événements. Le fournisseur Console affiche les ID d’événements entre crochets après la catégorie :

```console
info: Example.DefaultService.GetAsync[1001]
      Reading value for a1b2c3
warn: Example.DefaultService.GetAsync[4000]
      GetAsync(a1b2c3) not found
```

Certains fournisseurs de journalisation stockent l’ID d’événement dans un champ, ce qui permet de filtrer l’ID.

## <a name="log-message-template"></a>Modèle de message de journal

Chaque API de journal utilise un modèle de message. Ce dernier peut contenir des espaces réservés pour lesquels les arguments sont fournis. Utilisez des noms et non des nombres pour les espaces réservés. L’ordre des espaces réservés, pas leurs noms, détermine quels paramètres sont utilisés pour fournir leurs valeurs. Dans le code suivant, les noms de paramètres sont hors séquence dans le modèle de message :

```csharp
string p1 = "param1";
string p2 = "param2";
_logger.LogInformation("Parameter values: {p2}, {p1}", p1, p2);
```

Le code précédent crée un message de journal avec les valeurs de paramètre dans l’ordre :

```text
Parameter values: param1, param2
```

Cette approche permet aux fournisseurs de journalisation d’implémenter la [journalisation sémantique ou structurée](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging). Les arguments proprement dits, et pas seulement le modèle de message mis en forme, sont transmis au système de journalisation. Cela permet aux fournisseurs de journalisation de stocker les valeurs de paramètres en tant que champs. Examinez la méthode d’enregistreur d’événements suivante :

```csharp
_logger.LogInformation("Getting item {Id} at {RunTime}", id, DateTime.Now);
```

Par exemple, lors de la journalisation dans le stockage table Azure :

- Chaque entité de table Azure peut avoir des `ID` `RunTime` Propriétés et.
- Les tables avec des propriétés simplifient les requêtes sur les données journalisées. Par exemple, une requête peut trouver tous les journaux d’une `RunTime` plage donnée sans avoir à analyser le délai d’attente du message texte.

## <a name="log-exceptions"></a>Enregistrer des exceptions

Les méthodes d’enregistreur d’événements ont des surcharges qui prennent un paramètre d’exception :

```csharp
public void Test(string id)
{
    try
    {
        if (id == "none")
        {
            throw new Exception("Default Id detected.");
        }
    }
    catch (Exception ex)
    {
        _logger.LogWarning(
            AppLogEvents.Error, ex,
            "Failed to process iteration: {Id}", id)
    }
}
```

La journalisation des exceptions est spécifique au fournisseur.

### <a name="default-log-level"></a>Niveau de journalisation par défaut

Si le niveau de journalisation par défaut n’est pas défini, la valeur par défaut du niveau de journal est `Information` .

Par exemple, considérez l’application de service de travail suivante :

- Créé avec les modèles de travail .NET.
- *appsettings.jssur* et *appsettings.Development.jssur* supprimé ou renommé.

Avec la configuration précédente, la navigation vers la page confidentialité ou d’origine génère de nombreux `Trace` `Debug` messages, et `Information`  avec `Microsoft` dans le nom de catégorie.

Le code suivant définit le niveau de journalisation par défaut lorsque le niveau de journalisation par défaut n’est pas défini dans la configuration :

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging => logging.SetMinimumLevel(LogLevel.Warning));
}
```

### <a name="filter-function"></a>fonction Filter

Une fonction de filtre est appelée pour tous les fournisseurs et toutes les catégories pour lesquels aucune règle n’est assignée par la configuration ou le code :

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddFilter((provider, category, logLevel) =>
                {
                    return provider.Contains("ConsoleLoggerProvider")
                        && (category.Contains("Example") || category.Contains("Microsoft"))
                        && logLevel >= LogLevel.Information;
                }));
}
```

Le code précédent affiche les journaux de console lorsque la catégorie contient `Example` ou `Microsoft` et que le niveau de journal est `Information` ou supérieur.

## <a name="log-scopes"></a>Étendues de journal

 Une *étendue* peut regrouper un ensemble d’opérations logiques. Ce regroupement permet de joindre les mêmes données à tous les journaux créés au sein d’un ensemble. Par exemple, chaque journal créé dans le cadre du traitement d’une transaction peut contenir l’ID de la transaction.

Une étendue :

- Est un <xref:System.IDisposable> type qui est retourné par la <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> méthode.
- Dure jusqu’à ce qu’il soit supprimé.

Les fournisseurs suivants prennent en charge les étendues :

- `Console`
- [AzureAppServicesFile et AzureAppServicesBlob](xref:Microsoft.Extensions.Logging.AzureAppServices.BatchingLoggerOptions.IncludeScopes)

Utilisez une étendue en incluant les appels de l’enregistrement d’événements dans un bloc `using` :

```csharp
public async Task<T> GetAsync<T>(string id)
{
    T result;

    using (_logger.BeginScope("using block message"))
    {
        _logger.LogInformation(
            AppLogEvents.Read, "Reading value for {Id}", id);

        var result = await _repository.GetAsync(id);
        if (result is null)
        {
            _logger.LogWarning(
                AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
        }
    }

    return result;
}
```

Le code JSON suivant active des étendues pour le fournisseur de console :

:::code language="json" source="snippets/configuration/worker-service/appsettings.IncludeScopes.json" highlight="9":::

Le code suivant active les étendues pour le fournisseur Console :

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging((_, logging) =>
                logging.ClearProviders()
                    .AddConsole(options => options.IncludeScopes = true));
}
```

## <a name="non-host-console-app"></a>Application console non-hôte

La journalisation du code pour les applications sans [hôte générique](generic-host.md) diffère dans la façon dont les [fournisseurs sont ajoutés](logging-providers.md#built-in-logging-providers) et les [journaux sont créés](#create-logs). Dans une application de console non hôte, appelez la méthode d’extension `Add{provider name}` du fournisseur lors de la création d’un `LoggerFactory` :

```csharp
class Program
{
    static void Main(string[] args)
    {
        using var loggerFactory = LoggerFactory.Create(builder =>
        {
            builder
                .AddFilter("Microsoft", LogLevel.Warning)
                .AddFilter("System", LogLevel.Warning)
                .AddFilter("LoggingConsoleApp.Program", LogLevel.Debug)
                .AddConsole();
        });

        ILogger logger = loggerFactory.CreateLogger<Program>();
        logger.LogInformation("Example log message");
    }
}
```

L' `loggerFactory` objet est utilisé pour créer une <xref:Microsoft.Extensions.Logging.ILogger> instance.

## <a name="create-logs-in-main"></a>Créer des journaux dans main

Le code suivant se connecte `Main` en obtenant une `ILogger` instance à partir de di après avoir généré l’hôte :

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

class Program
{
    static Task Main(string[] args)
    {
        IHost host = Host.CreateDefaultBuilder(args).Build();

        var logger = host.Services.GetRequiredService<ILogger<Program>>();
        logger.LogInformation("Host created.");

        return host.RunAsync();
    }
}
```

### <a name="no-asynchronous-logger-methods"></a>Aucune méthode d’enregistreur d’événements asynchrone

La journalisation doit être suffisamment rapide par rapport au coût du code asynchrone en matière de performances. Si un magasin de données de journalisation est lent, n’écrivez pas directement dessus. Envisagez d’écrire les messages du journal dans un magasin rapide, puis de les déplacer ultérieurement vers la Banque lente. Par exemple, lorsque vous vous connectez à SQL Server, ne le faites pas directement dans une `Log` méthode, puisque les `Log` méthodes sont synchrones. Ajoutez plutôt de façon synchronisée des messages de journal à une file d’attente en mémoire, puis configurez un traitement en arrière-plan afin d’extraire les messages de la file d’attente et d’effectuer le travail asynchrone d’envoi des données vers SQL Server.

## <a name="change-log-levels-in-a-running-app"></a>Modifier les niveaux de journal dans une application en cours d’exécution

L’API de journalisation n’inclut pas de scénario pour modifier les niveaux de journal lorsqu’une application est en cours d’exécution. Toutefois, certains fournisseurs de configuration sont en charge du rechargement de la configuration, ce qui prend immédiatement effet sur la configuration de la journalisation. Par exemple, le [fournisseur de configuration de fichier](configuration-providers.md#file-configuration-provider) recharge la configuration de journalisation par défaut. Si la configuration est modifiée dans le code pendant qu’une application est en cours d’exécution, l’application peut appeler [IConfigurationRoot. Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) pour mettre à jour la configuration de journalisation de l’application.

## <a name="nuget-packages"></a>Packages NuGet

Les <xref:Microsoft.Extensions.Logging.ILogger%601> <xref:Microsoft.Extensions.Logging.ILoggerFactory> interfaces et et les implémentations sont incluses dans la kit SDK .net core. Ils sont également disponibles dans les packages NuGet suivants :

- Les interfaces se trouvent dans [Microsoft. extensions. Logging. Abstracts](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions).
- Les implémentations par défaut se trouvent dans [Microsoft. extensions. Logging](https://www.nuget.org/packages/microsoft.extensions.logging).

## <a name="apply-log-filter-rules-in-code"></a>Appliquer les règles de filtre de journal dans le code

L’approche recommandée pour définir des règles de filtre de journal consiste à utiliser la [configuration](configuration.md).

L'exemple suivant montre comment enregistrer des règles de filtre dans le code :

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
               logging.AddFilter("System", LogLevel.Debug)
                  .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)
                  .AddFilter<ConsoleLoggerProvider>("Microsoft", LogLevel.Trace));
}
```

`logging.AddFilter("System", LogLevel.Debug)` spécifie la `System` catégorie et le niveau de journalisation `Debug` . Le filtre est appliqué à tous les fournisseurs, car un fournisseur spécifique n’a pas été configuré.

`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` indiquant

- `Debug`Fournisseur de journalisation.
- Niveau de journalisation `Information` et supérieur.
- Toutes les catégories commençant par `"Microsoft"` .

## <a name="see-also"></a>Voir aussi

- [Fournisseurs de journalisation dans .NET](logging-providers.md)
- [Implémenter un fournisseur de journalisation personnalisé dans .NET](custom-logging-provider.md)
- [Mise en forme des journaux de la console](console-log-formatter.md)
- [Journalisation hautes performances dans .NET](high-performance-logging.md)
- Les bogues de journalisation doivent être créés dans [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) référentiel
