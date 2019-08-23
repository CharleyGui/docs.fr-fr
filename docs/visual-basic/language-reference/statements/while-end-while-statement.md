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
ms.openlocfilehash: 7ea0814c587f65ddc1f114d2314ac7147143d40d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965813"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While, instruction (Visual Basic)
Exécute une série d’instructions tant qu’une condition donnée a `True`la valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`condition`|Requis. `Boolean`formule. Si `condition` `False`est `Nothing`, Visual Basic le traite comme.|  
|`statements`|facultatif. Une ou plusieurs instructions qui `While`suivent sont `True`exécutées à `condition` chaque fois.|  
|`Continue While`|facultatif. Transfère le contrôle à l’itération suivante du `While` bloc.|  
|`Exit While`|facultatif. Transfère le `While` contrôle hors du bloc.|  
|`End While`|Requis. Met fin à la définition du bloc `While`.|  
  
## <a name="remarks"></a>Notes  
 Utilisez une `While...End While` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre infini de fois, tant qu’une condition est conservée `True`. Si vous souhaitez plus de flexibilité lorsque vous testez la condition ou le résultat pour lequel vous la Testez, vous pouvez préférer le [... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md). Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) est généralement un meilleur choix.  
  
> [!NOTE]
> Le `While` mot clé est également utilisé dans le [... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md), la [clause Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) et la [clause Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).  
  
 Si `condition` est `True`, tout `statements` est exécuté jusqu’à ce `End While` que l’instruction soit rencontrée. Le contrôle retourne ensuite à `While` l’instruction et `condition` est à nouveau vérifié. Si `condition` est toujours `True`, le processus est répété. Si c’est `False`le cas, le contrôle passe à l’instruction `End While` qui suit l’instruction.  
  
 L' `While` instruction vérifie toujours la condition avant de démarrer la boucle. Le bouclage continue tant que la condition `True`est conservée. Si `condition` est`False` lorsque vous entrez pour la première fois la boucle, elle ne s’exécute pas même une fois.  
  
 Le `condition` résultat est généralement une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de`True` type `False`de [données booléenne](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (ou). Cette expression peut inclure une valeur d’un autre type de données, tel qu’un type numérique, qui a été `Boolean`converti en.  
  
 Vous pouvez imbriquer `While` des boucles en plaçant une boucle dans une autre. Vous pouvez également imbriquer différents genres de structures de contrôle dans l’un l’autre. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Quitter pendant  
 L’instruction [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) peut fournir une autre façon de `While` quitter une boucle. `Exit While`transfère immédiatement le contrôle à l’instruction qui suit `End While` l’instruction.  
  
 Vous utilisez `Exit While` généralement une fois que certaines conditions ont été évaluées (par `If...Then...Else` exemple, dans une structure). Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt. Vous pouvez utiliser `Exit While` lorsque vous testez une condition susceptible de provoquer une *boucle*infinie, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini. Vous pouvez ensuite utiliser `Exit While` pour échapper la boucle.  
  
 Vous pouvez placer n’importe quel `Exit While` nombre d’instructions n' `While` importe où dans la boucle.  
  
 Lorsqu’il est utilisé dans `While` les boucles `Exit While` imbriquées, transfère le contrôle hors de la boucle la plus profonde et passe au niveau d’imbrication supérieur suivant.  
  
 L' `Continue While` instruction transfère immédiatement le contrôle à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu' `index` à ce que la variable soit supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation des `Continue While` instructions et. `Exit While`  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant lit toutes les lignes d’un fichier texte. La <xref:System.IO.File.OpenText%2A> méthode ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères. Dans la `While` condition, la <xref:System.IO.StreamReader.Peek%2A> méthode de `StreamReader` détermine si le fichier contient des caractères supplémentaires.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue (instruction)](../../../visual-basic/language-reference/statements/continue-statement.md)
