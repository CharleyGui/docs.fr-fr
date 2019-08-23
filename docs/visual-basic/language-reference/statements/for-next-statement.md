---
title: For...Next, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 9a9aed51f6d7bf3233e6e89116b8209b22f3d15d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912415"
---
# <a name="fornext-statement-visual-basic"></a>For...Next, instruction (Visual Basic)
Répète un groupe d’instructions un nombre de fois spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>Composants  
  
|Élément|Description|  
|----------|-----------------|  
|`counter`|Obligatoire dans l' `For` instruction. Variable numérique. Variable de contrôle de la boucle. Pour plus d’informations, consultez l' [argument Counter](#BKMK_Counter) plus loin dans cette rubrique.|  
|`datatype`|facultatif. Type de données `counter`de. Pour plus d’informations, consultez l' [argument Counter](#BKMK_Counter) plus loin dans cette rubrique.|  
|`start`|Requis. Expression numérique. Valeur initiale de `counter`.|  
|`end`|Requis. Expression numérique. Valeur finale de `counter`.|  
|`step`|facultatif. Expression numérique. Quantité d' `counter` incrémentation à chaque fois par la boucle.|  
|`statements`|facultatif. Une ou plusieurs instructions entre `For` et `Next` qui exécutent le nombre de fois spécifié.|  
|`Continue For`|facultatif. Transfère le contrôle à l’itération de boucle suivante.|  
|`Exit For`|facultatif. Transfère le contrôle hors de `For` la boucle.|  
|`Next`|Requis. Termine la définition de la `For` boucle.|  
  
> [!NOTE]
> Le `To` mot clé est utilisé dans cette instruction pour spécifier la plage du compteur. Vous pouvez également utiliser ce mot clé dans la [sélection... Instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md) et déclarations de tableau. Pour plus d’informations sur les déclarations de tableau, consultez [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Exemples simples  
 Vous utilisez un `For`... `Next` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre défini de fois.  
  
 Dans l’exemple suivant, la `index` variable commence par une valeur de 1 et est incrémentée à chaque itération de la boucle, se terminant après que `index` la valeur de atteint 5.  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 Dans l’exemple suivant, la `number` variable commence à 2 et est réduite de 0,25 sur chaque itération de la boucle, se terminant après que `number` la valeur de atteint 0. L' `Step` argument de `-.25` réduit la valeur de 0,25 à chaque itération de la boucle.  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  Une [fois... Instruction End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ou [do... Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) fonctionne bien lorsque vous ne connaissez pas à l’avance le nombre de fois où les instructions doivent être exécutées dans la boucle. Toutefois, lorsque vous prévoyez d’exécuter la boucle un nombre spécifique de fois, une `For`... `Next` la boucle est un meilleur choix. Vous déterminez le nombre d’itérations lorsque vous entrez pour la première fois la boucle.  
  
## <a name="nesting-loops"></a>Imbrication de boucles  
 Vous pouvez imbriquer `For` des boucles en plaçant une boucle dans une autre. L’exemple suivant illustre l’imbrication `For`de... `Next` structures qui ont des valeurs d’étape différentes. La boucle externe crée une chaîne pour chaque itération de la boucle. La boucle interne décrémente une variable de compteur de boucle pour chaque itération de la boucle.  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 Lors de l’imbrication de boucles, chaque boucle doit avoir `counter` une variable unique.  
  
 Vous pouvez également imbriquer des structures de contrôle de types différents les unes dans les autres. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Quitter pour et continuer pour  
 L' `Exit For` instruction quitte `For`immédiatement...`Next` effectue une boucle et transfère le contrôle à l’instruction `Next` qui suit l’instruction.  
  
 L' `Continue For` instruction transfère immédiatement le contrôle à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 L’exemple suivant illustre l’utilisation des `Continue For` instructions et. `Exit For`  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 Vous pouvez placer n’importe quel `Exit For` nombre d’instructions `For`dans un...`Next` circuit. En cas d’utilisation dans `For`des...`Next` boucles, `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau supérieur d’imbrication suivant.  
  
 `Exit For`est souvent utilisé après l’évaluation d’une condition (par exemple, dans `If`une... `Then`... `Else` structure). Vous pouvez utiliser `Exit For` pour les conditions suivantes:  
  
- La poursuite de l’itération est inutile ou impossible. Une valeur erronée ou une demande d’arrêt peut créer cette condition.  
  
- `Try`... `Catch`... `Finally` l’instruction intercepte une exception. Vous pouvez utiliser `Exit For` à la fin `Finally` du bloc.  
  
- Vous avez une boucle infinie, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini. Si vous détectez une telle condition, vous pouvez `Exit For` utiliser pour échapper la boucle. Pour plus d’informations, consultez [do... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Implémentation technique  
 Quand un `For`... la boucle démarre, Visual Basic `start`évalue `end`, et `step`. `Next` Visual Basic évalue ces valeurs uniquement à ce moment-là, puis `start` affecte `counter`à. Avant l’exécution du bloc d’instructions, Visual Basic `counter` est `end`comparé à. Si `counter` est déjà supérieur à la `end` valeur (ou plus petit `step` si est négatif), `For` la boucle se termine et le contrôle passe à l' `Next` instruction qui suit l’instruction. Dans le cas contraire, le bloc d’instructions s’exécute.  
  
 Chaque fois que Visual Basic rencontre `Next` l’instruction, il s' `counter` incrémente `step` de et retourne à l' `For` instruction. Là encore, il `counter` effectue `end`une comparaison avec, et il exécute à nouveau le bloc ou quitte la boucle, en fonction du résultat. Ce processus se poursuit `counter` jusqu' `end` à la `Exit For` réussite ou l’exécution d’une instruction.  
  
 La boucle ne s’arrête `counter` pas tant `end`que n’a pas réussi. Si `counter` est égal à `end`, la boucle continue. La comparaison qui détermine s’il faut exécuter le bloc `counter` est `step` `counter` `end`  <=  si est positif et `step`  >=  `end` si est négatif.  
  
 Si vous modifiez la valeur de `counter` dans une boucle, votre code peut être plus difficile à lire et à déboguer. La modification de la `start`valeur `end`de, `step` ou n’affecte pas les valeurs d’itération qui ont été déterminées lors de la première entrée de la boucle.  
  
 Si vous imbriquez des boucles, le compilateur signale une erreur s’il `Next` rencontre l’instruction d’un niveau d’imbrication externe `Next` avant l’instruction d’un niveau interne. Toutefois, le compilateur peut détecter cette erreur qui se chevauche uniquement `counter` si vous `Next` spécifiez dans chaque instruction.  
  
### <a name="step-argument"></a>Argument Step  
 La valeur de `step` peut être positive ou négative. Ce paramètre détermine le traitement des boucles en fonction du tableau suivant:  
  
|**Valeur de l’étape**|**La boucle s’exécute si**|  
|--------------------|--------------------------|  
|Positif ou zéro|`counter` <= `end`|  
|Négatif|`counter` >= `end`|  
  
 La valeur par défaut `step` de est 1.  
  
### <a name="BKMK_Counter"></a>Argument de compteur  
 Le tableau suivant indique si `counter` définit une nouvelle variable locale dont la portée est limitée à la `For…Next` totalité de la boucle. Cette détermination varie selon que `datatype` est présent et si `counter` est déjà défini.  
  
|Est `datatype` présent?|Est `counter` déjà défini?|Result (indique `counter` si une nouvelle variable locale est étendue à l’ensemble `For...Next` de la boucle)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Non|Oui|Non, car `counter` est déjà défini. Si la portée de `counter` n’est pas locale à la procédure, un avertissement se produit au moment de la compilation.|  
|Non|Non|Oui. Le type de données est déduit à partir `start`des `end`expressions, `step` et. Pour plus d’informations sur l’inférence de type, consultez [instruction Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) et inférence de [type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Oui|Oui|Oui, mais uniquement si la variable `counter` existante est définie à l’extérieur de la procédure. Cette variable reste séparée. Si la portée de la variable `counter` existante est locale à la procédure, une erreur de compilation se produit.|  
|Oui|Non|Oui.|  
  
 Le type de données `counter` de détermine le type de l’itération, qui doit être l’un des types suivants:  
  
- `Byte` ,`SByte`, ,,`Decimal`, ,`Double`,, ,,Ou.`Long` `ULong` `Integer` `UShort` `Short` `UInteger` `Single`  
  
- Énumération que vous déclarez à l’aide d’une [instruction enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
- Élément `Object`.  
  
- Type `T` qui a les opérateurs suivants, où `B` est un type qui peut être utilisé dans une `Boolean` expression.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Vous pouvez éventuellement spécifier la `counter` variable dans l' `Next` instruction. Cette syntaxe améliore la lisibilité de votre programme, en particulier si vous avez des `For` boucles imbriquées. Vous devez spécifier la variable qui apparaît dans l’instruction `For` correspondante.  
  
 Les `start`expressions `end`, `counter`et `step` peuvent correspondre à n’importe quel type de données qui s’étend au type de. Si vous utilisez un type défini par l’utilisateur `counter`pour, vous devrez peut-être `CType` définir l’opérateur de conversion pour convertir `start`les `end`types de `step` , ou en type `counter`de.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant supprime tous les éléments d’une liste générique. Au lieu d’une variable [for each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md), l’exemple montre une `For`... `Next` instruction qui itère dans l’ordre décroissant. L’exemple utilise cette technique, car `removeAt` la méthode amène les éléments après l’élément supprimé à avoir une valeur d’index inférieure.  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant itère au sein d’une énumération déclarée à l’aide d’une [instruction enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les paramètres d’instruction utilisent une classe qui a des surcharges d' `+`opérateur `-`pour les opérateurs `<=` ,, `>=`et.  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic.List%601>
- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Collections](../../programming-guide/concepts/collections.md)
