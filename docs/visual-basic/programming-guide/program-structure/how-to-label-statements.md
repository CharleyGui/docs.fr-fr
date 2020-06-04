---
title: 'Procédure : Étiqueter des instructions'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 8f04d592c51b6a0630bfe623fd3574555aef9ff8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403211"
---
# <a name="how-to-label-statements-visual-basic"></a>Comment : étiqueter des instructions (Visual Basic)

Les blocs d’instructions sont constitués de lignes de code séparées par des signes deux-points. Les lignes de code précédées d’une chaîne ou d’un entier d’identification sont dites *étiquetées*. Les étiquettes d’instructions sont utilisées pour marquer une ligne de code afin de l’identifier pour une utilisation avec des instructions telles que `On Error Goto` .

Les étiquettes peuvent être des identificateurs de Visual Basic valides, tels que ceux qui identifient des éléments de programmation, ou des littéraux entiers. Une étiquette doit apparaître au début d’une ligne de code source et doit être suivie d’un signe deux-points, qu’elle soit suivie ou non d’une instruction sur la même ligne.

Le compilateur identifie les étiquettes en vérifiant si le début de la ligne correspond à un identificateur déjà défini. Si ce n’est pas le cas, le compilateur suppose qu’il s’agit d’une étiquette.

Les étiquettes ont leur propre espace de déclaration et n’interfèrent pas avec d’autres identificateurs. La portée d’une étiquette est le corps de la méthode. La déclaration d’étiquette est prioritaire dans toute situation ambiguë.

> [!NOTE]
> Les étiquettes peuvent être utilisées uniquement sur des instructions exécutables à l’intérieur de méthodes.

## <a name="to-label-a-line-of-code"></a>Pour étiqueter une ligne de code

Placez un identificateur, suivi d’un signe deux-points, au début de la ligne de code source.

Par exemple, les lignes de code suivantes sont étiquetées avec `Jump` et `120` , respectivement :

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a>Voir aussi

- [Instructions](../language-features/statements.md)
- [Declared Element Names](../language-features/declared-elements/declared-element-names.md)
- [Structure de programme et conventions de code](program-structure-and-code-conventions.md)
