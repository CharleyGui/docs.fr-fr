---
title: Overloads (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: 838207fe3ac5b8f57d030617546b9b7fa25dc939
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663539"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="7dd07-102">Overloads (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dd07-102">Overloads (Visual Basic)</span></span>

<span data-ttu-id="7dd07-103">Spécifie qu'une propriété ou une procédure redéclare une ou plusieurs propriétés ou procédures existantes avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="7dd07-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7dd07-104">Notes</span><span class="sxs-lookup"><span data-stu-id="7dd07-104">Remarks</span></span>

<span data-ttu-id="7dd07-105">*La surcharge* consiste à fournir plusieurs définitions pour un nom de propriété ou procédure donné dans la même portée.</span><span class="sxs-lookup"><span data-stu-id="7dd07-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="7dd07-106">La redéclaration d’une propriété ou procédure avec une signature différente est parfois appelée *masquage par signature*.</span><span class="sxs-lookup"><span data-stu-id="7dd07-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>

## <a name="rules"></a><span data-ttu-id="7dd07-107">Règles</span><span class="sxs-lookup"><span data-stu-id="7dd07-107">Rules</span></span>

- <span data-ttu-id="7dd07-108">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="7dd07-108">**Declaration Context.**</span></span> <span data-ttu-id="7dd07-109">Vous pouvez utiliser `Overloads` uniquement dans une instruction de déclaration de propriété ou de procédure.</span><span class="sxs-lookup"><span data-stu-id="7dd07-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>

- <span data-ttu-id="7dd07-110">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="7dd07-110">**Combined Modifiers.**</span></span> <span data-ttu-id="7dd07-111">Vous ne pouvez pas spécifier `Overloads` avec [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) dans la même déclaration de procédure.</span><span class="sxs-lookup"><span data-stu-id="7dd07-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>

- <span data-ttu-id="7dd07-112">**Différences requises.**</span><span class="sxs-lookup"><span data-stu-id="7dd07-112">**Required Differences.**</span></span> <span data-ttu-id="7dd07-113">Le *signature* dans cette déclaration doit être différente de la signature de chaque propriété ou procédure qu’elle surcharge.</span><span class="sxs-lookup"><span data-stu-id="7dd07-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="7dd07-114">La signature comprend le nom de la propriété ou de la procédure ainsi que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="7dd07-114">The signature comprises the property or procedure name together with the following:</span></span>

  - <span data-ttu-id="7dd07-115">le nombre de paramètres</span><span class="sxs-lookup"><span data-stu-id="7dd07-115">the number of parameters</span></span>

  - <span data-ttu-id="7dd07-116">l'ordre des paramètres</span><span class="sxs-lookup"><span data-stu-id="7dd07-116">the order of the parameters</span></span>

  - <span data-ttu-id="7dd07-117">les types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="7dd07-117">the data types of the parameters</span></span>

  - <span data-ttu-id="7dd07-118">le nombre de paramètres de type (pour une procédure générique)</span><span class="sxs-lookup"><span data-stu-id="7dd07-118">the number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="7dd07-119">le type de retour (uniquement pour une procédure d'opérateur de conversion)</span><span class="sxs-lookup"><span data-stu-id="7dd07-119">the return type (only for a conversion operator procedure)</span></span>

  <span data-ttu-id="7dd07-120">Toutes les surcharges doivent avoir le même nom, mais chacune doit différer de toutes les autres à l'égard d'une ou de plusieurs des raisons ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="7dd07-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="7dd07-121">Cela permet au compilateur de distinguer la version à utiliser quand le code appelle la propriété ou la procédure.</span><span class="sxs-lookup"><span data-stu-id="7dd07-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>

- <span data-ttu-id="7dd07-122">**Différences interdites.**</span><span class="sxs-lookup"><span data-stu-id="7dd07-122">**Disallowed Differences.**</span></span> <span data-ttu-id="7dd07-123">La modification d'un ou de plusieurs des éléments suivants n'est pas valide pour la surcharge d'une propriété ou d'une procédure, parce qu'elles ne font pas partie de la signature :</span><span class="sxs-lookup"><span data-stu-id="7dd07-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>

  - <span data-ttu-id="7dd07-124">elle retourne ou non une valeur (pour une procédure)</span><span class="sxs-lookup"><span data-stu-id="7dd07-124">whether or not it returns a value (for a procedure)</span></span>

  - <span data-ttu-id="7dd07-125">le type de données de la valeur de retour (sauf pour un opérateur de conversion)</span><span class="sxs-lookup"><span data-stu-id="7dd07-125">the data type of the return value (except for a conversion operator)</span></span>

  - <span data-ttu-id="7dd07-126">les noms des paramètres ou des paramètres de type</span><span class="sxs-lookup"><span data-stu-id="7dd07-126">the names of the parameters or type parameters</span></span>

  - <span data-ttu-id="7dd07-127">les contraintes sur les paramètres de type (pour une procédure générique)</span><span class="sxs-lookup"><span data-stu-id="7dd07-127">the constraints on the type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="7dd07-128">les mots clés de modificateur de paramètre (tels que `ByRef` ou `Optional`)</span><span class="sxs-lookup"><span data-stu-id="7dd07-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>

  - <span data-ttu-id="7dd07-129">les mots clés de modificateur de propriété ou de procédure (tels que `Public` ou `Shared`)</span><span class="sxs-lookup"><span data-stu-id="7dd07-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>

- <span data-ttu-id="7dd07-130">**Modificateur facultatif.**</span><span class="sxs-lookup"><span data-stu-id="7dd07-130">**Optional Modifier.**</span></span> <span data-ttu-id="7dd07-131">Vous n'êtes pas tenu d'utiliser le modificateur `Overloads` quand vous définissez plusieurs propriétés ou procédures surchargées dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="7dd07-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="7dd07-132">Toutefois, si vous utilisez `Overloads` dans l'une des déclarations, vous devez l'utiliser dans toutes.</span><span class="sxs-lookup"><span data-stu-id="7dd07-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>

- <span data-ttu-id="7dd07-133">**Occultation et surcharge.**</span><span class="sxs-lookup"><span data-stu-id="7dd07-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="7dd07-134">`Overloads` peut également être utilisé pour occulter un membre existant, ou un ensemble de membres surchargés, dans une classe de base.</span><span class="sxs-lookup"><span data-stu-id="7dd07-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="7dd07-135">Quand vous utilisez `Overloads` de cette façon, vous déclarez la propriété ou la méthode avec le même nom et la même liste de paramètres que le membre de classe de base, et vous ne spécifiez pas le mot clé `Shadows`.</span><span class="sxs-lookup"><span data-stu-id="7dd07-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>

<span data-ttu-id="7dd07-136">Si vous utilisez `Overrides`, le compilateur ajoute implicitement `Overloads` afin que vos API de bibliothèque fonctionnent plus facilement avec C#.</span><span class="sxs-lookup"><span data-stu-id="7dd07-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>

<span data-ttu-id="7dd07-137">Le modificateur `Overloads` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="7dd07-137">The `Overloads` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="7dd07-138">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="7dd07-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="7dd07-139">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="7dd07-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)

- [<span data-ttu-id="7dd07-140">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="7dd07-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="7dd07-141">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="7dd07-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="7dd07-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dd07-142">See also</span></span>

- [<span data-ttu-id="7dd07-143">Shadows</span><span class="sxs-lookup"><span data-stu-id="7dd07-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="7dd07-144">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="7dd07-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="7dd07-145">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7dd07-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="7dd07-146">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="7dd07-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="7dd07-147">Guide pratique pour Définir un opérateur de Conversion</span><span class="sxs-lookup"><span data-stu-id="7dd07-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
