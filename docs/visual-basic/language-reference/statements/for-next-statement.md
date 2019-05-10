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
ms.openlocfilehash: 7f982c97bd76288ecd1a8d1f53fc2b25b0bb829e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623883"
---
# <a name="fornext-statement-visual-basic"></a>For...Next, instruction (Visual Basic)
Répète un groupe d’instructions un nombre spécifié de fois.  
  
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
|`counter`|Requis dans le `For` instruction. Variable numérique. La variable de contrôle de la boucle. Pour plus d’informations, consultez [compteur Argument](#BKMK_Counter) plus loin dans cette rubrique.|  
|`datatype`|Facultatif. Type de données de `counter`. Pour plus d’informations, consultez [compteur Argument](#BKMK_Counter) plus loin dans cette rubrique.|  
|`start`|Obligatoire. Expression numérique. Valeur initiale de `counter`.|  
|`end`|Obligatoire. Expression numérique. La valeur finale de `counter`.|  
|`step`|Facultatif. Expression numérique. Le montant par lequel `counter` est incrémenté chaque fois que la boucle.|  
|`statements`|Facultatif. Une ou plusieurs instructions entre `For` et `Next` qui exécutent le nombre de fois spécifié.|  
|`Continue For`|Facultatif. Transfère le contrôle à la prochaine itération de boucle.|  
|`Exit For`|Facultatif. Transfère le contrôle de la `For` boucle.|  
|`Next`|Obligatoire. Termine la définition de la `For` boucle.|  
  
> [!NOTE]
>  Le `To` mot clé est utilisé dans cette instruction pour spécifier la plage pour le compteur. Vous pouvez également utiliser ce mot clé dans le [sélectionnez... Instruction case](../../../visual-basic/language-reference/statements/select-case-statement.md) et dans les déclarations de tableau. Pour plus d’informations sur les déclarations de tableau, consultez [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="simple-examples"></a>Exemples simples  
 Vous utilisez un `For`... `Next` structure lorsque vous souhaitez répéter un ensemble d’instructions un nombre défini de fois.  
  
 Dans l’exemple suivant, le `index` variable commence par une valeur de 1 et est incrémenté à chaque itération de la boucle, de fin postérieure à la valeur de `index` atteint 5.  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 Dans l’exemple suivant, le `number` variable commence à 2 et est réduite par 0,25 à chaque itération de la boucle, de fin postérieure à la valeur de `number` atteint 0. Le `Step` argument de `-.25` réduit la valeur de 0,25 à chaque itération de la boucle.  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  Un [tandis que... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ou [faire... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md) fonctionne bien lorsque vous ne savez pas à l’avance combien de fois pour exécuter les instructions dans la boucle. Toutefois, lorsque vous prévoyez d’exécuter la boucle un certain nombre de fois, un `For`... `Next` boucle est un meilleur choix. Vous déterminez le nombre d’itérations lorsque vous entrez tout d’abord la boucle.  
  
## <a name="nesting-loops"></a>Imbrication de boucles  
 Vous pouvez imbriquer `For` boucles en plaçant une boucle à l’intérieur d’une autre. L’exemple suivant illustre des structures `For`... `Next` structures qui ont différentes valeurs d’étape. La boucle externe crée une chaîne pour chaque itération de la boucle. La boucle interne décrémente une variable de compteur de boucle pour chaque itération de la boucle.  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 Lors de l’imbrication des boucles, chaque boucle doit posséder une valeur unique `counter` variable.  
  
 Vous pouvez également imbriquer des structures de contrôle de différents types dans d’autres. Pour plus d’informations, consultez [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## <a name="exit-for-and-continue-for"></a>Quitter pour et continuer pour  
 Le `Exit For` instruction quitte immédiatement la `For`...`Next` boucle et transfère le contrôle à l’instruction qui suit la `Next` instruction.  
  
 La `Continue For` instruction transfère le contrôle immédiatement à l’itération suivante de la boucle. Pour plus d’informations, consultez [instruction Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 L’exemple suivant illustre l’utilisation de la `Continue For` et `Exit For` instructions.  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 Vous pouvez placer un nombre quelconque de `Exit For` instructions dans un `For`...`Next` Une boucle. Lorsqu’il est utilisé dans imbriqués `For`...`Next` boucles, `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau d’imbrication supérieur suivant.  
  
 `Exit For` est souvent utilisé après l’évaluation d’une condition (par exemple, dans un `If`... `Then`... `Else` structure). Vous souhaiterez peut-être utiliser `Exit For` pour les conditions suivantes :  
  
- Pour continuer à effectuer une itération est inutile ou impossible. Une valeur erronée ou une demande d’arrêt peut créer cette condition.  
  
- Un `Try`... `Catch`... `Finally` instruction intercepte une exception. Vous pouvez utiliser `Exit For` à la fin de la `Finally` bloc.  
  
- Vous avez une boucle infinie, ce qui est une boucle qui pourrait s’exécuter de volumineux ou même infini de fois. Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour abandonner la boucle. Pour plus d’informations, consultez [faire... Instruction de boucle](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## <a name="technical-implementation"></a>Implémentation technique  
 Quand un `For`... `Next` commence, Visual Basic évalue `start`, `end`, et `step`. Visual Basic évalue ces valeurs uniquement à ce moment, puis assigne `start` à `counter`. Avant l’instruction bloc s’exécute, Visual Basic compare `counter` à `end`. Si `counter` est déjà supérieure à la `end` valeur (ou plus petits si `step` est un nombre négatif), le `For` boucle se termine et le contrôle passe à l’instruction qui suit la `Next` instruction. Sinon, le bloc d’instructions s’exécute.  
  
 Chaque fois que Visual Basic rencontre le `Next` instruction, elle incrémente `counter` par `step` et retourne à la `For` instruction. Il compare de nouveau `counter` à `end`, et à nouveau exécute le bloc ou quitte la boucle, en fonction du résultat. Ce processus se poursuit jusqu'à ce que `counter` passe `end` ou un `Exit For` est rencontrée.  
  
 La boucle ne s’arrête jusqu'à ce que `counter` écoulé `end`. Si `counter` est égal à `end`, la boucle continue. La comparaison qui détermine s’il faut exécuter le bloc est `counter`  <=  `end` si `step` est un nombre positif et `counter`  >=  `end` si `step` est un nombre négatif.  
  
 Si vous modifiez la valeur de `counter` tandis que dans une boucle, votre code peut être plus difficile à lire et à déboguer. Modification de la valeur de `start`, `end`, ou `step` n’affecte pas les valeurs d’itération qui ont été déterminés lorsque la première entrée de la boucle.  
  
 Si vous imbriquez des boucles, le compilateur signale une erreur si elle rencontre le `Next` instruction d’un niveau d’imbrication externe avant la `Next` instruction d’un niveau interne. Toutefois, le compilateur peut détecter cette erreur de chevauchement uniquement si vous spécifiez `counter` dans chaque `Next` instruction.  
  
### <a name="step-argument"></a>Argument d’étape  
 La valeur de `step` peut être positif ou négatif. Ce paramètre détermine le traitement des boucles conformément au tableau suivant :  
  
|**Valeur de l’étape**|**La boucle s’exécute si**|  
|--------------------|--------------------------|  
|Positif ou zéro|`counter` <= `end`|  
|Négatif|`counter` >= `end`|  
  
 La valeur par défaut de `step` est 1.  
  
### <a name="BKMK_Counter"></a> Argument de compteur  
 Le tableau suivant indique si `counter` définit une nouvelle variable locale dont l’étendue correspond à l’intégralité de `For…Next` boucle. Cette détermination varie selon que `datatype` est présent et si `counter` est déjà défini.  
  
|Est `datatype` présent ?|Est `counter` déjà défini ?|Résultat (si `counter` définit une nouvelle variable locale dont l’étendue correspond à l’intégralité de `For...Next` boucle)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Non|Oui|Non, étant donné que `counter` est déjà défini. Si l’étendue de `counter` n’est pas local à la procédure, un avertissement de compilation se produit.|  
|Non|Non|Oui. Le type de données est déduit à partir de la `start`, `end`, et `step` expressions. Pour plus d’informations sur l’inférence de type, consultez [Option Infer, instruction](../../../visual-basic/language-reference/statements/option-infer-statement.md) et [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Oui|Oui|Oui, mais uniquement si existant `counter` variable est définie en dehors de la procédure. Cette variable reste distincte. Si l’étendue existants `counter` variable est locale à la procédure, une erreur de compilation se produit.|  
|Oui|Non|Oui.|  
  
 Le type de données de `counter` détermine le type de l’itération, qui doit être un des types suivants :  
  
- Un `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, ou `Double`.  
  
- Une énumération que vous déclarez en utilisant un [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
- Élément `Object`.  
  
- Un type `T` qui a les opérateurs suivants, où `B` est un type qui peut être utilisé dans un `Boolean` expression.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Vous pouvez éventuellement spécifier le `counter` variable dans la `Next` instruction. Cette syntaxe améliore la lisibilité de votre programme, en particulier si vous avez imbriqué `For` boucles. Vous devez spécifier la variable qui s’affiche dans le correspondantes `For` instruction.  
  
 Le `start`, `end`, et `step` expressions peuvent correspondre à n’importe quel type de données qui s’étend au type de `counter`. Si vous utilisez un type défini par l’utilisateur pour `counter`, vous devrez peut-être définir le `CType` opérateur de conversion pour convertir les types de `start`, `end`, ou `step` au type de `counter`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant supprime tous les éléments d’une liste générique. Au lieu d’un [pour chaque... L’instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md), l’exemple montre un `For`... `Next` qui itère dans l’ordre décroissant. L’exemple utilise cette technique, car le `removeAt` (méthode), les éléments après l’élément supprimé ont une valeur d’index inférieure.  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant effectue une itération dans une énumération qui est déclarée à l’aide un [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, les paramètres d’instruction utilisent une classe qui a les surcharges d’opérateur pour le `+`, `-`, `>=`, et `<=` opérateurs.  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic.List%601>
- [Structures de boucle](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While (instruction)](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop (instruction)](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [Structures de contrôle imbriquées](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Collections](../../programming-guide/concepts/collections.md)
