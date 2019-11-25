---
title: Syntax used by DebugView property
description: Décrit la syntaxe spéciale utilisée par la propriété DebugView pour produire une représentation de chaîne d’arborescences d’expression
author: zspitz
ms.author: wiwagn
ms.date: 05/22/2019
ms.topic: reference
helpviewer_keywords:
- expression trees
- debugview
ms.openlocfilehash: 98ceba37aa226fab68ae1c1028e2a1139b3b8e7e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346866"
---
# <a name="debugview-syntax"></a><span data-ttu-id="62cbc-103">Syntaxe `DebugView`</span><span class="sxs-lookup"><span data-stu-id="62cbc-103">`DebugView` syntax</span></span>

<span data-ttu-id="62cbc-104">La propriété `DebugView` (disponible uniquement lors du débogage) fournit un rendu de la chaîne d’arborescences d’expression.</span><span class="sxs-lookup"><span data-stu-id="62cbc-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="62cbc-105">La plupart de la syntaxe est assez simple à comprendre ; les cas spéciaux sont décrits dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="62cbc-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="62cbc-106">Each example is followed by a comment block containing the `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="62cbc-106">Each example is followed by a comment block containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="62cbc-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="62cbc-107">ParameterExpression</span></span>

<span data-ttu-id="62cbc-108">Les noms de variables <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> s’affichent avec le symbole "$" en préfixe.</span><span class="sxs-lookup"><span data-stu-id="62cbc-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="62cbc-109">Si un paramètre n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="62cbc-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="62cbc-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="62cbc-110">Examples</span></span>

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

## <a name="constantexpressions"></a><span data-ttu-id="62cbc-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="62cbc-111">ConstantExpressions</span></span>

<span data-ttu-id="62cbc-112">Pour les objets <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> qui représentent des valeurs entières, des chaînes et des valeurs `null`, la valeur de la constante est affichée.</span><span class="sxs-lookup"><span data-stu-id="62cbc-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="62cbc-113">For some numeric types, a suffix is added to the value:</span><span class="sxs-lookup"><span data-stu-id="62cbc-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="62cbc-114">Tapez</span><span class="sxs-lookup"><span data-stu-id="62cbc-114">Type</span></span> | <span data-ttu-id="62cbc-115">Mot clé</span><span class="sxs-lookup"><span data-stu-id="62cbc-115">Keyword</span></span> | <span data-ttu-id="62cbc-116">Suffixe</span><span class="sxs-lookup"><span data-stu-id="62cbc-116">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32> | [<span data-ttu-id="62cbc-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="62cbc-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="62cbc-118">U</span><span class="sxs-lookup"><span data-stu-id="62cbc-118">U</span></span> |
| <xref:System.Int64> | [<span data-ttu-id="62cbc-119">Long</span><span class="sxs-lookup"><span data-stu-id="62cbc-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="62cbc-120">L</span><span class="sxs-lookup"><span data-stu-id="62cbc-120">L</span></span> |
| <xref:System.UInt64> | [<span data-ttu-id="62cbc-121">ULong</span><span class="sxs-lookup"><span data-stu-id="62cbc-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="62cbc-122">UL</span><span class="sxs-lookup"><span data-stu-id="62cbc-122">UL</span></span> |
| <xref:System.Double> | [<span data-ttu-id="62cbc-123">Double</span><span class="sxs-lookup"><span data-stu-id="62cbc-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="62cbc-124">D</span><span class="sxs-lookup"><span data-stu-id="62cbc-124">D</span></span> |
| <xref:System.Single> | [<span data-ttu-id="62cbc-125">Single</span><span class="sxs-lookup"><span data-stu-id="62cbc-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="62cbc-126">F</span><span class="sxs-lookup"><span data-stu-id="62cbc-126">F</span></span> |
| <xref:System.Decimal> | [<span data-ttu-id="62cbc-127">Decimal</span><span class="sxs-lookup"><span data-stu-id="62cbc-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="62cbc-128">M</span><span class="sxs-lookup"><span data-stu-id="62cbc-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="62cbc-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="62cbc-129">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="62cbc-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="62cbc-130">BlockExpression</span></span>

<span data-ttu-id="62cbc-131">Si le type d’un objet <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> diffère du type de la dernière expression du bloc, le type est affiché entre crochets pointus (`<` et `>`).</span><span class="sxs-lookup"><span data-stu-id="62cbc-131">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="62cbc-132">Sinon, le type de l’objet <xref:System.Linq.Expressions.BlockExpression> n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="62cbc-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="62cbc-133">Exemples</span><span class="sxs-lookup"><span data-stu-id="62cbc-133">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="62cbc-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="62cbc-134">LambdaExpression</span></span>

<span data-ttu-id="62cbc-135">Les objets <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> sont affichés avec leurs types délégués.</span><span class="sxs-lookup"><span data-stu-id="62cbc-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="62cbc-136">Si une expression lambda n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="62cbc-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="62cbc-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="62cbc-137">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="62cbc-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="62cbc-138">LabelExpression</span></span>

<span data-ttu-id="62cbc-139">Si vous spécifiez une valeur par défaut pour l’objet <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, cette valeur est affichée avant l’objet <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="62cbc-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="62cbc-140">Le jeton `.Label` indique le début de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="62cbc-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="62cbc-141">Le jeton `.LabelTarget` indique la destination de la cible à laquelle accéder.</span><span class="sxs-lookup"><span data-stu-id="62cbc-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="62cbc-142">Si une étiquette n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="62cbc-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="62cbc-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="62cbc-143">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="62cbc-144">Opérateurs Checked</span><span class="sxs-lookup"><span data-stu-id="62cbc-144">Checked Operators</span></span>

<span data-ttu-id="62cbc-145">Des opérateurs activés sont affichés avec le symbole `#` en regard de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="62cbc-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="62cbc-146">Par exemple, l’opérateur d’addition checked est affiché sous la forme `#+`.</span><span class="sxs-lookup"><span data-stu-id="62cbc-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="62cbc-147">Exemples</span><span class="sxs-lookup"><span data-stu-id="62cbc-147">Examples</span></span>

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
