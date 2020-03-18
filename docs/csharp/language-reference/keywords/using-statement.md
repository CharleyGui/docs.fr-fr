---
title: using, instruction - Référence C#
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712960"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="b0534-102">using, instruction (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b0534-102">using statement (C# Reference)</span></span>

<span data-ttu-id="b0534-103">Fournit une syntaxe pratique qui garantit l’utilisation correcte d’objets <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="b0534-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="b0534-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="b0534-104">Example</span></span>

<span data-ttu-id="b0534-105">L’exemple suivant montre comment utiliser l’instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="b0534-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

<span data-ttu-id="b0534-106">En commençant par C 8.0, vous pouvez utiliser `using` la syntaxe alternative suivante pour l’énoncé qui ne nécessite pas d’accolades :</span><span class="sxs-lookup"><span data-stu-id="b0534-106">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a><span data-ttu-id="b0534-107">Notes </span><span class="sxs-lookup"><span data-stu-id="b0534-107">Remarks</span></span>

<span data-ttu-id="b0534-108"><xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples de types managés qui accèdent à des ressources non managées (dans le cas présent, des handles de fichiers et des contextes d’appareil).</span><span class="sxs-lookup"><span data-stu-id="b0534-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="b0534-109">Beaucoup d’autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler.</span><span class="sxs-lookup"><span data-stu-id="b0534-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="b0534-110">Tous les types de cette sorte doivent implémentent l’interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="b0534-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="b0534-111">Quand la durée de vie d’un objet `IDisposable` est limitée à une seule méthode, vous devez le déclarer et l’instancier dans l’instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="b0534-111">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="b0534-112">L’instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> correctement sur l’objet et, quand vous l’utilisez comme indiqué précédemment, elle met également l’objet lui-même hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelée.</span><span class="sxs-lookup"><span data-stu-id="b0534-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="b0534-113">Dans le bloc `using`, l’objet est en lecture seule et ne peut être ni modifié ni réassigné.</span><span class="sxs-lookup"><span data-stu-id="b0534-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="b0534-114">L’instruction `using` garantit que <xref:System.IDisposable.Dispose%2A> est appelée même si une exception se produit dans le bloc `using`.</span><span class="sxs-lookup"><span data-stu-id="b0534-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="b0534-115">Vous pouvez obtenir le même résultat en plaçant l’objet dans un bloc `try`, puis en appelant <xref:System.IDisposable.Dispose%2A> dans un bloc `finally` ; c’est d’ailleurs ainsi que l’instruction `using` est traduite par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="b0534-115">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="b0534-116">L’exemple de code précédent se développe pour donner le code suivant au moment de la compilation (notez les accolades supplémentaires pour créer la portée limitée de l’objet) :</span><span class="sxs-lookup"><span data-stu-id="b0534-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="b0534-117">La syntaxe de déclaration plus nouvelle `using` se traduit par un code très similaire.</span><span class="sxs-lookup"><span data-stu-id="b0534-117">The newer `using` statement syntax translates to very similar code.</span></span> <span data-ttu-id="b0534-118">Le `try` bloc s’ouvre là où la variable est déclarée.</span><span class="sxs-lookup"><span data-stu-id="b0534-118">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="b0534-119">Le `finally` bloc est ajouté à la fin du bloc d’enceinte, généralement à la fin d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="b0534-119">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="b0534-120">Pour plus d’informations sur l’instruction `try`-`finally`, consultez la rubrique [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="b0534-120">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="b0534-121">Vous pouvez déclarer plusieurs instances d’un type dans l’instruction `using`, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b0534-121">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="b0534-122">Vous pouvez combiner plusieurs déclarations du même type à l’aide de la nouvelle syntaxe introduite avec C 8 ainsi.</span><span class="sxs-lookup"><span data-stu-id="b0534-122">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well.</span></span> <span data-ttu-id="b0534-123">Ceci est illustré dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="b0534-123">This is shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

<span data-ttu-id="b0534-124">Il n’est pas recommandé d’instancier l’objet de ressource, puis de passer la variable à l’instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="b0534-124">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="b0534-125">Dans ce cas, une fois que le contrôle a quitté le bloc `using`, l’objet reste dans la portée mais n’a probablement pas accès à ses ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="b0534-125">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="b0534-126">En d’autres termes, il n’est plus complètement initialisé.</span><span class="sxs-lookup"><span data-stu-id="b0534-126">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="b0534-127">Si vous essayez d’utiliser l’objet à l’extérieur du bloc `using`, vous risquez de provoquer la levée d’une exception.</span><span class="sxs-lookup"><span data-stu-id="b0534-127">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="b0534-128">C’est pourquoi il est généralement préférable d’instancier l’objet dans l’instruction `using` et de limiter sa portée au bloc `using`.</span><span class="sxs-lookup"><span data-stu-id="b0534-128">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="b0534-129">Pour plus d’informations sur la suppression d’objets `IDisposable`, consultez [Utilisation d’objets qui implémentent IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="b0534-129">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b0534-130">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b0534-130">C# language specification</span></span>

<span data-ttu-id="b0534-131">Pour plus d’informations, consultez [Instruction using](~/_csharplang/spec/statements.md#the-using-statement) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b0534-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="b0534-132">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="b0534-132">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0534-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0534-133">See also</span></span>

- [<span data-ttu-id="b0534-134">Référence C</span><span class="sxs-lookup"><span data-stu-id="b0534-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0534-135">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b0534-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0534-136">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="b0534-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b0534-137">en utilisant la directive</span><span class="sxs-lookup"><span data-stu-id="b0534-137">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="b0534-138">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="b0534-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b0534-139">Utilisation d’objets implémentant IDisposable</span><span class="sxs-lookup"><span data-stu-id="b0534-139">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="b0534-140">Interface IDisposable</span><span class="sxs-lookup"><span data-stu-id="b0534-140">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="b0534-141">à l’aide de l’énoncé dans C 8.0</span><span class="sxs-lookup"><span data-stu-id="b0534-141">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
