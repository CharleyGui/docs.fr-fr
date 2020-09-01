---
description: '#line - Référence C#'
title: '#line - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: e2a5ecb6c29184123b8a88ae1b12caf24ec7296a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137992"
---
# <a name="line-c-reference"></a>#line (référence C#)

`#line` vous permet de changer la numérotation de lignes du compilateur et (éventuellement) le nom de fichier pour les erreurs et les avertissements.

L’exemple suivant montre comment signaler deux avertissements associés à des numéros de ligne. La directive `#line 200` assigne de force le numéro 200 à la ligne suivante (bien que le numéro par défaut soit 6) ; jusqu’à la prochaine directive `#line`, le nom de fichier indiqué est « Special ». La directive `#line default` rétablit la numérotation de lignes par défaut, qui compte les lignes renumérotées par la directive précédente.

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

La compilation produit la sortie suivante :

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Remarques

La directive `#line` peut être utilisée dans une étape intermédiaire automatisée du processus de génération. Par exemple, si des lignes ont été supprimées du fichier de code source d’origine, mais que vous voulez que le compilateur continue de générer une sortie sur la base de la numérotation de lignes d’origine du fichier, vous pouvez supprimer les lignes et simuler ensuite la numérotation de lignes d’origine avec `#line`.

La directive `#line hidden` masque les lignes successives du débogueur, de sorte que quand le développeur parcourt le code, les lignes situées entre une directive `#line hidden` et la directive `#line` suivante (en supposant qu’il ne s’agit pas d’une autre directive `#line hidden`) sont ignorées. Cette option peut aussi être utilisée pour permettre à ASP.NET de différencier le code défini par l’utilisateur du code généré par l’ordinateur. Même si ASP.NET est le principal utilisateur de cette fonctionnalité, il est probable que d’autres générateurs de code source pourront l’utiliser.

Une directive `#line hidden` n’affecte ni les noms de fichiers ni les numéros de lignes dans les rapports d’erreurs. Autrement dit, si une erreur se produit dans un bloc masqué, le compilateur indique le nom du fichier et le numéro de ligne actuels de l’erreur.

La directive `#line filename` spécifie le nom de fichier que vous souhaitez voir apparaître dans la sortie du compilateur. Par défaut, le nom réel du fichier de code source est utilisé. Le nom de fichier doit être entre guillemets doubles (" ") et doit être précédé d’un numéro de ligne.

Un fichier de code source peut contenir un nombre illimité de directives `#line`.

## <a name="example-1"></a>Exemple 1

L’exemple suivant montre comment le débogueur ignore les lignes masquées dans le code. Quand vous exécutez l’exemple, celui-ci affiche trois lignes de texte. Or, quand vous définissez un point d’arrêt, comme dans l’exemple, et que vous appuyez sur F10 pour parcourir le code, vous pouvez remarquer que le débogueur ignore la ligne masquée. Vous remarquerez aussi que même si vous définissez un point d’arrêt au niveau de la ligne masquée, le débogueur continuera de l’ignorer.

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur C#](./index.md)
