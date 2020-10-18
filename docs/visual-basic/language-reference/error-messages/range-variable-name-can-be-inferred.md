---
title: Le nom de la variable de portée peut être déduit uniquement à partir d’un nom qualifié ou d’un nom simple sans arguments
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: 63990b7d37388057ff2cdb430d29878a1c7b39ba
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162360"
---
# <a name="bc36599-range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="b5667-102">BC36599 : le nom de la variable de portée ne peut être déduit qu’à partir d’un nom simple ou qualifié sans argument</span><span class="sxs-lookup"><span data-stu-id="b5667-102">BC36599: Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="b5667-103">Un élément de programmation qui accepte un ou plusieurs arguments est inclus dans une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="b5667-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="b5667-104">Le compilateur ne peut pas déduire une variable de portée à partir de cet élément de programmation.</span><span class="sxs-lookup"><span data-stu-id="b5667-104">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="b5667-105">**ID d’erreur :** BC36599</span><span class="sxs-lookup"><span data-stu-id="b5667-105">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b5667-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b5667-106">To correct this error</span></span>

<span data-ttu-id="b5667-107">Fournissez un nom de variable explicite pour l’élément de programmation, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b5667-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="b5667-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5667-108">See also</span></span>

- [<span data-ttu-id="b5667-109">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5667-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b5667-110">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="b5667-110">Select Clause</span></span>](../queries/select-clause.md)
