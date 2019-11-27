---
title: Function, instruction
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
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345922"
---
# <a name="function-statement-visual-basic"></a>Function, instruction (Visual Basic)

Déclare le nom, les paramètres et le code qui définissent une procédure `Function`.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>Composants

- `attributelist`

  Ce paramètre est facultatif. Consultez la [liste des attributs](attribute-list.md).

- `accessmodifier`

  Ce paramètre est facultatif. Il peut s'agir de l'un des éléments suivants :

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Ce paramètre est facultatif. Il peut s'agir de l'un des éléments suivants :

  - [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Ce paramètre est facultatif. Consultez [partagé](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  Ce paramètre est facultatif. Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Async`

  Ce paramètre est facultatif. Consultez [Async](../../../visual-basic/language-reference/modifiers/async.md).

- `Iterator`

  Ce paramètre est facultatif. Consultez [iterator](../../../visual-basic/language-reference/modifiers/iterator.md).

- `name`

  Requis. Nom de la procédure. Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).

- `typeparamlist`

  Ce paramètre est facultatif. Liste des paramètres de type pour une procédure générique. Consultez la [liste des types](type-list.md).

- `parameterlist`

  Ce paramètre est facultatif. Liste des noms de variables locales représentant les paramètres de cette procédure. Consultez la [liste des paramètres](parameter-list.md).

- `returntype`

  Obligatoire si `Option Strict` est `On`. Type de données de la valeur retournée par cette procédure.

- `Implements`

  Ce paramètre est facultatif. Indique que cette procédure implémente une ou plusieurs procédures `Function`, chacune d’elles étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure. Consultez [Implements, instruction](implements-statement.md).

- `implementslist`

  Obligatoire si `Implements` est utilisé. Liste des procédures `Function` en cours d'implémentation.

  `implementedprocedure [ , implementedprocedure ... ]`

  Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :

  `interface.definedname`

  |Élément|Description|
  |---|---|
  |`interface`|Requis. Nom d’une interface implémentée par la classe ou la structure conteneur de cette procédure.|
  |`definedname`|Requis. Nom par lequel la procédure est définie dans `interface`.|

- `Handles`

  Ce paramètre est facultatif. Indique que cette procédure peut gérer un ou plusieurs événements spécifiques. Consultez [Handles](handles-clause.md).

- `eventlist`

  Obligatoire si `Handles` est utilisé. Liste des événements gérés par cette procédure.

  `eventspecifier [ , eventspecifier ... ]`

  Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :

  `eventvariable.event`

  |Élément|Description|
  |---|---|
  |`eventvariable`|Requis. Variable objet déclarée avec le type de données de la classe ou de la structure qui déclenche l’événement.|
  |`event`|Requis. Nom de l’événement géré par cette procédure.|

- `statements`

  Ce paramètre est facultatif. Bloc d’instructions à exécuter dans cette procédure.

- `End Function`

  Met fin à la définition de cette procédure.

## <a name="remarks"></a>Notes

Tout le code exécutable doit être à l’intérieur d’une procédure. Chaque procédure, à son tour, est déclarée dans une classe, une structure ou un module qui est désigné comme la classe, la structure ou le module qui le contient.

Pour retourner une valeur au code appelant, utilisez une procédure `Function` ; dans le cas contraire, utilisez une procédure `Sub`.

## <a name="defining-a-function"></a>Définition d’une fonction

Vous pouvez définir une procédure `Function` uniquement au niveau du module. Par conséquent, le contexte de déclaration pour une fonction doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

`Function` les procédures par défaut sont accès public. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.

Une procédure `Function` peut déclarer le type de données de la valeur retournée par la procédure. Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, d’une structure, d’une classe ou d’une interface. Si vous ne spécifiez pas le paramètre `returntype`, la procédure retourne `Object`.

Si cette procédure utilise le mot clé `Implements`, la classe ou la structure conteneur doit également avoir une instruction `Implements` qui suit immédiatement son `Class` ou `Structure` instruction. L’instruction `Implements` doit inclure chaque interface spécifiée dans `implementslist`. Toutefois, le nom par lequel une interface définit le `Function` (dans `definedname`) ne doit pas nécessairement correspondre au nom de cette procédure (dans `name`).

> [!NOTE]
> Vous pouvez utiliser des expressions lambda pour définir des expressions de fonction Inline. Pour plus d’informations, consultez [expression de fonction](../../../visual-basic/language-reference/operators/function-expression.md) et [expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Retour à partir d’une fonction

Lorsque la procédure `Function` retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure.

Pour retourner une valeur à partir d’une fonction, vous pouvez affecter la valeur au nom de la fonction ou l’inclure dans une instruction `Return`.

L’instruction `Return` assigne simultanément la valeur de retour et quitte la fonction, comme le montre l’exemple suivant.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

L’exemple suivant affecte la valeur de retour au nom de la fonction `myFunction` puis utilise l’instruction `Exit Function` pour retourner.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

Les instructions `Exit Function` et `Return` provoquent une sortie immédiate d’une procédure `Function`. Un nombre quelconque d’instructions `Exit Function` et `Return` peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des instructions `Exit Function` et `Return`.

Si vous utilisez `Exit Function` sans assigner de valeur à `name`, la procédure retourne la valeur par défaut pour le type de données spécifié dans `returntype`. Si `returntype` n’est pas spécifié, la procédure retourne `Nothing`, qui est la valeur par défaut pour `Object`.

## <a name="calling-a-function"></a>Appel d’une fonction

Vous appelez une procédure `Function` en utilisant le nom de la procédure, suivi de la liste d’arguments entre parenthèses, dans une expression. Vous pouvez omettre les parenthèses uniquement si vous ne fournissez pas d’arguments. Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.

Vous appelez une procédure `Function` de la même façon que vous appelez une fonction de bibliothèque comme `Sqrt`, `Cos`ou `ChrW`.

Vous pouvez également appeler une fonction à l’aide du mot clé `Call`. Dans ce cas, la valeur de retour est ignorée. L’utilisation du mot clé `Call` n’est pas recommandée dans la plupart des cas. Pour plus d’informations, consultez [Call, instruction](call-statement.md).

Visual Basic réorganise parfois des expressions arithmétiques pour augmenter l’efficacité interne. Pour cette raison, vous ne devez pas utiliser une procédure `Function` dans une expression arithmétique lorsque la fonction modifie la valeur des variables dans la même expression.

## <a name="async-functions"></a>Fonctions Async

La fonctionnalité *Async* vous permet d’appeler des fonctions asynchrones sans utiliser de rappels explicites ou de fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.

Si vous marquez une fonction avec le modificateur [Async](../../../visual-basic/language-reference/modifiers/async.md) , vous pouvez utiliser l’opérateur [await](../../../visual-basic/language-reference/operators/await-operator.md) dans la fonction. Quand le contrôle atteint une expression `Await` dans la fonction `Async`, le contrôle retourne à l’appelant, et la progression dans la fonction est suspendue jusqu’à ce que la tâche attendue se termine. Une fois la tâche terminée, l’exécution peut reprendre dans la fonction.

> [!NOTE]
> Une procédure `Async` retourne à l’appelant lorsqu’il rencontre le premier objet attendu qui n’est pas encore terminé ou qu’il atteint la fin de la procédure `Async`, selon ce qui se produit en premier.

Une fonction `Async` peut avoir un type de retour <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>. Vous trouverez ci-dessous un exemple de `Async` fonction dont le type de retour est <xref:System.Threading.Tasks.Task%601>.

Une fonction `Async` ne peut pas déclarer de paramètres [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .

Une [sous-instruction](sub-statement.md) peut également être marquée avec le modificateur `Async`. Il est principalement utilisé pour les gestionnaires d’événements, où une valeur ne peut pas être retournée. Une procédure de `Sub` `Async` ne peut pas être attendue, et l’appelant d’une procédure de `Sub` de `Async` ne peut pas intercepter les exceptions levées par la procédure `Sub`.

Pour plus d’informations sur les fonctions de `Async`, consultez [programmation asynchrone avec Async et await](../../../visual-basic/programming-guide/concepts/async/index.md), [Workflow de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)et [types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Fonctions d’itérateur

Une fonction d' *itérateur* effectue une itération personnalisée sur une collection, telle qu’une liste ou un tableau. Une fonction d’itérateur utilise l’instruction [yield](yield-statement.md) pour retourner chaque élément un par un. Quand une instruction [yield](yield-statement.md) est atteinte, l’emplacement actuel dans le code est mémorisé. L’exécution est redémarrée à partir de cet emplacement lors de l’appel suivant de la fonction d’itérateur.

Vous appelez un itérateur à partir du code client à l’aide [d’un for each... Instruction suivante](for-each-next-statement.md) .

Le type de retour d’une fonction d’itérateur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>ou <xref:System.Collections.Generic.IEnumerator%601>.

Pour plus d’informations, consultez [Itérateurs](../../programming-guide/concepts/iterators.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise l’instruction `Function` pour déclarer le nom, les paramètres et le code qui forment le corps d’une procédure `Function`. Le modificateur `ParamArray` permet à la fonction d’accepter un nombre variable d’arguments.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>Exemple

L’exemple suivant appelle la fonction déclarée dans l’exemple précédent.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>Exemple

Dans l’exemple suivant, `DelayAsync` est un `Async` `Function` dont le type de retour est <xref:System.Threading.Tasks.Task%601>. `DelayAsync` a une instruction `Return` qui retourne un entier. Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour `Task(Of Integer)`. Étant donné que le type de retour est `Task(Of Integer)`, l’évaluation de l’expression de `Await` dans `DoSomethingAsync` produit un entier. Cela est illustré dans cette instruction : `Dim result As Integer = Await delayTask`.

La procédure `startButton_Click` est un exemple de `Async Sub` procédure. Étant donné que `DoSomethingAsync` est une fonction `Async`, la tâche pour l’appel à `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()`. La procédure `Sub` `startButton_Click` doit être définie avec le modificateur `Async`, car elle a une expression `Await`.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Sub (instruction)](sub-statement.md)
- [Procédures Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Liste de paramètres](parameter-list.md)
- [Dim (instruction)](dim-statement.md)
- [Call (instruction)](call-statement.md)
- [Of](of-clause.md)
- [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Guide pratique : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Expression de fonction](../../../visual-basic/language-reference/operators/function-expression.md)
