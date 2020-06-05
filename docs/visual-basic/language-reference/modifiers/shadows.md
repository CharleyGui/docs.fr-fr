---
title: Shadows
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402705"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="37e9a-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37e9a-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="37e9a-103">Spécifie qu’un élément de programmation déclaré redéclare et masque un élément portant le même nom, ou un ensemble d’éléments surchargés, dans une classe de base.</span><span class="sxs-lookup"><span data-stu-id="37e9a-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="37e9a-104">Notes</span><span class="sxs-lookup"><span data-stu-id="37e9a-104">Remarks</span></span>

<span data-ttu-id="37e9a-105">L’objectif principal de l’occultation (qui est également connu sous le *nom de masquage par nom*) consiste à conserver la définition de vos membres de classe.</span><span class="sxs-lookup"><span data-stu-id="37e9a-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="37e9a-106">La classe de base peut subir une modification qui crée un élément avec le même nom que celui que vous avez déjà défini.</span><span class="sxs-lookup"><span data-stu-id="37e9a-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="37e9a-107">Dans ce cas, le `Shadows` modificateur force les références via votre classe à être résolues vers le membre que vous avez défini, et non vers le nouvel élément de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="37e9a-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="37e9a-108">L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="37e9a-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="37e9a-109">Pour plus d’informations, consultez [occultation dans Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="37e9a-109">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="37e9a-110">Règles</span><span class="sxs-lookup"><span data-stu-id="37e9a-110">Rules</span></span>

- <span data-ttu-id="37e9a-111">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="37e9a-111">**Declaration Context.**</span></span> <span data-ttu-id="37e9a-112">Vous pouvez utiliser `Shadows` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="37e9a-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="37e9a-113">Cela signifie que le contexte de déclaration pour un `Shadows` élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="37e9a-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="37e9a-114">Vous pouvez déclarer un seul élément d’occultation dans une instruction de déclaration unique.</span><span class="sxs-lookup"><span data-stu-id="37e9a-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="37e9a-115">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="37e9a-115">**Combined Modifiers.**</span></span> <span data-ttu-id="37e9a-116">Vous ne pouvez pas spécifier `Shadows` avec `Overloads` , `Overrides` ou `Static` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="37e9a-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="37e9a-117">**Types d’éléments.**</span><span class="sxs-lookup"><span data-stu-id="37e9a-117">**Element Types.**</span></span> <span data-ttu-id="37e9a-118">Vous pouvez occulter tout type d'élément déclaré par un autre type.</span><span class="sxs-lookup"><span data-stu-id="37e9a-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="37e9a-119">Si vous occultez une propriété ou une procédure avec une autre propriété ou procédure, il n’est pas nécessaire que les paramètres et le type de retour correspondent à ceux de la procédure ou de la propriété de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="37e9a-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="37e9a-120">**L’accès à.**</span><span class="sxs-lookup"><span data-stu-id="37e9a-120">**Accessing.**</span></span> <span data-ttu-id="37e9a-121">L’élément occulté dans la classe de base est normalement indisponible à partir de la classe dérivée qui l’occulte.</span><span class="sxs-lookup"><span data-stu-id="37e9a-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="37e9a-122">Toutefois, les considérations suivantes s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="37e9a-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="37e9a-123">Si l’élément d’occultation n’est pas accessible à partir du code qui y fait référence, la référence est résolue en élément occulté.</span><span class="sxs-lookup"><span data-stu-id="37e9a-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="37e9a-124">Par exemple, si un `Private` élément occulte un élément de classe de base, le code qui n’a pas l’autorisation d’accéder à l' `Private` élément accède à l’élément de classe de base à la place.</span><span class="sxs-lookup"><span data-stu-id="37e9a-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="37e9a-125">Si vous occultez un élément, vous pouvez toujours accéder à l’élément occulté à l’aide d’un objet déclaré avec le type de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="37e9a-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="37e9a-126">Vous pouvez également y accéder via `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="37e9a-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="37e9a-127">Le modificateur `Shadows` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="37e9a-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="37e9a-128">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="37e9a-128">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="37e9a-129">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="37e9a-129">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="37e9a-130">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="37e9a-130">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="37e9a-131">Delegate, instruction</span><span class="sxs-lookup"><span data-stu-id="37e9a-131">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="37e9a-132">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="37e9a-132">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="37e9a-133">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="37e9a-133">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="37e9a-134">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="37e9a-134">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="37e9a-135">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="37e9a-135">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="37e9a-136">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="37e9a-136">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="37e9a-137">Property Statement</span><span class="sxs-lookup"><span data-stu-id="37e9a-137">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="37e9a-138">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="37e9a-138">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="37e9a-139">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="37e9a-139">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="37e9a-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37e9a-140">See also</span></span>

- [<span data-ttu-id="37e9a-141">Partagé</span><span class="sxs-lookup"><span data-stu-id="37e9a-141">Shared</span></span>](shared.md)
- [<span data-ttu-id="37e9a-142">Statique</span><span class="sxs-lookup"><span data-stu-id="37e9a-142">Static</span></span>](static.md)
- [<span data-ttu-id="37e9a-143">Privé</span><span class="sxs-lookup"><span data-stu-id="37e9a-143">Private</span></span>](private.md)
- [<span data-ttu-id="37e9a-144">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="37e9a-144">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="37e9a-145">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="37e9a-145">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="37e9a-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="37e9a-146">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="37e9a-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="37e9a-147">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="37e9a-148">Surcharges</span><span class="sxs-lookup"><span data-stu-id="37e9a-148">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="37e9a-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="37e9a-149">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="37e9a-150">Remplacements</span><span class="sxs-lookup"><span data-stu-id="37e9a-150">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="37e9a-151">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="37e9a-151">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
