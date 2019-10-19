---
title: Do...Loop, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: eff5239e07ca27f40ece5af68f46c491be91cf09
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583441"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop, instruction (Visual Basic)
Répète un bloc d’instructions tant qu’une condition `Boolean` est `True` ou jusqu’à ce que la condition soit `True`.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`Do`|Requis. Démarre la définition de la boucle de `Do`.|  
|`While`|Requis, sauf si l'option `Until` est utilisée. Répétez la boucle jusqu’à ce que `condition` soit `False`.|  
|`Until`|Requis, sauf si l'option `While` est utilisée. Répétez la boucle jusqu’à ce que `condition` soit `True`.|  
|`condition`|Optionnel. expression `Boolean`. Si `condition` est `Nothing`, Visual Basic le traite comme `False`.|  
|`statements`|Optionnel. Une ou plusieurs instructions qui sont répétées tant que `condition` n’est `True`.|  
|`Continue Do`|Optionnel. Transfère le contrôle à l’itération suivante de la boucle `Do`.|  
|`Exit Do`|Optionnel. Transfère le contrôle hors de la boucle de `Do`.|  
|`Loop`|Requis. Termine la définition de la boucle `Do`.|  
  
## <a name="remarks"></a>Notes  
 Utilisez une structure `Do...Loop` lorsque vous souhaitez répéter un ensemble d’instructions un nombre infini de fois, jusqu’à ce qu’une condition soit satisfaite. Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) est généralement un meilleur choix.  
  
 Vous pouvez utiliser `While` ou `Until` pour spécifier `condition`, mais pas les deux.  
  
 Vous ne pouvez tester `condition` qu’une seule fois, au début ou à la fin de la boucle. Si vous testez `condition` au début de la boucle (dans l’instruction `Do`), la boucle peut ne pas s’exécuter même une fois. Si vous testez à la fin de la boucle (dans l’instruction `Loop`), la boucle s’exécute toujours au moins une fois.  
  
 La condition résulte généralement d’une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de [type de données booléenne](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` ou `False`). Cela comprend les valeurs d’autres types de données, tels que les types numériques, qui ont été converties en `Boolean`.  
  
 Vous pouvez imbriquer des boucles `Do` en plaçant une boucle dans une autre. Vous pouvez également imbriquer différents genres de structures de contrôle dans les deux. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> La structure `Do...Loop` offre plus de souplesse que le [tout... End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , car elle vous permet de décider s’il faut mettre fin à la boucle lorsque `condition` cesse d’être `True` ou lorsqu’elle est d’abord `True`. Elle vous permet également de tester `condition` au début ou à la fin de la boucle.  
  
## <a name="exit-do"></a>Quitter  
 L’instruction [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) peut fournir une autre façon de quitter une `Do…Loop`. `Exit Do` transfère immédiatement le contrôle à l’instruction qui suit l’instruction `Loop`.  
  
 `Exit Do` est souvent utilisé après l’évaluation d’une condition, par exemple dans une structure `If...Then...Else`. Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt. L’une des utilisations de `Exit Do` consiste à tester une condition susceptible de provoquer une *boucle infinie*, qui est une boucle qui peut exécuter un nombre de fois beaucoup voire infini. Vous pouvez utiliser `Exit Do` pour échapper à la boucle.  
  
 Vous pouvez inclure n’importe quel nombre d’instructions `Exit Do` n’importe où dans une `Do…Loop`.  
  
 Lorsqu’il est utilisé dans des boucles `Do` imbriquées, `Exit Do` transfère le contrôle hors de la boucle la plus profonde et le plus élevé de l’imbrication.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu’à ce que la variable `index` soit supérieure à 10. La clause `Until` se trouve à la fin de la boucle.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une clause `While` au lieu d’une clause `Until`, et `condition` est testé au début de la boucle et non à la fin.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `condition` arrête la boucle lorsque la variable `index` est supérieure à 100. Toutefois, l’instruction `If` dans la boucle entraîne l’arrêt de la boucle par l’instruction `Exit Do` quand la variable d’index est supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant lit toutes les lignes d’un fichier texte. La méthode <xref:System.IO.File.OpenText%2A> ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères. Dans la condition `Do...Loop`, la méthode <xref:System.IO.StreamReader.Peek%2A> de l' `StreamReader` détermine s’il existe des caractères supplémentaires.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
