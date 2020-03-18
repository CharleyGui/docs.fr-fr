---
title: Syntaxe utilisée par la propriété DebugView (C#)
description: Décrit la syntaxe spéciale utilisée par la propriété DebugView pour produire une représentation de chaîne d’arborescences d’expression
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: ba695fc808108c49a4eee3c70a305b24c91769d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "67661717"
---
# <a name="debugview-syntax"></a>Syntaxe de `DebugView`

La propriété `DebugView` (disponible uniquement lors du débogage) fournit un rendu de la chaîne d’arborescences d’expression. La plupart de la syntaxe est assez simple à comprendre ; les cas spéciaux sont décrits dans les sections suivantes.

Chaque exemple est suivi d’un commentaire en bloc contenant le `DebugView`.

## <a name="parameterexpression"></a>ParameterExpression

Les noms de variables <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> s’affichent avec le symbole `$` au début.

Si un paramètre n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `$var1` ou `$var2`.

### <a name="examples"></a>Exemples

```csharp
ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");
/*
    $num
*/

ParameterExpression numParam =  Expression.Parameter(typeof(int));
/*
    $var1
*/
```

## <a name="constantexpression"></a>ConstantExpression

Pour les objets <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> qui représentent des valeurs entières, des chaînes et des valeurs `null`, la valeur de la constante est affichée.

Pour les types numériques comportant des suffixes standard comme littéraux C#, le suffixe est ajouté à la valeur. Le tableau suivant indique les suffixes associés aux différents types numériques.

| Type | Mot clé | Suffixe |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [uint](../../../language-reference/builtin-types/integral-numeric-types.md) | U |
| <xref:System.Int64?displayProperty=nameWithType> | [Long](../../../language-reference/builtin-types/integral-numeric-types.md) | L |
| <xref:System.UInt64?displayProperty=nameWithType> | [Ulong](../../../language-reference/builtin-types/integral-numeric-types.md) | UL |
| <xref:System.Double?displayProperty=nameWithType> | [Double](../../../language-reference/builtin-types/floating-point-numeric-types.md) | D |
| <xref:System.Single?displayProperty=nameWithType> | [Flotteur](../../../language-reference/builtin-types/floating-point-numeric-types.md) | F |
| <xref:System.Decimal?displayProperty=nameWithType> | [Decimales](../../../language-reference/builtin-types/floating-point-numeric-types.md) | M |

### <a name="examples"></a>Exemples

```csharp
int num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10
*/

double num = 10;
ConstantExpression expr = Expression.Constant(num);
/*
    10D
*/
```

## <a name="blockexpression"></a>BlockExpression

Si le type d’un objet <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> diffère du type de la dernière expression du bloc, le type est affiché entre crochets pointus (`<` et `>`). Sinon, le type de l’objet <xref:System.Linq.Expressions.BlockExpression> n’est pas affiché.

### <a name="examples"></a>Exemples

```csharp
BlockExpression block = Expression.Block(Expression.Constant("test"));
/*
    .Block() {
        "test"
    }
*/

BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));
/*
    .Block<System.Object>() {
        "test"
    }
*/
```

## <a name="lambdaexpression"></a>LambdaExpression

Les objets <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> sont affichés avec leurs types délégués.

Si une expression lambda n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Lambda1` ou `#Lambda2`.

### <a name="examples"></a>Exemples

```csharp
LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));
/*
    .Lambda #Lambda1<System.Func'1[System.Int32]>() {
        1
    }
*/

LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);
/*
    .Lambda #SampleLambda<System.Func'1[System.Int32]>() {
        1
    }
*/
```

## <a name="labelexpression"></a>LabelExpression

Si vous spécifiez une valeur par défaut pour l’objet <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, cette valeur est affichée avant l’objet <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.

Le jeton `.Label` indique le début de l’étiquette. Le jeton `.LabelTarget` indique la destination de la cible à laquelle accéder.

Si une étiquette n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Label1` ou `#Label2`.

### <a name="examples"></a>Exemples

```csharp
LabelTarget target = Expression.Label(typeof(int), "SampleLabel");
BlockExpression block = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1))
);
/*
    .Block() {
        .Goto SampleLabel { 0 };
        .Label
            -1
        .LabelTarget SampleLabel:
    }
*/

LabelTarget target = Expression.Label();
BlockExpression block = Expression.Block(
    Expression.Goto(target),
    Expression.Label(target)
);
/*
    .Block() {
        .Goto #Label1 { };
        .Label
        .LabelTarget #Label1:
    }
*/
```

## <a name="checked-operators"></a>Opérateurs Checked

Des opérateurs activés sont affichés avec le symbole `#` en regard de l’opérateur. Par exemple, l’opérateur d’addition checked est affiché sous la forme `#+`.

### <a name="examples"></a>Exemples

```csharp
Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));
/*
    1 #+ 2
*/

Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));
/*
    #(System.Int32)10D
*/
```
