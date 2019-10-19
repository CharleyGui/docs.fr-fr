---
title: Sub, instruction (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 7dc0ea1f1b30f5ffb0db8917538adf440c5ef891
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583199"
---
# <a name="sub-statement-visual-basic"></a>Sub, instruction (Visual Basic)

Déclare le nom, les paramètres et le code qui définissent une procédure `Sub`.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>Composants

- `attributelist`

  Optionnel. Consultez la [liste des attributs](attribute-list.md).

- `Partial`

  Optionnel. Indique la définition d’une méthode partielle. Consultez [méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).

- `accessmodifier`

  Optionnel. Il peut s'agir d'une des valeurs suivantes :

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

- `proceduremodifiers`

  Optionnel. Il peut s'agir d'une des valeurs suivantes :

  - [Surcharges](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  Optionnel. Consultez [partagé](../modifiers/shared.md).

- `Shadows`

  Optionnel. Consultez [Shadows](../modifiers/shadows.md).

- `Async`

  Optionnel. Consultez [Async](../modifiers/async.md).

- `name`

  Requis. Nom de la procédure. Consultez [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Pour créer une procédure constructeur pour une classe, définissez le nom d’une `Sub` procédure sur le mot clé `New`. Pour plus d’informations, consultez durée de vie d’un [objet : comment les objets sont créés et détruits](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

- `typeparamlist`

  Optionnel. Liste des paramètres de type pour une procédure générique. Consultez la [liste des types](type-list.md).

- `parameterlist`

  Optionnel. Liste des noms de variables locales représentant les paramètres de cette procédure. Consultez la [liste des paramètres](parameter-list.md).

- `Implements`

  Optionnel. Indique que cette procédure implémente une ou plusieurs procédures `Sub`, chacune d’elles étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure. Consultez [Implements, instruction](implements-statement.md).

- `implementslist`

  Obligatoire si `Implements` est utilisé. Liste des procédures `Sub` en cours d'implémentation.

  `implementedprocedure [ , implementedprocedure ... ]`

  Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :

  `interface.definedname`

  |Élément|Description|
  |---|---|
  |`interface`|Requis. Nom d’une interface implémentée par la classe ou la structure conteneur de cette procédure.|
  |`definedname`|Requis. Nom par lequel la procédure est définie dans `interface`.|

- `Handles`

  Optionnel. Indique que cette procédure peut gérer un ou plusieurs événements spécifiques. Consultez [Handles](handles-clause.md).

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

  Optionnel. Bloc d’instructions à exécuter dans cette procédure.

- `End Sub`

  Met fin à la définition de cette procédure.

## <a name="remarks"></a>Notes

Tout le code exécutable doit être à l’intérieur d’une procédure. Utilisez une procédure `Sub` lorsque vous ne souhaitez pas retourner une valeur au code appelant. Utilisez une procédure `Function` lorsque vous souhaitez retourner une valeur.

## <a name="defining-a-sub-procedure"></a>Définition d’une procédure Sub

Vous pouvez définir une procédure `Sub` uniquement au niveau du module. Le contexte de déclaration d’une procédure Sub doit, par conséquent, être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).

`Sub` les procédures par défaut sont accès public. Vous pouvez ajuster leurs niveaux d’accès à l’aide des modificateurs d’accès.

Si la procédure utilise le mot clé `Implements`, la classe ou la structure conteneur doit avoir une instruction `Implements` qui suit immédiatement son `Class` ou `Structure` instruction. L’instruction `Implements` doit inclure chaque interface spécifiée dans `implementslist`. Toutefois, le nom par lequel une interface définit le `Sub` (dans `definedname`) ne doit pas nécessairement correspondre au nom de cette procédure (dans `name`).

## <a name="returning-from-a-sub-procedure"></a>Retour d’une procédure Sub

Quand une procédure `Sub` retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui l’a appelée.

L’exemple suivant montre un retour d’une procédure `Sub`.

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

Les instructions `Exit Sub` et `Return` provoquent une sortie immédiate d’une procédure `Sub`. Un nombre quelconque d’instructions `Exit Sub` et `Return` peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger des instructions `Exit Sub` et `Return`.

## <a name="calling-a-sub-procedure"></a>Appel d’une procédure Sub

Vous appelez une procédure `Sub` en utilisant le nom de la procédure dans une instruction, puis en suivant ce nom avec sa liste d’arguments entre parenthèses. Vous pouvez omettre les parenthèses uniquement si vous ne fournissez pas d’arguments. Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.

Une procédure `Sub` et une procédure `Function` peuvent avoir des paramètres et exécuter une série d’instructions. Toutefois, une procédure `Function` retourne une valeur, contrairement à une procédure `Sub`. Par conséquent, vous ne pouvez pas utiliser une procédure `Sub` dans une expression.

Vous pouvez utiliser le mot clé `Call` lorsque vous appelez une procédure `Sub`, mais ce mot clé n’est pas recommandé pour la plupart des utilisations. Pour plus d’informations, consultez [Call, instruction](call-statement.md).

Visual Basic réorganise parfois des expressions arithmétiques pour augmenter l’efficacité interne. Pour cette raison, si votre liste d’arguments comprend des expressions qui appellent d’autres procédures, vous ne devez pas supposer que ces expressions seront appelées dans un ordre particulier.

## <a name="async-sub-procedures"></a>Procédures Sub Async

À l’aide de la fonctionnalité Async, vous pouvez appeler des fonctions asynchrones sans utiliser de rappels explicites ni fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.

Si vous marquez une procédure avec le modificateur [Async](../modifiers/async.md) , vous pouvez utiliser l’opérateur [await](../../../visual-basic/language-reference/operators/await-operator.md) dans la procédure. Quand le contrôle atteint une expression `Await` dans la procédure `Async`, le contrôle retourne à l’appelant, et la progression de la procédure est suspendue jusqu’à ce que la tâche attendue se termine. Une fois la tâche terminée, l’exécution peut reprendre dans la procédure.

> [!NOTE]
> Une procédure `Async` retourne à l’appelant lorsque le premier objet attendu qui n’est pas encore terminé est rencontré ou que la fin de la procédure `Async` est atteinte, selon la première valeur qui se produit.

Vous pouvez également marquer une [instruction de fonction](function-statement.md) avec le modificateur `Async`. Une fonction `Async` peut avoir un type de retour <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>. Un exemple plus loin dans cette rubrique illustre une fonction `Async` dont le type de retour est <xref:System.Threading.Tasks.Task%601>.

`Async` procédures `Sub` sont principalement utilisées pour les gestionnaires d’événements, où une valeur ne peut pas être retournée. Une procédure de `Sub` `Async` ne peut pas être attendue, et l’appelant d’une procédure de `Sub` de `Async` ne peut pas intercepter les exceptions levées par la procédure `Sub`.

Une procédure `Async` ne peut pas déclarer de paramètres [ByRef](../modifiers/byref.md) .

Pour plus d’informations sur les procédures de `Async`, consultez [programmation asynchrone avec Async et await](../../../visual-basic/programming-guide/concepts/async/index.md), [Workflow de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)et [types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>Exemple

L’exemple suivant utilise l’instruction `Sub` pour définir le nom, les paramètres et le code qui forment le corps d’une procédure `Sub`.

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>Exemple

Dans l’exemple suivant, `DelayAsync` est un `Async` `Function` dont le type de retour est <xref:System.Threading.Tasks.Task%601>. `DelayAsync` a une instruction `Return` qui retourne un entier. Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour `Task(Of Integer)`. Étant donné que le type de retour est `Task(Of Integer)`, l’évaluation de l’expression de `Await` dans `DoSomethingAsync` produit un entier, comme le montre l’instruction suivante : `Dim result As Integer = Await delayTask`.

La procédure `startButton_Click` est un exemple de `Async Sub` procédure. Étant donné que `DoSomethingAsync` est une fonction `Async`, la tâche pour l’appel à `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()`. La procédure `Sub` `startButton_Click` doit être définie avec le modificateur `Async`, car elle a une expression `Await`.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Implements (instruction)](implements-statement.md)
- [Function (instruction)](function-statement.md)
- [Liste de paramètres](parameter-list.md)
- [Dim (instruction)](dim-statement.md)
- [Call (instruction)](call-statement.md)
- [Of](of-clause.md)
- [tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Guide pratique : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
