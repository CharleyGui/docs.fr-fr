---
title: Gestion des versions du langage C# - Guide C#
description: Découvrez comment la version du langage C# est déterminée en fonction de votre projet et des raisons qui sous-tendent ce choix. Découvrez comment remplacer manuellement la valeur par défaut.
ms.custom: updateeachrelease
ms.date: 08/11/2020
ms.openlocfilehash: b022b726861bd6ea45b188df44549dc279d34a74
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96598921"
---
# <a name="c-language-versioning"></a>Gestion des versions du langage C#

Le compilateur C# le plus récent détermine une version du langage par défaut en fonction du ou des frameworks cibles de votre projet. Visual Studio ne fournit pas d’interface utilisateur pour modifier la valeur, mais vous pouvez la modifier en modifiant le fichier *csproj* . Le choix de la valeur par défaut garantit que vous utilisez la dernière version de langage compatible avec votre Framework cible. Vous bénéficiez d’un accès aux fonctionnalités de langage les plus récentes compatibles avec la cible de votre projet. Ce choix par défaut garantit également que vous n’utilisez pas un langage qui requiert des types ou un comportement d’exécution non disponible dans votre version cible de .NET Framework. Si vous choisissez une version de langue plus récente que la valeur par défaut, il est difficile de diagnostiquer les erreurs de compilation et d’exécution.

Les règles de cet article s’appliquent au compilateur fourni avec Visual Studio 2019 ou le kit de développement logiciel (SDK) .NET. Les compilateurs C# qui sont installés en même temps que Visual Studio 2017 ou les versions antérieures du kit SDK .NET Core ciblent C# 7.0 par défaut.

C# 8,0 est pris en charge uniquement sur .NET Core 3. x et les versions plus récentes. La plupart des fonctionnalités les plus récentes requièrent des fonctionnalités de bibliothèque et d’exécution introduites dans .NET Core 3. x :

- L’implémentation de l' [interface par défaut](../whats-new/csharp-8.md#default-interface-methods) nécessite de nouvelles fonctionnalités dans le CLR .net Core 3,0.
- Les [flux asynchrones](../whats-new/csharp-8.md#asynchronous-streams) requièrent les nouveaux types <xref:System.IAsyncDisposable?displayProperty=nameWithType> , <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .
- Les [index et les plages](../whats-new/csharp-8.md#indices-and-ranges) nécessitent les nouveaux types <xref:System.Index?displayProperty=nameWithType> et <xref:System.Range?displayProperty=nameWithType> .
- Les [types de référence Nullable](../whats-new/csharp-8.md#nullable-reference-types) utilisent plusieurs [attributs](attributes/nullable-analysis.md) pour fournir de meilleurs avertissements. Ces attributs ont été ajoutés dans .NET Core 3,0. D’autres frameworks cibles n’ont pas été annotés avec l’un de ces attributs. Cela signifie que les avertissements Nullable peuvent ne pas refléter avec précision les problèmes potentiels.

C# 9,0 est pris en charge uniquement sur .NET 5 et les versions plus récentes.

## <a name="defaults"></a>Valeurs par défaut

Le compilateur détermine une valeur par défaut en fonction de ces règles :

| Version cible de .NET Framework | version | Version du langage C# par défaut |
|------------------|---------|-----------------------------|
| .NET             | 5     | C# 9.0                      |
| .NET Core        | 3.x     | C# 8.0                      |
| .NET Core        | 2.x     | C# 7.3                      |
| .NET Standard    | 2.1     | C# 8.0                      |
| .NET Standard    | 2.0     | C# 7.3                      |
| .NET Standard    | 1.x     | C# 7.3                      |
| .NET Framework   | all     | C# 7.3                      |

Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée. Vous utilisez les fonctionnalités les plus récentes avec cette préversion dans n’importe quel environnement, sans affecter les projets qui ciblent une version .NET Core publiée.

> [!IMPORTANT]
> Visual Studio 2017 a ajouté une `<LangVersion>latest</LangVersion>` entrée aux fichiers projet qu’il a créés. Cela signifiait *C# 7,0* quand il a été ajouté. Toutefois, une fois que vous avez mis à niveau vers Visual Studio 2019, cela signifie la dernière version publiée, quelle que soit la version cible de .NET Framework. Ces projets [remplacent désormais le comportement par défaut](#override-a-default). Vous devez modifier le fichier projet et supprimer ce nœud. Votre projet utilisera ensuite la version du compilateur recommandée pour votre version cible de .NET Framework.

## <a name="override-a-default"></a>Remplacer les valeurs par défaut

Si vous devez spécifier votre version C# explicitement, vous pouvez le faire de plusieurs façons :

- Modifiez manuellement votre [fichier projet](#edit-the-project-file).
- Définissez la version du langage [pour plusieurs projets d’un sous-répertoire](#configure-multiple-projects).
- Configurez l' [ `-langversion` option du compilateur](compiler-options/langversion-compiler-option.md).

> [!TIP]
> Pour connaître la version linguistique que vous utilisez actuellement, mettez- `#error version` la (respecte la casse) dans votre code. Ainsi, le compilateur produit un diagnostic, CS8304, avec un message contenant la version du compilateur utilisée et la version de langage actuellement sélectionnée.

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

Le tableau suivant montre toutes les versions actuelles du langage C#. Votre compilateur peut ne pas nécessairement comprendre chaque valeur si elle est plus ancienne. Si vous installez le dernier Kit de développement logiciel (SDK) .NET, vous avez accès à tout ce qui est listé.

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
> 8.0
> 9.0 (default)
> latestmajor
> preview
> latest
> ```
