---
title: 'Comment : utiliser des exceptions spécifiques dans un bloc catch'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- try/catch blocks
- catch blocks
ms.assetid: 12af9ff3-8587-4f31-90cf-6c2244e0fdae
ms.openlocfilehash: bf4813e950b034cb807abebfe016c1e34487d594
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828021"
---
# <a name="how-to-use-specific-exceptions-in-a-catch-block"></a><span data-ttu-id="bef5e-102">Utiliser des exceptions spécifiques dans un bloc Catch</span><span class="sxs-lookup"><span data-stu-id="bef5e-102">How to use specific exceptions in a catch block</span></span>

<span data-ttu-id="bef5e-103">En général, il est conseillé en programmation d’intercepter un type d’exception spécifique au lieu d’utiliser une instruction `catch` de base.</span><span class="sxs-lookup"><span data-stu-id="bef5e-103">In general, it's good programming practice to catch a specific type of exception rather than use a basic `catch` statement.</span></span>

<span data-ttu-id="bef5e-104">Quand une exception se produit, elle remonte la pile et chaque bloc catch a la possibilité de la gérer.</span><span class="sxs-lookup"><span data-stu-id="bef5e-104">When an exception occurs, it is passed up the stack and each catch block is given the opportunity to handle it.</span></span> <span data-ttu-id="bef5e-105">L’ordre des instructions catch est important.</span><span class="sxs-lookup"><span data-stu-id="bef5e-105">The order of catch statements is important.</span></span> <span data-ttu-id="bef5e-106">Placez les blocs catch ciblés sur des exceptions spécifiques avant un bloc catch d’exceptions générales, sinon le compilateur peut générer une erreur.</span><span class="sxs-lookup"><span data-stu-id="bef5e-106">Put catch blocks targeted to specific exceptions before a general exception catch block or the compiler might issue an error.</span></span> <span data-ttu-id="bef5e-107">Le bloc catch approprié est déterminé en mettant en correspondance le type de l’exception avec le nom de l’exception spécifiée dans le bloc catch.</span><span class="sxs-lookup"><span data-stu-id="bef5e-107">The proper catch block is determined by matching the type of the exception to the name of the exception specified in the catch block.</span></span> <span data-ttu-id="bef5e-108">S’il n’existe aucun bloc catch spécifique, l’exception est interceptée par un bloc catch général, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="bef5e-108">If there is no specific catch block, the exception is caught by a general catch block, if one exists.</span></span>

<span data-ttu-id="bef5e-109">L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="bef5e-109">The following code example uses a `try`/`catch` block to catch an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="bef5e-110">L’exemple crée une classe appelée `Employee` avec une propriété unique, le niveau de l’employé (`Emlevel`).</span><span class="sxs-lookup"><span data-stu-id="bef5e-110">The sample creates a class called `Employee` with a single property, employee level (`Emlevel`).</span></span> <span data-ttu-id="bef5e-111">Une méthode `PromoteEmployee` prend un objet et incrémente le niveau de l’employé.</span><span class="sxs-lookup"><span data-stu-id="bef5e-111">A method, `PromoteEmployee`, takes an object and increments the employee level.</span></span> <span data-ttu-id="bef5e-112">Une exception <xref:System.InvalidCastException> se produit quand une instance <xref:System.DateTime> est passée à la méthode `PromoteEmployee`.</span><span class="sxs-lookup"><span data-stu-id="bef5e-112">An <xref:System.InvalidCastException> occurs when a <xref:System.DateTime> instance is passed to the `PromoteEmployee` method.</span></span>

[!code-cpp[CatchException#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CatchException/CPP/catchexception1.cpp#2)]
[!code-csharp[CatchException#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception1.cs#2)]
[!code-vb[CatchException#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="bef5e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bef5e-113">See also</span></span>

- [<span data-ttu-id="bef5e-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="bef5e-114">Exceptions</span></span>](index.md)
