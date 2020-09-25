---
title: Injection de dépendances dans .NET
description: Découvrez comment .NET implémente l’injection de dépendances et comment l’utiliser.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: overview
ms.openlocfilehash: b986f414dcc0e81578e6cf57304f6e5c31578e88
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247897"
---
# <a name="dependency-injection-in-net"></a>Injection de dépendances dans .NET

.NET prend en charge le modèle de conception de logiciels d’injection de dépendances, qui est une technique permettant d’obtenir une [inversion de contrôle (IOC, inversion of Control)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) entre les classes et leurs dépendances. L’injection de dépendances dans .NET est un [citoyen de première classe](https://en.wikipedia.org/wiki/First-class_citizen), avec la configuration, la journalisation et le modèle d’options.

Une *dépendance* est un objet dont dépend un autre objet. Examinez la `MessageWriter` classe suivante avec une `Write` méthode dont dépendent d’autres classes :

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

Une classe peut créer une instance de la `MessageWriter` classe pour utiliser sa `Write` méthode. Dans l’exemple suivant, la `MessageWriter` classe est une dépendance de la `Worker` classe :

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

La classe crée et dépend directement de la `MessageWriter` classe. Les dépendances codées en dur, comme dans l’exemple précédent, sont problématiques et doivent être évitées pour les raisons suivantes :

- Pour remplacer `MessageWriter` par une implémentation différente, vous `MessageService` devez modifier la classe.
- Si `MessageWriter` a des dépendances, ils doivent également être configurés par la `MessageService` classe. Dans un grand projet comportant plusieurs classes dépendant de `MessageWriter`, le code de configuration est disséminé dans l’application.
- Cette implémentation complique le test unitaire. L’application doit utiliser une classe `MessageWriter` fictive ou stub, ce qui est impossible avec cette approche.

L’injection de dépendances résout ces problèmes via :

- L’utilisation d’une interface ou classe de base pour extraire l’implémentation des dépendances.
- L’inscription de la dépendance dans un conteneur de service. .NET fournit un conteneur de service intégré, <xref:System.IServiceProvider> . Les services sont généralement inscrits au démarrage de l’application et ajoutés à un <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> . Une fois tous les services ajoutés, vous utilisez <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> pour créer le conteneur de service.
- *Injection* du service dans le constructeur de la classe où il est utilisé. Le framework prend la responsabilité de la création d’une instance de la dépendance et de sa suppression lorsqu’elle n’est plus nécessaire.

Par exemple, l' `IMessageWriter` interface définit la `Write` méthode :

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

Cette interface est implémentée par un type concret, `MessageWriter` :

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

L’exemple de code inscrit le `IMessageWriter` service avec le type concret `MessageWriter` . La <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> méthode enregistre le service avec une durée de vie limitée, la durée de vie d’une requête unique. Les [durées de vie du service](#service-lifetimes) sont décrites plus loin dans cette rubrique.

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

Dans l’exemple d’application, le `IMessageWriter` service est demandé et utilisé pour appeler la `Write` méthode :

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

En utilisant le modèle DI, le service Worker :

- N’utilise pas le type concret `MessageWriter` , mais uniquement l' `IMessageWriter` interface qui l’implémente. Cela facilite la modification de l’implémentation que le contrôleur utilise sans modifier le contrôleur.
- Ne crée pas d’instance de `MessageWriter` , elle est créée par le conteneur di.

L’implémentation de l' `IMessageWriter` interface peut être améliorée à l’aide de l’API de journalisation intégrée :

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

La méthode mise à jour `ConfigureServices` inscrit la nouvelle `IMessageWriter` implémentation :

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

`LoggingMessageWriter` dépend de <xref:Microsoft.Extensions.Logging.ILogger%601> , qu’il demande dans le constructeur. `ILogger<TCategoryName>` est un [service fourni par le Framework](#framework-provided-services).

Il n’est pas rare que l’injection de dépendances soit utilisée de manière chaînée. Dans ce cas, chaque dépendance demandée demande à son tour ses propres dépendances. Le conteneur résout les dépendances dans le graphique et retourne le service entièrement résolu. L’ensemble collectif de dépendances qui doivent être résolues est généralement appelé *arborescence des dépendances*, *graphique de dépendance* ou *graphique d’objet*.

Le conteneur se résout `ILogger<TCategoryName>` en tirant parti de [types ouverts (génériques)](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types), ce qui évite d’avoir à inscrire chaque [type construit (Générique)](/dotnet/csharp/language-reference/language-specification/types#constructed-types).

Dans la terminologie d’injection de dépendances, un service :

- Est généralement un objet qui fournit un service à d’autres objets, tels que le `IMessageWriter` service.
- N’est pas associé à un service Web, bien que le service puisse utiliser un service Web.

Le Framework fournit un système de journalisation robuste. Les `IMessageWriter` implémentations présentées dans les exemples précédents ont été écrites pour illustrer la di de base, et non pour implémenter la journalisation. La plupart des applications n’ont pas besoin d’écrire des enregistreurs. Le code suivant illustre l’utilisation de la journalisation par défaut, qui nécessite uniquement l' `Worker` inscription de dans `ConfigureServices` en tant que service hébergé <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> :

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

À l’aide du code précédent, il n’est pas nécessaire de mettre à jour `ConfigureServices` , car la journalisation est assurée par l’infrastructure.

## <a name="register-groups-of-services-with-extension-methods"></a>Inscrire des groupes de services avec des méthodes d’extension

Les extensions Microsoft utilisent une convention pour l’enregistrement d’un groupe de services connexes. La Convention consiste à utiliser une `Add{GROUP_NAME}` méthode d’extension unique pour inscrire tous les services requis par une fonctionnalité de l’infrastructure. Par exemple, la <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> méthode d’extension inscrit tous les services requis pour l’utilisation des options.

## <a name="framework-provided-services"></a>Services fournis par le framework

La `ConfigureServices` méthode enregistre les services utilisés par l’application, y compris les fonctionnalités de plateforme. Initialement, le `IServiceCollection` fourni pour `ConfigureServices` possède des services définis par l’infrastructure en fonction de la [façon dont l’hôte a été configuré](generic-host.md#host-configuration). Pour les applications basées sur les modèles .NET, le Framework inscrit des centaines de services.

Le tableau suivant répertorie un petit exemple de ces services inscrits au Framework :

| Type de service                                                                       | Durée de vie  |
|------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                       | Singleton |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>           | Singleton |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>        | Singleton |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName> | Singleton |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName> | Temporaire |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>          | Singleton |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>              | Singleton |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                | Singleton |

## <a name="service-lifetimes"></a>Durées de service

Les services peuvent être enregistrés avec l’une des durées de vie suivantes :

- Temporaire
- Délimité
- Singleton

Les sections suivantes décrivent chacune des durées de vie précédentes. Choisissez une durée de vie appropriée pour chaque service inscrit.

### <a name="transient"></a>Temporaire

Des services à durée de vie temporaire (Transient) sont créés chaque fois qu’ils sont demandés à partir du conteneur de service. Cette durée de vie convient parfaitement aux services légers et sans état. Inscrire des services temporaires avec <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> .

Dans les applications qui traitent les demandes, les services transitoires sont supprimés à la fin de la demande.

### <a name="scoped"></a>Délimité

Pour les applications Web, une durée de vie limitée indique que les services sont créés une seule fois par demande du client (connexion). Inscrire les services délimités avec <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> .

Dans les applications qui traitent les requêtes, les services délimités sont supprimés à la fin de la demande.

Lors de l’utilisation de Entity Framework Core, la <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> méthode d’extension inscrit les `DbContext` types avec une durée de vie limitée par défaut.

> [!NOTE]
> Ne résolvez ***pas*** un service étendu à partir d’un singleton. L’état du service risque de ne pas être correct lors du traitement des requêtes suivantes. Il convient d’effectuer les opérations suivantes :
>
> - Résoudre un service Singleton à partir d’un service délimité ou étendu.
> - Résoudre un service étendu à partir d’un autre service étendu ou temporaire.

Par défaut, dans l’environnement de développement, la résolution d’un service à partir d’un autre service avec une durée de vie plus longue lève une exception. Pour plus d’informations, consultez [Validation de l’étendue](#scope-validation).

### <a name="singleton"></a>Singleton

Les services de durée de vie Singleton sont créés :

- La première fois qu’ils sont demandés.
- Par le développeur, lors de la fourniture d’une instance d’implémentation directement au conteneur. Cette approche est rarement nécessaire.

Chaque demande ultérieure de l’implémentation de service à partir du conteneur d’injection de dépendances utilise la même instance. Si l’application requiert un comportement Singleton, autorisez le conteneur de service à gérer la durée de vie du service. N’implémentez pas le modèle de conception Singleton et fournissez du code pour supprimer le singleton. Les services ne doivent jamais être supprimés par du code qui a résolu le service à partir du conteneur. Si un type ou une fabrique est inscrit en tant que singleton, le conteneur supprime automatiquement le singleton.

Inscrire des services Singleton avec <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> . Les services Singleton doivent être thread-safe et sont souvent utilisés dans les services sans État.

Dans les applications qui traitent les requêtes, les services Singleton sont supprimés lorsque le <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> est supprimé lors de l’arrêt de l’application. Étant donné que la mémoire n’est pas libérée tant que l’application n’est pas arrêtée, envisagez d’utiliser la mémoire avec un service Singleton.

> [!WARNING]
> Ne résolvez ***pas*** un service étendu à partir d’un singleton. L’état du service risque de ne pas être correct lors du traitement des requêtes suivantes. Il est parfait de résoudre un service Singleton à partir d’un service étendu ou temporaire.

## <a name="service-registration-methods"></a>Méthodes d’inscription du service

Le Framework fournit des méthodes d’extension d’inscription de service qui sont utiles dans des scénarios spécifiques :

| Méthode | Automatique<br>object<br>suppression | Multiple<br>implémentations | Passage d’args |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br>Exemple :<br><br>`services.AddSingleton<IMyDep, MyDep>();` | Oui | Oui | Non |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br>Exemples :<br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | Oui | Oui | Oui |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br>Exemple :<br><br>`services.AddSingleton<MyDep>();` | Oui | Non | Non |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br>Exemples :<br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | Non | Oui | Oui |
| `AddSingleton(new {IMPLEMENTATION})`<br><br>Exemples :<br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | Non | Non | Oui |

Pour plus d’informations sur la suppression de type, consultez la section [Suppression des services](dependency-injection-guidelines.md#disposal-of-services).

Le Framework fournit également des `TryAdd{LIFETIME}` méthodes d’extension, qui inscrivent le service uniquement si aucune implémentation n’est déjà inscrite.

Dans l’exemple suivant, l’appel à `AddSingleton` s’inscrit `MessageWriter` en tant qu’implémentation de `IMessageWriter` . L’appel à n' `TryAddSingleton` a aucun effet, car `IMessageWriter` a déjà une implémentation inscrite :

```csharp
services.AddSingleton<IMessageWriter, MessageWriter>();
services.TryAddSingleton<IMessageWriter, DifferentMessageWriter>();
```

Le n' `TryAddSingleton` a aucun effet, car il a déjà été ajouté et le « try » échoue.

Pour plus d'informations, consultez les pages suivantes :

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

Les méthodes [TryAddEnumerable (ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) inscrivent le service uniquement s’il n’existe pas déjà une implémentation *du même type*. Plusieurs services sont résolus par le biais de `IEnumerable<{SERVICE}>`. Lors de l’inscription des services, ajoutez une instance si l’un des mêmes types n’a pas déjà été ajouté. Les auteurs de bibliothèque utilisent `TryAddEnumerable` pour éviter d’inscrire plusieurs copies d’une implémentation dans le conteneur.

Dans l’exemple suivant, le premier appel à `TryAddEnumerable` s’inscrit `MessageWriter` en tant qu’implémentation pour `IMessageWriter1` . Le deuxième appel s’inscrit `MessageWriter` pour `IMessageWriter2` . Le troisième appel n’a aucun effet, car `IMessageWriter1` a déjà une implémentation inscrite de `MessageWriter` :

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

L’inscription de service est généralement indépendante de l’ordre, sauf lors de l’inscription de plusieurs implémentations du même type.

`IServiceCollection` est une collection d' <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> objets. L’exemple suivant montre comment inscrire un service en créant et en ajoutant un `ServiceDescriptor` :

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

Les `Add{LIFETIME}` méthodes intégrées utilisent la même approche. Par exemple, consultez le [code source AddScoped](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237).

### <a name="constructor-injection-behavior"></a>Comportement d’injection de constructeurs

Les services peuvent être résolus à l’aide de :

- <xref:System.IServiceProvider>
- <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:
  - Crée des objets qui ne sont pas inscrits dans le conteneur.
  - Utilisé avec certaines fonctionnalités de l’infrastructure.

Les constructeurs peuvent accepter des arguments qui ne sont pas fournis par l’injection de dépendances, mais les arguments doivent affecter des valeurs par défaut.

Lorsque des services sont résolus par `IServiceProvider` ou `ActivatorUtilities`, l’injection de constructeurs exige un constructeur *public*.

Lorsque des services sont résolus par `ActivatorUtilities`, l’injection de constructeurs exige qu’un seul constructeur applicable existe. Les surcharges de constructeurs sont prises en charge, mais une seule peut exister dont les arguments peuvent tous être satisfaits par l’injection de dépendances.

## <a name="scope-validation"></a>Validation de l’étendue

Lorsque l’application s’exécute dans l' `Development` environnement et appelle [CreateDefaultBuilder](generic-host.md#default-builder-settings) pour générer l’hôte, le fournisseur de services par défaut effectue des vérifications pour vérifier que :

- Les services délimités ne sont pas résolus à partir du fournisseur de services racine.
- Les services délimités ne sont pas injectés dans les singletons.

Le fournisseur de services racine est créé quand <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> est appelé. La durée de vie du fournisseur de services racine correspond à la durée de vie de l’application lorsque le fournisseur démarre avec l’application et est supprimée lorsque l’application s’arrête.

Les services Scoped sont supprimés par le conteneur qui les a créés. Si un service étendu est créé dans le conteneur racine, la durée de vie du service est effectivement promue en Singleton, car il est supprimé uniquement par le conteneur racine lorsque l’application s’arrête. La validation des étendues du service permet de traiter ces situations quand `BuildServiceProvider` est appelé.

## <a name="see-also"></a>Voir aussi

- [Utiliser l’injection de dépendances dans .NET](dependency-injection-usage.md)
- [Instructions relatives à l’injection de dépendances](dependency-injection-guidelines.md)
- [Modèles de conférence norvégiens pour le développement d’applications DI](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [Principe des dépendances explicites](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [Inversion des conteneurs de contrôle et le modèle d’injection de dépendances (Martin Fowler)](https://www.martinfowler.com/articles/injection.html)
