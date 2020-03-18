---
title: -langversion (Options du compilateur C#)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 007b10f6f27233c43caad4c1910e3d1158682950
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920365"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (Options du compilateur C#)

Force le compilateur à accepter uniquement la syntaxe incluse dans la spécification choisie du langage C#.

## <a name="syntax"></a>Syntaxe

```console
-langversion:option
```

## <a name="arguments"></a>Arguments

`option`

Les valeurs suivantes sont valides :

|Option|Signification|
|------------|-------------|
|preview|Le compilateur accepte toute la syntaxe de langage valide de la dernière préversion qu’il peut prendre en charge.|
|latest|Le compilateur accepte toute la syntaxe de langage valide de la dernière version (versions mineures incluses) qu’il peut prendre en charge.|
|latestMajor|Le compilateur accepte toute la syntaxe de langage valide de la dernière version principale qu’il peut prendre en charge.|
|8.0|Le compilateur accepte uniquement la syntaxe incluse dans C# 8.0 ou une version antérieure.|
|7.3|Le compilateur accepte uniquement la syntaxe incluse dans C# 7.3 ou une version antérieure.|
|7.2|Le compilateur accepte uniquement la syntaxe incluse dans C# 7.2 ou une version antérieure.|
|7.1|Le compilateur accepte uniquement la syntaxe incluse dans C# 7.1 ou une version antérieure.|
|7|Le compilateur accepte uniquement la syntaxe incluse dans C# 7.0 ou une version antérieure.|
|6|Le compilateur accepte uniquement la syntaxe incluse dans C# 6.0 ou une version antérieure.|
|5|Le compilateur accepte uniquement la syntaxe incluse dans C# 5.0 ou une version antérieure.|
|4|Le compilateur accepte uniquement la syntaxe incluse dans C# 4.0 ou une version antérieure.|
|3|Le compilateur accepte uniquement la syntaxe incluse dans C# 3.0 ou une version antérieure.|
|ISO-2|Le compilateur n’accepte que la syntaxe incluse dans ISO/IEC 23270:2006 CMD (2,0).|
|ISO-1|Le compilateur n’accepte que la syntaxe incluse dans ISO/IEC 23270:2003 CMD (1,0/1,2).|

La version du langage par défaut dépend du framework cible de votre application et de la version installée du kit SDK ou de Visual Studio. Ces règles sont définies dans la [configuration de l’article de version linguistique.](../configure-language-version.md#defaults)

## <a name="remarks"></a>Notes 

Les métadonnées référencées par votre application C# ne sont pas visées par l’option de compilateur **-langversion**.

Sachant que chaque version du compilateur C# contient des extensions de la spécification du langage, **-langversion** ne vous offre pas les fonctionnalités équivalentes d’une version antérieure du compilateur.

De plus, alors que les mises à jour de la version de C# coïncident généralement avec les versions principales du .NET Framework, la nouvelle syntaxe et les nouvelles fonctionnalités ne sont pas nécessairement liées à cette version spécifique du framework. Alors que les nouvelles fonctionnalités nécessitent une nouvelle mise à jour du compilateur, publiée en même temps que la révision de C#, chaque fonctionnalité spécifique a ses propres exigences minimales relatives à l’API .NET ou au Common Language Runtime pour pouvoir s’exécuter sur des frameworks de bas niveau en incluant des packages NuGet ou d’autres bibliothèques.

Indépendamment de quel **réglage -langversion** que vous utilisez, utilisez la version actuelle de l’heure d’exécution de la langue commune pour créer votre .exe ou .dll. Une exception est les assemblages d’amis et [-moduleassemblyname (Option compilateur C)](./moduleassemblyname-compiler-option.md), qui fonctionnent sous **-langversion:ISO-1**.

Pour d’autres façons de spécifier la version linguistique C, consultez l’article [de la version linguistique Select the C.](../configure-language-version.md)

Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.

## <a name="c-language-specification"></a>spécification du langage C#

|Version|Lien|Description|
|-------|----|-----------|
|C# 7.0 et versions ultérieures||actuellement non disponible|
|C# 6.0|[Lien](/dotnet/csharp/language-reference/language-specification/introduction)|Spécification du langage C# version 6 - Ébauche non officielle : .NET Foundation|
|C# 5.0|[Télécharger le PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Norme ECMA-334 5e édition|
|C# 3.0|[Télécharger DOC](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|Spécification du langage C# version 3.0 : Microsoft Corporation|
|C# 2.0|[Télécharger le PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Norme ECMA-334 4e édition|
|C# 1.2|[Télécharger DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|Spécification du langage C# version 1.2 : Microsoft Corporation|
|C# 1.0|[Télécharger DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|Spécification du langage C# version 1.0 : Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Version SDK minimale nécessaire pour prendre en charge toutes les fonctionnalités linguistiques

Le tableau suivant répertorie les versions minimales du SDK avec le compilateur CMD qui prend en charge la version linguistique correspondante :

|Version C|Version SDK minimale|
|----------|-------------------|
|C# 8.0| Microsoft Visual Studio/Build Tools 2019, version 16.3, ou .NET Core 3.0 SDK |
|C# 7.3| Microsoft Visual Studio/Build Tools 2017, version 15.7 |
|C# 7.2| Microsoft Visual Studio/Build Tools 2017, version 15.5 |
|C# 7.1| Microsoft Visual Studio/Build Tools 2017, version 15.3 |
|C# 7.0| Microsoft Visual Studio/Build Tools 2017 |
|C# 6| Microsoft Visual Studio/Build Tools 2015 |
|C 5| Microsoft Visual Studio/Build Tools 2012 ou compilateur .NET Framework 4.5 groupé |
|C# 4| Microsoft Visual Studio/Build Tools 2010 ou compilateur .NET Framework 4.0 groupé |
|C 3| Microsoft Visual Studio/Build Tools 2008 ou compilateur .NET Framework 3.5 groupé |
|C 2| Microsoft Visual Studio/Build Tools 2005 ou compilateur .NET Framework 2.0 groupé |
|C 1.0/1.2 | Microsoft Visual Studio/Build Tools .NET 2002 ou groupé .NET Framework 1.0 compilateur |

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
