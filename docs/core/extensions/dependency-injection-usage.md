---
title: Utiliser l’injection de dépendances dans .NET
description: Découvrez comment utiliser l’injection de dépendances dans vos applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 11/13/2020
ms.topic: tutorial
no-loc:
- Transient
- Scoped
- Singleton
- Example
ms.openlocfilehash: b1e84685ad95372c4b2038e913199f7283135b71
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634517"
---
# <a name="tutorial-use-dependency-injection-in-net"></a>Didacticiel : utiliser l’injection de dépendances dans .NET

Ce didacticiel montre comment utiliser [l’injection de dépendances (di) dans .net](dependency-injection.md). Avec les *extensions Microsoft* , di est un citoyen de première classe dans lequel les services sont ajoutés et configurés dans un <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> . L' <xref:Microsoft.Extensions.Hosting.IHost> interface expose l' <xref:System.IServiceProvider> instance, qui joue le rôle de conteneur de tous les services inscrits.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> - Créer une application console .NET qui utilise l’injection de dépendances
> - Créer et configurer un [hôte générique](generic-host.md)
> - Écrire plusieurs interfaces et implémentations correspondantes
> - Utiliser la durée de vie et l’étendue du service pour DI

## <a name="prerequisites"></a>Prérequis

- [.Net Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.
- Vous êtes familiarisé avec la création d’applications .NET et l’installation de packages NuGet.

## <a name="create-a-new-console-application"></a>Créer une application console

À l’aide de la commande [dotnet New](../tools/dotnet-new.md) ou de l’Assistant Nouveau projet IDE, créez une nouvelle application console .NET nommée **ConsoleDI. Example**. Ajoutez le package NuGet [Microsoft. extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) au projet.

## <a name="add-interfaces"></a>Ajouter des interfaces

Ajoutez les interfaces suivantes au répertoire racine du projet :

*IOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

L' `IOperation` interface définit une seule `OperationId` propriété.

*Je Transient operation.cs*

::: code Language = "CSharp" source = "extraits/configuration/console-di/I Transient operation.cs" :::

*Je Scoped operation.cs*

::: code Language = "CSharp" source = "extraits/configuration/console-di/I Scoped operation.cs" :::

*Je Singleton operation.cs*

::: code Language = "CSharp" source = "extraits/configuration/console-di/I Singleton operation.cs" :::

Toutes les sous-interfaces de `IOperation` nom leur durée de vie de service prévue. Par exemple, « Transient » ou «» Singleton .

## <a name="add-default-implementation"></a>Ajouter une implémentation par défaut

Ajoutez l’implémentation par défaut suivante pour les diverses opérations :

*DefaultOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

`DefaultOperation`Implémente toutes les interfaces de marqueur nommées et initialise la `OperationId` propriété avec les quatre derniers caractères d’un nouvel identificateur global unique (Guid).

## <a name="add-service-that-requires-di"></a>Ajouter un service qui requiert DI

Ajoutez l’objet logger d’opération suivant, qui agit en tant que service à l’application console :

*OperationLogger.cs*

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

Le `OperationLogger` définit un constructeur qui requiert chacune des interfaces de marqueur susmentionnées, autrement dit ; `ITransientOperation` , `IScopedOperation` et `ISingletonOperation` . L’objet expose une méthode unique qui permet au consommateur d’enregistrer les opérations avec un `scope` paramètre donné. Lorsqu’elle est appelée, la `LogOperations` méthode journalise l’identificateur unique de chaque opération avec la chaîne et le message de l’étendue.

## <a name="register-services-for-di"></a>Inscrire des services pour DI

Mettez à jour *Program.cs* avec le code suivant :

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

> Chaque `services.Add{SERVICE_NAME}` méthode d’extension ajoute et configure éventuellement des services. Il est recommandé que les applications suivent cette convention. Placez les méthodes d’extension dans l’espace de noms <xref:Microsoft.Extensions.DependencyInjection?displayProperty=fullName> pour encapsuler des groupes d’inscriptions de service. L’inclusion de la partie espace `Microsoft.Extensions.DependencyInjection` de noms pour les méthodes d’extension di est également :
>
> - Permet de les afficher dans [IntelliSense](/visualstudio/ide/using-intellisense) sans ajouter de `using` blocs supplémentaires.
> - Empêche `using` des instructions excessives dans les `Program` `Startup` classes ou où ces méthodes d’extension sont généralement appelées.

L’application :

- Crée une <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance avec les [paramètres de binder par défaut](generic-host.md#default-builder-settings).
- Configure les services et les ajoute avec leur durée de vie de service correspondante.
- Appelle <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> et assigne une instance de <xref:Microsoft.Extensions.Hosting.IHost> .
- Appelle `ExemplifyScoping` , en passant le <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .

## <a name="conclusion"></a>Conclusion

L’application affiche une sortie similaire à l’exemple suivant :

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

À partir de la sortie de l’application, vous pouvez voir que :

- Transient les opérations sont toujours différentes, une nouvelle instance est créée avec chaque récupération du service.
- Scoped les opérations changent uniquement avec une nouvelle étendue, mais sont la même instance au sein d’une étendue.
- Singleton les opérations sont toujours les mêmes, une nouvelle instance n’est créée qu’une seule fois.

## <a name="see-also"></a>Voir aussi

* [Recommandations relatives à l’injection de dépendances](dependency-injection-guidelines.md)
* [Injection de dépendances dans ASP.NET Core](/aspnet/core/fundamentals/dependency-injection)
