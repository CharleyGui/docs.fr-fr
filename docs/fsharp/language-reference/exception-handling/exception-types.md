---
title: Types d'exceptions
description: Découvrez comment définir et utiliser F# des types d’exception.
ms.date: 05/16/2016
ms.openlocfilehash: 8545fab50ff6338d1f1621710a838a200f9ac705
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630317"
---
# <a name="exception-types"></a><span data-ttu-id="3541a-103">Types d'exceptions</span><span class="sxs-lookup"><span data-stu-id="3541a-103">Exception Types</span></span>

<span data-ttu-id="3541a-104">Il existe deux catégories d’exceptions dans F#: les types d’exception F# .net et les types d’exception.</span><span class="sxs-lookup"><span data-stu-id="3541a-104">There are two categories of exceptions in F#: .NET exception types and F# exception types.</span></span> <span data-ttu-id="3541a-105">Cette rubrique explique comment définir et utiliser F# des types d’exception.</span><span class="sxs-lookup"><span data-stu-id="3541a-105">This topic describes how to define and use F# exception types.</span></span>

## <a name="syntax"></a><span data-ttu-id="3541a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3541a-106">Syntax</span></span>

```fsharp
exception exception-type of argument-type
```

## <a name="remarks"></a><span data-ttu-id="3541a-107">Notes</span><span class="sxs-lookup"><span data-stu-id="3541a-107">Remarks</span></span>

<span data-ttu-id="3541a-108">Dans la syntaxe précédente, *exception-type* est le nom d’un nouveau F# type d’exception, et *argument-type* représente le type d’un argument qui peut être fourni lorsque vous levez une exception de ce type.</span><span class="sxs-lookup"><span data-stu-id="3541a-108">In the previous syntax, *exception-type* is the name of a new F# exception type, and *argument-type* represents the type of an argument that can be supplied when you raise an exception of this type.</span></span> <span data-ttu-id="3541a-109">Vous pouvez spécifier plusieurs arguments à l’aide d’un type de tuple pour l' *argument-type*.</span><span class="sxs-lookup"><span data-stu-id="3541a-109">You can specify multiple arguments by using a tuple type for *argument-type*.</span></span>

<span data-ttu-id="3541a-110">Une définition classique d’une F# exception ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="3541a-110">A typical definition for an F# exception resembles the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5501.fs)]

<span data-ttu-id="3541a-111">Vous pouvez générer une exception de ce type à l’aide `raise` de la fonction, comme suit.</span><span class="sxs-lookup"><span data-stu-id="3541a-111">You can generate an exception of this type by using the `raise` function, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5502.fs)]

<span data-ttu-id="3541a-112">Vous pouvez utiliser un F# type d’exception directement dans les filtres d' `try...with` une expression, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3541a-112">You can use an F# exception type directly in the filters in a `try...with` expression, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5503.fs)]

<span data-ttu-id="3541a-113">Le type d’exception que vous définissez avec `exception` le mot F# clé dans est un nouveau type qui hérite de `System.Exception`.</span><span class="sxs-lookup"><span data-stu-id="3541a-113">The exception type that you define with the `exception` keyword in F# is a new type that inherits from `System.Exception`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3541a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3541a-114">See also</span></span>

- [<span data-ttu-id="3541a-115">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="3541a-115">Exception Handling</span></span>](index.md)
- [<span data-ttu-id="3541a-116">Exceptions : fonction `raise`</span><span class="sxs-lookup"><span data-stu-id="3541a-116">Exceptions: the `raise` Function</span></span>](the-raise-function.md)
- [<span data-ttu-id="3541a-117">Hiérarchie des exceptions</span><span class="sxs-lookup"><span data-stu-id="3541a-117">Exception Hierarchy</span></span>](https://msdn.microsoft.com/library/z4c5tckx.aspx)
