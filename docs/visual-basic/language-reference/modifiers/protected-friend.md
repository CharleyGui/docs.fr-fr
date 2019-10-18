---
title: Ami protégé (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524772"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="8b2b8-102">Ami protégé (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b2b8-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="8b2b8-103">La combinaison de mots clés `Protected Friend` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="8b2b8-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="8b2b8-104">Il confère à l’accès [Friend](friend.md) et à l’accès [protégé](protected.md) sur les éléments déclarés, de sorte qu’ils sont accessibles depuis n’importe où dans le même assembly, à partir de leur propre classe et à partir de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="8b2b8-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="8b2b8-105">Vous pouvez spécifier `Protected Friend` uniquement sur les membres de classes ; vous ne pouvez pas appliquer de `Protected Friend` aux membres d’une structure, car les structures ne peuvent pas être héritées.</span><span class="sxs-lookup"><span data-stu-id="8b2b8-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="8b2b8-106">Dans Visual Studio, la sélection de l’aide F1 sur `protected friend` fournit de l’aide pour [protected](protected.md) ou [Friend](friend.md).</span><span class="sxs-lookup"><span data-stu-id="8b2b8-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="8b2b8-107">L’IDE sélectionne le jeton unique sous le curseur plutôt que le mot composé.</span><span class="sxs-lookup"><span data-stu-id="8b2b8-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="8b2b8-108">Règles</span><span class="sxs-lookup"><span data-stu-id="8b2b8-108">Rules</span></span>

<span data-ttu-id="8b2b8-109">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="8b2b8-109">**Declaration Context.**</span></span> <span data-ttu-id="8b2b8-110">Vous pouvez utiliser `Protected Friend` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="8b2b8-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="8b2b8-111">Cela signifie que le contexte de déclaration pour un élément de `Protected` doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="8b2b8-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b2b8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b2b8-112">See also</span></span>

- [<span data-ttu-id="8b2b8-113">Public</span><span class="sxs-lookup"><span data-stu-id="8b2b8-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="8b2b8-114">Protected</span><span class="sxs-lookup"><span data-stu-id="8b2b8-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="8b2b8-115">Friend</span><span class="sxs-lookup"><span data-stu-id="8b2b8-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="8b2b8-116">Private</span><span class="sxs-lookup"><span data-stu-id="8b2b8-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="8b2b8-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="8b2b8-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="8b2b8-118">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b2b8-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="8b2b8-119">Procédures</span><span class="sxs-lookup"><span data-stu-id="8b2b8-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="8b2b8-120">Structures</span><span class="sxs-lookup"><span data-stu-id="8b2b8-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="8b2b8-121">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="8b2b8-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
