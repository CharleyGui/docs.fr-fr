---
title: While...End While, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 5da05835998b2e9ef9aeefe5b00faf9e1ecb9ce2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582269"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While, instruction (Visual Basic)
Exécute une série d’instructions tant qu’une condition donnée n’est `True`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`condition`|Requis. expression `Boolean`. Si `condition` est `Nothing`, Visual Basic le traite comme `False`.|  
|`statements`|Optionnel. Une ou plusieurs instructions qui suivent `While`, qui s’exécutent chaque fois que `condition` est `True`.|  
|`Continue While`|Optionnel. Transfère le contrôle à l’itération suivante du bloc `While`.|  
|`Exit While`|Optionnel. Transfère le contrôle hors du bloc `While`.|  
|`End While`|Requis. Met fin à la définition du bloc `While`.|  
  
## <a name="remarks"></a>Notes  
 Utilisez une structure `While...End While` lorsque vous souhaitez répéter un ensemble d’instructions un nombre infini de fois, tant qu’une condition reste `True`. Si vous souhaitez plus de flexibilité lorsque vous testez la condition ou le résultat pour lequel vous la Testez, vous pouvez préférer le [... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md). Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) est généralement un meilleur choix.  
  
> [!NOTE]
> Le mot clé `While` est également utilisé dans le [... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md), la [clause Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) et la [clause Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Si `condition` est `True`, toutes les `statements` s’exécutent jusqu’à ce que l’instruction `End While` soit rencontrée. Le contrôle retourne ensuite à l’instruction `While` et `condition` est à nouveau vérifié. Si `condition` est toujours `True`, le processus est répété. S’il est `False`, le contrôle passe à l’instruction qui suit l’instruction `End While`.  
  
 L’instruction `While` vérifie toujours la condition avant de démarrer la boucle. Le bouclage continue tant que la condition reste `True`. Si `condition` est `False` lorsque vous entrez pour la première fois la boucle, elle ne s’exécute pas même une fois.  
  
 Le `condition` résulte généralement d’une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de [type de données booléenne](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` ou `False`). Cette expression peut inclure une valeur d’un autre type de données, tel qu’un type numérique, qui a été convertie en `Boolean`.  
  
 Vous pouvez imbriquer des boucles `While` en plaçant une boucle dans une autre. Vous pouvez également imbriquer différents genres de structures de contrôle dans l’un l’autre. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Quitter pendant  
 L’instruction [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) peut fournir une autre façon de quitter une boucle `While`. `Exit While` transfère immédiatement le contrôle à l’instruction qui suit l’instruction `End While`.  
  
 En général, vous utilisez `Exit While` une fois qu’une condition est évaluée (par exemple, dans une structure `If...Then...Else`). Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt. Vous pouvez utiliser `Exit While` lorsque vous testez une condition susceptible de provoquer une *boucle infinie*, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini. Vous pouvez ensuite utiliser `Exit While` pour échapper à la boucle.  
  
 Vous pouvez placer n’importe quel nombre d’instructions `Exit While` n’importe où dans la boucle `While`.  
  
 Lorsqu’il est utilisé dans des boucles `While` imbriquées, `Exit While` transfère le contrôle hors de la boucle la plus profonde et le plus élevé de l’imbrication.  
  
 L’instruction `Continue While` transfère immédiatement le contrôle à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu’à ce que la variable `index` soit supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation des instructions `Continue While` et `Exit While`.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant lit toutes les lignes d’un fichier texte. La méthode <xref:System.IO.File.OpenText%2A> ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères. Dans la condition `While`, la méthode <xref:System.IO.StreamReader.Peek%2A> de l' `StreamReader` détermine si le fichier contient des caractères supplémentaires.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue (instruction)](../../../visual-basic/language-reference/statements/continue-statement.md)
