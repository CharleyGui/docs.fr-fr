---
title: Évolution de .NET Core vers .NET 5
description: Découvrez .NET 5, une plateforme de développement multiplateforme et open source qui est la prochaine évolution de .NET Core.
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: f9fd0d09dbb65c2367ac268ea4a7055a299a7586
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89471988"
---
# <a name="the-evolution-of-net-core-to-net-5"></a>Évolution de .NET Core vers .NET 5

Cet article détaille ce qui est inclus dans .NET 5, qui est la prochaine version de .NET Core suivant 3,1. Le numéro de version est 5,0 pour éviter toute confusion avec .NET Framework 4. x. « Core » est supprimé du nom, car il s’agit de l’implémentation principale de .NET à l’avenir. .NET 5 prend en charge davantage de types d’applications et de plateformes que .NET Core ou .NET Framework.

L’avènement de .NET Core a évolué l’écosystème .NET de manière attrayante. Il a évolué en tant que projet open source sur GitHub, célébrant les contributions de la communauté et remarquer amélioré au fil du temps.

.NET Core présente plusieurs caractéristiques principales :

> [!div class="checklist"]
>
> - Système multiplateforme
> - Open source
> - Installation côte à côte
> - Petits fichiers de projet (style SDK)
> - Déploiement flexible

.NET 5 étend ces caractéristiques, ce qui apporte des améliorations incrémentielles :

- Applications à fichier unique
- Intrinsèques Windows ARM64 et ARM64
- Amélioration des performances :
  - [Garbage collection (GC)](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [System.Text.Json](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [System.Text.RegularExpressions](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [Regroupement ValueTask asynchrone](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [Beaucoup plus de zones](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- Optimisations de la taille du conteneur
- [Suppression d’application](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [Améliorations du compilateur C#](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- Prise en charge des outils pour le débogage de vidage
- La plateforme est 80% annotée pour les [types de référence Nullable](csharp/nullable-references.md)

### <a name="what-net-5-is-not"></a>Ce que .NET 5 n’est pas

.NET 5 n’est pas un substitut pour .NET Framework. Il n’est pas prévu de porter les technologies suivantes de .NET Framework vers .NET 5, mais il existe des alternatives prises en charge incluses dans .NET 5 :

| Technologie                             | Recommandation                                              |
|----------------------------------------|-------------------------------------------------------------|
| Web Forms                              | [ASP.NET Core éblouissant](/aspnet/core/blazor)                  |
| Windows Communication Foundation (WCF) | [gRPC](/aspnet/core/grpc)                                   |
| Windows Workflow (WF)                  | [CoreWF Open source](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a>.NET Standard

Le développement d’une nouvelle application peut spécifier le `net5.0` moniker du Framework cible (TFM) pour tous les types de projets, y compris les bibliothèques de classes. Le partage de code entre les charges de travail .NET 5 est simplifié en ce que vous avez tout ce dont vous avez besoin `net5.0` TFM.

Le `net5.0` TFM combine et remplace `netcoreapp` les `netstandard` noms. Ce TFM inclut généralement des technologies qui fonctionnent sur plusieurs plateformes, comme c’est le cas avec .NET Standard. Toutefois, si vous envisagez de partager du code entre des charges de travail de .NET Framework, .NET Core et .NET 5, vous pouvez le faire en spécifiant `netstandard2.0` comme TFM. Pour plus d’informations, consultez [comment spécifier des frameworks cibles](standard/frameworks.md#how-to-specify-target-frameworks).

## <a name="language-updates"></a>Mises à jour du langage

Avec .NET 5, les langages de programmation .NET continuent à s’améliorer.

### <a name="c-updates"></a>Mises à jour C#

Les développeurs qui écrivent des applications .NET 5 auront accès à la version et aux fonctionnalités C# les plus récentes. .NET 5 est associé à C# 9. C# 9 apporte de nombreuses nouvelles fonctionnalités au langage. Voici quelques points importants :

- Enregistrements : types référence immuables qui se comportent comme des types valeur et introduisent le nouveau `with` mot clé dans le langage.
- Critères spéciaux relationnels : étend les fonctionnalités de critères spéciaux aux opérateurs relationnels pour les évaluations comparatives et les expressions, y compris les modèles logiques, les nouveaux mots clés `and` , `or` et `not` .
- Instructions de niveau supérieur : comme un moyen d’accélérer l’adoption et l’apprentissage de C#, la `Main` méthode peut être omise et l’application est aussi simple que les éléments suivants :

   ```csharp
   System.Console.Write("Hello world!");
   ```

- Pointeurs fonctionnels : constructions de langage qui exposent le langage intermédiaire (IL) les OpCodes `ldftn` et `calli` .

Pour plus d’informations sur les fonctionnalités C# 9 disponibles, consultez [Nouveautés de c# 9](csharp/whats-new/csharp-9.md).

#### <a name="source-generators"></a>Générateurs de sources

En plus de certaines des nouvelles fonctionnalités en C#, les générateurs de code source s’intègrent dans des projets de développement. Les générateurs de source autorisent le code qui s’exécute pendant la compilation à inspecter votre programme et à produire des fichiers supplémentaires qui sont compilés avec le reste de votre code.

Pour plus d’informations sur les générateurs de source, consultez [Présentation des générateurs de source c#](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) et [exemples de générateur de source c#](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).

### <a name="f-updates"></a>Mises à jour de F #

F # est le langage de programmation fonctionnel .NET et, avec .NET 5, les développeurs ont accès à F # 5. Voici plusieurs nouvelles fonctionnalités de F # 5 :

#### <a name="interpolated-strings"></a>Chaînes interpolées

Semblable à la chaîne interpolée en C#, et même JavaScript-F # prend en charge l’interpolation de chaîne de base.

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

Outre l’interpolation de chaîne de base, il existe une interpolation typée. Avec l’interpolation typée, un type donné doit correspondre au spécificateur de format.

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

Cela est similaire à la [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) fonction qui met en forme une chaîne en fonction des entrées de type sécurisé. Pour plus d’informations, consultez [what’s New in F # 5](fsharp/whats-new/fsharp-50.md) .

### <a name="visual-basic-updates"></a>Mises à jour de Visual Basic

Il n’existe aucune nouvelle fonctionnalité de langage pour Visual Basic dans .NET 5. Toutefois, avec .NET 5, la prise en charge Visual Basic est étendue à :

| Description                            | Paramètre `dotnet new` |
|----------------------------------------|------------------------|
| Application console                    | `console`              |
| Bibliothèque de classes                          | `classlib`             |
| Application WPF                        | `wpf`                  |
| Bibliothèque de classes WPF                      | `wpflib`               |
| Bibliothèque de contrôles personnalisés WPF             | `wpfcustomcontrollib`  |
| Bibliothèque de contrôles utilisateur WPF               | `wpfusercontrollib`    |
| Application Windows Forms (WinForms)   | `winforms`             |
| Bibliothèque de classes Windows Forms (WinForms) | `winformslib`          |
| Projet de test unitaire                      | `mstest`               |
| Projet de test NUnit 3                   | `nunit`                |
| Élément de test NUnit 3                      | `nunit-test`           |
| Projet de test xUnit                     | `xunit`                |

Pour plus d’informations sur les modèles de projet à partir de l’interface CLI .NET, consultez [`dotnet new`](core/tools/dotnet-new.md) .

## <a name="net-maui"></a>MAUI .NET

.NET MAUI est une évolution du Xamarin. Forms Toolkit de plus en plus populaire et est open source sur GitHub à l’adresse [dotnet/Maui](https://github.com/dotnet/maui). Avec .NET MAUI, le choix pour les développeurs .NET est simplifié, fournissant une pile unique qui prend en charge toutes les charges de travail modernes : Android, iOS, macOS et Windows. Avec .NET MAUI, vous bénéficiez d’une expérience de développement de projet unique qui cible plusieurs plateformes et appareils.

> [!IMPORTANT]
> .NET MAUI est en version préliminaire. Vous trouverez un exemple de code source sur [xamarin/net6-Samples](https://github.com/xamarin/net6-samples).

### <a name="model-view-update-pattern"></a>Modèle Model-View-Update

Les développeurs aiment les modèles de développement modernes. Une approche Fluent du développement de l’interface utilisateur, inspirée par « l’architecture Elm », est le modèle [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) ou MVU. MVU favorise un traitement unidirectionnel des données et de la gestion de l’État, ainsi qu’une expérience de développement Code First qui met à jour rapidement l’interface utilisateur en appliquant uniquement les modifications nécessaires.

À titre d’exemple, considérez le compteur suivant écrit dans .NET MAUI à l’aide du modèle MVU :

```csharp
readonly State<int> _count = 0;

[Body]
View body() => new StackLayout
{
    new Label("Welcome to .NET MAUI!"),
    new Button(
        () => $"You clicked {_count} times.",
        () => ++ _count.Value)
    )
};
```

Pour plus d’informations, consultez la feuille de [route .net Maui](https://github.com/dotnet/maui/wiki/Roadmap)et présentation de l’article [.net Maui](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .

## <a name="see-also"></a>Voir aussi

- [Le trajet vers un .NET](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [Améliorations des performances dans .NET 5](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
