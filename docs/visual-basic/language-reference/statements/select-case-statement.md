---
title: Select...Case (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 3dedd43f920b493a0aca9ce48460b00815e1af5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404237"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case, instruction (Visual Basic)
Exécute l’un des différents groupes d’instructions, en fonction de la valeur d’une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`testexpression`|Obligatoire. Expression. Doit correspondre à l’un des types de données élémentaires ( `Boolean` , `Byte` , `Char` , `Date` , `Double` , `Decimal` , `Integer` , `Long` , `Object` , `SByte` , `Short` , `Single` , `String` , `UInteger` , `ULong` et `UShort` ).|  
|`expressionlist`|Obligatoire dans une `Case` instruction. Liste des clauses d’expression représentant les valeurs de correspondance pour `testexpression` . Plusieurs clauses d’expression sont séparées par des virgules. Chaque clause peut prendre l’une des formes suivantes :<br /><br /> -   *expression1* `To` *Expression2*<br />-[ `Is` ] *comparisonoperator* *expression* ComparisonOperator<br />-   *formule*<br /><br /> Utilisez le `To` mot clé pour spécifier les limites d’une plage de valeurs de correspondance pour `testexpression` . La valeur de `expression1` doit être inférieure ou égale à la valeur de `expression2` .<br /><br /> Utilisez le `Is` mot clé avec un opérateur de comparaison ( `=` ,,,, `<>` `<` `<=` `>` ou `>=` ) pour spécifier une restriction sur les valeurs de correspondance pour `testexpression` . Si le `Is` mot clé n’est pas fourni, il est automatiquement inséré avant *comparisonoperator*.<br /><br /> Le formulaire spécifiant uniquement `expression` est traité comme un cas spécial de la `Is` forme où *comparisonoperator* est le signe égal ( `=` ). Ce formulaire est évalué comme `testexpression`  =  `expression` .<br /><br /> Les expressions dans `expressionlist` peuvent être de n’importe quel type de données, à condition qu’elles soient implicitement convertibles dans le type de `testexpression` et que le approprié `comparisonoperator` soit valide pour les deux types avec lesquels il est utilisé.|  
|`statements`|Facultatif. Une ou plusieurs instructions qui suivent s' `Case` exécutent si `testexpression` correspond à une clause de `expressionlist` .|  
|`elsestatements`|Facultatif. Une ou plusieurs instructions qui suivent s' `Case Else` exécutent si `testexpression` ne correspond à aucune clause dans le `expressionlist` de l’une des `Case` instructions.|  
|`End Select`|Termine la définition de la `Select` construction... `Case` .|  
  
## <a name="remarks"></a>Notes  
 Si `testexpression` correspond à une `Case` `expressionlist` clause, les instructions qui suivent cette `Case` instruction s’exécutent jusqu’à l' `Case` `Case Else` instruction, ou suivante `End Select` . Le contrôle passe ensuite à l’instruction qui suit `End Select` . Si `testexpression` correspond à une `expressionlist` clause dans plusieurs `Case` clauses, seules les instructions qui suivent la première correspondance sont exécutées.  
  
 L' `Case Else` instruction est utilisée pour introduire le `elsestatements` à exécuter si aucune correspondance n’est trouvée entre les `testexpression` `expressionlist` clauses et dans les autres `Case` instructions. Bien que cela ne soit pas obligatoire, il est judicieux d’avoir une `Case Else` instruction dans votre `Select Case` construction pour gérer des valeurs imprévues `testexpression` . Si aucune `Case` `expressionlist` clause ne correspond `testexpression` et qu’il n’y a aucune `Case Else` instruction, le contrôle passe à l’instruction qui suit `End Select` .  
  
 Vous pouvez utiliser plusieurs expressions ou plages dans chaque `Case` clause. Par exemple, la ligne suivante est valide.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> Le `Is` mot clé utilisé dans `Case` les `Case Else` instructions et n’est pas le même que l' [opérateur is](../operators/is-operator.md), qui est utilisé pour la comparaison des références d’objet.  
  
 Vous pouvez spécifier des plages et plusieurs expressions pour les chaînes de caractères. Dans l’exemple suivant, `Case` correspond à toute chaîne qui est exactement égale à « apples », a une valeur comprise entre « NUTS » et « soupe » dans l’ordre alphabétique, ou contient la même valeur que la valeur actuelle de `testItem` .  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 La valeur de `Option Compare` peut affecter les comparaisons de chaînes. Sous `Option Compare Text` , les chaînes « Apples » et « Apples » sont considérées comme égales, mais sous `Option Compare Binary` , elles ne le sont pas.  
  
> [!NOTE]
> Une `Case` instruction avec plusieurs clauses peut présenter un comportement connu sous le nom de *court-circuit*. Visual Basic évalue les clauses de gauche à droite et, si une correspondance est trouvée avec `testexpression` , les clauses restantes ne sont pas évaluées. Le court-circuit peut améliorer les performances, mais il peut produire des résultats inattendus si chaque expression dans `expressionlist` doit être évaluée. Pour plus d’informations sur le court-circuit, consultez [expressions booléennes](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Si le code d’un `Case` `Case Else` bloc d’instructions ou n’a pas besoin d’exécuter d’autres instructions dans le bloc, il peut quitter le bloc à l’aide de l' `Exit Select` instruction. Cela transfère immédiatement le contrôle à l’instruction qui suit `End Select` .  
  
 `Select Case`les constructions peuvent être imbriquées. Chaque construction imbriquée `Select Case` doit avoir une `End Select` instruction correspondante et doit être entièrement contenue dans un `Case` `Case Else` bloc d’instructions unique ou de la construction externe `Select Case` dans laquelle elle est imbriquée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une `Select Case` construction pour écrire une ligne correspondant à la valeur de la variable `number` . La deuxième `Case` instruction contient la valeur qui correspond à la valeur actuelle de `number` , donc l’instruction qui écrit « entre 6 et 8 inclus » s’exécute.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End (instruction)](end-statement.md)
- [If...Then...Else (instruction)](if-then-else-statement.md)
- [Option Compare, instruction](option-compare-statement.md)
- [Exit (instruction)](exit-statement.md)
