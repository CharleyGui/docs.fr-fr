---
title: Types d’erreurs
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: caeaab9a358e3e3a995c1df7274d16daaff7a667
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083993"
---
# <a name="error-types-visual-basic"></a>Types d'erreurs (Visual Basic)

Dans Visual Basic, les erreurs appartiennent à l’une des trois catégories suivantes : erreurs de syntaxe, erreurs d’exécution et erreurs logiques.

## <a name="syntax-errors"></a>Erreurs de syntaxe

 Les *Erreurs de syntaxe* sont celles qui apparaissent lorsque vous écrivez du code. Si vous utilisez Visual Studio, Visual Basic vérifie votre code au fur et à mesure que vous le tapez dans la fenêtre de l' **éditeur de code** et vous avertit si vous faites une erreur, telle que l’orthographe d’un mot ou l’utilisation incorrecte d’un élément de langage. Si vous compilez à partir de la ligne de commande, Visual Basic affiche une erreur du compilateur avec des informations sur l’erreur de syntaxe. Les erreurs de syntaxe sont le type le plus courant d’erreurs. Vous pouvez les corriger facilement dans l’environnement de codage dès qu’elles se produisent.

> [!NOTE]
> L' `Option Explicit` instruction est un moyen d’éviter les erreurs de syntaxe. Elle vous oblige à déclarer, à l’avance, toutes les variables à utiliser dans l’application. Par conséquent, lorsque ces variables sont utilisées dans le code, toutes les erreurs typographiques sont interceptées immédiatement et peuvent être résolues.

## <a name="run-time-errors"></a>Erreurs d’exécution

 Les *Erreurs d’exécution* sont celles qui s’affichent uniquement après la compilation et l’exécution de votre code. Celles-ci impliquent du code qui peut paraître correct dans la mesure où il n’y a pas d’erreurs de syntaxe, mais qui ne s’exécutent pas. Par exemple, vous pouvez écrire correctement une ligne de code pour ouvrir un fichier. Toutefois, si le fichier n’existe pas, l’application ne peut pas ouvrir le fichier et lève une exception. Vous pouvez résoudre la plupart des erreurs d’exécution en réécrivant le code défectueux ou en utilisant la [gestion des exceptions](../../language-reference/statements/try-catch-finally-statement.md), puis en le recompilant et en le réexécutant.
  
## <a name="logic-errors"></a>Erreurs logiques

 Les *Erreurs de logique* sont celles qui s’affichent une fois que l’application est en cours d’utilisation. Il s’agit généralement d’hypothèses erronées émises par le développeur ou de résultats indésirables ou inattendus en réponse aux actions de l’utilisateur. Par exemple, une clé mal typée peut fournir des informations incorrectes à une méthode, ou vous pouvez supposer qu’une valeur valide est toujours fournie à une méthode lorsque ce n’est pas le cas. Bien que les erreurs de logique puissent être gérées à l’aide de la [gestion des exceptions](../../language-reference/statements/try-catch-finally-statement.md) (par exemple, en testant si un argument est `Nothing` et en levant un <xref:System.ArgumentNullException> ), le plus souvent, ils doivent être traités en corrigeant l’erreur dans la logique et en recompilant l’application.

## <a name="see-also"></a>Voir aussi

- [Try...Catch...Finally (instruction)](../../language-reference/statements/try-catch-finally-statement.md)
- [Principes de base du débogueur](/visualstudio/debugger/debugger-feature-tour)
