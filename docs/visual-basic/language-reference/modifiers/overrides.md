---
title: Overrides
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351385"
---
# <a name="overrides-visual-basic"></a><span data-ttu-id="1fe16-102">Overrides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fe16-102">Overrides (Visual Basic)</span></span>

<span data-ttu-id="1fe16-103">Spécifie qu'une propriété ou procédure substitue une propriété ou procédure ayant un nom identique et ayant été héritée d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="1fe16-103">Specifies that a property or procedure overrides an identically named property or procedure inherited from a base class.</span></span>

## <a name="rules"></a><span data-ttu-id="1fe16-104">Règles</span><span class="sxs-lookup"><span data-stu-id="1fe16-104">Rules</span></span>

- <span data-ttu-id="1fe16-105">**Declaration Context.**</span><span class="sxs-lookup"><span data-stu-id="1fe16-105">**Declaration Context.**</span></span> <span data-ttu-id="1fe16-106">You can use `Overrides` only in a property or procedure declaration statement.</span><span class="sxs-lookup"><span data-stu-id="1fe16-106">You can use `Overrides` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="1fe16-107">**Combined Modifiers.**</span><span class="sxs-lookup"><span data-stu-id="1fe16-107">**Combined Modifiers.**</span></span> <span data-ttu-id="1fe16-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span><span class="sxs-lookup"><span data-stu-id="1fe16-108">You cannot specify `Overrides` together with `Shadows` or `Shared` in the same declaration.</span></span> <span data-ttu-id="1fe16-109">Comme un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="1fe16-109">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>

- <span data-ttu-id="1fe16-110">**Matching Signatures.**</span><span class="sxs-lookup"><span data-stu-id="1fe16-110">**Matching Signatures.**</span></span> <span data-ttu-id="1fe16-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span><span class="sxs-lookup"><span data-stu-id="1fe16-111">The signature of this declaration must exactly match the *signature* of the property or procedure that it overrides.</span></span> <span data-ttu-id="1fe16-112">Cela signifie que les listes de paramètres doivent avoir le même nombre de paramètres, dans le même ordre, avec les mêmes types de données.</span><span class="sxs-lookup"><span data-stu-id="1fe16-112">This means the parameter lists must have the same number of parameters, in the same order, with the same data types.</span></span>

  <span data-ttu-id="1fe16-113">Outre la signature, la déclaration de substitution doit également correspondre exactement à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="1fe16-113">In addition to the signature, the overriding declaration must also exactly match the following:</span></span>

  - <span data-ttu-id="1fe16-114">Niveau d'accès</span><span class="sxs-lookup"><span data-stu-id="1fe16-114">The access level</span></span>

  - <span data-ttu-id="1fe16-115">Type de retour, le cas échéant</span><span class="sxs-lookup"><span data-stu-id="1fe16-115">The return type, if any</span></span>

- <span data-ttu-id="1fe16-116">**Generic Signatures.**</span><span class="sxs-lookup"><span data-stu-id="1fe16-116">**Generic Signatures.**</span></span> <span data-ttu-id="1fe16-117">Pour une procédure générique, la signature inclut le nombre de paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="1fe16-117">For a generic procedure, the signature includes the number of type parameters.</span></span> <span data-ttu-id="1fe16-118">Par conséquent, la déclaration de substitution doit correspondre à la version de la classe de base également selon ce critère.</span><span class="sxs-lookup"><span data-stu-id="1fe16-118">Therefore, the overriding declaration must match the base class version in that respect as well.</span></span>

- <span data-ttu-id="1fe16-119">**Additional Matching.**</span><span class="sxs-lookup"><span data-stu-id="1fe16-119">**Additional Matching.**</span></span> <span data-ttu-id="1fe16-120">Cette déclaration doit non seulement correspondre à la signature de la version de la classe de base, mais aussi lui correspondre selon les critères suivants :</span><span class="sxs-lookup"><span data-stu-id="1fe16-120">In addition to matching the signature of the base class version, this declaration must also match it in the following respects:</span></span>

  - <span data-ttu-id="1fe16-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span><span class="sxs-lookup"><span data-stu-id="1fe16-121">Access-level modifier (such as [Public](../../../visual-basic/language-reference/modifiers/public.md))</span></span>

  - <span data-ttu-id="1fe16-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span><span class="sxs-lookup"><span data-stu-id="1fe16-122">Passing mechanism of each parameter ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))</span></span>

  - <span data-ttu-id="1fe16-123">Listes de contraintes pour chaque paramètre de type d'une procédure générique</span><span class="sxs-lookup"><span data-stu-id="1fe16-123">Constraint lists on each type parameter of a generic procedure</span></span>

- <span data-ttu-id="1fe16-124">**Shadowing and Overriding.**</span><span class="sxs-lookup"><span data-stu-id="1fe16-124">**Shadowing and Overriding.**</span></span> <span data-ttu-id="1fe16-125">L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="1fe16-125">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="1fe16-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="1fe16-126">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>

<span data-ttu-id="1fe16-127">Si vous utilisez `Overrides`, le compilateur ajoute implicitement `Overloads` afin que vos API de bibliothèque fonctionnent plus facilement avec C#.</span><span class="sxs-lookup"><span data-stu-id="1fe16-127">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="1fe16-128">Le modificateur `Overrides` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="1fe16-128">The `Overrides` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="1fe16-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="1fe16-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="1fe16-130">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="1fe16-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="1fe16-131">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="1fe16-131">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="1fe16-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fe16-132">See also</span></span>

- [<span data-ttu-id="1fe16-133">MustOverride</span><span class="sxs-lookup"><span data-stu-id="1fe16-133">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="1fe16-134">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="1fe16-134">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="1fe16-135">Overridable</span><span class="sxs-lookup"><span data-stu-id="1fe16-135">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="1fe16-136">Mots clés</span><span class="sxs-lookup"><span data-stu-id="1fe16-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="1fe16-137">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fe16-137">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="1fe16-138">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fe16-138">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="1fe16-139">Liste de types</span><span class="sxs-lookup"><span data-stu-id="1fe16-139">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
