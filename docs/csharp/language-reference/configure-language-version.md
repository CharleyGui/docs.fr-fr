---
title: Gestion des versions du langage C# - Guide C#
description: Découvrez comment la version du langage C# est déterminée en fonction de votre projet, et les différentes valeurs que vous pouvez y ajuster manuellement.
ms.date: 07/10/2019
ms.openlocfilehash: 3c1035d983660ea0a945e4d4b7b72c69736c90cb
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980130"
---
# <a name="c-language-versioning"></a>Gestion des versions du langage C#

Le compilateur C# le plus récent détermine une version du langage par défaut en fonction du ou des frameworks cibles de votre projet. La raison est que le langage C# peut avoir des fonctionnalités qui reposent sur des types ou des composants d’exécution qui ne sont pas disponibles dans chaque implémentation .NET. Cela garantit aussi que quelle que soit la cible sur laquelle votre projet est créé, vous obtenez la version de langage compatible la plus récente par défaut.

Les règles de cet article s’appliquent au compilateur fourni avec Visual Studio 2019 ou le kit de développement logiciel (SDK) .NET Core 3,0. Les compilateurs C# qui sont installés en même temps que Visual Studio 2017 ou les versions antérieures du kit SDK .NET Core ciblent C# 7.0 par défaut. 

## <a name="defaults"></a>Valeurs par défaut

Le compilateur détermine une valeur par défaut en fonction de ces règles :

|Version cible de .NET Framework|Version de|Version du langage C# par défaut|
|----------------|-------|---------------------------|
|.NET Core|3|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|toutes les|C# 7.3|

## <a name="default-for-previews"></a>Valeur par défaut pour les préversions

Lorsqu’il s’agit d’une préversion cible pour laquelle il existe une préversion du langage correspondante, c’est cette dernière qui est utilisée. Vous avez ainsi l’assurance de pouvoir utiliser les fonctionnalités les plus récentes dont le fonctionnement est garanti avec cette préversion dans n’importe quel environnement sans affecter vos projets qui ciblent une version finale de .NET Core.

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

Maintenant, les builds de chaque sous-répertoire du répertoire contenant ce fichier vont utiliser la préversion de C#. Pour plus d’informations, consultez l’article sur [Personnaliser votre build](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Informations de référence sur la version du langage C#

Le tableau suivant montre toutes les versions actuelles du langage C#. Votre compilateur peut ne pas nécessairement comprendre chaque valeur si celle-ci est plus ancienne. Si vous installez .NET Core 3.0, vous avez accès à toutes les versions listées.

|Value|Signification|
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
