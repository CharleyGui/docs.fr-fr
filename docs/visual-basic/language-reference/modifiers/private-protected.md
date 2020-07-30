---
title: Private Protected
ms.date: 05/10/2018
f1_keywords:
- vb.PrivateProtected
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 8ad1509da71bc80b33700d363ddd4569a0965dff
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303463"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="1317f-102">Protégé privé (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1317f-102">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="1317f-103">La combinaison de mots clés `Private Protected` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="1317f-103">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="1317f-104">Un `Private Protected` membre est accessible par tous les membres de sa classe conteneur, ainsi que par les types dérivés de la classe conteneur, mais uniquement s’ils sont trouvés dans son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="1317f-104">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="1317f-105">Vous pouvez spécifier `Private Protected` uniquement sur les membres de classes ; vous ne pouvez pas appliquer `Private Protected` aux membres d’une structure, car les structures ne peuvent pas être héritées.</span><span class="sxs-lookup"><span data-stu-id="1317f-105">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="1317f-106">Le `Private Protected` modificateur d’accès est pris en charge par Visual Basic 15,5 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1317f-106">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="1317f-107">Pour l’utiliser, vous pouvez ajouter l’élément suivant à votre fichier projet de Visual Basic ( \* . vbproj).</span><span class="sxs-lookup"><span data-stu-id="1317f-107">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="1317f-108">Tant que Visual Basic 15,5 ou version ultérieure est installé sur votre système, il vous permet de tirer parti de toutes les fonctionnalités de langage prises en charge par la dernière version du compilateur Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="1317f-108">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="1317f-109">Pour plus d’informations, consultez [définition de la version du langage Visual Basic](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="1317f-109">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1317f-110">Dans Visual Studio, la sélection de l’aide F1 dans `private protected` fournit de l’aide pour [privé](private.md) ou [protégé](protected.md).</span><span class="sxs-lookup"><span data-stu-id="1317f-110">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="1317f-111">L’IDE sélectionne le jeton unique sous le curseur plutôt que le mot composé.</span><span class="sxs-lookup"><span data-stu-id="1317f-111">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="1317f-112">Règles</span><span class="sxs-lookup"><span data-stu-id="1317f-112">Rules</span></span>

- <span data-ttu-id="1317f-113">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="1317f-113">**Declaration Context.**</span></span> <span data-ttu-id="1317f-114">Vous pouvez utiliser `Private Protected` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="1317f-114">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="1317f-115">Cela signifie que le contexte de déclaration pour un `Protected` élément doit être une classe et ne peut pas être un fichier source, un espace de noms, une interface, un module, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="1317f-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="1317f-116">Comportement</span><span class="sxs-lookup"><span data-stu-id="1317f-116">Behavior</span></span>

- <span data-ttu-id="1317f-117">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="1317f-117">**Access Level.**</span></span> <span data-ttu-id="1317f-118">Tout le code d’une classe peut accéder à ses éléments.</span><span class="sxs-lookup"><span data-stu-id="1317f-118">All code in a class can access its elements.</span></span> <span data-ttu-id="1317f-119">Le code d’une classe qui dérive d’une classe de base et est contenu dans le même assembly peut accéder à tous les `Private Protected` éléments de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="1317f-119">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="1317f-120">Toutefois, le code d’une classe qui dérive d’une classe de base et qui est contenu dans un assembly différent ne peut pas accéder aux éléments de la classe de base `Private Protected` .</span><span class="sxs-lookup"><span data-stu-id="1317f-120">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="1317f-121">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="1317f-121">**Access Modifiers.**</span></span> <span data-ttu-id="1317f-122">Les mots clés qui spécifient le niveau d’accès sont appelés *modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="1317f-122">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="1317f-123">Pour une comparaison des modificateurs d’accès, consultez [niveaux d’accès dans Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1317f-123">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="1317f-124">Le modificateur `Private Protected` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="1317f-124">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="1317f-125">[Instruction de classe](../statements/class-statement.md) d’une classe imbriquée</span><span class="sxs-lookup"><span data-stu-id="1317f-125">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="1317f-126">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="1317f-126">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="1317f-127">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="1317f-127">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="1317f-128">[Déléguer une instruction](../statements/delegate-statement.md) d’un délégué imbriqué dans une classe</span><span class="sxs-lookup"><span data-stu-id="1317f-128">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="1317f-129">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="1317f-129">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="1317f-130">[Instruction enum](../statements/enum-statement.md) d’une énumération imbriquée dans une classe</span><span class="sxs-lookup"><span data-stu-id="1317f-130">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="1317f-131">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="1317f-131">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="1317f-132">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="1317f-132">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="1317f-133">[Instruction d’interface](../statements/interface-statement.md) d’une interface imbriquée dans une classe</span><span class="sxs-lookup"><span data-stu-id="1317f-133">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="1317f-134">Property Statement</span><span class="sxs-lookup"><span data-stu-id="1317f-134">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="1317f-135">[Instruction de structure](../statements/structure-statement.md) d’une structure imbriquée dans une classe</span><span class="sxs-lookup"><span data-stu-id="1317f-135">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="1317f-136">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="1317f-136">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="1317f-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1317f-137">See also</span></span>

- [<span data-ttu-id="1317f-138">Public</span><span class="sxs-lookup"><span data-stu-id="1317f-138">Public</span></span>](public.md)
- [<span data-ttu-id="1317f-139">Protect</span><span class="sxs-lookup"><span data-stu-id="1317f-139">Protected</span></span>](protected.md)
- [<span data-ttu-id="1317f-140">Contact</span><span class="sxs-lookup"><span data-stu-id="1317f-140">Friend</span></span>](friend.md)
- [<span data-ttu-id="1317f-141">Privé</span><span class="sxs-lookup"><span data-stu-id="1317f-141">Private</span></span>](private.md)
- [<span data-ttu-id="1317f-142">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="1317f-142">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="1317f-143">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1317f-143">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="1317f-144">Procédures</span><span class="sxs-lookup"><span data-stu-id="1317f-144">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="1317f-145">Structures</span><span class="sxs-lookup"><span data-stu-id="1317f-145">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="1317f-146">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="1317f-146">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
