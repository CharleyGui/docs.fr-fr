---
title: Gestion des versions du langage C# - Guide C#
description: Découvrez comment la version du langage C# est déterminée en fonction de votre projet et des raisons qui sous-tendent ce choix. Découvrez comment remplacer manuellement la valeur par défaut.
ms.custom: updateeachrelease
ms.date: 05/20/2020
ms.openlocfilehash: a27f3210f399f1bed190c18d778cf3824772d576
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656849"
---
# <a name="c-language-versioning"></a>Gestion des versions du langage C#

Le compilateur C# le plus récent détermine une version du langage par défaut en fonction du ou des frameworks cibles de votre projet. Visual Studio ne fournit pas d’interface utilisateur pour modifier la valeur, mais vous pouvez la modifier en modifiant le fichier *csproj* . Le choix de la valeur par défaut garantit que vous utilisez la dernière version de langage compatible avec votre Framework cible. Vous bénéficiez d’un accès aux fonctionnalités de langage les plus récentes compatibles avec la cible de votre projet. Ce choix par défaut garantit également que vous n’utilisez pas un langage qui requiert des types ou un comportement d’exécution non disponible dans votre version cible de .NET Framework. Si vous choisissez une version de langue plus récente que la valeur par défaut, il est difficile de diagnostiquer les erreurs de compilation et d’exécution.

Les règles de cet article s’appliquent au compilateur fourni avec Visual Studio 2019 ou le kit de développement logiciel (SDK) .NET Core 3,0. Les compilateurs C# qui sont installés en même temps que Visual Studio 2017 ou les versions antérieures du kit SDK .NET Core ciblent C# 7.0 par défaut.

C# 8,0 (et versions ultérieures) est pris en charge uniquement sur .NET Core 3. x et les versions plus récentes. La plupart des fonctionnalités les plus récentes requièrent des fonctionnalités de bibliothèque et d’exécution introduites dans .NET Core 3. x :

- L’implémentation de l' [interface par défaut](../whats-new/csharp-8.md#default-interface-methods) nécessite de nouvelles fonctionnalités dans le CLR .net Core 3,0.
- Les [flux asynchrones](../whats-new/csharp-8.md#asynchronous-streams) requièrent les nouveaux types <xref:System.IAsyncDisposable?displayProperty=nameWithType> , <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .
- Les [index et les plages](../whats-new/csharp-8.md#indices-and-ranges) nécessitent les nouveaux types <xref:System.Index?displayProperty=nameWithType> et <xref:System.Range?displayProperty=nameWithType> .
- Les [types de référence Nullable](../whats-new/csharp-8.md#nullable-reference-types) utilisent plusieurs [attributs](attributes/nullable-analysis.md) pour fournir de meilleurs avertissements. Ces attributs ont été ajoutés dans .NET Core 3,0. D’autres frameworks cibles n’ont pas été annotés avec l’un de ces attributs. Cela signifie que les avertissements Nullable peuvent ne pas refléter avec précision les problèmes potentiels.

## <a name="defaults"></a>Valeurs par défaut

Le compilateur détermine une valeur par défaut en fonction de ces règles :

| Version cible de .NET Framework | version | Version du langage C# par défaut |
|------------------|---------|-----------------------------|
| .NET Core        | 3.x     | C# 8.0                      |
| .NET Core        | 2.x     | C# 7.3                      |
| .NET Standard    | 2.1     | C# 8.0                      |
| .NET Standard    | 2.0     | C# 7.3                      |
| .NET Standard    | 1.x     | C# 7.3                      |
| .NET Framework   | all     | C# 7.3                      |

Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée. Vous utilisez les fonctionnalités les plus récentes avec cette préversion dans n’importe quel environnement, sans affecter les projets qui ciblent une version .NET Core publiée.

## <a name="override-a-default"></a>Remplacer les valeurs par défaut

Si vous devez spécifier votre version C# explicitement, vous pouvez le faire de plusieurs façons :

- Modifiez manuellement votre [fichier projet](#edit-the-project-file).
- Définissez la version du langage [pour plusieurs projets d’un sous-répertoire](#configure-multiple-projects).
- Configurez l' [ `-langversion` option du compilateur](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Modifier le fichier projet

Vous pouvez définir la version du langage dans votre fichier projet. Par exemple, si vous souhaitez accéder explicitement aux fonctionnalités d’évaluation, ajoutez un élément comme suit :

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

La valeur `preview` utilise la dernière préversion disponible du langage C# que prend en charge votre compilateur.

### <a name="configure-multiple-projects"></a>Configurer plusieurs projets

Pour configurer plusieurs projets, vous pouvez créer un fichier **Directory. Build. props** qui contient l' `<LangVersion>` élément. En règle générale, vous faites cela dans votre répertoire de solution. Ajoutez le code suivant à un fichier **Directory. Build. props** dans le répertoire de votre solution :

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Les builds dans tous les sous-répertoires du répertoire contenant ce fichier utiliseront la version d’évaluation en C#. Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Informations de référence sur la version du langage C#

Le tableau suivant montre toutes les versions actuelles du langage C#. Votre compilateur peut ne pas nécessairement comprendre chaque valeur si elle est plus ancienne. Si vous installez .NET Core 3,0 ou une version ultérieure, vous avez accès à tout ce qui est listé.

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> Ouvrez le [invite de commandes développeur pour Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), puis exécutez la commande suivante pour afficher la liste des versions de langue disponibles sur votre ordinateur.
>
> ```CMD
> csc -langversion:?
> ```
>
> En cas de question de l’option [de compilation-langversion](compiler-options/langversion-compiler-option.md) comme ceci, imprimera un résultat similaire à ce qui suit :
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
