---
description: Types référence - Référence C#
title: Types référence - Référence C#
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 1a9df3c95d6f5052821be8db5ecf5a8ed99a8ba7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137056"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="317a2-103">Types référence (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="317a2-103">Reference types (C# Reference)</span></span>

<span data-ttu-id="317a2-104">Il existe deux genres de types en C# : les types référence et les types valeur.</span><span class="sxs-lookup"><span data-stu-id="317a2-104">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="317a2-105">Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données.</span><span class="sxs-lookup"><span data-stu-id="317a2-105">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="317a2-106">Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable.</span><span class="sxs-lookup"><span data-stu-id="317a2-106">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="317a2-107">Avec les types valeur, chaque variable a sa propre copie des données et les opérations sur une variable ne peuvent pas affecter l’autre (sauf pour les variables de paramètre in, ref et out ; consultez les modificateurs de paramètre [in](in-parameter-modifier.md), [ref](ref.md) et [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="317a2-107">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="317a2-108">Les mots clés suivants sont utilisés pour déclarer des types référence :</span><span class="sxs-lookup"><span data-stu-id="317a2-108">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="317a2-109">class</span><span class="sxs-lookup"><span data-stu-id="317a2-109">class</span></span>](class.md)

- [<span data-ttu-id="317a2-110">interface</span><span class="sxs-lookup"><span data-stu-id="317a2-110">interface</span></span>](interface.md)

- [<span data-ttu-id="317a2-111">delegate</span><span class="sxs-lookup"><span data-stu-id="317a2-111">delegate</span></span>](../builtin-types/reference-types.md)

 <span data-ttu-id="317a2-112">C# fournit également les types référence intégrés suivants :</span><span class="sxs-lookup"><span data-stu-id="317a2-112">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="317a2-113">dynamic</span><span class="sxs-lookup"><span data-stu-id="317a2-113">dynamic</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="317a2-114">object</span><span class="sxs-lookup"><span data-stu-id="317a2-114">object</span></span>](../builtin-types/reference-types.md)

- [<span data-ttu-id="317a2-115">string</span><span class="sxs-lookup"><span data-stu-id="317a2-115">string</span></span>](../builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="317a2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="317a2-116">See also</span></span>

- [<span data-ttu-id="317a2-117">Référence C#</span><span class="sxs-lookup"><span data-stu-id="317a2-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="317a2-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="317a2-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="317a2-119">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="317a2-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="317a2-120">Types de valeur</span><span class="sxs-lookup"><span data-stu-id="317a2-120">Value types</span></span>](../builtin-types/value-types.md)
