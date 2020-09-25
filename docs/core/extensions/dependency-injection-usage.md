---
title: Utiliser l’injection de dépendances dans .NET
description: Découvrez comment utiliser l’injection de dépendances dans vos applications .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
ms.openlocfilehash: f2298cb0be6d555a7636903dc251f022a6a62a43
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247893"
---
# <a name="tutorial-use-dependency-injection-in-net"></a>Didacticiel : utiliser l’injection de dépendances dans .NET

Ce didacticiel montre comment utiliser [l’injection de dépendances (di) dans .net](dependency-injection.md). Avec les *extensions Microsoft*, di est un citoyen de première classe dans lequel les services sont ajoutés et configurés dans un <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> . L' <xref:Microsoft.Extensions.Hosting.IHost> interface expose l' <xref:System.IServiceProvider> instance, qui joue le rôle de conteneur de tous les services inscrits.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> - Créer une application console .NET qui utilise l’injection de dépendances
> - Créer et configurer un [hôte générique](generic-host.md)
> - Écrire plusieurs interfaces et implémentations correspondantes
> - Utiliser la durée de vie et l’étendue du service pour DI

## <a name="prerequisites"></a>Prérequis

- [Kit de développement logiciel (SDK) .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.
- Un environnement de développement intégré (IDE), [Visual Studio, Visual Studio code ou Visual Studio pour Mac](https://visualstudio.microsoft.com) sont tous des choix valides.
- Vous êtes familiarisé avec la création d’applications .NET et l’installation de packages NuGet.

## <a name="create-a-new-console-application"></a>Créer une application console

À l’aide de la commande [dotnet New](../tools/dotnet-new.md) ou de l’Assistant Nouveau projet IDE, créez une nouvelle application console .NET nommée **ConsoleDI. example**. Ajoutez le package NuGet [Microsoft. extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) au projet.

## <a name="add-interfaces"></a>Ajouter des interfaces

Ajoutez les interfaces suivantes au répertoire racine du projet :

*IOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

L' `IOperation` interface définit une seule `OperationId` propriété.

*ITransientOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::

*IScopedOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::

*ISingletonOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::

Toutes les sous-interfaces de `IOperation` nom leur durée de vie de service prévue. Par exemple, « Transient » ou « singleton ».

## <a name="add-default-implementation"></a>Ajouter une implémentation par défaut

Ajoutez l’implémentation par défaut suivante pour les diverses opérations :

*DefaultOperation.cs*

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

`DefaultOperation`Implémente toutes les interfaces nommées/de marqueur et initialise la `OperationId` propriété aux quatre derniers caractères d’un nouvel identificateur global unique (Guid).

## <a name="add-service-that-requires-di"></a>Ajouter un service qui requiert DI

Ajoutez l’objet logger d’opération suivant, qui agit en tant que service à votre application console :

*OperationLogger.cs*

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

Le `OperationLogger` définit un constructeur qui requiert chacune des interfaces de marqueur susmentionnées, autrement dit ; `ITransientOperation` , `IScopedOperation` et `ISingletonOperation` . L’objet expose une méthode unique qui permet au consommateur d’enregistrer les opérations avec un `scope` paramètre donné. Lorsqu’elle est appelée, la `LogOperations` méthode enregistre l’identificateur unique de chaque opération avec la chaîne et le message de l’étendue.

## <a name="register-services-for-di"></a>Inscrire des services pour DI

Enfin, mettez à jour le fichier *Program.cs* pour qu’il corresponde à ce qui suit :

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

L’application :

- Crée une <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance avec les [paramètres de binder par défaut](generic-host.md#default-builder-settings).
- Configure les services et les ajoute avec leur durée de vie de service correspondante.
- Appelle <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> et assigne une instance de <xref:Microsoft.Extensions.Hosting.IHost> .
- Appelle `ExemplifyScoping` , en passant le <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .

## <a name="conclusion"></a>Conclusion

L’application produit une sortie similaire à l’exemple suivant :

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

- Les opérations transitoires sont toujours différentes, ce qui signifie qu’une nouvelle instance est créée avec chaque récupération du service.
- Les opérations délimitées changent uniquement avec une nouvelle étendue, mais sont la même instance au sein d’une étendue.
- Les opérations Singleton sont toujours les mêmes, ce qui signifie qu’une nouvelle instance n’est créée qu’une seule fois.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Instructions relatives à l’injection de dépendances](dependency-injection-guidelines.md)
