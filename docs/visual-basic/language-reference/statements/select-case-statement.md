---
title: Select...Case, instruction
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
ms.openlocfilehash: 4dddfe5fbf7092c911291ffc6841e76f8c2748e9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352826"
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
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`testexpression`|Requis. Formule. Doit correspondre à l’un des types de données élémentaires (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`et `UShort`).|  
|`expressionlist`|Obligatoire dans une instruction `Case`. Liste des clauses d’expression représentant les valeurs de correspondance pour `testexpression`. Plusieurs clauses d’expression sont séparées par des virgules. Chaque clause peut prendre l’une des formes suivantes :<br /><br /> -   *expression1* `To` *Expression2*<br />-[`Is`] *expression* ComparisonOperator<br />*expression* -   <br /><br /> Utilisez le mot clé `To` pour spécifier les limites d’une plage de valeurs de correspondance pour `testexpression`. La valeur de `expression1` doit être inférieure ou égale à la valeur de `expression2`.<br /><br /> Utilisez le mot clé `Is` avec un opérateur de comparaison (`=`, `<>`, `<`, `<=`, `>`ou `>=`) pour spécifier une restriction sur les valeurs de correspondance pour `testexpression`. Si le mot clé `Is` n’est pas fourni, il est automatiquement inséré avant *comparisonoperator*.<br /><br /> Le formulaire spécifiant uniquement `expression` est traité comme un cas spécial du formulaire `Is` où *comparisonoperator* est le signe égal (`=`). Ce formulaire est évalué comme `testexpression` = `expression`.<br /><br /> Les expressions dans `expressionlist` peuvent être de n’importe quel type de données, à condition qu’elles soient implicitement convertibles en type de `testexpression` et que le `comparisonoperator` approprié soit valide pour les deux types avec lesquels il est utilisé.|  
|`statements`|Ce paramètre est facultatif. Une ou plusieurs instructions qui suivent `Case` qui s’exécutent si `testexpression` correspond à une clause dans `expressionlist`.|  
|`elsestatements`|Ce paramètre est facultatif. Une ou plusieurs instructions qui suivent `Case Else` qui s’exécutent si `testexpression` ne correspond à aucune clause de la `expressionlist` de l’une des instructions `Case`.|  
|`End Select`|Met fin à la définition de la construction `Select`...`Case`.|  
  
## <a name="remarks"></a>Notes  
 Si `testexpression` correspond à une clause `Case` `expressionlist`, les instructions qui suivent cette `Case` instruction s’exécutent jusqu’à l’instruction `Case`, `Case Else`ou `End Select` suivante. Le contrôle passe ensuite à l’instruction qui suit `End Select`. Si `testexpression` correspond à une clause `expressionlist` dans plusieurs clauses `Case`, seules les instructions qui suivent la première correspondance s’exécutent.  
  
 L’instruction `Case Else` est utilisée pour introduire le `elsestatements` à exécuter si aucune correspondance n’est trouvée entre le `testexpression` et une clause `expressionlist` dans une des autres instructions `Case`. Bien que cela ne soit pas obligatoire, il est judicieux de disposer d’une instruction `Case Else` dans votre construction `Select Case` pour gérer les valeurs de `testexpression` imprévues. Si aucune clause `Case` `expressionlist` ne correspond `testexpression` et qu’il n’y a pas d’instruction `Case Else`, le contrôle passe à l’instruction qui suit `End Select`.  
  
 Vous pouvez utiliser plusieurs expressions ou plages dans chaque clause `Case`. Par exemple, la ligne suivante est valide.  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> Le mot clé `Is` utilisé dans les instructions `Case` et `Case Else` n’est pas le même que l' [opérateur is](../../../visual-basic/language-reference/operators/is-operator.md), qui est utilisé pour la comparaison des références d’objet.  
  
 Vous pouvez spécifier des plages et plusieurs expressions pour les chaînes de caractères. Dans l’exemple suivant, `Case` correspond à une chaîne qui est exactement égale à « apples », a une valeur comprise entre « NUTS » et « soupe » dans l’ordre alphabétique, ou contient la même valeur que la valeur actuelle de `testItem`.  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 Le paramètre de `Option Compare` peut affecter les comparaisons de chaînes. Sous `Option Compare Text`, les chaînes « Apples » et « Apples » sont considérées comme égales, mais sous `Option Compare Binary`, ce n’est pas le cas.  
  
> [!NOTE]
> Une instruction `Case` avec plusieurs clauses peut présenter un comportement connu sous le nom de *court-circuit*. Visual Basic évalue les clauses de gauche à droite et, si une correspondance est trouvée avec `testexpression`, les clauses restantes ne sont pas évaluées. Le court-circuit peut améliorer les performances, mais il peut produire des résultats inattendus si chaque expression de `expressionlist` doit être évaluée. Pour plus d’informations sur le court-circuit, consultez [expressions booléennes](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).  
  
 Si le code d’un bloc d’instructions `Case` ou `Case Else` n’a pas besoin d’exécuter d’autres instructions dans le bloc, il peut quitter le bloc à l’aide de l’instruction `Exit Select`. Cela transfère immédiatement le contrôle à l’instruction qui suit `End Select`.  
  
 les constructions de `Select Case` peuvent être imbriquées. Chaque construction de `Select Case` imbriquée doit avoir une instruction `End Select` correspondante et doit être entièrement contenue dans un bloc d’instructions `Case` ou `Case Else` unique de la construction de `Select Case` externe dans laquelle elle est imbriquée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise une construction de `Select Case` pour écrire une ligne correspondant à la valeur de la variable `number`. La deuxième instruction `Case` contient la valeur qui correspond à la valeur actuelle de `number`. par conséquent, l’instruction qui écrit « entre 6 et 8 inclus » s’exécute.  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
