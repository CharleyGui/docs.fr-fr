---
title: While...End While (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: e3ab95f43e101a9ad8abe6fa61b94ae7542e409c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869484"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While, instruction (Visual Basic)

Exécute une série d’instructions tant qu’une condition donnée a la valeur `True` .  
  
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
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`condition`|Obligatoire. Expression `Boolean`. Si `condition` est `Nothing` , Visual Basic le traite comme `False` .|  
|`statements`|Optionnel. Une ou plusieurs instructions `While` qui suivent sont exécutées à chaque fois `condition` `True` .|  
|`Continue While`|Optionnel. Transfère le contrôle à l’itération suivante du `While` bloc.|  
|`Exit While`|Optionnel. Transfère le contrôle hors du `While` bloc.|  
|`End While`|Obligatoire. Met fin à la définition du bloc `While`.|  
  
## <a name="remarks"></a>Notes  

 Utilisez une `While...End While` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre infini de fois, tant qu’une condition est conservée `True` . Si vous souhaitez plus de flexibilité lorsque vous testez la condition ou le résultat pour lequel vous la Testez, vous pouvez préférer le [... Instruction de boucle](do-loop-statement.md). Si vous souhaitez répéter les instructions un nombre défini de fois, le [... L’instruction suivante](for-next-statement.md) est généralement un meilleur choix.  
  
> [!NOTE]
> Le `While` mot clé est également utilisé dans le [... Instruction de boucle](do-loop-statement.md), la [clause Skip While](../queries/skip-while-clause.md) et la [clause Take While](../queries/take-while-clause.md).  
  
 Si `condition` est `True` , tout est `statements` exécuté jusqu’à ce que l' `End While` instruction soit rencontrée. Le contrôle retourne ensuite à l' `While` instruction et `condition` est à nouveau vérifié. Si `condition` est toujours `True` , le processus est répété. Si c’est le cas `False` , le contrôle passe à l’instruction qui suit l' `End While` instruction.  
  
 L' `While` instruction vérifie toujours la condition avant de démarrer la boucle. Le bouclage continue tant que la condition est conservée `True` . Si `condition` est `False` lorsque vous entrez pour la première fois la boucle, elle ne s’exécute pas même une fois.  
  
 Le `condition` résultat est généralement une comparaison de deux valeurs, mais il peut s’agir d’une expression qui prend la valeur d’une valeur de [type de données booléenne](../data-types/boolean-data-type.md) ( `True` ou `False` ). Cette expression peut inclure une valeur d’un autre type de données, tel qu’un type numérique, qui a été converti en `Boolean` .  
  
 Vous pouvez imbriquer `While` des boucles en plaçant une boucle dans une autre. Vous pouvez également imbriquer différents genres de structures de contrôle dans l’un l’autre. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-while"></a>Quitter pendant  

 L’instruction [Exit while](exit-statement.md) peut fournir une autre façon de quitter une `While` boucle. `Exit While` transfère immédiatement le contrôle à l’instruction qui suit l' `End While` instruction.  
  
 Vous utilisez généralement `Exit While` une fois que certaines conditions ont été évaluées (par exemple, dans une `If...Then...Else` structure). Vous pouvez quitter une boucle si vous détectez une condition qui le rend inutile ou impossible de poursuivre l’itération, telle qu’une valeur erronée ou une demande d’arrêt. Vous pouvez utiliser `Exit While` lorsque vous testez une condition susceptible de provoquer une *boucle infinie*, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini. Vous pouvez ensuite utiliser `Exit While` pour échapper la boucle.  
  
 Vous pouvez placer n’importe quel nombre d' `Exit While` instructions n’importe où dans la `While` boucle.  
  
 Lorsqu’il est utilisé dans `While` les boucles imbriquées, `Exit While` transfère le contrôle hors de la boucle la plus profonde et passe au niveau d’imbrication supérieur suivant.  
  
 L' `Continue While` instruction transfère immédiatement le contrôle à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction continue](continue-statement.md).  
  
## <a name="example"></a>Exemple  

 Dans l’exemple suivant, les instructions de la boucle continuent à s’exécuter jusqu’à ce que la `index` variable soit supérieure à 10.  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant illustre l’utilisation des `Continue While` `Exit While` instructions et.  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant lit toutes les lignes d’un fichier texte. La <xref:System.IO.File.OpenText%2A> méthode ouvre le fichier et retourne un <xref:System.IO.StreamReader> qui lit les caractères. Dans la `While` condition, la <xref:System.IO.StreamReader.Peek%2A> méthode de `StreamReader` détermine si le fichier contient des caractères supplémentaires.  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de boucle](../../programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop (instruction)](do-loop-statement.md)
- [For...Next (instruction)](for-next-statement.md)
- [Booléen (type de données)](../data-types/boolean-data-type.md)
- [Structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](exit-statement.md)
- [Continue (instruction)](continue-statement.md)
