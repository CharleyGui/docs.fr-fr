---
title: Nouveautés de .NET 5
description: Découvrez .NET 5, une plateforme de développement multiplateforme et open source qui est la prochaine évolution de .NET Core.
ms.date: 11/18/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 1101e218f225eed2a2013ed9e19b60f4ece57738
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982299"
---
# <a name="whats-new-in-net-5"></a>Nouveautés de .NET 5

.NET 5,0 est la prochaine version majeure de .NET Core suivant 3,1. Nous avons nommé cette nouvelle version .NET 5,0 au lieu de .NET Core 4,0 pour deux raisons :

- Nous avons ignoré les numéros de version 4. x pour éviter toute confusion avec .NET Framework 4. x.
- Nous avons supprimé « Core » du nom pour insister sur le fait qu’il s’agit de la principale implémentation de .NET. .NET 5,0 prend en charge davantage de types d’applications et de plateformes que .NET Core ou .NET Framework.

ASP.NET Core 5,0 est basé sur .NET 5,0, mais conserve le nom « Core » pour éviter qu’il ne soit confus avec ASP.NET MVC 5. De même, Entity Framework Core 5,0 conserve le nom « Core » pour éviter qu’il ne soit confus avec Entity Framework 5 et 6.

.NET 5,0 comprend les améliorations et les nouvelles fonctionnalités suivantes par rapport à .NET Core 3,1 :

- [Mises à jour C#](#c-updates)
- [Mises à jour de F #](#f-updates)
- [Mises à jour de Visual Basic](#visual-basic-updates)
- [System.Text.Jssur les nouvelles fonctionnalités](#systemtextjson-new-features)
- [Applications à fichier unique](deploying/single-file.md)
- [Suppression d’application](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- Intrinsèques Windows ARM64 et ARM64
- Prise en charge des outils pour le débogage de vidage
- Les bibliothèques Runtime sont 80% annotées pour les [types référence Nullable](../csharp/nullable-references.md)
- Améliorations des performances :
  - [Garbage collection (GC)](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [System.Text.Json](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [System.Text.RegularExpressions](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [Regroupement ValueTask asynchrone](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [Optimisations de la taille du conteneur](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [Beaucoup plus de zones](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a>.NET 5,0 ne remplace pas .NET Framework

.NET 5,0 est la principale implémentation de .NET à l’avenir et .NET Framework 4. x est toujours pris en charge.

Il n’est pas prévu de porter les technologies suivantes de .NET Framework vers .NET 5,0, mais il existe des alternatives dans .NET 5,0 :

| Technology            | Alternative recommandée                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------|
| Web Forms             | ASP.NET Core [éblouissant](/aspnet/core/blazor) ou [Razor pages](/aspnet/core/tutorials/razor-pages) |
| Windows Workflow (WF) | [CoreWF Open source](https://github.com/UiPath-Open/corewf)                                     |

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

L’implémentation d’origine de [Windows Communication Foundation (WCF)](../framework/wcf/index.md) était uniquement prise en charge sur Windows. Toutefois, il existe un port client disponible à partir de .NET Foundation. Il est entièrement [Open source](https://github.com/dotnet/wcf), multiplateforme et pris en charge par Microsoft. Les packages NuGet principaux sont répertoriés ci-dessous :

- [System.ServiceModel.Duplex](https://www.nuget.org/packages/System.ServiceModel.Duplex)
- [System. ServiceModel. Federation](https://www.nuget.org/packages/System.ServiceModel.Federation)
- [System.ServiceModel.Http](https://www.nuget.org/packages/System.ServiceModel.Http)
- [System.ServiceModel.NetTcp](https://www.nuget.org/packages/System.ServiceModel.NetTcp)
- [System.ServiceModel.Primitives](https://www.nuget.org/packages/System.ServiceModel.Primitives)
- [System. ServiceModel. Security](https://www.nuget.org/packages/System.ServiceModel.Security)

La Communauté gère les composants serveur qui complètent les bibliothèques clientes mentionnées ci-dessus. Le référentiel GitHub se trouve sur [CoreWCF](https://github.com/CoreWCF/CoreWCF). Les composants serveur ne sont _pas_ officiellement pris en charge par Microsoft. Pour une alternative à WCF, pensez à [gRPC](/aspnet/core/grpc).

## <a name="net-50-doesnt-replace-net-standard"></a>.NET 5,0 ne remplace pas .NET Standard

Le développement d’une nouvelle application peut spécifier le `net5.0` moniker du Framework cible (TFM) pour tous les types de projets, y compris les bibliothèques de classes. Le partage de code entre les charges de travail .NET 5 est simplifié en ce que vous avez tout ce dont vous avez besoin `net5.0` TFM.

Pour les applications et les bibliothèques .NET 5,0, le `net5.0` moniker du Framework cible (TFM) combine et remplace les `netcoreapp` `netstandard` TFM. Toutefois, si vous envisagez de partager du code entre des charges de travail .NET Framework, .NET Core et .NET 5, vous pouvez le faire en spécifiant `netstandard2.0` comme TFM. Pour plus d'informations, consultez [.NET Standard](../standard/net-standard.md).

## <a name="c-updates"></a>Mises à jour C#

Les développeurs qui écrivent des applications .NET 5 auront accès à la version et aux fonctionnalités C# les plus récentes. .NET 5 est associé à C# 9, qui offre de nombreuses nouvelles fonctionnalités au langage. Voici quelques points importants :

- Enregistrements : types référence avec une sémantique d’égalité basée sur des valeurs et une mutation non destructrice prise en charge par une nouvelle `with` expression.
- Critères spéciaux relationnels : étend les fonctionnalités de critères spéciaux aux opérateurs relationnels pour les évaluations comparatives et les expressions, y compris les modèles logiques, les nouveaux mots clés `and` , `or` et `not` .
- Instructions de niveau supérieur : comme un moyen d’accélérer l’adoption et l’apprentissage de C#, la `Main` méthode peut être omise et l’application est aussi simple que les éléments suivants :

   ```csharp
   System.Console.Write("Hello world!");
   ```

- Pointeurs fonction : constructions de langage qui exposent les OpCodes de langage intermédiaire (IL) suivants : `ldftn` et `calli` .

Pour plus d’informations sur les fonctionnalités C# 9 disponibles, consultez [Nouveautés de c# 9](../csharp/whats-new/csharp-9.md).

### <a name="source-generators"></a>Générateurs de sources

En plus de certaines des nouvelles fonctionnalités en C#, les générateurs de code source s’intègrent dans des projets de développement. Les générateurs de source autorisent le code qui s’exécute pendant la compilation à inspecter votre programme et à produire des fichiers supplémentaires qui sont compilés avec le reste de votre code.

Pour plus d’informations sur les générateurs de source, consultez [Présentation des générateurs de source c#](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) et [exemples de générateur de source c#](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples).

## <a name="f-updates"></a>Mises à jour de F #

F # est le langage de programmation fonctionnel .NET et, avec .NET 5, les développeurs ont accès à F # 5. Voici plusieurs nouvelles fonctionnalités de F # 5 :

### <a name="interpolated-strings"></a>Chaînes interpolées

À l’instar de la chaîne interpolée en C#, et même de JavaScript, F # prend en charge l’interpolation de chaîne de base.

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

Cela est similaire à la [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) fonction qui met en forme une chaîne en fonction des entrées de type sécurisé. <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

## <a name="visual-basic-updates"></a>Mises à jour de Visual Basic

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

Pour plus d’informations sur les modèles de projet à partir de l’interface CLI .NET, consultez [`dotnet new`](tools/dotnet-new.md) .

## <a name="systemtextjson-new-features"></a>System.Text.Jssur les nouvelles fonctionnalités

Il existe de nouvelles fonctionnalités dans et pour [System.Text.Jssur](../standard/serialization/system-text-json-overview.md):

- [Conserver les références et gérer les références circulaires](../standard/serialization/system-text-json-how-to.md#preserve-references-and-handle-circular-references)
- [Méthodes d’extension HttpClient et HttpContent](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [Autoriser ou écrire des nombres entre guillemets](../standard/serialization/system-text-json-how-to.md#allow-or-write-numbers-in-quotes)
- [Prendre en charge les types immuables et les enregistrements C# 9](../standard/serialization/system-text-json-how-to.md#immutable-types-and-records)
- [Prendre en charge les accesseurs de propriété non publics](../standard/serialization/system-text-json-how-to.md#non-public-property-accessors)
- [champs de support](../standard/serialization/system-text-json-how-to.md#include-fields)
- [Ignorer conditionnellement les propriétés](../standard/serialization/system-text-json-how-to.md#ignore-properties)
- [Prise en charge des dictionnaires non-clés-chaîne](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [Autoriser les convertisseurs personnalisés à gérer la valeur null](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [Copier JsonSerializerOptions](../standard/serialization/system-text-json-how-to.md#copy-jsonserializeroptions)
- [Créer des JsonSerializerOptions avec des valeurs par défaut Web](../standard/serialization/system-text-json-how-to.md#web-defaults-for-jsonserializeroptions)

## <a name="see-also"></a>Voir aussi

- [Le trajet vers un .NET](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [Améliorations des performances dans .NET 5](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [Télécharger le Kit de développement logiciel (SDK) .NET](https://dotnet.microsoft.com/download)
