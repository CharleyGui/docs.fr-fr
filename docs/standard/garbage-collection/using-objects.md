---
title: Utilisation d’objets implémentant IDisposable
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 87eefe2bd347ba1564b2f06d49bbee3b85efdb97
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287595"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="c3419-102">Utilisation d’objets implémentant IDisposable</span><span class="sxs-lookup"><span data-stu-id="c3419-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="c3419-103">Le « garbage collector » de l’common language runtime récupère la mémoire utilisée par les objets managés, mais les types qui utilisent des ressources non managées implémentent l' <xref:System.IDisposable> interface pour permettre la récupération des ressources requises par ces ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="c3419-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the resources needed by these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="c3419-104">Une fois que vous avez fini d'utiliser un objet qui implémente <xref:System.IDisposable>, vous devez appeler l'implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> de l'objet.</span><span class="sxs-lookup"><span data-stu-id="c3419-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="c3419-105">Vous pouvez le faire de deux façons :</span><span class="sxs-lookup"><span data-stu-id="c3419-105">You can do this in one of two ways:</span></span>

- <span data-ttu-id="c3419-106">Avec l' `using` instruction C# ( `Using` dans Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c3419-106">With the C# `using` statement (`Using` in Visual Basic).</span></span>
- <span data-ttu-id="c3419-107">En implémentant un `try/finally` bloc et en appelant le <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> dans le `finally` .</span><span class="sxs-lookup"><span data-stu-id="c3419-107">By implementing a `try/finally` block, and calling the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> in the `finally`.</span></span>

## <a name="the-using-statement"></a><span data-ttu-id="c3419-108">Instruction using</span><span class="sxs-lookup"><span data-stu-id="c3419-108">The using statement</span></span>

<span data-ttu-id="c3419-109">L' [ `using` instruction](../../csharp/language-reference/keywords/using-statement.md) en C# et l' [ `Using` instruction](../../visual-basic/language-reference/statements/using-statement.md) dans Visual Basic simplifient le code que vous devez écrire pour nettoyer un objet.</span><span class="sxs-lookup"><span data-stu-id="c3419-109">The [`using` statement](../../csharp/language-reference/keywords/using-statement.md) in C# and the [`Using` statement](../../visual-basic/language-reference/statements/using-statement.md) in Visual Basic simplify the code that you must write to cleanup an object.</span></span> <span data-ttu-id="c3419-110">L’instruction `using` obtient une ou plusieurs ressources, exécute les instructions que vous spécifiez, puis supprime automatiquement l’objet.</span><span class="sxs-lookup"><span data-stu-id="c3419-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="c3419-111">Toutefois, l’instruction `using` est utile uniquement pour les objets utilisés dans la portée de la méthode dans laquelle elles sont construites.</span><span class="sxs-lookup"><span data-stu-id="c3419-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>

<span data-ttu-id="c3419-112">L’exemple suivant utilise l’instruction `using` pour créer et libérer un objet <xref:System.IO.StreamReader?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c3419-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

<span data-ttu-id="c3419-113">Bien que la <xref:System.IO.StreamReader> classe implémente l' <xref:System.IDisposable> interface, ce qui indique qu’elle utilise une ressource non managée, l’exemple n’appelle pas explicitement la <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="c3419-113">Although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c3419-114">Quand le compilateur C# ou Visual Basic rencontre l’instruction `using`, il émet en langage intermédiaire qui est équivalent au code suivant contenant explicitement un bloc `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="c3419-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

<span data-ttu-id="c3419-115">L’instruction `using` en C# vous permet d’acquérir plusieurs ressources dans une seule instruction, ce qui équivaut en interne à des instructions `using` imbriquées.</span><span class="sxs-lookup"><span data-stu-id="c3419-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="c3419-116">L'exemple suivant instancie deux objets <xref:System.IO.StreamReader> pour lire le contenu de deux fichiers différents.</span><span class="sxs-lookup"><span data-stu-id="c3419-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="c3419-117">Bloc try/finally</span><span class="sxs-lookup"><span data-stu-id="c3419-117">Try/finally block</span></span>

<span data-ttu-id="c3419-118">Au lieu d’encapsuler un bloc `try/finally` dans une instruction `using`, vous pouvez choisir d’implémenter le bloc `try/finally` directement.</span><span class="sxs-lookup"><span data-stu-id="c3419-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="c3419-119">Il peut s’agir de votre style de codage personnel, ou vous pouvez le faire pour l’une des raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="c3419-119">It may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>

- <span data-ttu-id="c3419-120">Pour inclure un `catch` bloc pour gérer les exceptions levées dans le `try` bloc.</span><span class="sxs-lookup"><span data-stu-id="c3419-120">To include a `catch` block to handle exceptions thrown in the `try` block.</span></span> <span data-ttu-id="c3419-121">Sinon, toutes les exceptions levées dans l' `using` instruction ne sont pas gérées.</span><span class="sxs-lookup"><span data-stu-id="c3419-121">Otherwise, any exceptions thrown within the `using` statement are unhandled.</span></span>

- <span data-ttu-id="c3419-122">Pour instancier un objet qui implémente <xref:System.IDisposable> dont la portée n'est pas locale au bloc dans lequel elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="c3419-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>

<span data-ttu-id="c3419-123">L'exemple suivant est similaire à l'exemple précédent, mais il utilise un bloc `try/catch/finally` pour instancier, utiliser et supprimer un objet <xref:System.IO.StreamReader>, ainsi que pour gérer les exceptions levées par le constructeur <xref:System.IO.StreamReader> et sa méthode <xref:System.IO.StreamReader.ReadToEnd%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3419-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="c3419-124">Le code du `finally` bloc vérifie que l’objet qui implémente <xref:System.IDisposable> n’est pas `null` avant d’appeler la <xref:System.IDisposable.Dispose%2A> méthode.</span><span class="sxs-lookup"><span data-stu-id="c3419-124">The code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="c3419-125">La non-exécution de cette opération peut générer une <xref:System.NullReferenceException> au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="c3419-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

<span data-ttu-id="c3419-126">Vous pouvez suivre ce modèle de base si vous choisissez d’implémenter (ou que vous devez implémenter) un bloc `try/finally`, car votre langage de programmation ne prend pas en charge l’instruction `using`, mais autorise des appels directs à la méthode <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="c3419-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>

## <a name="idisposable-instance-members"></a><span data-ttu-id="c3419-127">Membres d’instance IDisposable</span><span class="sxs-lookup"><span data-stu-id="c3419-127">IDisposable instance members</span></span>

<span data-ttu-id="c3419-128">Si une classe contient une <xref:System.IDisposable> implémentation en tant que membre d’instance, qu’il s’agisse d’un champ ou d’une propriété, la classe doit également implémenter <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="c3419-128">If a class holds an <xref:System.IDisposable> implementation as an instance member, either a field or a property, the class should also implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="c3419-129">Pour plus d’informations, consultez [implémenter une suppression en cascade](implementing-dispose.md#cascade-dispose-calls).</span><span class="sxs-lookup"><span data-stu-id="c3419-129">For more information, see [implement a cascade dispose](implementing-dispose.md#cascade-dispose-calls).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3419-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3419-130">See also</span></span>

- [<span data-ttu-id="c3419-131">Nettoyage de ressources non managées</span><span class="sxs-lookup"><span data-stu-id="c3419-131">Cleaning up unmanaged resources</span></span>](unmanaged.md)
- [<span data-ttu-id="c3419-132">using, instruction (référence C#)</span><span class="sxs-lookup"><span data-stu-id="c3419-132">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="c3419-133">Using, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3419-133">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
