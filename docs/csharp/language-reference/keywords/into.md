---
description: into - Référence C#
title: into - Référence C#
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 4712a6906195c5d8bc09c7b734dba0df4d2b08c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134521"
---
# <a name="into-c-reference"></a><span data-ttu-id="1659e-103">into (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="1659e-103">into (C# Reference)</span></span>

<span data-ttu-id="1659e-104">Le mot clé contextuel `into` permet de créer un identificateur temporaire pour stocker les résultats d’une clause [group](group-clause.md), [join](join-clause.md) ou [select](select-clause.md) dans un nouvel identificateur.</span><span class="sxs-lookup"><span data-stu-id="1659e-104">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="1659e-105">Cet identificateur peut lui-même être un générateur pour d’autres commandes de requête.</span><span class="sxs-lookup"><span data-stu-id="1659e-105">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="1659e-106">Quand il est utilisé dans une clause `group` ou `select`, le nouvel identificateur est parfois appelé *continuation*.</span><span class="sxs-lookup"><span data-stu-id="1659e-106">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="1659e-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1659e-107">Example</span></span>

<span data-ttu-id="1659e-108">L’exemple suivant illustre l’utilisation du mot clé `into` pour activer un identificateur temporaire `fruitGroup` dont le type déduit est `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="1659e-108">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="1659e-109">En utilisant l’identificateur, vous pouvez appeler la méthode <xref:System.Linq.Enumerable.Count%2A> dans chaque groupe et sélectionner uniquement les groupes qui contiennent deux mots ou plus.</span><span class="sxs-lookup"><span data-stu-id="1659e-109">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="1659e-110">L’utilisation de `into` dans une clause `group` n’est nécessaire que si vous voulez effectuer des opérations de requête supplémentaires dans chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="1659e-110">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="1659e-111">Pour plus d’informations, consultez [Group, clause](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1659e-111">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="1659e-112">Pour obtenir un exemple d’utilisation de `into` dans une clause `join`, consultez [join, clause](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="1659e-112">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1659e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1659e-113">See also</span></span>

- [<span data-ttu-id="1659e-114">Mots clés de requête (LINQ)</span><span class="sxs-lookup"><span data-stu-id="1659e-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="1659e-115">LINQ en C#</span><span class="sxs-lookup"><span data-stu-id="1659e-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="1659e-116">group, clause</span><span class="sxs-lookup"><span data-stu-id="1659e-116">group clause</span></span>](group-clause.md)
