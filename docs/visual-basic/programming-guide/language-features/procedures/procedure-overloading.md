---
title: Surcharge de procédure
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: f8accc74fbdd9b1d8cf9bc3d8f6ddd26f73452b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363874"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="d4090-102">Surcharge de procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4090-102">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="d4090-103">La *surcharge* d’une procédure signifie la définir dans plusieurs versions, en utilisant le même nom mais des listes de paramètres différentes.</span><span class="sxs-lookup"><span data-stu-id="d4090-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="d4090-104">L’objectif de la surcharge est de définir plusieurs versions étroitement liées d’une procédure sans avoir à les différencier par nom.</span><span class="sxs-lookup"><span data-stu-id="d4090-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="d4090-105">Pour ce faire, vous devez faire varier la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="d4090-105">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="d4090-106">Surcharge des règles</span><span class="sxs-lookup"><span data-stu-id="d4090-106">Overloading Rules</span></span>

<span data-ttu-id="d4090-107">Lorsque vous surchargez une procédure, les règles suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="d4090-107">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="d4090-108">**Même nom**.</span><span class="sxs-lookup"><span data-stu-id="d4090-108">**Same Name**.</span></span> <span data-ttu-id="d4090-109">Chaque version surchargée doit utiliser le même nom de procédure.</span><span class="sxs-lookup"><span data-stu-id="d4090-109">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="d4090-110">**Signature différente**.</span><span class="sxs-lookup"><span data-stu-id="d4090-110">**Different Signature**.</span></span> <span data-ttu-id="d4090-111">Chaque version surchargée doit être différente de toutes les autres versions surchargées dans au moins l’un des aspects suivants :</span><span class="sxs-lookup"><span data-stu-id="d4090-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="d4090-112">Nombre de paramètres</span><span class="sxs-lookup"><span data-stu-id="d4090-112">Number of parameters</span></span>

  - <span data-ttu-id="d4090-113">Ordre des paramètres</span><span class="sxs-lookup"><span data-stu-id="d4090-113">Order of the parameters</span></span>

  - <span data-ttu-id="d4090-114">Types de données des paramètres</span><span class="sxs-lookup"><span data-stu-id="d4090-114">Data types of the parameters</span></span>

  - <span data-ttu-id="d4090-115">Nombre de paramètres de type (pour une procédure générique)</span><span class="sxs-lookup"><span data-stu-id="d4090-115">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="d4090-116">Type de retour (uniquement pour un opérateur de conversion)</span><span class="sxs-lookup"><span data-stu-id="d4090-116">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="d4090-117">Avec le nom de la procédure, les éléments précédents sont appelés collectivement la *signature* de la procédure.</span><span class="sxs-lookup"><span data-stu-id="d4090-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="d4090-118">Quand vous appelez une procédure surchargée, le compilateur utilise la signature pour vérifier que l’appel correspond correctement à la définition.</span><span class="sxs-lookup"><span data-stu-id="d4090-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="d4090-119">**Éléments ne faisant pas partie de la signature**.</span><span class="sxs-lookup"><span data-stu-id="d4090-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="d4090-120">Vous ne pouvez pas surcharger une procédure sans faire varier la signature.</span><span class="sxs-lookup"><span data-stu-id="d4090-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="d4090-121">En particulier, vous ne pouvez pas surcharger une procédure en faisant varier un ou plusieurs des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d4090-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="d4090-122">Mots clés de modificateur de procédure, tels que `Public` , `Shared` et`Static`</span><span class="sxs-lookup"><span data-stu-id="d4090-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="d4090-123">Noms de paramètre ou de paramètre de type</span><span class="sxs-lookup"><span data-stu-id="d4090-123">Parameter or type parameter names</span></span>

  - <span data-ttu-id="d4090-124">Contraintes de paramètre de type (pour une procédure générique)</span><span class="sxs-lookup"><span data-stu-id="d4090-124">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="d4090-125">Mots clés de modificateur de paramètre, tels que `ByRef` et`Optional`</span><span class="sxs-lookup"><span data-stu-id="d4090-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="d4090-126">Si elle retourne une valeur</span><span class="sxs-lookup"><span data-stu-id="d4090-126">Whether it returns a value</span></span>

  - <span data-ttu-id="d4090-127">Type de données de la valeur de retour (à l’exception d’un opérateur de conversion)</span><span class="sxs-lookup"><span data-stu-id="d4090-127">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="d4090-128">Les éléments de la liste précédente ne font pas partie de la signature.</span><span class="sxs-lookup"><span data-stu-id="d4090-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="d4090-129">Même si vous ne pouvez pas les utiliser pour différencier les versions surchargées, vous pouvez les faire varier parmi les versions surchargées qui sont correctement différenciées par leurs signatures.</span><span class="sxs-lookup"><span data-stu-id="d4090-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="d4090-130">**Arguments à liaison tardive**.</span><span class="sxs-lookup"><span data-stu-id="d4090-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="d4090-131">Si vous envisagez de passer une variable objet à liaison tardive à une version surchargée, vous devez déclarer le paramètre approprié comme <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="d4090-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="d4090-132">Plusieurs versions d’une procédure</span><span class="sxs-lookup"><span data-stu-id="d4090-132">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="d4090-133">Supposons que vous écriviez une `Sub` procédure de publication d’une transaction sur le solde d’un client et que vous souhaitez être en mesure de faire référence au client par son nom ou par son numéro de compte.</span><span class="sxs-lookup"><span data-stu-id="d4090-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="d4090-134">Pour ce faire, vous pouvez définir deux `Sub` procédures différentes, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d4090-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="d4090-135">Versions surchargées</span><span class="sxs-lookup"><span data-stu-id="d4090-135">Overloaded Versions</span></span>

<span data-ttu-id="d4090-136">Une alternative consiste à surcharger un nom de procédure unique.</span><span class="sxs-lookup"><span data-stu-id="d4090-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="d4090-137">Vous pouvez utiliser le mot clé [Overloads](../../../language-reference/modifiers/overloads.md) pour définir une version de la procédure pour chaque liste de paramètres, comme suit :</span><span class="sxs-lookup"><span data-stu-id="d4090-137">You can use the [Overloads](../../../language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="d4090-138">Surcharges supplémentaires</span><span class="sxs-lookup"><span data-stu-id="d4090-138">Additional Overloads</span></span>

<span data-ttu-id="d4090-139">Si vous souhaitez également accepter un montant de transaction dans `Decimal` ou `Single` , vous pouvez effectuer une surcharge supplémentaire `post` pour permettre cette variation.</span><span class="sxs-lookup"><span data-stu-id="d4090-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="d4090-140">Si vous l’avez fait pour chacune des surcharges de l’exemple précédent, vous avez quatre `Sub` procédures, toutes avec le même nom, mais avec quatre signatures différentes.</span><span class="sxs-lookup"><span data-stu-id="d4090-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="d4090-141">Avantages de la surcharge</span><span class="sxs-lookup"><span data-stu-id="d4090-141">Advantages of Overloading</span></span>

<span data-ttu-id="d4090-142">L’avantage de la surcharge d’une procédure est de la flexibilité de l’appel.</span><span class="sxs-lookup"><span data-stu-id="d4090-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="d4090-143">Pour utiliser la `post` procédure déclarée dans l’exemple précédent, le code appelant peut obtenir l’identification du client en tant que `String` ou `Integer` , puis appeler la même procédure dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="d4090-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="d4090-144">L'exemple suivant illustre ce mécanisme :</span><span class="sxs-lookup"><span data-stu-id="d4090-144">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="d4090-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4090-145">See also</span></span>

- [<span data-ttu-id="d4090-146">Procédures</span><span class="sxs-lookup"><span data-stu-id="d4090-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d4090-147">Comment : définir plusieurs versions d'une procédure</span><span class="sxs-lookup"><span data-stu-id="d4090-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="d4090-148">Comment : appeler une procédure surchargée</span><span class="sxs-lookup"><span data-stu-id="d4090-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="d4090-149">Comment : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="d4090-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="d4090-150">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres</span><span class="sxs-lookup"><span data-stu-id="d4090-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="d4090-151">Considérations sur les surcharges de procédures</span><span class="sxs-lookup"><span data-stu-id="d4090-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="d4090-152">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="d4090-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="d4090-153">Surcharges</span><span class="sxs-lookup"><span data-stu-id="d4090-153">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="d4090-154">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4090-154">Generic Types in Visual Basic</span></span>](../data-types/generic-types.md)
