---
title: Do...Loop (instruction)
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
ms.openlocfilehash: a9ec6caccbe161a39b592a642a938b81bae911a6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404782"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop, instruction (Visual Basic)
Répète un bloc d’instructions tant qu’une `Boolean` condition est `True` ou jusqu’à ce que la condition devienne `True` .  
  
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
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`Do`|Obligatoire. Démarre la définition de la `Do` boucle.|  
|`While`|Requis, sauf si l'option `Until` est utilisée. Répétez la boucle jusqu’à ce que `condition` soit `False` .|  
|`Until`|Requis, sauf si l'option `While` est utilisée. Répétez la boucle jusqu’à ce que `condition` soit `True` .|  
|`condition`|Facultatif. Expression `Boolean`. Si `condition` est `Nothing` , Visual Basic le traite comme `False` .|  
|`statements`|Facultatif. Une ou plusieurs instructions qui sont répétées quand, ou jusqu’à, `condition` est `True` .|  
|`Continue Do`|Facultatif. Transfère le contrôle à l’itération suivante de la `Do` boucle.|  
|`Exit Do`|Facultatif. Transfère le contrôle hors de la `Do` boucle.|  
|`Loop`|Obligatoire. Termine la définition de la `Do` boucle.|  
  
## <a name="remarks"></a>Notes  
 Utilisez une `Do...Loop` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre indéfini de fois, jusqu’à ce qu’une condition soit satisfaite. Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](for-next-statement.md) est généralement un meilleur choix.  
  
 Vous pouvez utiliser `While` ou `Until` pour spécifier `condition` , mais pas les deux.  
  
 Vous ne pouvez tester `condition` qu’une seule fois, au début ou à la fin de la boucle. Si vous `condition` effectuez un test au début de la boucle (dans l' `Do` instruction), la boucle peut ne pas s’exécuter même une fois. Si vous testez à la fin de la boucle (dans l' `Loop` instruction), la boucle s’exécute toujours au moins une fois.  
  
 La condition résulte généralement d’une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de [type de données booléenne](../data-types/boolean-data-type.md) ( `True` ou `False` ). Cela comprend les valeurs d’autres types de données, tels que les types numériques, qui ont été converties en `Boolean` .  
  
 Vous pouvez imbriquer `Do` des boucles en plaçant une boucle dans une autre. Vous pouvez également imbriquer différents genres de structures de contrôle dans les deux. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md).  
  
> [!NOTE]
> La `Do...Loop` structure offre plus de souplesse que le [tout... End While](while-end-while-statement.md) , car elle vous permet de décider s’il faut mettre fin à la boucle lorsque `condition` cesse d’être `True` ou lorsqu’elle se transforme pour la première fois `True` . Elle vous permet également de tester `condition` au début ou à la fin de la boucle.  
  
## <a name="exit-do"></a>Quitter  
 L’instruction [Exit Do](exit-statement.md) peut fournir une autre façon de quitter un `Do…Loop` . `Exit Do`transfère immédiatement le contrôle à l’instruction qui suit l' `Loop` instruction.  
  
 `Exit Do`est souvent utilisé après l’évaluation d’une condition, par exemple dans une `If...Then...Else` structure. Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt. L’une des utilisations de `Exit Do` consiste à tester une condition susceptible de provoquer une *boucle infinie*, qui est une boucle qui peut exécuter un nombre de fois trop long, voire infini. Vous pouvez utiliser `Exit Do` pour échapper à la boucle.  
  
 Vous pouvez inclure n’importe quel nombre d' `Exit Do` instructions n’importe où dans un `Do…Loop` .  
  
 Lorsqu’il est utilisé dans `Do` les boucles imbriquées, `Exit Do` transfère le contrôle hors de la boucle la plus profonde et passe au niveau d’imbrication supérieur suivant.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu’à ce que la `index` variable soit supérieure à 10. La `Until` clause se trouve à la fin de la boucle.  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une `While` clause au lieu d’une `Until` clause, et `condition` est testé au début de la boucle plutôt qu’à la fin.  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `condition` arrête la boucle lorsque la `index` variable est supérieure à 100. `If`Toutefois, l’instruction dans la boucle provoque l’arrêt de la boucle par l' `Exit Do` instruction quand la variable d’index est supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant lit toutes les lignes d’un fichier texte. La <xref:System.IO.File.OpenText%2A> méthode ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères. Dans la `Do...Loop` condition, la <xref:System.IO.StreamReader.Peek%2A> méthode de `StreamReader` détermine s’il existe des caractères supplémentaires.  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de boucle](../../programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next (instruction)](for-next-statement.md)
- [Booléen (type de données)](../data-types/boolean-data-type.md)
- [Structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](exit-statement.md)
- [While...End While (instruction)](while-end-while-statement.md)
