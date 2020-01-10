---
title: partial, méthode - Référence C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713220"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="74e37-102">partial, méthode (référence C#)</span><span class="sxs-lookup"><span data-stu-id="74e37-102">partial method (C# Reference)</span></span>

<span data-ttu-id="74e37-103">La signature d’une méthode partielle est définie dans une partie d’un type partiel, tandis que son implémentation est définie dans une autre partie du type.</span><span class="sxs-lookup"><span data-stu-id="74e37-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="74e37-104">Les méthodes partielles permettent aux concepteurs de classes de fournir des hooks de méthode, semblables aux gestionnaires d’événements, que les développeurs peuvent décider ou non d’implémenter.</span><span class="sxs-lookup"><span data-stu-id="74e37-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="74e37-105">Si le développeur ne fournit pas d’implémentation, le compilateur supprime la signature au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="74e37-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="74e37-106">Les méthodes partielles obéissent aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="74e37-106">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="74e37-107">Les signatures des deux parties du type partiel doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="74e37-107">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="74e37-108">La méthode doit retourner void.</span><span class="sxs-lookup"><span data-stu-id="74e37-108">The method must return void.</span></span>

- <span data-ttu-id="74e37-109">Aucun modificateur d’accès n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="74e37-109">No access modifiers are allowed.</span></span> <span data-ttu-id="74e37-110">Les méthodes partielles sont implicitement privées.</span><span class="sxs-lookup"><span data-stu-id="74e37-110">Partial methods are implicitly private.</span></span>

<span data-ttu-id="74e37-111">L’exemple suivant illustre une méthode partielle définie dans deux parties d’une classe partielle :</span><span class="sxs-lookup"><span data-stu-id="74e37-111">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="74e37-112">Pour plus d’informations, consultez [Classes et méthodes partielles](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="74e37-112">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74e37-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74e37-113">See also</span></span>

- [<span data-ttu-id="74e37-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="74e37-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="74e37-115">partial, type</span><span class="sxs-lookup"><span data-stu-id="74e37-115">partial type</span></span>](partial-type.md)
