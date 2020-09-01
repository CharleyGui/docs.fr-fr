---
description: partial, méthode - Référence C#
title: partial, méthode - Référence C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: d6c433fd30f6ec51355bdefee90d815783487c1b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134378"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="a44dc-103">partial, méthode (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a44dc-103">partial method (C# Reference)</span></span>

<span data-ttu-id="a44dc-104">La signature d’une méthode partielle est définie dans une partie d’un type partiel, tandis que son implémentation est définie dans une autre partie du type.</span><span class="sxs-lookup"><span data-stu-id="a44dc-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="a44dc-105">Les méthodes partielles permettent aux concepteurs de classes de fournir des hooks de méthode, semblables aux gestionnaires d’événements, que les développeurs peuvent décider ou non d’implémenter.</span><span class="sxs-lookup"><span data-stu-id="a44dc-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="a44dc-106">Si le développeur ne fournit pas d’implémentation, le compilateur supprime la signature au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="a44dc-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="a44dc-107">Les méthodes partielles obéissent aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="a44dc-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="a44dc-108">Les signatures des deux parties du type partiel doivent correspondre.</span><span class="sxs-lookup"><span data-stu-id="a44dc-108">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="a44dc-109">La méthode doit retourner void.</span><span class="sxs-lookup"><span data-stu-id="a44dc-109">The method must return void.</span></span>

- <span data-ttu-id="a44dc-110">Aucun modificateur d’accès n’est autorisé.</span><span class="sxs-lookup"><span data-stu-id="a44dc-110">No access modifiers are allowed.</span></span> <span data-ttu-id="a44dc-111">Les méthodes partielles sont implicitement privées.</span><span class="sxs-lookup"><span data-stu-id="a44dc-111">Partial methods are implicitly private.</span></span>

<span data-ttu-id="a44dc-112">L’exemple suivant illustre une méthode partielle définie dans deux parties d’une classe partielle :</span><span class="sxs-lookup"><span data-stu-id="a44dc-112">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="a44dc-113">Pour plus d’informations, consultez la page [Classes et méthodes partielles](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a44dc-113">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a44dc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a44dc-114">See also</span></span>

- [<span data-ttu-id="a44dc-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a44dc-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a44dc-116">type partiel</span><span class="sxs-lookup"><span data-stu-id="a44dc-116">partial type</span></span>](partial-type.md)
