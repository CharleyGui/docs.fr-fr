---
title: Select...Case, instruction (Visual Basic)
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
ms.openlocfilehash: 627318677270ba4ffa8ee430febea7ddf83bd245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957658"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case, instruction (Visual Basic)
Exécute l’un des différents groupes d’instructions, en fonction de la valeur d’une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`testexpression`|Requis. Formule. Doit correspondre à l’un des types de données élémentaires `Byte`( `Char``Boolean`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`,,, `Single`, ,`String` ,et`UShort`). `UInteger` `ULong`|  
|`expressionlist`|Obligatoire dans une `Case` instruction. Liste des clauses d’expression représentant les valeurs `testexpression`de correspondance pour. Plusieurs clauses d’expression sont séparées par des virgules. Chaque clause peut prendre l’une des formes suivantes:<br /><br /> -   *expression1* `To` *expression2*<br />-[ `Is` ] *expression* ComparisonOperator<br />-   *expression*<br /><br /> Utilisez le `To` mot clé pour spécifier les limites d’une plage de valeurs de `testexpression`correspondance pour. La valeur de `expression1` doit être inférieure ou égale à la valeur de. `expression2`<br /><br /> Utilisez le `Is` mot clé avec un opérateur de`=`comparaison `<>`( `<`, `<=`, `>`,, `>=`ou) pour spécifier une restriction sur les valeurs de `testexpression`correspondance pour. Si le `Is` mot clé n’est pas fourni, il est automatiquement inséré avant *comparisonoperator*.<br /><br /> Le formulaire spécifiant `expression` uniquement est traité comme un cas spécial de `Is` la forme où *comparisonoperator* est le signe égal`=`(). Ce formulaire est évalué comme `testexpression`.  =  `expression`<br /><br /> Les expressions dans `expressionlist` peuvent être de n’importe quel type de données, à condition qu’elles soient implicitement `testexpression` convertibles dans `comparisonoperator` le type de et que le approprié soit valide pour les deux types avec lesquels il est utilisé.|  
|`statements`|facultatif. Une ou plusieurs instructions qui `Case` suivent s’exécutent si `testexpression` correspond à `expressionlist`une clause de.|  
|`elsestatements`|facultatif. Une ou plusieurs instructions qui `Case Else` suivent s’exécutent si `testexpression` ne correspond à aucune clause `expressionlist` dans `Case` le de l’une des instructions.|  
|`End Select`|Met fin à la définition de `Select`... `Case` construction.|  
  
## <a name="remarks"></a>Notes  
 Si `testexpression` correspond à `Case` une `Case` `Case` `End Select` `Case Else`clause, les instructions qui suivent cette instruction s’exécutent jusqu’à l’instruction, ou suivante. `expressionlist` Le contrôle passe ensuite à l’instruction `End Select`qui suit. Si `testexpression` correspond à `expressionlist` une`Case` clause dans plusieurs clauses, seules les instructions qui suivent la première correspondance sont exécutées.  
  
 L' `Case Else` instruction est utilisée pour introduire le `elsestatements` à exécuter si aucune correspondance n’est `expressionlist` trouvée entre `testexpression` les clauses et dans les autres `Case` instructions. Bien que cela ne soit pas obligatoire, il est judicieux d' `Case Else` avoir une instruction `Select Case` dans votre construction pour gérer `testexpression` des valeurs imprévues. Si aucune `Case` clause ne `expressionlist` correspond `testexpression` et qu’il `Case Else` n’y a aucune instruction, le contrôle `End Select`passe à l’instruction qui suit.  
  
 Vous pouvez utiliser plusieurs expressions ou plages dans chaque `Case` clause. Par exemple, la ligne suivante est valide.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> Le `Is` mot clé utilisé dans `Case` les `Case Else` instructions et n’est pas le même que l' [opérateur is](../../../visual-basic/language-reference/operators/is-operator.md), qui est utilisé pour la comparaison des références d’objet.  
  
 Vous pouvez spécifier des plages et plusieurs expressions pour les chaînes de caractères. Dans l’exemple suivant, `Case` correspond à toute chaîne qui est exactement égale à «apples», a une valeur comprise entre «NUTS» et «soupe» dans l’ordre alphabétique, ou contient la même valeur `testItem`que la valeur actuelle de.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 La valeur de `Option Compare` peut affecter les comparaisons de chaînes. Sous `Option Compare Text`, les chaînes «Apples» et «Apples» sont considérées comme `Option Compare Binary`égales, mais sous, elles ne le sont pas.  
  
> [!NOTE]
> Une `Case` instruction avec plusieurs clauses peut présenter un comportement connu sous le nom de *court-circuit*. Visual Basic évalue les clauses de gauche à droite et, si une correspondance est trouvée avec `testexpression`, les clauses restantes ne sont pas évaluées. Le court-circuit peut améliorer les performances, mais il peut produire des résultats inattendus si chaque expression `expressionlist` dans doit être évaluée. Pour plus d’informations sur le court-circuit, consultez [expressions booléennes](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Si le code d’un `Case` bloc `Case Else` d’instructions ou n’a pas besoin d’exécuter d’autres instructions dans le bloc, il peut quitter le bloc à l’aide `Exit Select` de l’instruction. Cela transfère immédiatement le contrôle à l’instruction `End Select`qui suit.  
  
 `Select Case`les constructions peuvent être imbriquées. Chaque `Select Case` construction imbriquée doit avoir une instruction `End Select` correspondante et doit être entièrement contenue dans un `Case` bloc `Case Else` d’instructions unique ou de `Select Case` la construction externe dans laquelle elle est imbriquée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une `Select Case` construction pour écrire une ligne correspondant à la valeur de la variable `number`. La deuxième `Case` instruction contient la valeur qui correspond à la valeur actuelle `number`de, donc l’instruction qui écrit «entre 6 et 8 inclus» s’exécute.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
