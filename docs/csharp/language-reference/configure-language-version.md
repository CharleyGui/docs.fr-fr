---
title: Gestion des versions du langage C# - Guide C#
description: En savoir plus sur C# la façon dont la version du langage est déterminée en fonction de votre projet et des raisons qui sous-tendent ce choix. Découvrez comment remplacer manuellement la valeur par défaut.
ms.date: 02/21/2020
ms.openlocfilehash: 2be76fdac471a7175b661d896b0da2910b3609f3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626762"
---
# <a name="c-language-versioning"></a>Gestion des versions du langage C#

Le compilateur C# le plus récent détermine une version du langage par défaut en fonction du ou des frameworks cibles de votre projet. Visual Studio ne fournit pas d’interface utilisateur pour modifier la valeur, mais vous pouvez la modifier en modifiant le fichier *csproj* . Le choix de la valeur par défaut garantit que vous utilisez la dernière version de langage compatible avec votre Framework cible. Vous bénéficiez d’un accès aux fonctionnalités de langage les plus récentes compatibles avec la cible de votre projet. Ce choix par défaut garantit également que vous n’utilisez pas un langage qui requiert des types ou un comportement d’exécution non disponible dans votre version cible de .NET Framework. Si vous choisissez une version de langue plus récente que la valeur par défaut, il est difficile de diagnostiquer les erreurs de compilation et d’exécution.

C#8,0 (et versions ultérieures) est pris en charge uniquement sur .NET Core 3. x et les versions plus récentes. La plupart des fonctionnalités les plus récentes requièrent des fonctionnalités de bibliothèque et d’exécution introduites dans .NET Core 3. x :

- L’implémentation par défaut des membres d’interface requiert de nouvelles fonctionnalités dans le CLR .NET Core 3,0.
- Les flux asynchrones nécessitent les nouveaux types <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>et <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.
- Les index et les plages nécessitent les nouveaux types <xref:System.Index?displayProperty=nameWithType> et <xref:System.Range?displayProperty=nameWithType>.
- Les types de référence Nullable utilisent plusieurs [attributs](../nullable-attributes.md) pour fournir de meilleurs avertissements. Ces attributs ont été ajoutés dans .NET Core 3,0. D’autres frameworks cibles n’ont pas été annotés avec l’un de ces attributs. Cela signifie que les avertissements Nullable peuvent ne pas refléter avec précision les problèmes potentiels.

## <a name="defaults"></a>Valeurs par défaut

Le compilateur détermine une valeur par défaut en fonction de ces règles :

|Framework cible|version|Version du langage C# par défaut|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|all|C# 7.3|

Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée. Vous utilisez les fonctionnalités les plus récentes avec cette préversion dans n’importe quel environnement, sans affecter les projets qui ciblent une version .NET Core publiée.

## <a name="override-a-default"></a>Remplacer les valeurs par défaut

Si vous devez spécifier votre version C# explicitement, vous pouvez le faire de plusieurs façons :

- Modifiez manuellement votre [fichier projet](#edit-the-project-file).
- Définissez la version du langage [pour plusieurs projets d’un sous-répertoire](#configure-multiple-projects).
- Configurez l’[option de compilateur `-langversion`](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Modifier le fichier projet

Vous pouvez définir la version du langage dans votre fichier projet. Par exemple, si vous souhaitez accéder explicitement aux fonctionnalités d’évaluation, ajoutez un élément comme suit :

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

La valeur `preview` utilise la dernière préversion disponible du langage C# que prend en charge votre compilateur.

### <a name="configure-multiple-projects"></a>Configurer plusieurs projets

Pour configurer plusieurs projets, vous pouvez créer un fichier **Directory. Build. props** contenant l’élément `<LangVersion>`. En règle générale, vous faites cela dans votre répertoire de solution. Ajoutez le code suivant à un fichier **Directory.build.props** dans votre répertoire de solution :

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Les builds dans tous les sous-répertoires du répertoire contenant ce fichier utiliseront la version préliminaire C# . Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Informations de référence sur la version du langage C#

Le tableau suivant montre toutes les versions actuelles du langage C#. Votre compilateur peut ne pas nécessairement comprendre chaque valeur si elle est plus ancienne. Si vous installez .NET Core 3,0 ou une version ultérieure, vous avez accès à tout ce qui est listé.

|Valeur|Signification|
|------------|-------------|
|preview|Le compilateur accepte toute la syntaxe de langage valide de la dernière préversion.|
|latest|Le compilateur accepte la syntaxe de la dernière version publiée du compilateur (versions mineures incluses).|
|latestMajor|Le compilateur accepte la syntaxe de la dernière version principale publiée du compilateur.|
|8.0|Le compilateur accepte uniquement la syntaxe incluse dans C# 8.0 ou une version antérieure.|
|7.3|Le compilateur accepte uniquement la syntaxe incluse dans C# 7.3 ou une version antérieure.|
|7.2|Le compilateur accepte uniquement la syntaxe incluse dans C# 7.2 ou une version antérieure.|
|7.1|Le compilateur accepte uniquement la syntaxe incluse dans C# 7.1 ou une version antérieure.|
|7|Le compilateur accepte uniquement la syntaxe incluse dans C# 7.0 ou une version antérieure.|
|6|Le compilateur accepte uniquement la syntaxe incluse dans C# 6.0 ou une version antérieure.|
|5|Le compilateur accepte uniquement la syntaxe incluse dans C# 5.0 ou une version antérieure.|
|4|Le compilateur accepte uniquement la syntaxe incluse dans C# 4.0 ou une version antérieure.|
|3|Le compilateur accepte uniquement la syntaxe incluse dans C# 3.0 ou une version antérieure.|
|ISO-2|Le compilateur accepte uniquement la syntaxe qui est incluse dans ISO/IEC C# 23270:2006 (2,0). |
|ISO-1|Le compilateur accepte uniquement la syntaxe qui est incluse dans la norme ISO C# /IEC 23270:2003 (1.0/1.2). |
