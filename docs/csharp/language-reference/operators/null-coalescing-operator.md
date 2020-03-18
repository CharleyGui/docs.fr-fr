---
title: ?? Et?? Opérateurs - Référence C
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847311"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="95af0-103">??</span><span class="sxs-lookup"><span data-stu-id="95af0-103">??</span></span> <span data-ttu-id="95af0-104">Et?? - opérateurs (référence C)</span><span class="sxs-lookup"><span data-stu-id="95af0-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="95af0-105">L’opérateur de fusion null `??` retourne la valeur de l’opérande de gauche si elle n’est pas `null` ; sinon, il évalue l’opérande de droite et retourne son résultat.</span><span class="sxs-lookup"><span data-stu-id="95af0-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="95af0-106">L’opérateur `??` n’évalue pas son opérande de droite si l’opérande de gauche n’est pas Null.</span><span class="sxs-lookup"><span data-stu-id="95af0-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="95af0-107">Disponible en C 8.0 et plus tard, l’opérateur `??=` d’affectation de fusion nulle attribue la valeur de son opérande de droite `null`à son opératment de gauche seulement si l’opérand gauche évalue à .</span><span class="sxs-lookup"><span data-stu-id="95af0-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="95af0-108">L’opérateur `??=` n’évalue pas son opérande de droite si l’opérande de gauche n’est pas Null.</span><span class="sxs-lookup"><span data-stu-id="95af0-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="95af0-109">L’opératoire gauche `??=` de l’opérateur doit être une variable, une [propriété,](../../programming-guide/classes-and-structs/properties.md)ou un élément [d’indexeur.](../../programming-guide/indexers/index.md)</span><span class="sxs-lookup"><span data-stu-id="95af0-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="95af0-110">Dans C 7.3 et plus tôt, le type de `??` l’opératoire gauche de l’opérateur doit être soit un type de [référence,](../keywords/reference-types.md) soit un [type de valeur nul](../builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="95af0-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="95af0-111">À partir de C 8.0, cette exigence est remplacée par ce qui `??` suit `??=` : le type de l’opéra de gauche et les opérateurs ne peuvent pas être un type de valeur non annulable.</span><span class="sxs-lookup"><span data-stu-id="95af0-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="95af0-112">En particulier, en commençant par le C 8.0, vous pouvez utiliser les opérateurs de fusion nulle avec des paramètres de type sans contrainte :</span><span class="sxs-lookup"><span data-stu-id="95af0-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="95af0-113">Les opérateurs de fusion nul sont de droite-associative.</span><span class="sxs-lookup"><span data-stu-id="95af0-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="95af0-114">C’est-à-dire, les expressions de la forme</span><span class="sxs-lookup"><span data-stu-id="95af0-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="95af0-115">sont évalués comme</span><span class="sxs-lookup"><span data-stu-id="95af0-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="95af0-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="95af0-116">Examples</span></span>

<span data-ttu-id="95af0-117">Les `??` `??=` opérateurs et les opérateurs peuvent être utiles dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="95af0-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="95af0-118">Dans les expressions avec les [opérateurs null-conditionnels ?. et ?[]](member-access-operators.md#null-conditional-operators--and-), vous pouvez utiliser l’opérateur `??` pour `null`fournir une expression alternative à évaluer au cas où le résultat de l’expression avec des opérations non conditionnelles est:</span><span class="sxs-lookup"><span data-stu-id="95af0-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="95af0-119">Lorsque vous [travaillez](../builtin-types/nullable-value-types.md) avec des types de valeur nul et que `??` vous devez fournir une valeur d’un `null`type de valeur sous-jacent, utilisez l’opérateur pour spécifier la valeur à fournir au cas où une valeur de type nul serait :</span><span class="sxs-lookup"><span data-stu-id="95af0-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="95af0-120">Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> si la valeur à utiliser quand une valeur de type Nullable est `null` doit être la valeur par défaut du type valeur sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="95af0-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="95af0-121">En commençant par le numéro 7.0, vous pouvez utiliser une `??` [ `throw` expression](../keywords/throw.md#the-throw-expression) comme l’opéra de droite de l’opérateur pour rendre le code de vérification des arguments plus concis :</span><span class="sxs-lookup"><span data-stu-id="95af0-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="95af0-122">L’exemple précédent montre également comment utiliser des [membres expression-bodied](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) pour définir une propriété.</span><span class="sxs-lookup"><span data-stu-id="95af0-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="95af0-123">En commençant par le C 8.0, vous pouvez utiliser l’opérateur `??=` pour remplacer le code du formulaire</span><span class="sxs-lookup"><span data-stu-id="95af0-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="95af0-124">par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="95af0-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="95af0-125">Capacité de surcharge de l’opérateur</span><span class="sxs-lookup"><span data-stu-id="95af0-125">Operator overloadability</span></span>

<span data-ttu-id="95af0-126">Les `??` opérateurs `??=` et ne peuvent pas être surchargés.</span><span class="sxs-lookup"><span data-stu-id="95af0-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="95af0-127">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="95af0-127">C# language specification</span></span>

<span data-ttu-id="95af0-128">Pour plus d’informations sur l’opérateur, `??` voir La section de [l’opérateur](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) de fusion nul de la spécification linguistique [CMD](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="95af0-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="95af0-129">Pour plus d’informations sur l’opérateur, `??=` voir la note de proposition de [fonctionnalité](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span><span class="sxs-lookup"><span data-stu-id="95af0-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95af0-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95af0-130">See also</span></span>

- [<span data-ttu-id="95af0-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="95af0-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="95af0-132">Opérateurs CMD</span><span class="sxs-lookup"><span data-stu-id="95af0-132">C# operators</span></span>](index.md)
- <span data-ttu-id="95af0-133">[Opérateurs ?. et ?[]](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="95af0-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="95af0-134">?: opérateur</span><span class="sxs-lookup"><span data-stu-id="95af0-134">?: operator</span></span>](conditional-operator.md)
