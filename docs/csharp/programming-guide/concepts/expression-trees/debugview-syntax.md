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
ms.openlocfilehash: c42aacba9039b4a7807fc6084e548b84ef7be5f9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423701"
---
# <a name="debugview-syntax"></a><span data-ttu-id="0ad4b-103">Syntaxe `DebugView`</span><span class="sxs-lookup"><span data-stu-id="0ad4b-103">`DebugView` syntax</span></span>

<span data-ttu-id="0ad4b-104">La propriété `DebugView` (disponible uniquement lors du débogage) fournit un rendu de la chaîne d’arborescences d’expression.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="0ad4b-105">La plupart de la syntaxe est assez simple à comprendre ; les cas spéciaux sont décrits dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="0ad4b-106">Chaque exemple est suivi d’un commentaire en bloc contenant le `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="0ad4b-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="0ad4b-107">ParameterExpression</span></span>

<span data-ttu-id="0ad4b-108">Les noms de variables <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> s’affichent avec le symbole `$` au début.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="0ad4b-109">Si un paramètre n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="0ad4b-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="0ad4b-110">Examples</span></span>

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

## <a name="constantexpression"></a><span data-ttu-id="0ad4b-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="0ad4b-111">ConstantExpression</span></span>

<span data-ttu-id="0ad4b-112">Pour les objets <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> qui représentent des valeurs entières, des chaînes et des valeurs `null`, la valeur de la constante est affichée.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="0ad4b-113">Pour les types numériques comportant des suffixes standard comme littéraux C#, le suffixe est ajouté à la valeur.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="0ad4b-114">Le tableau suivant indique les suffixes associés aux différents types numériques.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="0ad4b-115">Type</span><span class="sxs-lookup"><span data-stu-id="0ad4b-115">Type</span></span> | <span data-ttu-id="0ad4b-116">Mot clé</span><span class="sxs-lookup"><span data-stu-id="0ad4b-116">Keyword</span></span> | <span data-ttu-id="0ad4b-117">Suffixe</span><span class="sxs-lookup"><span data-stu-id="0ad4b-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="0ad4b-118">uint</span><span class="sxs-lookup"><span data-stu-id="0ad4b-118">uint</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="0ad4b-119">U</span><span class="sxs-lookup"><span data-stu-id="0ad4b-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="0ad4b-120">long</span><span class="sxs-lookup"><span data-stu-id="0ad4b-120">long</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="0ad4b-121">L</span><span class="sxs-lookup"><span data-stu-id="0ad4b-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="0ad4b-122">ulong</span><span class="sxs-lookup"><span data-stu-id="0ad4b-122">ulong</span></span>](../../../language-reference/builtin-types/integral-numeric-types.md) | <span data-ttu-id="0ad4b-123">UL</span><span class="sxs-lookup"><span data-stu-id="0ad4b-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="0ad4b-124">double</span><span class="sxs-lookup"><span data-stu-id="0ad4b-124">double</span></span>](../../../language-reference/keywords/double.md) | <span data-ttu-id="0ad4b-125">D</span><span class="sxs-lookup"><span data-stu-id="0ad4b-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="0ad4b-126">float</span><span class="sxs-lookup"><span data-stu-id="0ad4b-126">float</span></span>](../../../language-reference/keywords/float.md) | <span data-ttu-id="0ad4b-127">F</span><span class="sxs-lookup"><span data-stu-id="0ad4b-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="0ad4b-128">decimal</span><span class="sxs-lookup"><span data-stu-id="0ad4b-128">decimal</span></span>](../../../language-reference/keywords/decimal.md) | <span data-ttu-id="0ad4b-129">M</span><span class="sxs-lookup"><span data-stu-id="0ad4b-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="0ad4b-130">Exemples</span><span class="sxs-lookup"><span data-stu-id="0ad4b-130">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="0ad4b-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="0ad4b-131">BlockExpression</span></span>

<span data-ttu-id="0ad4b-132">Si le type d’un objet <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> diffère du type de la dernière expression du bloc, le type est affiché entre crochets pointus (`<` et `>`).</span><span class="sxs-lookup"><span data-stu-id="0ad4b-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="0ad4b-133">Sinon, le type de l’objet <xref:System.Linq.Expressions.BlockExpression> n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="0ad4b-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="0ad4b-134">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="0ad4b-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="0ad4b-135">LambdaExpression</span></span>

<span data-ttu-id="0ad4b-136">Les objets <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> sont affichés avec leurs types délégués.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="0ad4b-137">Si une expression lambda n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="0ad4b-138">Exemples</span><span class="sxs-lookup"><span data-stu-id="0ad4b-138">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="0ad4b-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="0ad4b-139">LabelExpression</span></span>

<span data-ttu-id="0ad4b-140">Si vous spécifiez une valeur par défaut pour l’objet <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, cette valeur est affichée avant l’objet <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="0ad4b-141">Le jeton `.Label` indique le début de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="0ad4b-142">Le jeton `.LabelTarget` indique la destination de la cible à laquelle accéder.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="0ad4b-143">Si une étiquette n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="0ad4b-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="0ad4b-144">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="0ad4b-145">Opérateurs Checked</span><span class="sxs-lookup"><span data-stu-id="0ad4b-145">Checked Operators</span></span>

<span data-ttu-id="0ad4b-146">Des opérateurs activés sont affichés avec le symbole `#` en regard de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="0ad4b-147">Par exemple, l’opérateur d’addition checked est affiché sous la forme `#+`.</span><span class="sxs-lookup"><span data-stu-id="0ad4b-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="0ad4b-148">Exemples</span><span class="sxs-lookup"><span data-stu-id="0ad4b-148">Examples</span></span>

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
