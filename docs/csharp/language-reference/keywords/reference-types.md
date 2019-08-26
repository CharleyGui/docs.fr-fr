---
title: Types référence - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 27aed0a1805c1daf4491a3da26371e3312547a6f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608610"
---
# <a name="reference-types-c-reference"></a><span data-ttu-id="386e9-102">Types référence (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="386e9-102">Reference types (C# Reference)</span></span>

<span data-ttu-id="386e9-103">Il existe deux genres de types en C# : les types référence et les types valeur.</span><span class="sxs-lookup"><span data-stu-id="386e9-103">There are two kinds of types in C#: reference types and value types.</span></span> <span data-ttu-id="386e9-104">Les variables des types référence font référence à leurs données (objets), tandis que les variables des types valeur contiennent directement leurs données.</span><span class="sxs-lookup"><span data-stu-id="386e9-104">Variables of reference types store references to their data (objects), while variables of value types directly contain their data.</span></span> <span data-ttu-id="386e9-105">Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable.</span><span class="sxs-lookup"><span data-stu-id="386e9-105">With reference types, two variables can reference the same object; therefore, operations on one variable can affect the object referenced by the other variable.</span></span> <span data-ttu-id="386e9-106">Avec les types valeur, chaque variable a sa propre copie des données et les opérations sur une variable ne peuvent pas affecter l’autre (sauf pour les variables de paramètre in, ref et out ; consultez les modificateurs de paramètre [in](in-parameter-modifier.md), [ref](ref.md) et [out](out-parameter-modifier.md)).</span><span class="sxs-lookup"><span data-stu-id="386e9-106">With value types, each variable has its own copy of the data, and it is not possible for operations on one variable to affect the other (except in the case of in, ref and out parameter variables; see [in](in-parameter-modifier.md), [ref](ref.md) and [out](out-parameter-modifier.md) parameter modifier).</span></span>

 <span data-ttu-id="386e9-107">Les mots clés suivants sont utilisés pour déclarer des types référence :</span><span class="sxs-lookup"><span data-stu-id="386e9-107">The following keywords are used to declare reference types:</span></span>

- [<span data-ttu-id="386e9-108">class</span><span class="sxs-lookup"><span data-stu-id="386e9-108">class</span></span>](class.md)

- [<span data-ttu-id="386e9-109">interface</span><span class="sxs-lookup"><span data-stu-id="386e9-109">interface</span></span>](interface.md)

- [<span data-ttu-id="386e9-110">delegate</span><span class="sxs-lookup"><span data-stu-id="386e9-110">delegate</span></span>](delegate.md)

 <span data-ttu-id="386e9-111">C# fournit également les types référence intégrés suivants :</span><span class="sxs-lookup"><span data-stu-id="386e9-111">C# also provides the following built-in reference types:</span></span>

- [<span data-ttu-id="386e9-112">dynamic</span><span class="sxs-lookup"><span data-stu-id="386e9-112">dynamic</span></span>](dynamic.md)

- [<span data-ttu-id="386e9-113">object</span><span class="sxs-lookup"><span data-stu-id="386e9-113">object</span></span>](object.md)

- [<span data-ttu-id="386e9-114">string</span><span class="sxs-lookup"><span data-stu-id="386e9-114">string</span></span>](string.md)

## <a name="see-also"></a><span data-ttu-id="386e9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="386e9-115">See also</span></span>

- [<span data-ttu-id="386e9-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="386e9-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="386e9-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="386e9-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="386e9-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="386e9-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="386e9-119">Types</span><span class="sxs-lookup"><span data-stu-id="386e9-119">Types</span></span>](types.md)
- [<span data-ttu-id="386e9-120">Types valeur</span><span class="sxs-lookup"><span data-stu-id="386e9-120">Value Types</span></span>](value-types.md)
