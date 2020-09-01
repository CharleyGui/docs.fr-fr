---
description: throw - Référence C#
title: throw - Référence C#
ms.date: 03/02/2015
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
ms.openlocfilehash: 4cad4810b89f976f92ce576917feb2398acce636
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142035"
---
# <a name="throw-c-reference"></a><span data-ttu-id="8cffe-103">throw (référence C#)</span><span class="sxs-lookup"><span data-stu-id="8cffe-103">throw (C# Reference)</span></span>

<span data-ttu-id="8cffe-104">Signale l’occurrence d’une exception pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="8cffe-104">Signals the occurrence of an exception during program execution.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cffe-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="8cffe-105">Remarks</span></span>

<span data-ttu-id="8cffe-106">La syntaxe de `throw` est :</span><span class="sxs-lookup"><span data-stu-id="8cffe-106">The syntax of `throw` is:</span></span>

```csharp
throw [e];
```

<span data-ttu-id="8cffe-107">où `e` est une instance d’une classe dérivée de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8cffe-107">where `e` is an instance of a class derived from <xref:System.Exception?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8cffe-108">L’exemple suivant utilise l’instruction `throw` pour lever une exception <xref:System.IndexOutOfRangeException> si l’argument passé à une méthode nommée `GetNumber` ne correspond pas à un index valide d’un tableau interne.</span><span class="sxs-lookup"><span data-stu-id="8cffe-108">The following example uses the `throw` statement to throw an <xref:System.IndexOutOfRangeException> if the argument passed to a method named `GetNumber` does not correspond to a valid index of an internal array.</span></span>

[!code-csharp[csrefKeyword#1](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]

<span data-ttu-id="8cffe-109">Les appelants de méthode utilisent alors un bloc `try-catch` ou `try-catch-finally` pour gérer l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="8cffe-109">Method callers then use a `try-catch` or `try-catch-finally` block to handle the thrown exception.</span></span> <span data-ttu-id="8cffe-110">L’exemple suivant gère l’exception levée par la méthode `GetNumber`.</span><span class="sxs-lookup"><span data-stu-id="8cffe-110">The following example handles the exception thrown by the `GetNumber` method.</span></span>

[!code-csharp[csrefKeyword#2](~/samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]

## <a name="re-throwing-an-exception"></a><span data-ttu-id="8cffe-111">Exception levée plusieurs fois</span><span class="sxs-lookup"><span data-stu-id="8cffe-111">Re-throwing an exception</span></span>

<span data-ttu-id="8cffe-112">`throw` peut également être utilisé dans un bloc `catch` pour lever de nouveau une exception gérée dans un bloc `catch`.</span><span class="sxs-lookup"><span data-stu-id="8cffe-112">`throw` can also be used in a `catch` block to re-throw an exception handled in a `catch` block.</span></span>  <span data-ttu-id="8cffe-113">Dans ce cas, `throw` n’accepte pas d’opérande d’exception.</span><span class="sxs-lookup"><span data-stu-id="8cffe-113">In this case, `throw` does not take an exception operand.</span></span> <span data-ttu-id="8cffe-114">Cela est très utile lorsqu’une méthode passe un argument d’un appelant à une autre méthode de bibliothèque, et que la méthode de bibliothèque lève une exception qui doit être passée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8cffe-114">It is most useful when a method passes on an argument from a caller to some other library method, and the library method throws an exception that must be passed on to the caller.</span></span> <span data-ttu-id="8cffe-115">Par exemple, l’exemple suivant lève de nouveau une exception <xref:System.NullReferenceException> qui est levée lorsque vous tentez de récupérer le premier caractère d’une chaîne non initialisée.</span><span class="sxs-lookup"><span data-stu-id="8cffe-115">For example, the following example re-throws an <xref:System.NullReferenceException> that is thrown when attempting to retrieve the first character of an uninitialized string.</span></span>

[!code-csharp[csrefKeyword#3](~/samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]

> [!IMPORTANT]
> <span data-ttu-id="8cffe-116">Vous pouvez également utiliser la syntaxe `throw e` dans un bloc `catch` pour instancier une nouvelle exception que vous passez à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8cffe-116">You can also use the `throw e` syntax in a `catch` block to instantiate a new exception that you pass on to the caller.</span></span> <span data-ttu-id="8cffe-117">Dans ce cas, la trace de la pile de l’exception d’origine, qui est disponible à partir de la propriété <xref:System.Exception.StackTrace>, n’est pas conservée.</span><span class="sxs-lookup"><span data-stu-id="8cffe-117">In this case, the stack trace of the original exception, which is available from the <xref:System.Exception.StackTrace> property, is not preserved.</span></span>

## <a name="the-throw-expression"></a><span data-ttu-id="8cffe-118">Expression `throw`</span><span class="sxs-lookup"><span data-stu-id="8cffe-118">The `throw` expression</span></span>

<span data-ttu-id="8cffe-119">À compter de C# 7.0, `throw` peut être utilisé comme expression et comme instruction.</span><span class="sxs-lookup"><span data-stu-id="8cffe-119">Starting with C# 7.0, `throw` can be used as an expression as well as a statement.</span></span> <span data-ttu-id="8cffe-120">Ainsi, une exception peut être levée dans des contextes qui n’étaient précédemment pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="8cffe-120">This allows an exception to be thrown in contexts that were previously unsupported.</span></span> <span data-ttu-id="8cffe-121">notamment :</span><span class="sxs-lookup"><span data-stu-id="8cffe-121">These include:</span></span>

- <span data-ttu-id="8cffe-122">[opérateur conditionnel](../operators/conditional-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8cffe-122">[the conditional operator](../operators/conditional-operator.md).</span></span> <span data-ttu-id="8cffe-123">l’exemple suivant utilise une expression `throw` pour lever une exception <xref:System.ArgumentException> si une méthode reçoit un tableau de chaînes vide.</span><span class="sxs-lookup"><span data-stu-id="8cffe-123">The following example uses a `throw` expression to throw an <xref:System.ArgumentException> if a method is passed an empty string array.</span></span> <span data-ttu-id="8cffe-124">Avant C# 7.0, cette logique devait figurer dans une instruction `if`/`else`.</span><span class="sxs-lookup"><span data-stu-id="8cffe-124">Before C# 7.0, this logic would need to appear in an `if`/`else` statement.</span></span>

   [!code-csharp[csrefKeyword#4](~/samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]

- <span data-ttu-id="8cffe-125">[l’opérateur de fusion de Null](../operators/null-coalescing-operator.md) :</span><span class="sxs-lookup"><span data-stu-id="8cffe-125">[the null-coalescing operator](../operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="8cffe-126">dans l’exemple suivant, une expression `throw` est utilisée avec un opérateur de fusion de Null pour lever une exception si la chaîne assignée à une propriété `Name` est `null`.</span><span class="sxs-lookup"><span data-stu-id="8cffe-126">In the following example, a `throw` expression is used with a null-coalescing operator to throw an exception if the string assigned to a `Name` property is `null`.</span></span>

   [!code-csharp[csrefKeyword#5](~/samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]

- <span data-ttu-id="8cffe-127">un [lambda](../operators/lambda-expressions.md) ou une méthode expression-bodied :</span><span class="sxs-lookup"><span data-stu-id="8cffe-127">an expression-bodied [lambda](../operators/lambda-expressions.md) or method.</span></span> <span data-ttu-id="8cffe-128">l’exemple suivant illustre une méthode expression-bodied qui lève une exception <xref:System.InvalidCastException>, car une conversion vers une valeur <xref:System.DateTime> n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8cffe-128">The following example illustrates an expression-bodied method that throws an <xref:System.InvalidCastException> because a conversion to a <xref:System.DateTime> value is not supported.</span></span>

   [!code-csharp[csrefKeyword#6](~/samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]

## <a name="c-language-specification"></a><span data-ttu-id="8cffe-129">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8cffe-129">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="8cffe-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cffe-130">See also</span></span>

- [<span data-ttu-id="8cffe-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="8cffe-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8cffe-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="8cffe-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8cffe-133">try-catch</span><span class="sxs-lookup"><span data-stu-id="8cffe-133">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="8cffe-134">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="8cffe-134">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8cffe-135">Comment : lever explicitement des exceptions</span><span class="sxs-lookup"><span data-stu-id="8cffe-135">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
