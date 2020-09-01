---
description: -langversion (Options du compilateur C#)
title: -langversion (Options du compilateur C#)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: b0e966bcc87303c0a7c2199fbfac743b22481424
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125473"
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

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

La version du langage par défaut dépend du framework cible de votre application et de la version installée du kit SDK ou de Visual Studio. Ces règles sont définies dans l’article [configuration de la version linguistique](../configure-language-version.md#defaults) .

## <a name="remarks"></a>Remarques

Les métadonnées référencées par votre application C# ne sont pas visées par l’option de compilateur **-langversion**.

Sachant que chaque version du compilateur C# contient des extensions de la spécification du langage, **-langversion** ne vous offre pas les fonctionnalités équivalentes d’une version antérieure du compilateur.

De plus, alors que les mises à jour de la version de C# coïncident généralement avec les versions principales du .NET Framework, la nouvelle syntaxe et les nouvelles fonctionnalités ne sont pas nécessairement liées à cette version spécifique du framework. Alors que les nouvelles fonctionnalités nécessitent une nouvelle mise à jour du compilateur, publiée en même temps que la révision de C#, chaque fonctionnalité spécifique a ses propres exigences minimales relatives à l’API .NET ou au Common Language Runtime pour pouvoir s’exécuter sur des frameworks de bas niveau en incluant des packages NuGet ou d’autres bibliothèques.

Quel que soit le paramètre **-langversion** utilisé, utilisez la version actuelle du Common Language Runtime pour créer votre fichier. exe ou. dll. Les assemblys friend et [-moduleassemblyname (option du compilateur C#)](./moduleassemblyname-compiler-option.md), qui fonctionnent sous **-langversion : ISO-1**, sont une exception.

Pour d’autres façons de spécifier la version du langage C#, consultez l’article [Sélectionner la version du langage c#](../configure-language-version.md) .

Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.

## <a name="c-language-specification"></a>spécification du langage C#

| Version          | Lien                       | Description                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| C# 7.0 et versions ultérieures |                            | Actuellement non disponible                                                 |
| C# 6.0           | [Lien][csharp-6]           | Spécification du langage C# version 6 - Ébauche non officielle : .NET Foundation |
| C# 5.0           | [Télécharger le PDF][csharp-5]   | Norme ECMA-334 5e édition                                           |
| C# 3.0           | [Télécharger DOC][csharp-3]   | Spécification du langage C# version 3.0 : Microsoft Corporation            |
| C# 2.0           | [Télécharger le PDF][csharp-2]   | Norme ECMA-334 4e édition                                           |
| C# 1.2           | [Télécharger DOC][csharp-1.2] | Spécification du langage C# version 1.2 : Microsoft Corporation            |
| C# 1.0           | [Télécharger DOC][csharp-1]   | Spécification du langage C# version 1.0 : Microsoft Corporation            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Version minimale du kit de développement logiciel nécessaire pour prendre en charge toutes les fonctionnalités de langage

Le tableau suivant répertorie les versions minimales du kit de développement logiciel (SDK) avec le compilateur C# qui prend en charge la version de langue correspondante :

| Version C# | Version minimale du kit de développement logiciel                                                                  |
|------------|--------------------------------------------------------------------------------------|
| C# 8.0     | Microsoft Visual Studio/Build Tools 2019, version 16,3 ou .NET Core 3,0 SDK         |
| C# 7.3     | Microsoft Visual Studio/Build Tools 2017, version 15.7                               |
| C# 7.2     | Microsoft Visual Studio/Build Tools 2017, version 15.5                               |
| C# 7.1     | Microsoft Visual Studio/Build Tools 2017, version 15.3                               |
| C# 7.0     | Microsoft Visual Studio/Build Tools 2017                                             |
| C# 6       | Microsoft Visual Studio/Build Tools 2015                                             |
| C# 5       | Microsoft Visual Studio/Build Tools 2012 ou compilateur .NET Framework 4.5 groupé      |
| C# 4       | Microsoft Visual Studio/Build Tools 2010 ou compilateur .NET Framework 4.0 groupé      |
| C# 3       | Microsoft Visual Studio/Build Tools 2008 ou compilateur .NET Framework 3.5 groupé      |
| C# 2       | Microsoft Visual Studio/Build Tools 2005 ou compilateur .NET Framework 2.0 groupé      |
| C# 1.0/1.2 | Microsoft Visual Studio/Build Tools .NET 2002 ou regroupé .NET Framework 1,0 du compilateur |

## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
