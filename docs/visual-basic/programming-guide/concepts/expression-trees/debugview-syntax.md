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
ms.openlocfilehash: 1b2a1164f02208cc7578820d8f8ed3bc145fb5b8
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196529"
---
# <a name="debugview-syntax"></a><span data-ttu-id="1584f-103">Syntaxe `DebugView`</span><span class="sxs-lookup"><span data-stu-id="1584f-103">`DebugView` syntax</span></span> 

<span data-ttu-id="1584f-104">Le `DebugView` (disponible uniquement lors du débogage) de la propriété fournit un rendu de la chaîne d’arborescences d’expression.</span><span class="sxs-lookup"><span data-stu-id="1584f-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="1584f-105">La plupart de la syntaxe est assez simple à comprendre ; les cas spéciaux sont décrits dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="1584f-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="1584f-106">Chaque exemple est suivi d’un bloc de commentaire contenant le `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="1584f-106">Each example is followed by a comment block containing the `DebugView`.</span></span> 

## <a name="parameterexpression"></a><span data-ttu-id="1584f-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="1584f-107">ParameterExpression</span></span>

<span data-ttu-id="1584f-108">Les noms de variables <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> s’affichent avec le symbole "$" en préfixe.</span><span class="sxs-lookup"><span data-stu-id="1584f-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="1584f-109">Si un paramètre n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="1584f-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="1584f-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="1584f-110">Examples</span></span>

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

## <a name="constantexpressions"></a><span data-ttu-id="1584f-111">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="1584f-111">ConstantExpressions</span></span>

<span data-ttu-id="1584f-112">Pour les objets <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> qui représentent des valeurs entières, des chaînes et des valeurs `null`, la valeur de la constante est affichée.</span><span class="sxs-lookup"><span data-stu-id="1584f-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="1584f-113">Pour certains types numériques, un suffixe est ajouté à la valeur :</span><span class="sxs-lookup"><span data-stu-id="1584f-113">For some numeric types, a suffix is added to the value:</span></span>

| <span data-ttu-id="1584f-114">Type</span><span class="sxs-lookup"><span data-stu-id="1584f-114">Type</span></span> | <span data-ttu-id="1584f-115">Mot clé</span><span class="sxs-lookup"><span data-stu-id="1584f-115">Keyword</span></span> | <span data-ttu-id="1584f-116">Suffix</span><span class="sxs-lookup"><span data-stu-id="1584f-116">Suffix</span></span> |  
|--|--|--|
| <xref:System.UInt32> | [<span data-ttu-id="1584f-117">UInteger</span><span class="sxs-lookup"><span data-stu-id="1584f-117">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md) | <span data-ttu-id="1584f-118">U</span><span class="sxs-lookup"><span data-stu-id="1584f-118">U</span></span> |
| <xref:System.Int64> | [<span data-ttu-id="1584f-119">Long</span><span class="sxs-lookup"><span data-stu-id="1584f-119">Long</span></span>](../../../language-reference/data-types/long-data-type.md) | <span data-ttu-id="1584f-120">L</span><span class="sxs-lookup"><span data-stu-id="1584f-120">L</span></span> |
| <xref:System.UInt64> | [<span data-ttu-id="1584f-121">ULong</span><span class="sxs-lookup"><span data-stu-id="1584f-121">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md) | <span data-ttu-id="1584f-122">UL</span><span class="sxs-lookup"><span data-stu-id="1584f-122">UL</span></span> |
| <xref:System.Double> | [<span data-ttu-id="1584f-123">Double</span><span class="sxs-lookup"><span data-stu-id="1584f-123">Double</span></span>](../../../language-reference/data-types/double-data-type.md) | <span data-ttu-id="1584f-124">D</span><span class="sxs-lookup"><span data-stu-id="1584f-124">D</span></span> |
| <xref:System.Single> | [<span data-ttu-id="1584f-125">Single</span><span class="sxs-lookup"><span data-stu-id="1584f-125">Single</span></span>](../../../language-reference/data-types/single-data-type.md) | <span data-ttu-id="1584f-126">F</span><span class="sxs-lookup"><span data-stu-id="1584f-126">F</span></span> | 
| <xref:System.Decimal> | [<span data-ttu-id="1584f-127">Decimal</span><span class="sxs-lookup"><span data-stu-id="1584f-127">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md) | <span data-ttu-id="1584f-128">M</span><span class="sxs-lookup"><span data-stu-id="1584f-128">M</span></span> |

### <a name="examples"></a><span data-ttu-id="1584f-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="1584f-129">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="1584f-130">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="1584f-130">BlockExpression</span></span>

<span data-ttu-id="1584f-131">Si le type d’un <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> objet est différent du type de la dernière expression dans le bloc, le type est affiché entre crochets (`<` et `>`).</span><span class="sxs-lookup"><span data-stu-id="1584f-131">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="1584f-132">Sinon, le type de l’objet <xref:System.Linq.Expressions.BlockExpression> n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="1584f-132">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="1584f-133">Exemples</span><span class="sxs-lookup"><span data-stu-id="1584f-133">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="1584f-134">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="1584f-134">LambdaExpression</span></span>

<span data-ttu-id="1584f-135">Les objets <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> sont affichés avec leurs types délégués.</span><span class="sxs-lookup"><span data-stu-id="1584f-135"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="1584f-136">Si une expression lambda n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="1584f-136">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="1584f-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="1584f-137">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="1584f-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="1584f-138">LabelExpression</span></span>

<span data-ttu-id="1584f-139">Si vous spécifiez une valeur par défaut pour l’objet <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, cette valeur est affichée avant l’objet <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1584f-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="1584f-140">Le jeton `.Label` indique le début de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="1584f-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="1584f-141">Le jeton `.LabelTarget` indique la destination de la cible à laquelle accéder.</span><span class="sxs-lookup"><span data-stu-id="1584f-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="1584f-142">Si une étiquette n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="1584f-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="1584f-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="1584f-143">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="1584f-144">Opérateurs Checked</span><span class="sxs-lookup"><span data-stu-id="1584f-144">Checked Operators</span></span>

<span data-ttu-id="1584f-145">Opérateurs checked sont affichés avec le `#` symbole devant l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="1584f-145">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="1584f-146">Par exemple, l’opérateur d’addition checked est affiché sous la forme `#+`.</span><span class="sxs-lookup"><span data-stu-id="1584f-146">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="1584f-147">Exemples</span><span class="sxs-lookup"><span data-stu-id="1584f-147">Examples</span></span>

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