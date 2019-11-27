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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352500"
---
# <a name="statements-in-visual-basic"></a>Instructions dans Visual Basic

Une instruction dans Visual Basic est une instruction complète. Il peut contenir des mots clés, des opérateurs, des variables, des constantes et des expressions. Chaque instruction appartient à l’une des catégories suivantes :

- Les **instructions de déclaration**, qui désignent une variable, une constante ou une procédure, peuvent également spécifier un type de données.

- **Instructions exécutables**, qui initient des actions. Ces instructions peuvent appeler une méthode ou une fonction, et elles peuvent parcourir ou créer des branches dans des blocs de code. Les instructions exécutables incluent des **instructions d’assignation**qui affectent une valeur ou une expression à une variable ou une constante.

Cette rubrique décrit chaque catégorie. En outre, cette rubrique explique comment combiner plusieurs instructions sur une seule ligne et comment continuer une instruction sur plusieurs lignes.

## <a name="declaration-statements"></a>Instructions de déclaration

Vous utilisez des instructions de déclaration pour nommer et définir des procédures, des variables, des propriétés, des tableaux et des constantes. Lorsque vous déclarez un élément de programmation, vous pouvez également définir son type de données, son niveau d’accès et sa portée. Pour plus d’informations, consultez [caractéristiques des éléments déclarés](./declared-elements/declared-element-characteristics.md).

L’exemple suivant contient trois déclarations.

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

La première déclaration est l’instruction `Sub`. Avec son instruction `End Sub` correspondante, elle déclare une procédure nommée `applyFormat`. Il spécifie également que `applyFormat` est `Public`, ce qui signifie que tout code qui peut y faire référence peut l’appeler.

La deuxième déclaration est l’instruction `Const`, qui déclare la constante `limit`, en spécifiant le type de données `Integer` et la valeur 33.

La troisième déclaration est l’instruction `Dim`, qui déclare la variable `thisWidget`. Le type de données est un objet spécifique, à savoir un objet créé à partir de la classe `Widget`. Vous pouvez déclarer une variable de n’importe quel type de données élémentaire ou de tout type d’objet exposé dans l’application que vous utilisez.

### <a name="initial-values"></a>valeurs initiales

Lorsque le code contenant une instruction de déclaration s’exécute, Visual Basic réserve la mémoire requise pour l’élément déclaré. Si l’élément contient une valeur, Visual Basic l’initialise à sa valeur par défaut pour son type de données. Pour plus d’informations, consultez « comportement » dans l' [instruction Dim](../../language-reference/statements/dim-statement.md).

Vous pouvez assigner une valeur initiale à une variable dans le cadre de sa déclaration, comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

Si une variable est une variable objet, vous pouvez créer explicitement une instance de sa classe quand vous la déclarez à l’aide du mot clé [New Operator](../../../visual-basic/language-reference/operators/new-operator.md) , comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

Notez que la valeur initiale que vous spécifiez dans une instruction de déclaration n’est pas assignée à une variable tant que l’exécution n’a pas atteint son instruction de déclaration. Jusqu’à ce moment-là, la variable contient la valeur par défaut pour son type de données.

## <a name="executable-statements"></a>Instructions exécutables

Une instruction exécutable effectue une action. Il peut appeler une procédure, créer une branche à un autre emplacement dans le code, parcourir plusieurs instructions ou évaluer une expression. Une instruction d’assignation est un cas spécial d’une instruction exécutable.

L’exemple suivant utilise une structure de contrôle `If...Then...Else` pour exécuter différents blocs de code en fonction de la valeur d’une variable. Dans chaque bloc de code, une boucle `For...Next` s’exécute un nombre de fois spécifié.

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

L’instruction `If` dans l’exemple précédent vérifie la valeur du paramètre `clockwise`. Si la valeur est `True`, elle appelle la méthode `spinClockwise` de `aWidget`. Si la valeur est `False`, elle appelle la méthode `spinCounterClockwise` de `aWidget`. La structure de contrôle `If...Then...Else` se termine par `End If`.

La boucle `For...Next` dans chaque bloc appelle la méthode appropriée un nombre de fois égal à la valeur du paramètre `revolutions`.

## <a name="assignment-statements"></a>Instructions d’assignation

Les instructions d’assignation effectuent des opérations d’assignation, qui consistent à prendre la valeur à droite de l’opérateur d’assignation (`=`) et à la stocker dans l’élément à gauche, comme dans l’exemple suivant.

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

Dans l’exemple précédent, l’instruction d’assignation stocke la valeur littérale 42 dans la variable `v`.

### <a name="eligible-programming-elements"></a>Éléments de programmation éligibles

L’élément de programmation situé à gauche de l’opérateur d’assignation doit être en mesure d’accepter et de stocker une valeur. Cela signifie qu’il doit s’agir d’une variable ou d’une propriété qui n’est pas [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), ou qu’il doit s’agir d’un élément de tableau. Dans le contexte d’une instruction d’assignation, un tel élément est parfois appelé *lvalue*, pour « valeur de gauche ».

La valeur située à droite de l’opérateur d’assignation est générée par une expression, qui peut être constituée de toute combinaison de littéraux, de constantes, de variables, de propriétés, d’éléments de tableau, d’autres expressions ou d’appels de fonction. L’exemple suivant illustre ces actions.

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

L’exemple précédent ajoute la valeur contenue dans la variable `y` à la valeur contenue dans la variable `z`, puis ajoute la valeur retournée par l’appel à la fonction `findResult`. La valeur totale de cette expression est ensuite stockée dans la variable `x`.

### <a name="data-types-in-assignment-statements"></a>Types de données dans les instructions d’assignation

Outre les valeurs numériques, l’opérateur d’assignation peut également assigner des valeurs `String`, comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

Vous pouvez également assigner des valeurs `Boolean`, à l’aide d’un littéral `Boolean` ou d’une expression `Boolean`, comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

De même, vous pouvez assigner des valeurs appropriées aux éléments de programmation du type de données `Char`, `Date`ou `Object`. Vous pouvez également assigner une instance d’objet à un élément déclaré comme étant de la classe à partir de laquelle cette instance est créée.

### <a name="compound-assignment-statements"></a>Instructions d’assignation composée

Les *instructions d’assignation composée* effectuent d’abord une opération sur une expression avant de l’assigner à un élément de programmation. L’exemple suivant illustre l’un de ces opérateurs, `+=`, qui incrémente la valeur de la variable sur le côté gauche de l’opérateur par la valeur de l’expression à droite.

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

L’exemple précédent ajoute 1 à la valeur de `n`, puis stocke cette nouvelle valeur dans `n`. Il s’agit d’un raccourci équivalent de l’instruction suivante :

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

Diverses opérations d’assignation composée peuvent être effectuées à l’aide d’opérateurs de ce type. Pour obtenir la liste de ces opérateurs et des informations supplémentaires à leur sujet, consultez [opérateurs d’affectation](../../../visual-basic/language-reference/operators/assignment-operators.md).

L’opérateur d’assignation de concaténation (`&=`) est utile pour ajouter une chaîne à la fin des chaînes déjà existantes, comme l’illustre l’exemple suivant.

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>Conversions de type dans les instructions d’assignation

La valeur que vous attribuez à une variable, une propriété ou un élément de tableau doit être d’un type de données approprié à cet élément de destination. En général, vous devez essayer de générer une valeur du même type de données que celui de l’élément de destination. Toutefois, certains types peuvent être convertis en d’autres types pendant l’assignation.

Pour plus d’informations sur la conversion entre types de données, consultez [conversions de type dans Visual Basic](./data-types/type-conversions.md). En bref, Visual Basic convertit automatiquement une valeur d’un type donné en un autre type auquel il s’étend. Une *conversion étendue* est un dans qui fonctionne toujours au moment de l’exécution et ne perd aucune donnée. Par exemple, Visual Basic convertit une valeur `Integer` en `Double`, le cas échéant, car `Integer` s’étend à `Double`. Pour plus d’informations, consultez [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md).

Les *conversions restrictives* (celles qui ne s’étendent pas) présentent un risque d’échec au moment de l’exécution ou de perte de données. Vous pouvez effectuer une conversion restrictive de manière explicite à l’aide d’une fonction de conversion de type, ou vous pouvez demander au compilateur d’effectuer toutes les conversions implicitement en définissant `Option Strict Off`. Pour plus d’informations, consultez [conversions implicites et explicites](./data-types/implicit-and-explicit-conversions.md).

## <a name="putting-multiple-statements-on-one-line"></a>Ajout de plusieurs instructions sur une seule ligne

Vous pouvez avoir plusieurs instructions sur une seule ligne, séparées par le caractère deux-points (`:`). L’exemple suivant illustre ces actions.

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

Bien qu’il soit parfois pratique, cette forme de syntaxe rend votre code difficile à lire et à gérer. Par conséquent, il est recommandé de conserver une instruction sur une ligne.

## <a name="continuing-a-statement-over-multiple-lines"></a>Poursuite d’une instruction sur plusieurs lignes

Une instruction tient généralement sur une ligne, mais lorsqu’elle est trop longue, vous pouvez la continuer sur la ligne suivante à l’aide d’une séquence de continuation de ligne, qui se compose d’un espace suivi d’un trait de soulignement (`_`) suivi d’un retour chariot. Dans l’exemple suivant, l' `MsgBox` instruction exécutable se poursuit sur deux lignes.

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>Continuation de ligne implicite

Dans de nombreux cas, vous pouvez continuer une instruction sur la ligne consécutive suivante sans utiliser le caractère de soulignement (`_`). Les éléments syntaxiques suivants continuent implicitement l’instruction sur la ligne de code suivante.

- Après une virgule (`,`). Exemple :

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- Après une parenthèse ouvrante (`(`) ou avant une parenthèse fermante (`)`). Exemple :

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- Après une accolade ouvrante (`{`) ou avant une accolade fermante (`}`). Exemple :

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    Pour plus d’informations, consultez [initialiseurs d’objets : types nommés et anonymes](./objects-and-classes/object-initializers-named-and-anonymous-types.md) ou [initialiseurs de collection](./collection-initializers/index.md).

- Après une expression incorporée ouverte (`<%=`) ou avant la fermeture d’une expression incorporée (`%>`) dans un littéral XML. Exemple :

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   Pour plus d’informations, consultez [expressions incorporées en XML](./xml/embedded-expressions-in-xml.md).

- Après l’opérateur de concaténation (`&`). Exemple :

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   Pour plus d’informations, consultez [opérateurs listés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Après les opérateurs d’assignation (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`). Exemple :

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Pour plus d’informations, consultez [opérateurs listés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Après les opérateurs binaires (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) au sein d’une expression. Exemple :

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   Pour plus d’informations, consultez [opérateurs listés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Après les opérateurs `Is` et `IsNot`. Exemple :

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   Pour plus d’informations, consultez [opérateurs listés par fonctionnalité](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).

- Après un caractère de qualificateur de membre (`.`) et avant le nom de membre. Exemple :

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   Toutefois, vous devez inclure un caractère de continuation de ligne (`_`) après un caractère qualificateur de membre lorsque vous utilisez l’instruction `With` ou que vous fournissez des valeurs dans la liste d’initialisation pour un type. Envisagez de rompre la ligne après l’opérateur d’assignation (par exemple, `=`) quand vous utilisez des instructions `With` ou des listes d’initialisation d’objet. Exemple :

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   Pour plus d’informations, consultez [avec... Terminer avec l’instruction ou les](../../../visual-basic/language-reference/statements/with-end-with-statement.md) [initialiseurs d’objets : types nommés et anonymes](./objects-and-classes/object-initializers-named-and-anonymous-types.md).

- Après un qualificateur de propriété d’axe XML (`.` ou `.@` ou `...`). Toutefois, vous devez inclure un caractère de continuation de ligne (`_`) quand vous spécifiez un qualificateur de membre lorsque vous utilisez le mot clé `With`. Exemple :

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   Pour plus d’informations, consultez Propriétés de l' [axe XML](../../../visual-basic/language-reference/xml-axis/index.md).

- Après un signe inférieur à (<) ou avant un signe supérieur à (`>`) quand vous spécifiez un attribut. Également après un signe supérieur à (`>`) lorsque vous spécifiez un attribut. Toutefois, vous devez inclure un caractère de continuation de ligne (`_`) quand vous spécifiez des attributs au niveau de l’assembly ou du module. Exemple :

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   Pour plus d’informations, consultez [vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md).

- Avant et après les opérateurs de requête (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`et `Descending`). Vous ne pouvez pas scinder une ligne entre les mots clés des opérateurs de requête composés de plusieurs mots clés (`Order By`, `Group Join`, `Take While`et `Skip While`). Exemple :

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   Pour plus d’informations, consultez [requêtes](../../../visual-basic/language-reference/queries/index.md).

- Après le mot clé `In` dans une instruction `For Each`. Exemple :

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   Pour plus d’informations, consultez [for each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md).

- Après le mot clé `From` dans un initialiseur de collection. Exemple :

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   Pour plus d’informations, consultez [Initialiseurs de collection](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

## <a name="adding-comments"></a>Ajout de commentaires

Le code source n’est pas toujours explicite, même pour le programmeur qui l’a écrit. Par conséquent, pour aider à documenter leur code, la plupart des programmeurs utilisent des commentaires incorporés. Les commentaires dans le code peuvent expliquer une procédure ou une instruction particulière à quiconque peut les lire ou les utiliser ultérieurement. Visual Basic ignore les commentaires pendant la compilation et n’affecte pas le code compilé.

Les lignes de commentaire commencent par une apostrophe (`'`) ou `REM` suivies d’un espace. Elles peuvent être ajoutées n’importe où dans le code, sauf dans une chaîne. Pour ajouter un commentaire à une instruction, insérez une apostrophe ou `REM` après l’instruction, suivi du commentaire. Les commentaires peuvent également se trouver sur une ligne distincte. L’exemple suivant illustre ces possibilités.

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>Vérification des erreurs de compilation

Si, après avoir tapé une ligne de code, la ligne est affichée avec un trait de soulignement ondulé bleu (un message d’erreur peut également s’afficher), il y a une erreur de syntaxe dans l’instruction. Vous devez savoir ce qui est incorrect avec l’instruction (en regardant dans la liste des tâches, ou en plaçant le pointeur de la souris et en lisant le message d’erreur) et le corriger. Tant que vous n’avez pas résolu toutes les erreurs de syntaxe dans votre code, votre programme ne pourra pas se compiler correctement.

## <a name="related-sections"></a>Rubriques connexes

|Terme|Définition|
|---|---|
|[Opérateurs d’assignation](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fournit des liens vers des pages de référence du langage couvrant des opérateurs d’assignation tels que `=`, `*=`et `&=`.|
|[Opérateurs et expressions](./operators-and-expressions/index.md)|Montre comment combiner des éléments avec des opérateurs pour produire de nouvelles valeurs.|
|[Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Montre comment fractionner une instruction unique en plusieurs lignes et comment placer plusieurs instructions sur la même ligne.|
|[Guide pratique : étiqueter des instructions](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Montre comment étiqueter une ligne de code.|
