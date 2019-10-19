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
ms.openlocfilehash: a60293fc837b6d12810a211892c391f24a46d4e6
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582963"
---
# <a name="fornext-statement-visual-basic"></a>For...Next, instruction (Visual Basic)

Répète un groupe d’instructions un nombre de fois spécifié.

## <a name="syntax"></a>Syntaxe

```vb
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
|`counter`|Obligatoire dans l’instruction `For`. Variable numérique. Variable de contrôle de la boucle. Pour plus d’informations, consultez l' [argument Counter](#BKMK_Counter) plus loin dans cette rubrique.|
|`datatype`|Optionnel. Type de données de `counter`. Pour plus d’informations, consultez l' [argument Counter](#BKMK_Counter) plus loin dans cette rubrique.|
|`start`|Requis. Expression numérique. Valeur initiale de `counter`.|
|`end`|Requis. Expression numérique. Valeur finale de `counter`.|
|`step`|Optionnel. Expression numérique. Valeur par laquelle `counter` est incrémenté à chaque fois par la boucle.|
|`statements`|Optionnel. Une ou plusieurs instructions entre `For` et `Next` qui exécutent le nombre de fois spécifié.|
|`Continue For`|Optionnel. Transfère le contrôle à l’itération de boucle suivante.|
|`Exit For`|Optionnel. Transfère le contrôle hors de la boucle de `For`.|
|`Next`|Requis. Termine la définition de la boucle `For`.|

> [!NOTE]
> Le mot clé `To` est utilisé dans cette instruction pour spécifier la plage du compteur. Vous pouvez également utiliser ce mot clé dans la [sélection... Instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md) et déclarations de tableau. Pour plus d’informations sur les déclarations de tableau, consultez [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md).

## <a name="simple-examples"></a>Exemples simples

Vous utilisez une `For`... `Next` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre défini de fois.

Dans l’exemple suivant, la variable `index` commence par la valeur 1 et est incrémentée à chaque itération de la boucle, se terminant après que la valeur de `index` atteint 5.

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

Dans l’exemple suivant, la variable `number` commence à 2 et est réduite de 0,25 sur chaque itération de la boucle, se terminant après que la valeur de `number` atteint 0. L’argument `Step` de `-.25` réduit la valeur de 0,25 à chaque itération de la boucle.

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> Une [fois... Instruction End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ou [do... Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) fonctionne bien lorsque vous ne connaissez pas à l’avance le nombre de fois où les instructions doivent être exécutées dans la boucle. Toutefois, lorsque vous prévoyez d’exécuter la boucle un nombre spécifique de fois, une `For`... `Next` boucle est un meilleur choix. Vous déterminez le nombre d’itérations lorsque vous entrez pour la première fois la boucle.

## <a name="nesting-loops"></a>Imbrication de boucles

Vous pouvez imbriquer des boucles `For` en plaçant une boucle dans une autre. L’exemple suivant illustre une `For` imbriquée... `Next` les structures qui ont des valeurs d’étape différentes. La boucle externe crée une chaîne pour chaque itération de la boucle. La boucle interne décrémente une variable de compteur de boucle pour chaque itération de la boucle.

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

Lors de l’imbrication de boucles, chaque boucle doit avoir une variable `counter` unique.

Vous pouvez également imbriquer des structures de contrôle de types différents les unes dans les autres. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).

## <a name="exit-for-and-continue-for"></a>Quitter pour et continuer pour

L’instruction `Exit For` quitte immédiatement l' `For`... `Next` effectue une boucle et transfère le contrôle à l’instruction qui suit l’instruction `Next`.

L’instruction `Continue For` transfère immédiatement le contrôle à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction continue](../../../visual-basic/language-reference/statements/continue-statement.md).

L’exemple suivant illustre l’utilisation des instructions `Continue For` et `Exit For`.

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

Vous pouvez placer n’importe quel nombre d’instructions `Exit For` dans un `For`... `Next` circuit. En cas d’utilisation dans les `For` imbriquées... `Next` boucles, `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau supérieur d’imbrication suivant.

`Exit For` est souvent utilisée après l’évaluation d’une condition (par exemple, dans une structure `If`... `Then`... `Else`). Vous pouvez utiliser `Exit For` pour les conditions suivantes :

- La poursuite de l’itération est inutile ou impossible. Une valeur erronée ou une demande d’arrêt peut créer cette condition.

- Une `Try`... `Catch`... `Finally` instruction intercepte une exception. Vous pouvez utiliser `Exit For` à la fin du bloc `Finally`.

- Vous avez une boucle infinie, qui est une boucle qui peut exécuter un nombre de fois très long, voire infini. Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour échapper à la boucle. Pour plus d’informations, consultez [do... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md).

## <a name="technical-implementation"></a>Implémentation technique

Quand un `For`... `Next` boucle démarre, Visual Basic évalue `start`, `end` et `step`. Visual Basic évalue ces valeurs uniquement à ce moment-là, puis affecte des `start` à `counter`. Avant l’exécution du bloc d’instructions, Visual Basic compare `counter` à `end`. Si `counter` est déjà supérieure à la valeur `end` (ou plus petite si `step` est négatif), la boucle `For` se termine et le contrôle passe à l’instruction qui suit l’instruction `Next`. Dans le cas contraire, le bloc d’instructions s’exécute.

Chaque fois que Visual Basic rencontre l’instruction `Next`, il incrémente `counter` par `step` et retourne à l’instruction `For`. Là encore, il compare `counter` à `end`, et il exécute à nouveau le bloc ou quitte la boucle, en fonction du résultat. Ce processus se poursuit jusqu’à ce que `counter` passe `end` ou qu’une instruction `Exit For` soit rencontrée.

La boucle ne s’arrête pas tant que `counter` n’a pas réussi `end`. Si `counter` est égal à `end`, la boucle continue. La comparaison qui détermine s’il faut exécuter le bloc est `counter`  <=  `end` si `step` est positive et `counter`  >=  `end` si `step` est négatif.

Si vous modifiez la valeur de `counter` à l’intérieur d’une boucle, votre code peut être plus difficile à lire et à déboguer. La modification de la valeur de `start`, `end` ou `step` n’affecte pas les valeurs d’itération qui ont été déterminées lors de la première entrée de la boucle.

Si vous imbriquez des boucles, le compilateur signale une erreur s’il rencontre l’instruction `Next` d’un niveau d’imbrication externe avant l’instruction `Next` d’un niveau interne. Toutefois, le compilateur peut détecter cette erreur qui se chevauche uniquement si vous spécifiez `counter` dans chaque instruction `Next`.

### <a name="step-argument"></a>Argument Step

La valeur de `step` peut être positive ou négative. Ce paramètre détermine le traitement des boucles en fonction du tableau suivant :

|**Valeur de l’étape**|**La boucle s’exécute si**|
|--------------------|--------------------------|
|Positif ou zéro|`counter` <= `end`|
|Négatif|`counter` >= `end`|

La valeur par défaut de `step` est 1.

### <a name="BKMK_Counter"></a>Argument de compteur

Le tableau suivant indique si `counter` définit une nouvelle variable locale dont la portée s’étend à l’ensemble de la boucle de `For…Next`. Cette détermination varie selon que `datatype` est présent et que `counter` est déjà défini.

|Est-il `datatype` présent ?|@No__t_0 déjà défini ?|Result (indique si `counter` définit une nouvelle variable locale dont la portée est limitée à l’ensemble de la boucle `For...Next`)|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|Non|Oui|Non, car `counter` est déjà défini. Si la portée de `counter` n’est pas locale à la procédure, un avertissement au moment de la compilation se produit.|
|Non|Non|Oui. Le type de données est déduit à partir des expressions `start`, `end` et `step`. Pour plus d’informations sur l’inférence de type, consultez [instruction Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) et [inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|
|Oui|Oui|Oui, mais uniquement si la variable `counter` existante est définie à l’extérieur de la procédure. Cette variable reste séparée. Si la portée de la variable `counter` existante est locale à la procédure, une erreur de compilation se produit.|
|Oui|Non|Oui.|

Le type de données de `counter` détermine le type de l’itération, qui doit être l’un des types suivants :

- @No__t_0, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single` ou 0.

- Énumération que vous déclarez à l’aide d’une [instruction enum](../../../visual-basic/language-reference/statements/enum-statement.md).

- Élément `Object`.

- @No__t_0 de type qui a les opérateurs suivants, où `B` est un type qui peut être utilisé dans une expression de `Boolean`.

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

Vous pouvez éventuellement spécifier la variable `counter` dans l’instruction `Next`. Cette syntaxe améliore la lisibilité de votre programme, surtout si vous avez imbriqué des boucles de `For`. Vous devez spécifier la variable qui apparaît dans l’instruction `For` correspondante.

Les expressions `start`, `end` et `step` peuvent correspondre à n’importe quel type de données qui s’étend au type de `counter`. Si vous utilisez un type défini par l’utilisateur pour `counter`, vous devrez peut-être définir l’opérateur de conversion `CType` pour convertir les types de `start`, `end` ou `step` en type de `counter`.

## <a name="example"></a>Exemple

L’exemple suivant supprime tous les éléments d’une liste générique. Au lieu d’une variable [for each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md), l’exemple montre une `For`... `Next` instruction qui itère dans l’ordre décroissant. L’exemple utilise cette technique, car la méthode `removeAt` amène les éléments après l’élément supprimé à avoir une valeur d’index inférieure.

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>Exemple

L’exemple suivant itère au sein d’une énumération déclarée à l’aide d’une [instruction enum](../../../visual-basic/language-reference/statements/enum-statement.md).

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>Exemple

Dans l’exemple suivant, les paramètres d’instruction utilisent une classe qui a des surcharges d’opérateur pour les opérateurs `+`, `-`, `>=` et `<=`.

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic.List%601>
- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Regroupements](../../programming-guide/concepts/collections.md)
