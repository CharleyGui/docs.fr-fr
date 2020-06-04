---
title: With...End With (instruction)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: 50f3bd0c6e96254274b429794901e2e4ac719ad0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401379"
---
# <a name="withend-with-statement-visual-basic"></a>With...End With, instruction (Visual Basic)

Exécute une série d'instructions qui font référence à plusieurs reprises à un objet ou une structure unique afin que ces instructions puissent utiliser une syntaxe simplifiée lors de l'accès aux membres de l'objet ou de la structure.  Lorsque vous utilisez une structure, vous ne pouvez lire que les valeurs des membres ou des méthodes invoke. En outre, vous obtenez une erreur si vous tentez d'assigner des valeurs aux membres d'une structure utilisée dans une instruction `With...End With`.

## <a name="syntax"></a>Syntaxe

```vb
With objectExpression
    [ statements ]
End With
```

## <a name="parts"></a>Éléments

|Terme|Définition|
|---|---|
|`objectExpression`|Obligatoire. Expression qui correspond à un objet. L'expression peut être arbitrairement complexe et n'est évaluée qu'une seule fois. L'expression peut correspondre à tout type de données, y compris des types élémentaires.|
|`statements`|Facultatif. Une ou plusieurs instructions entre `With` et `End With` qui peuvent faire référence aux membres d'un objet produit par l'évaluation de `objectExpression`.|
|`End With`|Obligatoire. Met fin à la définition du bloc `With`.|

## <a name="remarks"></a>Notes

À l'aide de `With...End With`, vous pouvez exécuter une série d'instructions sur un objet spécifique sans avoir à spécifier plusieurs fois le nom de cet objet. Dans un bloc d'instructions `With`, vous pouvez spécifier un membre de l'objet en commençant par un point, comme si l'instruction `With` le précédait.

Par exemple, pour modifier plusieurs propriétés d'un seul objet, placez les instructions d'assignation de propriétés dans le bloc `With...End With`. Vous ne faites ainsi référence qu'une seule fois à l'objet, au lieu de le faire à chaque assignation de propriété.

Si votre code accède au même objet dans plusieurs instructions, vous bénéficiez des avantages suivants via l'instruction `With` :

- Vous n'avez pas besoin d'évaluer une expression complexe plusieurs fois, ni d'assigner le résultat à une variable temporaire pour faire référence à ses membres à plusieurs reprises.

- Vous rendez votre code plus lisible en éliminant les expressions qualifiantes répétitives.

Le type de données de `objectExpression` peut être un type de classe ou de structure, ou même un type élémentaire Visual Basic, tel que `Integer`.  Si `objectExpression` est autre chose qu'un objet, vous ne pouvez lire que les valeurs de ses membres ou de ses méthodes invoke. En outre, vous obtenez une erreur si vous tentez d'assigner des valeurs aux membres d'une structure utilisée dans une instruction `With...End With`.  Il s'agit de la même erreur que celle que vous obtenez si vous appelez une méthode qui a retourné une structure et qui a immédiatement accédé à une valeur pour l'assigner à un membre du résultat de la fonction, par exemple `GetAPoint().x = 1`.  Dans les deux cas, le problème vient du fait que la structure existe uniquement dans la pile des appels. Par ailleurs, il n'existe aucun moyen dans ce cas pour qu'un membre de structure modifié puisse écrire dans un emplacement de manière à ce qu'une autre partie du code du programme puisse observer la modification.

`objectExpression` est évalué une seule fois, à l'entrée dans le bloc. Vous ne pouvez pas réassigner `objectExpression` à partir de l'intérieur du bloc `With`.

Dans un bloc `With`, vous pouvez accéder aux méthodes et propriétés de l'objet spécifié uniquement sans les qualifier. Vous pouvez utiliser les méthodes et propriétés des autres objets, mais vous devez les qualifier par leurs noms d'objets.

Vous pouvez placer une instruction `With...End With` dans une autre. Les instructions `With...End With` imbriquées peuvent prêter à confusion si les objets référencés ne sont pas clairs d'après le contexte. Vous devez fournir une référence qualifiée complète à un objet qui se trouve dans un bloc `With` externe lorsque l'objet est référencé à partir de l'intérieur d'un bloc `With`.

Vous ne pouvez pas créer de branche dans un bloc d’instructions `With` à partir de l’extérieur du bloc.

À moins que le bloc ne contienne une boucle, les instructions ne sont exécutées qu'une seule fois. Vous pouvez imbriquer différentes sortes de structures de contrôle. Pour plus d’informations, consultez [structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md).

> [!NOTE]
> Vous pouvez également utiliser le mot clé `With` dans les initialiseurs d'objets. Pour plus d’informations et d’exemples, consultez [initialiseurs d’objets : types nommés et anonymes](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) et [types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).
>
> Si vous utilisez un bloc `With` uniquement pour initialiser les propriétés ou les champs d'un objet que vous venez d'instancier, utilisez plutôt un initialiseur d'objet à la place.

## <a name="example"></a>Exemple

Dans l'exemple suivant, chaque bloc `With` exécute une série d'instructions sur un seul objet.

[!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]

## <a name="example"></a>Exemple

L'exemple suivant imbrique les instructions `With…End With`. Dans l'instruction `With` imbriquée, la syntaxe fait référence à l'objet interne.

[!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic.List%601>
- [Structures de contrôle imbriquées](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [Initialiseurs d'objets : types nommés et anonymes](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Types anonymes](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
