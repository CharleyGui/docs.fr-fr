---
title: Instructions
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: f63f0f0212913f95baab2a8a43c4b7f25a859cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400889"
---
# <a name="statements-in-visual-basic"></a>Instructions dans Visual Basic

Une déclaration dans Visual Basic est une instruction complète. Il peut contenir des mots clés, des opérateurs, des variables, des constantes et des expressions. Chaque déclaration appartient à l’une des catégories suivantes :

- **Déclaration ,** qui désignent une procédure variable, constante ou, et peut également spécifier un type de données.

- **Déclarations exécutables**, qui initient des actions. Ces déclarations peuvent appeler une méthode ou une fonction, et ils peuvent boucler ou brancher à travers des blocs de code. Les énoncés exécutables comprennent des **énoncés d’affectation**, qui attribuent une valeur ou une expression à une variable ou constante.

Ce sujet décrit chaque catégorie. En outre, ce sujet décrit comment combiner plusieurs déclarations sur une seule ligne et comment continuer une déclaration sur plusieurs lignes.

## <a name="declaration-statements"></a>Instructions de déclaration

Vous utilisez des relevés de déclaration pour nommer et définir les procédures, les variables, les propriétés, les tableaux et les constantes. Lorsque vous déclarez un élément de programmation, vous pouvez également définir son type de données, son niveau d’accès et sa portée. Pour plus d’informations, voir [Les caractéristiques déclarées](./declared-elements/declared-element-characteristics.md).

L’exemple suivant contient trois déclarations.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

La première déclaration `Sub` est la déclaration. Avec sa `End Sub` déclaration correspondante, il déclare `applyFormat`une procédure nommée . Il spécifie `Public`également que c’est `applyFormat` , ce qui signifie que n’importe quel code qui peut se référer à elle peut l’appeler.

La deuxième déclaration `Const` est la déclaration, `limit`qui déclare `Integer` la constante , spécifiant le type de données et une valeur de 33.

La troisième déclaration `Dim` est la déclaration, `thisWidget`qui déclare la variable . Le type de données est un objet `Widget` spécifique, à savoir un objet créé à partir de la classe. Vous pouvez déclarer qu’une variable est de n’importe quel type de données élémentaire ou de tout type d’objet exposé dans l’application que vous utilisez.

### <a name="initial-values"></a>valeurs initiales

Lorsque le code contenant une déclaration s’exécute, Visual Basic réserve la mémoire requise pour l’élément déclaré. Si l’élément a une valeur, Visual Basic l’a parasorit à la valeur par défaut de son type de données. Pour plus d’informations, voir "Comportement" dans [Dim Statement](../../language-reference/statements/dim-statement.md).

Vous pouvez attribuer une valeur initiale à une variable dans le cadre de sa déclaration, comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Si une variable est une variable d’objet, vous pouvez créer explicitement une instance de sa classe lorsque vous la déclarez en utilisant le mot clé [Du Nouvel Opérateur,](../../../visual-basic/language-reference/operators/new-operator.md) comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Notez que la valeur initiale que vous spécifiez dans une déclaration n’est pas attribuée à une variable jusqu’à ce que l’exécution atteigne son relevé de déclaration. Jusque-là, la variable contient la valeur par défaut pour son type de données.

## <a name="executable-statements"></a>Déclarations exécutables

Une déclaration exécutable effectue une action. Il peut appeler une procédure, branche à un autre endroit dans le code, boucler à travers plusieurs déclarations, ou évaluer une expression. Une déclaration d’affectation est un cas particulier d’une déclaration exécutable.

L’exemple suivant `If...Then...Else` utilise une structure de contrôle pour exécuter différents blocs de code en fonction de la valeur d’une variable. Dans chaque bloc de `For...Next` code, une boucle exécute un nombre spécifié de fois.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

L’énoncé `If` dans l’exemple précédent `clockwise`vérifie la valeur du paramètre . Si la `True`valeur est `spinClockwise` , `aWidget`il appelle la méthode de . Si la `False`valeur est `spinCounterClockwise` , `aWidget`il appelle la méthode de . La `If...Then...Else` structure de `End If`contrôle se termine par .

La `For...Next` boucle dans chaque bloc appelle la méthode appropriée un `revolutions` certain nombre de fois égale à la valeur du paramètre.

## <a name="assignment-statements"></a>Déclarations d’affectation

Les instructions d’affectation effectuent des opérations d’affectation, qui`=`consistent à prendre la valeur sur le côté droit de l’opérateur d’affectation ( ) et à la stocker dans l’élément de gauche, comme dans l’exemple suivant.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

Dans l’exemple précédent, l’énoncé d’affectation stocke `v`la valeur littérale 42 dans la variable .

### <a name="eligible-programming-elements"></a>Éléments de programmation admissibles

L’élément de programmation du côté gauche de l’opérateur d’affectation doit être en mesure d’accepter et de stocker une valeur. Cela signifie qu’il doit s’agir d’une variable ou d’une propriété qui n’est pas [ReadOnly,](../../../visual-basic/language-reference/modifiers/readonly.md)ou il doit s’agir d’un élément de tableau. Dans le contexte d’une déclaration d’affectation, un tel élément est parfois appelé *un lvalue*, pour la «valeur gauche».

La valeur du côté droit de l’opérateur d’affectation est générée par une expression, qui peut se composer de n’importe quelle combinaison de littérals, constantes, variables, propriétés, éléments de tableau, autres expressions, ou des appels de fonction. L'exemple suivant illustre ce comportement.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

L’exemple précédent ajoute la `y` valeur détenue en `z`variable à la valeur détenue en `findResult`variable, puis ajoute la valeur retournée par l’appel à fonctionner . La valeur totale de cette expression `x`est ensuite stockée dans variable .

### <a name="data-types-in-assignment-statements"></a>Types de données dans les énoncés d’affectation

En plus des valeurs numériques, `String` l’opérateur d’affectation peut également attribuer des valeurs, comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Vous pouvez `Boolean` également attribuer des `Boolean` valeurs, `Boolean` en utilisant un littéral ou une expression, comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

De même, vous pouvez attribuer des `Char` `Date`valeurs `Object` appropriées à des éléments de programmation du type de données, ou de type de données. Vous pouvez également attribuer une instance d’objet à un élément déclaré être de la classe à partir de laquelle cette instance est créée.

### <a name="compound-assignment-statements"></a>Déclarations d’affectation composées

*Les énoncés d’affectation composés* effectuent d’abord une opération sur une expression avant de l’attribuer à un élément de programmation. L’exemple suivant illustre l’un de ces opérateurs, `+=`qui incrémente la valeur de la variable sur le côté gauche de l’opérateur par la valeur de l’expression à droite.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

L’exemple précédent ajoute 1 `n`à la valeur de `n`, puis stocke cette nouvelle valeur en . Il s’agit d’un équivalent abréviation de la déclaration suivante :

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Une variété d’opérations d’affectation de composés peuvent être effectuées à l’aide d’opérateurs de ce type. Pour une liste de ces opérateurs et plus d’informations à leur sujet, voir [Opérateurs d’affectation](../../../visual-basic/language-reference/operators/assignment-operators.md).

L’opérateur d’affectation`&=`de concatenation ( ) est utile pour ajouter une chaîne à la fin des chaînes déjà existantes, comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Conversions de type dans les énoncés d’affectation

La valeur que vous attribuez à un élément variable, de propriété ou de tableau doit être d’un type de données approprié à cet élément de destination. En général, vous devriez essayer de générer une valeur du même type de données que celle de l’élément de destination. Cependant, certains types peuvent être convertis en d’autres types pendant l’affectation.

Pour plus d’informations sur la conversion entre les types de données, voir [Conversions de type dans Visual Basic](./data-types/type-conversions.md). En bref, Visual Basic convertit automatiquement une valeur d’un type donné à tout autre type auquel il s’élargit. Une *conversion croissante* est une conversion qui réussit toujours au moment de l’exécution et ne perd aucune donnée. Par exemple, Visual Basic `Integer` convertit une valeur au `Double` besoin, car `Integer` s’élargit à `Double`. Pour plus d’informations, consultez [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md).

*Le rétrécissement des conversions* (celles qui ne s’élargissent pas) comporte un risque d’échec au moment de la course ou de perte de données. Vous pouvez effectuer une conversion de rétrécissement explicitement en utilisant une fonction de conversion de type, ou vous pouvez diriger le compilateur pour effectuer toutes les conversions implicitement par réglage `Option Strict Off`. Pour plus d’informations, voir [Conversions implicites et explicites](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Mettre plusieurs déclarations sur une seule ligne

Vous pouvez avoir plusieurs déclarations sur une`:`seule ligne séparée par le côlon ( ) caractère. L'exemple suivant illustre ce comportement.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Bien que parfois pratique, cette forme de syntaxe rend votre code difficile à lire et à entretenir. Ainsi, il est recommandé de garder une déclaration à une ligne.

## <a name="continuing-a-statement-over-multiple-lines"></a>Poursuite d’une déclaration sur plusieurs lignes

Une déclaration s’adapte généralement sur une ligne, mais quand elle est trop longue, vous pouvez la continuer sur la`_`ligne suivante à l’aide d’une séquence de continuation de ligne, qui se compose d’un espace suivi d’un caractère de soulignement () suivi d’un retour de voiture. Dans l’exemple `MsgBox` suivant, la déclaration exécutable est poursuivie sur deux lignes.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Poursuite implicite de la ligne

Dans de nombreux cas, vous pouvez continuer une déclaration sur`_`la ligne suivante consécutive sans utiliser le caractère de souligner ( ). Les éléments syntaxiques suivants continuent implicitement l’énoncé sur la ligne suivante du code.

- Après une virgule (`,`). Par exemple :

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Après une parenthèse`(`ouverte ( ) ou`)`avant une parenthèse de clôture ( ). Par exemple :

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Après une accolade bouclée ouverte ()`{`ou`}`avant une accolade bouclée de fermeture (). Par exemple :

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Pour plus d’informations, voir [Object Initializers: Named and Anonymous Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md) or Collection [Initializers](./collection-initializers/index.md).

- Après une expression`<%=`intégrée ouverte ( ) ou`%>`avant la fin d’une expression intégrée ( ) dans un XML littéral. Par exemple :

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Pour plus d’informations, voir [Expressions intégrées dans XML](./xml/embedded-expressions-in-xml.md).

- Après l’opérateur concatenation (`&`). Par exemple :

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Pour plus d’informations, voir [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Après les`=`opérateurs `&=` `:=`d’affectation `*=` `/=`( `\=` `^=`, `<<=` `>>=`, , `+=`, `-=`, , , , , . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Par exemple :

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Pour plus d’informations, voir [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Après les`+`opérateurs `-` `/`binaires ( , , `>>`, `<<` `And`, `AndAlso` `Or` `OrElse` `Like` `Xor` `<` `>` `<=` `>=` `^` `*` `Mod`, `<>`, , , , , , , , , , , , , , ) dans une expression. Par exemple :

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Pour plus d’informations, voir [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Après `Is` le `IsNot` et les opérateurs. Par exemple :

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Pour plus d’informations, voir [Opérateurs répertoriés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Après un personnage`.`de qualification membre ( ) et avant le nom du membre. Par exemple :

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Toutefois, vous devez inclure un`_`caractère de continuation de ligne () suivant un personnage de qualification de membre lorsque vous utilisez l’énoncé `With` ou fournissez des valeurs dans la liste d’initialisation pour un type. Envisagez de casser la ligne après `=`l’opérateur `With` d’affectation (par exemple, ) lorsque vous utilisez des listes d’instructions ou d’initialisation d’objets. Par exemple :

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Pour plus d’informations, voir [Avec... Terminer avec déclaration](../../../visual-basic/language-reference/statements/with-end-with-statement.md) ou [initialisateurs d’objets: Nommés et Anonymes Types](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Après un qualificatif`.` `.@` de `...`propriété d’axe XML (ou ). Toutefois, vous devez inclure un`_`caractère de continuation de ligne ( `With` ) lorsque vous spécifiez un qualificatif membre lorsque vous utilisez le mot clé. Par exemple :

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Pour plus d’informations, voir [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).

- Après un signe moins que (<) ou avant un signe`>`plus grand que ( ) lorsque vous spécifiez un attribut. Aussi après un signe`>`plus grand que ( ) lorsque vous spécifiez un attribut. Toutefois, vous devez inclure un`_`caractère de continuation de ligne () lorsque vous spécifiez des attributs de niveau d’assemblage ou de module. Par exemple :

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Pour plus d’informations, voir [Aperçu des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Avant et après les`Aggregate` `Distinct`opérateurs `From` `Group By`de `Group Join` `Join`requête `Let` `Order By`( `Select`, , , `In` `Into`, `On` `Ascending`, `Descending`, , , , `Skip`, `Skip While`, , `Take`, `Take While`, `Where`, , , , , , , , , et . Vous ne pouvez pas briser une ligne entre les mots clés`Order By`des `Group Join` `Take While`opérateurs `Skip While`de requête qui sont composés de plusieurs mots clés ( , , , et ). Par exemple :

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Pour plus d’informations, voir [Questions](../../../visual-basic/language-reference/queries/index.md).

- Après `In` le mot `For Each` clé dans une déclaration. Par exemple :

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Pour plus d’informations, voir [Pour chaque... Énoncé suivant](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Après `From` le mot clé dans un initialisateur de collection. Par exemple :

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Pour plus d’informations, consultez [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Ajout de commentaires

Le code source n’est pas toujours explicite, même pour le programmeur qui l’a écrit. Pour aider à documenter leur code, la plupart des programmeurs font donc un usage libéral des commentaires intégrés. Les commentaires dans le code peuvent expliquer une procédure ou une instruction particulière à toute personne lisant ou travaillant avec elle plus tard. Visual Basic ignore les commentaires pendant la compilation, et ils n’affectent pas le code compilé.

Les lignes de commentaires commencent`'`par `REM` une apostrophe ( ) ou suivie d’un espace. Ils peuvent être ajoutés n’importe où dans le code, sauf dans une chaîne. Pour ajouter un commentaire à une déclaration, insérer une apostrophe ou `REM` après la déclaration, suivie du commentaire. Les commentaires peuvent également aller sur leur propre ligne séparée. L’exemple suivant montre ces possibilités.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Vérification des erreurs de compilation

Si, après avoir tapé une ligne de code, la ligne est affichée avec un soulignement bleu ondulé (un message d’erreur peut apparaître ainsi), il ya une erreur de syntaxe dans la déclaration. Vous devez savoir ce qui ne va pas avec l’instruction (en regardant dans la liste de tâches, ou planant sur l’erreur avec le pointeur de la souris et la lecture du message d’erreur) et le corriger. Jusqu’à ce que vous ayez corrigé toutes les erreurs de syntaxe dans votre code, votre programme ne sera pas compilé correctement.

## <a name="related-sections"></a>Sections connexes

|Terme|Définition|
|---|---|
|[Opérateurs d’affectation](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fournit des liens vers des pages `=` `*=`de `&=`référence linguistique couvrant les opérateurs d’affectation tels que , , et .|
|[Opérateurs et expressions](./operators-and-expressions/index.md)|Montre comment combiner les éléments avec les opérateurs pour produire de nouvelles valeurs.|
|[Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Montre comment briser une seule instruction en plusieurs lignes et comment placer plusieurs déclarations sur la même ligne.|
|[Guide pratique : étiqueter des instructions](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Montre comment étiqueter une ligne de code.|
