---
title: Function (instruction)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404626"
---
# <a name="function-statement-visual-basic"></a>Function, instruction (Visual Basic)

Déclare le nom, les paramètres et le code qui définissent une `Function` procédure.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>Éléments

- `attributelist`

  Facultatif. Consultez la [liste des attributs](attribute-list.md).

- `accessmodifier`

  Facultatif. Il peut s'agir d'une des méthodes suivantes :

  - [Public](../modifiers/public.md)

  - [Protect](../modifiers/protected.md)

  - [Contact](../modifiers/friend.md)

  - [Privé](../modifiers/private.md)

  - [Protected Friend](../modifiers/protected-friend.md)

  - [Protégé privé](../modifiers/private-protected.md)

  Consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Facultatif. Il peut s'agir d'une des méthodes suivantes :

  - [Surcharges](../modifiers/overloads.md)

  - [Remplacements](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Facultatif. Consultez [partagé](../modifiers/shared.md).

- `Shadows`

  Facultatif. Consultez [Shadows](../modifiers/shadows.md).

- `Async`

  Facultatif. Consultez [Async](../modifiers/async.md).

- `Iterator`

  Facultatif. Consultez [iterator](../modifiers/iterator.md).

- `name`

  Obligatoire. Nom de la procédure. Consultez [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).

- `typeparamlist`

  Facultatif. Liste des paramètres de type pour une procédure générique. Consultez la [liste des types](type-list.md).

- `parameterlist`

  Facultatif. Liste des noms de variables locales représentant les paramètres de cette procédure. Consultez la [liste des paramètres](parameter-list.md).

- `returntype`

  Obligatoire si `Option Strict` est `On` . Type de données de la valeur retournée par cette procédure.

- `Implements`

  Facultatif. Indique que cette procédure implémente une ou plusieurs `Function` procédures, chacune d’elles étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure. Consultez [Implements, instruction](implements-statement.md).

- `implementslist`

  Obligatoire si `Implements` est utilisé. Liste des procédures `Function` en cours d'implémentation.

  `implementedprocedure [ , implementedprocedure ... ]`

  Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :

  `interface.definedname`

  |Élément|Description|
  |---|---|
  |`interface`|Obligatoire. Nom d’une interface implémentée par la classe ou la structure conteneur de cette procédure.|
  |`definedname`|Obligatoire. Nom par lequel la procédure est définie dans `interface`.|

- `Handles`

  Facultatif. Indique que cette procédure peut gérer un ou plusieurs événements spécifiques. Consultez [Handles](handles-clause.md).

- `eventlist`

  Obligatoire si `Handles` est utilisé. Liste des événements gérés par cette procédure.

  `eventspecifier [ , eventspecifier ... ]`

  Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :

  `eventvariable.event`

  |Élément|Description|
  |---|---|
  |`eventvariable`|Obligatoire. Variable objet déclarée avec le type de données de la classe ou de la structure qui déclenche l’événement.|
  |`event`|Obligatoire. Nom de l’événement géré par cette procédure.|

- `statements`

  Facultatif. Bloc d’instructions à exécuter dans cette procédure.

- `End Function`

  Met fin à la définition de cette procédure.

## <a name="remarks"></a>Notes

Tout le code exécutable doit être à l’intérieur d’une procédure. Chaque procédure, à son tour, est déclarée dans une classe, une structure ou un module qui est désigné comme la classe, la structure ou le module qui le contient.

Pour retourner une valeur au code appelant, utilisez une `Function` procédure ; sinon, utilisez une `Sub` procédure.

## <a name="defining-a-function"></a>Définition d’une fonction

Vous pouvez définir une `Function` procédure uniquement au niveau du module. Par conséquent, le contexte de déclaration pour une fonction doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

`Function`les procédures ont par défaut accès public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.

Une `Function` procédure peut déclarer le type de données de la valeur retournée par la procédure. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface. Si vous ne spécifiez pas le `returntype` paramètre, la procédure retourne `Object` .

Si cette procédure utilise le `Implements` mot clé, la classe ou la structure conteneur doit également avoir une `Implements` instruction qui suit immédiatement son `Class` `Structure` instruction ou. L' `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist` . Toutefois, le nom par lequel une interface définit `Function` (dans `definedname` ) ne doit pas nécessairement correspondre au nom de cette procédure (dans `name` ).

> [!NOTE]
> Vous pouvez utiliser des expressions lambda pour définir des expressions de fonction Inline. Pour plus d’informations, consultez [expression de fonction](../operators/function-expression.md) et [expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Retour à partir d’une fonction

Lorsque la `Function` procédure revient au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure.

Pour retourner une valeur à partir d’une fonction, vous pouvez affecter la valeur au nom de la fonction ou l’inclure dans une `Return` instruction.

L' `Return` instruction assigne simultanément la valeur de retour et quitte la fonction, comme le montre l’exemple suivant.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

L’exemple suivant affecte la valeur de retour au nom de la fonction `myFunction` , puis utilise l' `Exit Function` instruction pour retourner.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

Les `Exit Function` `Return` instructions et provoquent une sortie immédiate d’une `Function` procédure. Un nombre quelconque `Exit Function` d' `Return` instructions et peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des `Exit Function` `Return` instructions et.

Si vous utilisez `Exit Function` sans assigner de valeur à `name` , la procédure retourne la valeur par défaut pour le type de données spécifié dans `returntype` . Si `returntype` n’est pas spécifié, la procédure retourne `Nothing` , qui est la valeur par défaut pour `Object` .

## <a name="calling-a-function"></a>Appel d’une fonction

Vous appelez une `Function` procédure en utilisant le nom de la procédure, suivi de la liste d’arguments entre parenthèses, dans une expression. Vous pouvez omettre les parenthèses uniquement si vous ne fournissez pas d’arguments. Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.

Vous appelez une `Function` procédure de la même façon que vous appelez une fonction de bibliothèque telle que `Sqrt` , `Cos` ou `ChrW` .

Vous pouvez également appeler une fonction à l’aide du `Call` mot clé. Dans ce cas, la valeur de retour est ignorée. L’utilisation du `Call` mot clé n’est pas recommandée dans la plupart des cas. Pour plus d’informations, consultez [Call, instruction](call-statement.md).

Visual Basic réorganise parfois des expressions arithmétiques pour augmenter l’efficacité interne. Pour cette raison, vous ne devez pas utiliser une `Function` procédure dans une expression arithmétique lorsque la fonction modifie la valeur des variables dans la même expression.

## <a name="async-functions"></a>Fonctions Async

La fonctionnalité *Async* vous permet d’appeler des fonctions asynchrones sans utiliser de rappels explicites ou de fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.

Si vous marquez une fonction avec le modificateur [Async](../modifiers/async.md) , vous pouvez utiliser l’opérateur [await](../operators/await-operator.md) dans la fonction. Quand le contrôle atteint une `Await` expression dans la `Async` fonction, le contrôle retourne à l’appelant, et la progression dans la fonction est suspendue jusqu’à ce que la tâche attendue se termine. Une fois la tâche terminée, l’exécution peut reprendre dans la fonction.

> [!NOTE]
> Une `Async` procédure est renvoyée à l’appelant lorsqu’elle rencontre le premier objet attendu qui n’est pas encore terminé ou qu’elle atteint la fin de la `Async` procédure, selon ce qui se produit en premier.

Une `Async` fonction peut avoir un type de retour <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task> . Vous trouverez `Async` ci-dessous un exemple de fonction qui a un type de retour <xref:System.Threading.Tasks.Task%601> .

Une `Async` fonction ne peut pas déclarer de paramètres [ByRef](../modifiers/byref.md) .

Une [sous-instruction](sub-statement.md) peut également être marquée avec le `Async` modificateur. Il est principalement utilisé pour les gestionnaires d’événements, où une valeur ne peut pas être retournée. Une `Async` `Sub` procédure ne peut pas être attendue, et l’appelant d’une `Async` `Sub` procédure ne peut pas intercepter les exceptions levées par la `Sub` procédure.

Pour plus d’informations sur les `Async` fonctions, consultez [programmation asynchrone avec Async et await](../../programming-guide/concepts/async/index.md), [Workflow de contrôle dans les programmes Async](../../programming-guide/concepts/async/control-flow-in-async-programs.md)et [types de retour Async](../../programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Fonctions d’itérateur

Une fonction d' *itérateur* effectue une itération personnalisée sur une collection, telle qu’une liste ou un tableau. Une fonction d’itérateur utilise l’instruction [yield](yield-statement.md) pour retourner chaque élément un par un. Quand une instruction [yield](yield-statement.md) est atteinte, l’emplacement actuel dans le code est mémorisé. L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.

Vous appelez un itérateur à partir du code client à l’aide [d’un for each... Instruction suivante](for-each-next-statement.md) .

Le type de retour d’une fonction d’itérateur peut être <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> .

Pour plus d’informations, consultez [itérateurs](../../programming-guide/concepts/iterators.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise l' `Function` instruction pour déclarer le nom, les paramètres et le code qui forment le corps d’une `Function` procédure. Le `ParamArray` modificateur permet à la fonction d’accepter un nombre variable d’arguments.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>Exemple

L’exemple suivant appelle la fonction déclarée dans l’exemple précédent.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>Exemple

Dans l’exemple suivant, `DelayAsync` est un `Async` `Function` qui a un type de retour <xref:System.Threading.Tasks.Task%601> . `DelayAsync` a une instruction `Return` qui retourne un entier. Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour `Task(Of Integer)` . Étant donné que le type de retour est `Task(Of Integer)` , l’évaluation de l' `Await` expression dans `DoSomethingAsync` produit un entier. Cela est illustré dans cette instruction : `Dim result As Integer = Await delayTask` .

La `startButton_Click` procédure est un exemple de `Async Sub` procédure. Étant donné que `DoSomethingAsync` est une `Async` fonction, la tâche pour l’appel à `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()` . La `startButton_Click` `Sub` procédure doit être définie avec le `Async` modificateur, car elle a une `Await` expression.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Sub (instruction)](sub-statement.md)
- [Function, procédures](../../programming-guide/language-features/procedures/function-procedures.md)
- [Liste de paramètres](parameter-list.md)
- [Dim (instruction)](dim-statement.md)
- [Call (instruction)](call-statement.md)
- [Of](of-clause.md)
- [Tableaux de paramètres](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [Procédure : Utiliser une classe générique](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procédures de dépannage](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Expressions lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Expression de fonction](../operators/function-expression.md)
