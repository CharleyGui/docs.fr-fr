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
ms.openlocfilehash: 75a2129a9f332024831d97021e381f1b3d4fa048
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942995"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop, instruction (Visual Basic)
Répète un bloc d’instructions tant qu’une `Boolean` condition est `True` ou jusqu’à ce que `True`la condition devienne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
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
|`Do`|Requis. Démarre la définition de la `Do` boucle.|  
|`While`|Requis, sauf si l'option `Until` est utilisée. Répétez la boucle `condition` jusqu' `False`à ce que soit.|  
|`Until`|Requis, sauf si l'option `While` est utilisée. Répétez la boucle `condition` jusqu' `True`à ce que soit.|  
|`condition`|facultatif. `Boolean`formule. Si `condition` `False`est `Nothing`, Visual Basic le traite comme.|  
|`statements`|facultatif. Une ou plusieurs instructions qui sont répétées quand, ou jusqu' `condition` à `True`, est.|  
|`Continue Do`|facultatif. Transfère le contrôle à l’itération suivante de `Do` la boucle.|  
|`Exit Do`|facultatif. Transfère le contrôle hors de `Do` la boucle.|  
|`Loop`|Requis. Termine la définition de la `Do` boucle.|  
  
## <a name="remarks"></a>Notes  
 Utilisez une `Do...Loop` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre indéfini de fois, jusqu’à ce qu’une condition soit satisfaite. Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) est généralement un meilleur choix.  
  
 Vous pouvez utiliser `While` ou `Until` pour spécifier `condition`, mais pas les deux.  
  
 Vous ne pouvez `condition` tester qu’une seule fois, au début ou à la fin de la boucle. Si vous effectuez `condition` un test au début de la boucle (dans `Do` l’instruction), la boucle peut ne pas s’exécuter même une fois. Si vous testez à la fin de la boucle (dans `Loop` l’instruction), la boucle s’exécute toujours au moins une fois.  
  
 La condition résulte généralement d’une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de`True` type `False`de [données booléenne](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (ou). Cela comprend les valeurs d’autres types de données, tels que les types numériques, qui ont `Boolean`été converties en.  
  
 Vous pouvez imbriquer `Do` des boucles en plaçant une boucle dans une autre. Vous pouvez également imbriquer différents genres de structures de contrôle dans les deux. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> La `Do...Loop` structure offre plus de souplesse que le [tout... End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , car elle vous permet de décider s’il faut mettre fin `condition` à la `True` boucle lorsque cesse d’être `True`ou lorsqu’elle se transforme pour la première fois. Elle vous permet également de tester `condition` au début ou à la fin de la boucle.  
  
## <a name="exit-do"></a>Quitter  
 L’instruction [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) peut fournir une autre façon de quitter un `Do…Loop`. `Exit Do`transfère immédiatement le contrôle à l’instruction qui suit `Loop` l’instruction.  
  
 `Exit Do`est souvent utilisé après l’évaluation d’une condition, par exemple dans `If...Then...Else` une structure. Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt. L’une des `Exit Do` utilisations de consiste à tester une condition susceptible de provoquer une *boucle*infinie, qui est une boucle qui peut exécuter un nombre de fois trop long, voire infini. Vous pouvez utiliser `Exit Do` pour échapper à la boucle.  
  
 Vous pouvez inclure n’importe quel `Exit Do` nombre d’instructions n' `Do…Loop`importe où dans un.  
  
 Lorsqu’il est utilisé dans `Do` les boucles `Exit Do` imbriquées, transfère le contrôle hors de la boucle la plus profonde et passe au niveau d’imbrication supérieur suivant.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu' `index` à ce que la variable soit supérieure à 10. La `Until` clause se trouve à la fin de la boucle.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une `While` clause au lieu d' `Until` une clause, `condition` et est testé au début de la boucle plutôt qu’à la fin.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Exemples  
 Dans l’exemple suivant, `condition` arrête la boucle lorsque la `index` variable est supérieure à 100. Toutefois `If` , l’instruction dans la boucle provoque l’arrêt `Exit Do` de la boucle par l’instruction quand la variable d’index est supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant lit toutes les lignes d’un fichier texte. La <xref:System.IO.File.OpenText%2A> méthode ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères. Dans la `Do...Loop` condition, la <xref:System.IO.StreamReader.Peek%2A> méthode de `StreamReader` détermine s’il existe des caractères supplémentaires.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
