---
title: procédures Sub
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 9ca1d302a0bc8e989e0b2dddf8cce68e89211d57
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163811"
---
# <a name="sub-procedures-visual-basic"></a>Procédures Sub (Visual Basic)

Une procédure `Sub` est une série d’instructions Visual Basic délimitée par les instructions `Sub` et `End Sub`. La procédure `Sub` effectue une tâche, puis retourne le contrôle au code appelant, mais elle ne retourne pas de valeur au code appelant.

Chaque fois que la procédure est appelée, ses instructions sont exécutées, en commençant par la première instruction exécutable après l’instruction `Sub` et en se terminant par la première instruction `End Sub`, `Exit Sub`ou `Return` rencontrée.

Vous pouvez définir une procédure `Sub` dans des modules, des classes et des structures. Par défaut, il s’agit de `Public`, ce qui signifie que vous pouvez l’appeler à partir de n’importe quel endroit de votre application ayant accès au module, à la classe ou à la structure dans laquelle vous l’avez défini. La *méthode* term décrit une `Sub` ou `Function` procédure accessible à partir de l’extérieur de son module, de sa classe ou de sa structure de définition. Pour plus d’informations, consultez [Procédures](./index.md).

Une procédure `Sub` peut prendre des arguments, tels que des constantes, des variables ou des expressions, qui lui sont passés par le code appelant.

## <a name="declaration-syntax"></a>Syntaxe de déclaration

La syntaxe de la déclaration d’une procédure `Sub` se présente comme suit :

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

La `modifiers` peut spécifier le niveau d’accès et des informations sur la surcharge, le remplacement, le partage et l’occultation. Pour plus d’informations, consultez [Sub, instruction](../../../language-reference/statements/sub-statement.md).

## <a name="parameter-declaration"></a>Déclaration de paramètre

Vous pouvez déclarer chaque paramètre de procédure de la même façon que vous déclarez une variable, en spécifiant le nom du paramètre et le type de données. Vous pouvez également spécifier le mécanisme de passage, et si le paramètre est facultatif ou un tableau de paramètres.

La syntaxe de chaque paramètre dans la liste de paramètres est la suivante :

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration. La syntaxe permettant de spécifier une valeur par défaut est la suivante :

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a>Paramètres en tant que variables locales

Lorsque le contrôle passe à la procédure, chaque paramètre est traité comme une variable locale. Cela signifie que sa durée de vie est la même que celle de la procédure, et que son étendue est l’ensemble de la procédure.

## <a name="calling-syntax"></a>Syntaxe d’appel

Vous appelez explicitement une procédure `Sub` à l’aide d’une instruction d’appel autonome. Vous ne pouvez pas l’appeler en utilisant son nom dans une expression. Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses. Si aucun argument n’est fourni, vous pouvez éventuellement omettre les parenthèses. L’utilisation du mot clé `Call` est facultative, mais n’est pas recommandée.

La syntaxe d’un appel à une procédure `Sub` se présente comme suit :

```vb
[Call] SubName[(argumentlist)]
```

Vous pouvez appeler une méthode `Sub` à partir de l’extérieur de la classe qui la définit. Tout d’abord, vous devez utiliser le mot clé `New` pour créer une instance de la classe ou appeler une méthode qui retourne une instance de la classe. Pour plus d’informations, consultez [New, opérateur](../../../language-reference/operators/new-operator.md). Ensuite, vous pouvez utiliser la syntaxe suivante pour appeler la méthode `Sub` sur l’objet d’instance :

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a>Illustration de la déclaration et de l’appel

La procédure `Sub` suivante indique à l’opérateur d’ordinateur quelle tâche l’application est sur le point d’effectuer, et affiche également un horodatage. Au lieu de dupliquer ce code au début de chaque tâche, l’application appelle simplement `tellOperator` à partir de différents emplacements. Chaque appel passe une chaîne dans l’argument `task` qui identifie la tâche en cours de démarrage.

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

L’exemple suivant montre un appel typique à `tellOperator`.

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Function](./function-procedures.md)
- [Procédures de propriété](./property-procedures.md)
- [Procédures d’opérateur](./operator-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Sub (instruction)](../../../language-reference/statements/sub-statement.md)
- [Guide pratique : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [Comment : appeler un gestionnaire d’événements dans Visual Basic](./how-to-call-an-event-handler.md)
