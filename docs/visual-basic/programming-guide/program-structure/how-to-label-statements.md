---
title: 'Procédure : Instructions d’étiquette (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 9a5f2039716a18011cac3dfd9b011d5b3868c294
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054052"
---
# <a name="how-to-label-statements-visual-basic"></a>Procédure : Instructions d’étiquette (Visual Basic)

Les blocs d’instructions sont constitués de lignes de code séparées par des signes deux-points. Les lignes de code précédées d’une chaîne ou d’un entier d’identification sont dites *étiquetées*. Les étiquettes d’instructions sont utilisées pour marquer une ligne de code afin de l’identifier pour une utilisation `On Error Goto`avec des instructions telles que.

Les étiquettes peuvent être des identificateurs de Visual Basic valides, tels que ceux qui identifient des éléments de programmation, ou des littéraux entiers. Une étiquette doit apparaître au début d’une ligne de code source et doit être suivie d’un signe deux-points, qu’elle soit suivie ou non d’une instruction sur la même ligne.

Le compilateur identifie les étiquettes en vérifiant si le début de la ligne correspond à un identificateur déjà défini. Si ce n’est pas le cas, le compilateur suppose qu’il s’agit d’une étiquette.

Les étiquettes ont leur propre espace de déclaration et n’interfèrent pas avec d’autres identificateurs. La portée d’une étiquette est le corps de la méthode. La déclaration d’étiquette est prioritaire dans toute situation ambiguë.

> [!NOTE]
> Les étiquettes peuvent être utilisées uniquement sur des instructions exécutables à l’intérieur de méthodes.

## <a name="to-label-a-line-of-code"></a>Pour étiqueter une ligne de code

Placez un identificateur, suivi d’un signe deux-points, au début de la ligne de code source.

Par exemple, les lignes de code suivantes sont étiquetées `Jump` avec `120`et, respectivement :

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a>Voir aussi

- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
- [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
