---
title: Syntaxe utilisée par la propriété DebugView (Visual Basic)
description: Décrit la syntaxe spéciale utilisée par la propriété DebugView pour produire une représentation de chaîne d’arborescences d’expression
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ae2c75607f7b9cdc40fc5c163ce533f0472ab454
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689538"
---
# <a name="debugview-syntax"></a>Syntaxe `DebugView`

La propriété `DebugView` (disponible uniquement lors du débogage) fournit un rendu de la chaîne d’arborescences d’expression. La plupart de la syntaxe est assez simple à comprendre ; les cas spéciaux sont décrits dans les sections suivantes.

Chaque exemple est suivi d’un bloc de commentaire contenant le `DebugView`.

## <a name="parameterexpression"></a>ParameterExpression

Les noms de variables <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> s’affichent avec le symbole "$" en préfixe.

Si un paramètre n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `$var1` ou `$var2`.

### <a name="examples"></a>Exemples

```vb
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")
'
'    $num
'

Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer))
'
'    $var1
'
```

## <a name="constantexpressions"></a>ConstantExpressions

Pour les objets <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> qui représentent des valeurs entières, des chaînes et des valeurs `null`, la valeur de la constante est affichée.

Pour certains types numériques, un suffixe est ajouté à la valeur :

| Type | Mot clé | Suffix |
|--|--|--|
| <xref:System.UInt32> | [UInteger](../../../language-reference/data-types/uinteger-data-type.md) | U |
| <xref:System.Int64> | [Long](../../../language-reference/data-types/long-data-type.md) | L |
| <xref:System.UInt64> | [ULong](../../../language-reference/data-types/ulong-data-type.md) | UL |
| <xref:System.Double> | [Double](../../../language-reference/data-types/double-data-type.md) | D |
| <xref:System.Single> | [Single](../../../language-reference/data-types/single-data-type.md) | F |
| <xref:System.Decimal> | [Decimal](../../../language-reference/data-types/decimal-data-type.md) | M |

### <a name="examples"></a>Exemples

```vb
Dim num as Integer = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10
'

Dim num As Double = 10
Dim expr As ConstantExpression = Expression.Constant(num)
'
'    10D
'
```

## <a name="blockexpression"></a>BlockExpression

Si le type d’un objet <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> diffère du type de la dernière expression du bloc, le type est affiché entre crochets pointus (`<` et `>`). Sinon, le type de l’objet <xref:System.Linq.Expressions.BlockExpression> n’est pas affiché.

### <a name="examples"></a>Exemples

```vb
Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
'
'    .Block() {
'        "test"
'    }
'

Dim block As BlockExpression = Expression.Block(
    GetType(Object),
    Expression.Constant("test")
)
'
'    .Block<System.Object>() {
'        "test"
'    }
'
```

## <a name="lambdaexpression"></a>LambdaExpression

Les objets <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> sont affichés avec leurs types délégués.

Si une expression lambda n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Lambda1` ou `#Lambda2`.

### <a name="examples"></a>Exemples

```vb
Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1)
)
'
'    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
'        1
'    }
'

Dim lambda As LambdaExpression = Expression.Lambda(Of Func(Of Integer))(
    Expression.Constant(1),
    "SampleLambda",
    Nothing
)
'
'    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
'        1
'    }
'
```

## <a name="labelexpression"></a>LabelExpression

Si vous spécifiez une valeur par défaut pour l’objet <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, cette valeur est affichée avant l’objet <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.

Le jeton `.Label` indique le début de l’étiquette. Le jeton `.LabelTarget` indique la destination de la cible à laquelle accéder.

Si une étiquette n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Label1` ou `#Label2`.

### <a name="examples"></a>Exemples

```vb
Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
)
'
'    .Block() {
'        .Goto SampleLabel { 0 };
'        .Label
'            -1
'        .LabelTarget SampleLabel:
'    }
'

Dim target As LabelTarget = Expression.Label()
Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
)
'
'    .Block() {
'        .Goto #Label1 { };
'        .Label
'        .LabelTarget #Label1:
'    }
'
```

## <a name="checked-operators"></a>Opérateurs Checked

Des opérateurs activés sont affichés avec le symbole `#` en regard de l’opérateur. Par exemple, l’opérateur d’addition checked est affiché sous la forme `#+`.

### <a name="examples"></a>Exemples

```vb
Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1),
    Expression.Constant(2)
)
'
'     1 #+ 2
'

Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0),
    GetType(Integer)
)
'
'    #(System.Int32)10D
'
```
