---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 202d4f4a3a05a64ab1d74621268f28f6b55e8952
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404834"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="72d90-102">Ami protégé (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72d90-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="72d90-103">La combinaison de mots clés `Protected Friend` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="72d90-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="72d90-104">Il confère à l’accès [Friend](friend.md) et à l’accès [protégé](protected.md) sur les éléments déclarés, de sorte qu’ils sont accessibles depuis n’importe où dans le même assembly, à partir de leur propre classe et à partir de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="72d90-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="72d90-105">Vous pouvez spécifier `Protected Friend` uniquement sur les membres de classes ; vous ne pouvez pas appliquer `Protected Friend` aux membres d’une structure, car les structures ne peuvent pas être héritées.</span><span class="sxs-lookup"><span data-stu-id="72d90-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="72d90-106">Dans Visual Studio, la sélection de l’aide F1 dans `protected friend` fournit de l’aide pour [protected](protected.md) ou [Friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="72d90-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="72d90-107">L’IDE sélectionne le jeton unique sous le curseur plutôt que le mot composé.</span><span class="sxs-lookup"><span data-stu-id="72d90-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="72d90-108">Règles</span><span class="sxs-lookup"><span data-stu-id="72d90-108">Rules</span></span>

<span data-ttu-id="72d90-109">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="72d90-109">**Declaration Context.**</span></span> <span data-ttu-id="72d90-110">Vous pouvez utiliser `Protected Friend` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="72d90-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="72d90-111">Cela signifie que le contexte de déclaration pour un `Protected` élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="72d90-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="72d90-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72d90-112">See also</span></span>

- [<span data-ttu-id="72d90-113">Public</span><span class="sxs-lookup"><span data-stu-id="72d90-113">Public</span></span>](public.md)
- [<span data-ttu-id="72d90-114">Protect</span><span class="sxs-lookup"><span data-stu-id="72d90-114">Protected</span></span>](protected.md)
- [<span data-ttu-id="72d90-115">Contact</span><span class="sxs-lookup"><span data-stu-id="72d90-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="72d90-116">Privé</span><span class="sxs-lookup"><span data-stu-id="72d90-116">Private</span></span>](private.md)
- [<span data-ttu-id="72d90-117">Protégé privé</span><span class="sxs-lookup"><span data-stu-id="72d90-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="72d90-118">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72d90-118">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="72d90-119">Procédures</span><span class="sxs-lookup"><span data-stu-id="72d90-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="72d90-120">Structures</span><span class="sxs-lookup"><span data-stu-id="72d90-120">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="72d90-121">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="72d90-121">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
