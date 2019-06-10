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
ms.openlocfilehash: bc3fc579ed8031d818241f41ac728ef7e5be0b99
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690116"
---
# <a name="debugview-syntax"></a><span data-ttu-id="04edf-103">Syntaxe `DebugView`</span><span class="sxs-lookup"><span data-stu-id="04edf-103">`DebugView` syntax</span></span>

<span data-ttu-id="04edf-104">La propriété `DebugView` (disponible uniquement lors du débogage) fournit un rendu de la chaîne d’arborescences d’expression.</span><span class="sxs-lookup"><span data-stu-id="04edf-104">The `DebugView` property (available only when debugging) provides a string rendering of expression trees.</span></span> <span data-ttu-id="04edf-105">La plupart de la syntaxe est assez simple à comprendre ; les cas spéciaux sont décrits dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="04edf-105">Most of the syntax is fairly straightforward to understand; the special cases are described in the following sections.</span></span>

<span data-ttu-id="04edf-106">Chaque exemple est suivi d’un commentaire en bloc contenant le `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="04edf-106">Each example is followed by a block comment, containing the `DebugView`.</span></span>

## <a name="parameterexpression"></a><span data-ttu-id="04edf-107">ParameterExpression</span><span class="sxs-lookup"><span data-stu-id="04edf-107">ParameterExpression</span></span>

<span data-ttu-id="04edf-108">Les noms de variables <xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> s’affichent avec le symbole `$` au début.</span><span class="sxs-lookup"><span data-stu-id="04edf-108"><xref:System.Linq.Expressions.ParameterExpression?displayProperty=nameWithType> variable names are displayed with a `$` symbol at the beginning.</span></span>

<span data-ttu-id="04edf-109">Si un paramètre n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="04edf-109">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="04edf-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="04edf-110">Examples</span></span>

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

## <a name="constantexpression"></a><span data-ttu-id="04edf-111">ConstantExpression</span><span class="sxs-lookup"><span data-stu-id="04edf-111">ConstantExpression</span></span>

<span data-ttu-id="04edf-112">Pour les objets <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> qui représentent des valeurs entières, des chaînes et des valeurs `null`, la valeur de la constante est affichée.</span><span class="sxs-lookup"><span data-stu-id="04edf-112">For <xref:System.Linq.Expressions.ConstantExpression?displayProperty=nameWithType> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

<span data-ttu-id="04edf-113">Pour les types numériques comportant des suffixes standard comme littéraux C#, le suffixe est ajouté à la valeur.</span><span class="sxs-lookup"><span data-stu-id="04edf-113">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="04edf-114">Le tableau suivant indique les suffixes associés aux différents types numériques.</span><span class="sxs-lookup"><span data-stu-id="04edf-114">The following table shows the suffixes associated with various numeric types.</span></span>

| <span data-ttu-id="04edf-115">Type</span><span class="sxs-lookup"><span data-stu-id="04edf-115">Type</span></span> | <span data-ttu-id="04edf-116">Mot clé</span><span class="sxs-lookup"><span data-stu-id="04edf-116">Keyword</span></span> | <span data-ttu-id="04edf-117">Suffixe</span><span class="sxs-lookup"><span data-stu-id="04edf-117">Suffix</span></span> |
|--|--|--|
| <xref:System.UInt32?displayProperty=nameWithType> | [<span data-ttu-id="04edf-118">uint</span><span class="sxs-lookup"><span data-stu-id="04edf-118">uint</span></span>](../../../language-reference/keywords/uint.md) | <span data-ttu-id="04edf-119">U</span><span class="sxs-lookup"><span data-stu-id="04edf-119">U</span></span> |
| <xref:System.Int64?displayProperty=nameWithType> | [<span data-ttu-id="04edf-120">long</span><span class="sxs-lookup"><span data-stu-id="04edf-120">long</span></span>](../../../language-reference/keywords/long.md) | <span data-ttu-id="04edf-121">L</span><span class="sxs-lookup"><span data-stu-id="04edf-121">L</span></span> |
| <xref:System.UInt64?displayProperty=nameWithType> | [<span data-ttu-id="04edf-122">ulong</span><span class="sxs-lookup"><span data-stu-id="04edf-122">ulong</span></span>](../../../language-reference/keywords/ulong.md) | <span data-ttu-id="04edf-123">UL</span><span class="sxs-lookup"><span data-stu-id="04edf-123">UL</span></span> |
| <xref:System.Double?displayProperty=nameWithType> | [<span data-ttu-id="04edf-124">double</span><span class="sxs-lookup"><span data-stu-id="04edf-124">double</span></span>](../../../language-reference/keywords/double.md) | <span data-ttu-id="04edf-125">D</span><span class="sxs-lookup"><span data-stu-id="04edf-125">D</span></span> |
| <xref:System.Single?displayProperty=nameWithType> | [<span data-ttu-id="04edf-126">float</span><span class="sxs-lookup"><span data-stu-id="04edf-126">float</span></span>](../../../language-reference/keywords/float.md) | <span data-ttu-id="04edf-127">F</span><span class="sxs-lookup"><span data-stu-id="04edf-127">F</span></span> |
| <xref:System.Decimal?displayProperty=nameWithType> | [<span data-ttu-id="04edf-128">decimal</span><span class="sxs-lookup"><span data-stu-id="04edf-128">decimal</span></span>](../../../language-reference/keywords/decimal.md) | <span data-ttu-id="04edf-129">M</span><span class="sxs-lookup"><span data-stu-id="04edf-129">M</span></span> |

### <a name="examples"></a><span data-ttu-id="04edf-130">Exemples</span><span class="sxs-lookup"><span data-stu-id="04edf-130">Examples</span></span>

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

## <a name="blockexpression"></a><span data-ttu-id="04edf-131">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="04edf-131">BlockExpression</span></span>

<span data-ttu-id="04edf-132">Si le type d’un objet <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> diffère du type de la dernière expression du bloc, le type est affiché entre crochets pointus (`<` et `>`).</span><span class="sxs-lookup"><span data-stu-id="04edf-132">If the type of a <xref:System.Linq.Expressions.BlockExpression?displayProperty=nameWithType> object differs from the type of the last expression in the block, the type is displayed within angle brackets (`<` and `>`).</span></span> <span data-ttu-id="04edf-133">Sinon, le type de l’objet <xref:System.Linq.Expressions.BlockExpression> n’est pas affiché.</span><span class="sxs-lookup"><span data-stu-id="04edf-133">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="04edf-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="04edf-134">Examples</span></span>

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

## <a name="lambdaexpression"></a><span data-ttu-id="04edf-135">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="04edf-135">LambdaExpression</span></span>

<span data-ttu-id="04edf-136">Les objets <xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> sont affichés avec leurs types délégués.</span><span class="sxs-lookup"><span data-stu-id="04edf-136"><xref:System.Linq.Expressions.LambdaExpression?displayProperty=nameWithType> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="04edf-137">Si une expression lambda n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="04edf-137">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="04edf-138">Exemples</span><span class="sxs-lookup"><span data-stu-id="04edf-138">Examples</span></span>

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

## <a name="labelexpression"></a><span data-ttu-id="04edf-139">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="04edf-139">LabelExpression</span></span>

<span data-ttu-id="04edf-140">Si vous spécifiez une valeur par défaut pour l’objet <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType>, cette valeur est affichée avant l’objet <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04edf-140">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression?displayProperty=nameWithType> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="04edf-141">Le jeton `.Label` indique le début de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="04edf-141">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="04edf-142">Le jeton `.LabelTarget` indique la destination de la cible à laquelle accéder.</span><span class="sxs-lookup"><span data-stu-id="04edf-142">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="04edf-143">Si une étiquette n’a pas de nom, un nom généré automatiquement lui est assigné, tel que `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="04edf-143">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="04edf-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="04edf-144">Examples</span></span>

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

## <a name="checked-operators"></a><span data-ttu-id="04edf-145">Opérateurs Checked</span><span class="sxs-lookup"><span data-stu-id="04edf-145">Checked Operators</span></span>

<span data-ttu-id="04edf-146">Des opérateurs activés sont affichés avec le symbole `#` en regard de l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="04edf-146">Checked operators are displayed with the `#` symbol in front of the operator.</span></span> <span data-ttu-id="04edf-147">Par exemple, l’opérateur d’addition checked est affiché sous la forme `#+`.</span><span class="sxs-lookup"><span data-stu-id="04edf-147">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="04edf-148">Exemples</span><span class="sxs-lookup"><span data-stu-id="04edf-148">Examples</span></span>

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
