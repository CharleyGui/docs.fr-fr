---
title: Instructions relatives à l’injection de dépendances
description: Découvrez les différentes recommandations en matière d’injection de dépendances et les meilleures pratiques pour le développement d’applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: guide
ms.openlocfilehash: a8d52642b9217c7340db69494624d8ab85ea6c92
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247896"
---
# <a name="dependency-injection-guidelines"></a>Instructions relatives à l’injection de dépendances

Cet article fournit des recommandations générales et les meilleures pratiques pour implémenter l’injection de dépendances dans les applications .NET.

## <a name="design-services-for-dependency-injection"></a>Conception de services pour l’injection de dépendances

Lors de la conception de services pour l’injection de dépendances :

- Évitez les classes et les membres avec état, static. Évitez de créer un état global en concevant des applications qui utilisent des services Singleton à la place.
- Éviter une instanciation directe de classes dépendantes au sein de services. L’instanciation directe associe le code à une implémentation particulière.
- Rendez les services petits, bien factorisés et faciles à tester.

Si une classe possède de nombreuses dépendances injectées, il peut s’agir d’un signe que la classe a trop de responsabilités et viole le [principe de responsabilité unique (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility). Essayez de refactoriser la classe en déplaçant certaines de ses responsabilités dans de nouvelles classes.

### <a name="disposal-of-services"></a>Suppression des services

Le conteneur est responsable du nettoyage des types qu’il crée et appelle <xref:System.IDisposable.Dispose%2A> sur les <xref:System.IDisposable> instances. Les services résolus à partir du conteneur ne doivent jamais être supprimés par le développeur. Si un type ou une fabrique est inscrit en tant que singleton, le conteneur supprime automatiquement le singleton.

Dans l’exemple suivant, les services sont créés par le conteneur de service et supprimés automatiquement :

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60":::

La console de débogage affiche l’exemple de sortie suivant après l’exécution de :

```console
Scope 1...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

Scope 2...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

info: Microsoft.Hosting.Lifetime[0]
      Application started.Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
     Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
     Content root path: .\configuration\console-di-disposable\bin\Debug\net5.0
info: Microsoft.Hosting.Lifetime[0]
     Application is shutting down...
SingletonDisposable.Dispose()
```

### <a name="services-not-created-by-the-service-container"></a>Services non créés par le conteneur de service

Considérez le code suivant :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

Dans le code précédent :

- L' `ExampleService` instance n’est **pas** créée par le conteneur de service.
- L’infrastructure ne supprime **pas** automatiquement les services.
- Le développeur est responsable de la suppression des services.

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a>Recommandations IDisposable pour les instances temporaires et partagées

#### <a name="transient-limited-lifetime"></a>Transitoire, durée de vie limitée

**Scénario**

L’application requiert une <xref:System.IDisposable> instance avec une durée de vie transitoire pour l’un des scénarios suivants :

- L’instance est résolue dans l’étendue racine (conteneur racine).
- L’instance doit être supprimée avant la fin de l’étendue.

**Solution**

Utilisez le modèle de fabrique pour créer une instance en dehors de l’étendue parente. Dans ce cas, l’application a généralement une `Create` méthode qui appelle directement le constructeur du type final. Si le type final a d’autres dépendances, la fabrique peut :

- Recevoir un <xref:System.IServiceProvider> dans son constructeur.
- Utilisez <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> pour instancier l’instance en dehors du conteneur, tout en utilisant le conteneur pour ses dépendances.

#### <a name="shared-instance-limited-lifetime"></a>Instance partagée, durée de vie limitée

**Scénario**

L’application requiert une <xref:System.IDisposable> instance partagée sur plusieurs services, mais l' <xref:System.IDisposable> instance doit avoir une durée de vie limitée.

**Solution**

Inscrivez l’instance avec une durée de vie limitée. Utilisez <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> pour créer un <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> . Utilisez les étendues <xref:System.IServiceProvider> pour accéder aux services requis. Supprimez l’étendue lorsqu’elle n’est plus nécessaire.

#### <a name="general-idisposable-guidelines"></a>`IDisposable`Recommandations générales

- N’inscrivez pas <xref:System.IDisposable> les instances avec une durée de vie transitoire. Utilisez à la place le modèle de fabrique.
- Ne résolvez pas <xref:System.IDisposable> les instances avec une durée de vie transitoire ou limitée dans l’étendue racine. La seule exception à cela est que l’application crée/recrée et supprime <xref:System.IServiceProvider> , mais ce n’est pas un modèle idéal.
- La réception d’une <xref:System.IDisposable> dépendance via l’injection de dépendances ne nécessite pas que le récepteur s’implémente <xref:System.IDisposable> lui-même. Le récepteur de la <xref:System.IDisposable> dépendance ne doit pas appeler <xref:System.IDisposable.Dispose%2A> sur cette dépendance.
- Utilisez des étendues pour contrôler les durées de vie des services. Les étendues ne sont pas hiérarchiques, et il n’existe pas de connexion spéciale entre les étendues.

Pour plus d’informations sur le nettoyage des ressources, consultez [implémenter une méthode dispose](../../standard/garbage-collection/implementing-dispose.md)

## <a name="default-service-container-replacement"></a>Remplacement de conteneur de services par défaut

Le conteneur de service intégré est conçu pour répondre aux besoins de l’infrastructure et de la plupart des applications grand public. Nous vous recommandons d’utiliser le conteneur intégré, sauf si vous avez besoin d’une fonctionnalité spécifique qu’il ne prend pas en charge, par exemple :

- Injection de propriétés
- Injection en fonction du nom
- Conteneurs enfants
- Gestion personnalisée de la durée de vie
- `Func<T>` prend en charge l’initialisation tardive
- Inscription basée sur une convention

Les conteneurs tiers suivants peuvent être utilisés avec les applications ASP.NET Core :

- [Autofac](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [DryIoc](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [Grace](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [LightInject](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [Lamar](https://jasperfx.github.io/lamar/)
- [Stashbox](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [Unity](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a>Sécurité des threads

Créez des services singleton thread-safe. Si un service Singleton a une dépendance vis-à-vis d’un service temporaire, le service temporaire peut également nécessiter la sécurité des threads en fonction de la façon dont il est utilisé par le singleton.

La méthode de fabrique d’un service unique, telle que le deuxième argument de [AddSingleton \<TService> (IServiceCollection, Func \<IServiceProvider,TService> )](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), n’a pas besoin d’être thread-safe. À l’instar d’un constructeur de type ( `static` ), il est garanti qu’il soit appelé une seule fois par un seul thread.

## <a name="recommendations"></a>Recommandations

- `async/await` et la `Task` résolution de service basée sur n’est pas prise en charge. Étant donné que C# ne prend pas en charge les constructeurs asynchrones, utilisez des méthodes asynchrones après la résolution synchrone du service.
- Évitez de stocker des données et des configurations directement dans le conteneur de services. Par exemple, le panier d’achat d’un utilisateur ne doit en général pas être ajouté au conteneur de services. La configuration doit utiliser le modèle d’options. De même, évitez les objets « garde-données » qui existent uniquement pour autoriser l’accès à un autre objet. Il est préférable de demander l’élément réel par le biais de l’injection de dépendance.
- Évitez l’accès statique aux services. Par exemple, évitez de capturer [IApplicationBuilder. ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) en tant que champ ou propriété statique à utiliser ailleurs.
- Conservez les fabriques DI en mode rapide et synchrone.
- Évitez d’utiliser le *modèle de localisation de service*. Par exemple, n’appelez pas <xref:System.IServiceProvider.GetService%2A> pour obtenir une instance de service lorsque vous pouvez utiliser l’injection de dépendance à la place.
- Une autre variante du localisateur de service à éviter est l’injection d’une fabrique qui résout les dépendances au moment de l’exécution. Ces deux pratiques combinent des stratégies [Inversion de contrôle](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion).
- Évitez les appels à <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> dans `ConfigureServices` . L’appel de `BuildServiceProvider` se produit généralement lorsque le développeur souhaite résoudre un service dans `ConfigureServices` .
- Les services transitoires jetables sont capturés par le conteneur pour la suppression. Cela peut entraîner une fuite de mémoire si elle est résolue à partir du conteneur de niveau supérieur.
- Activez la validation de l’étendue pour vous assurer que l’application n’a pas de singletons qui capturent les services délimités. Pour plus d’informations, consultez [Validation de l’étendue](dependency-injection.md#scope-validation).

Comme pour toutes les recommandations, vous pouvez vous trouver dans des situations où il est nécessaire d’ignorer une recommandation. Les exceptions sont rares, principalement des cas spéciaux dans l’infrastructure elle-même.

L’injection de dépendance constitue une *alternative* aux modèles d’accès aux objets statiques/globaux. Il est possible que vous ne bénéficiez pas des avantages de l’injection de dépendances si vous la combinez avec l’accès aux objets statiques.

## <a name="see-also"></a>Voir aussi

- [Injection de dépendances dans .NET](dependency-injection.md)
