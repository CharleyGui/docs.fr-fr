---
title: Gestion des versions du langage C# - Guide C#
description: Découvrez comment la version linguistique C est déterminée en fonction de votre projet et des raisons de ce choix. Apprenez à remplacer manuellement la valeur par défaut.
ms.date: 02/21/2020
ms.openlocfilehash: ef7275aad7638f52ecbfca1dfbdb962ae242fb48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399538"
---
# <a name="c-language-versioning"></a>Gestion des versions du langage C#

Le compilateur C# le plus récent détermine une version du langage par défaut en fonction du ou des frameworks cibles de votre projet. Visual Studio ne fournit pas d’interface utilisateur pour changer la valeur, mais vous pouvez la modifier en éditant le fichier *csproj.* Le choix par défaut vous assure d’utiliser la dernière version linguistique compatible avec votre cadre cible. Vous bénéficiez de l’accès aux dernières fonctionnalités linguistiques compatibles avec la cible de votre projet. Ce choix par défaut garantit également que vous n’utilisez pas un langage qui nécessite des types ou un comportement en temps d’exécution qui n’est pas disponible dans votre cadre cible. Le choix d’une version linguistique plus récente que la valeur par défaut peut causer des erreurs de compilation et de temps d’exécution.

Les règles de cet article s’appliquent au compilateur livré avec Visual Studio 2019 ou au .NET Core 3.0 SDK. Les compilateurs C# qui sont installés en même temps que Visual Studio 2017 ou les versions antérieures du kit SDK .NET Core ciblent C# 7.0 par défaut.

C 8.0 (et plus) n’est pris en charge que sur .NET Core 3.x et les versions plus nouvelles. Bon nombre des fonctionnalités les plus récentes nécessitent des fonctionnalités de bibliothèque et d’exécution introduites dans .NET Core 3.x :

- L’implémentation par défaut des membres de l’interface nécessite de nouvelles fonctionnalités dans le CLR .NET Core 3.0.
- Les flux Async nécessitent <xref:System.IAsyncDisposable?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>les <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>nouveaux types, , et .
- Les index et les gammes nécessitent les nouveaux types <xref:System.Index?displayProperty=nameWithType> et <xref:System.Range?displayProperty=nameWithType>.
- Les types de référence nuls utilisent plusieurs [attributs](../nullable-attributes.md) pour fournir de meilleurs avertissements. Ces attributs ont été ajoutés dans .NET Core 3.0. D’autres cadres cibles n’ont pas été annotés avec l’un de ces attributs. Cela signifie que les avertissements annulés peuvent ne pas refléter avec précision les problèmes potentiels.

## <a name="defaults"></a>Valeurs par défaut

Le compilateur détermine une valeur par défaut en fonction de ces règles :

|Version cible de .NET Framework|version|Version du langage C# par défaut|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|all|C# 7.3|

Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée. Vous utilisez les dernières fonctionnalités avec cet aperçu dans n’importe quel environnement, sans affecter les projets qui ciblent une version .NET Core publiée.

## <a name="override-a-default"></a>Remplacer les valeurs par défaut

Si vous devez spécifier votre version C# explicitement, vous pouvez le faire de plusieurs façons :

- Modifiez manuellement votre [fichier projet](#edit-the-project-file).
- Définissez la version du langage [pour plusieurs projets d’un sous-répertoire](#configure-multiple-projects).
- Configurer [ `-langversion` l’option compilateur](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Modifier le fichier projet

Vous pouvez définir la version du langage dans votre fichier projet. Par exemple, si vous souhaitez accéder explicitement aux fonctionnalités d’évaluation, ajoutez un élément comme suit :

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

La valeur `preview` utilise la dernière préversion disponible du langage C# que prend en charge votre compilateur.

### <a name="configure-multiple-projects"></a>Configurer plusieurs projets

Pour configurer plusieurs projets, vous pouvez créer un fichier `<LangVersion>` **Directory.Build.props** qui contient l’élément. En règle générale, vous faites cela dans votre répertoire de solution. Ajoutez ce qui suit à un fichier **Directory.Build.props** dans votre répertoire de solutions :

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Les builds dans toutes les sous-direction de l’annuaire contenant ce fichier utiliseront la version de prévisualisation C. Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Informations de référence sur la version du langage C#

Le tableau suivant montre toutes les versions actuelles du langage C#. Votre compilateur peut ne pas nécessairement comprendre toutes les valeurs si elle est plus ancienne. Si vous installez .NET Core 3.0 ou plus tard, alors vous avez accès à tout ce qui est répertorié.

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
|ISO-2|Le compilateur n’accepte que la syntaxe incluse dans ISO/IEC 23270:2006 CMD (2,0). |
|ISO-1|Le compilateur n’accepte que la syntaxe incluse dans ISO/IEC 23270:2003 CMD (1,0/1,2). |
