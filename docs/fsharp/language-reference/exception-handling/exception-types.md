---
title: Types d'exceptions
description: 'Découvrez comment définir et utiliser les types d’exception F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 8b4ceec31a2d68abbcd025812ffeeefc0c090efb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557227"
---
# <a name="exception-types"></a><span data-ttu-id="c701b-103">Types d'exceptions</span><span class="sxs-lookup"><span data-stu-id="c701b-103">Exception Types</span></span>

<span data-ttu-id="c701b-104">Il existe deux catégories d’exceptions en F # : les types d’exception .NET et les types d’exception F #.</span><span class="sxs-lookup"><span data-stu-id="c701b-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="c701b-105">Cette rubrique explique comment définir et utiliser les types d’exception F #.</span><span class="sxs-lookup"><span data-stu-id="c701b-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="c701b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c701b-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="c701b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c701b-107">Remarks</span></span>

<span data-ttu-id="c701b-108">Dans la syntaxe précédente, *exception-type* est le nom d’un nouveau type d’exception F #, et *argument-type* représente le type d’un argument qui peut être fourni lorsque vous levez une exception de ce type.</span><span class="sxs-lookup"><span data-stu-id="c701b-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="c701b-109">Vous pouvez spécifier plusieurs arguments à l’aide d’un type de tuple pour l' *argument-type*.</span><span class="sxs-lookup"><span data-stu-id="c701b-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="c701b-110">Une définition type pour une exception F # ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="c701b-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="c701b-111">Vous pouvez générer une exception de ce type à l’aide de la `raise` fonction, comme suit.</span><span class="sxs-lookup"><span data-stu-id="c701b-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="c701b-112">Vous pouvez utiliser un type d’exception F # directement dans les filtres d’une `try...with` expression, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c701b-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="c701b-113">Le type d’exception que vous définissez avec le `exception` mot clé en F # est un nouveau type qui hérite de `System.Exception` .</span><span class="sxs-lookup"><span data-stu-id="c701b-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c701b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c701b-114">See also</span></span>

- [<span data-ttu-id="c701b-115">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="c701b-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="c701b-116">Exceptions : la `raise` fonction</span><span class="sxs-lookup"><span data-stu-id="c701b-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="c701b-117">Hiérarchie des exceptions</span><span class="sxs-lookup"><span data-stu-id="c701b-117">Exception Hierarchy</span></span>](../../../standard/exceptions/index.md)
