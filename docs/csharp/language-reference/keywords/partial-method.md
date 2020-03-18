---
title: partial, méthode - Référence C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713220"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="1b77a-102">partial, méthode (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1b77a-102">partial method (C# Reference)</span></span>

<span data-ttu-id="1b77a-103">La signature d’une méthode partielle est définie dans une partie d’un type partiel, tandis que son implémentation est définie dans une autre partie du type.</span><span class="sxs-lookup"><span data-stu-id="1b77a-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="1b77a-104">Les méthodes partielles permettent aux concepteurs de classes de fournir des hooks de méthode, semblables aux gestionnaires d’événements, que les développeurs peuvent décider ou non d’implémenter.</span><span class="sxs-lookup"><span data-stu-id="1b77a-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="1b77a-105">Si le développeur ne fournit pas d’implémentation, le compilateur supprime la signature au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="1b77a-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="1b77a-106">Les méthodes partielles obéissent aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="1b77a-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="1b77a-107">Les signatures des deux parties du type partiel doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="1b77a-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="1b77a-108">La méthode doit retourner void.</span><span class="sxs-lookup"><span data-stu-id="1b77a-108">The method must return void.</span></span>

- <span data-ttu-id="1b77a-109">Aucun modificateur d’accès n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="1b77a-109">No access modifiers are allowed.</span></span> <span data-ttu-id="1b77a-110">Les méthodes partielles sont implicitement privées.</span><span class="sxs-lookup"><span data-stu-id="1b77a-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="1b77a-111">L’exemple suivant illustre une méthode partielle définie dans deux parties d’une classe partielle :</span><span class="sxs-lookup"><span data-stu-id="1b77a-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="1b77a-112">Pour plus d’informations, consultez la page [Classes et méthodes partielles](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="1b77a-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1b77a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b77a-113">See also</span></span>

- [<span data-ttu-id="1b77a-114">Référence C</span><span class="sxs-lookup"><span data-stu-id="1b77a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1b77a-115">type partiel</span><span class="sxs-lookup"><span data-stu-id="1b77a-115">partial type</span></span>](partial-type.md)
