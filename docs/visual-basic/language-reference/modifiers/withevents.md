---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350742"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="dd5a3-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd5a3-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="dd5a3-103">Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd5a3-104">Notes</span><span class="sxs-lookup"><span data-stu-id="dd5a3-104">Remarks</span></span>

<span data-ttu-id="dd5a3-105">Quand une variable est définie à l’aide de `WithEvents`, vous pouvez spécifier de façon déclarative qu’une méthode gère les événements de la variable à l’aide du mot clé `Handles`.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="dd5a3-106">Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou du module.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="dd5a3-107">Cela signifie que le contexte de déclaration pour une variable de `WithEvents` doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="dd5a3-108">Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="dd5a3-109">Vous pouvez déclarer uniquement des variables individuelles, et non des tableaux, avec `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="dd5a3-110">Règles</span><span class="sxs-lookup"><span data-stu-id="dd5a3-110">Rules</span></span>

<span data-ttu-id="dd5a3-111">**Types d’éléments.**</span><span class="sxs-lookup"><span data-stu-id="dd5a3-111">**Element Types.**</span></span> <span data-ttu-id="dd5a3-112">Vous devez déclarer les variables de `WithEvents` comme des variables d’objet afin qu’elles puissent accepter des instances de classe.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="dd5a3-113">Toutefois, vous ne pouvez pas les déclarer en tant que `Object`.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="dd5a3-114">Vous devez les déclarer en tant que classe spécifique qui peut déclencher les événements.</span><span class="sxs-lookup"><span data-stu-id="dd5a3-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="dd5a3-115">Le modificateur de `WithEvents` peut être utilisé dans ce contexte : [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="dd5a3-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="dd5a3-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd5a3-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="dd5a3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd5a3-117">See also</span></span>

- [<span data-ttu-id="dd5a3-118">Handles</span><span class="sxs-lookup"><span data-stu-id="dd5a3-118">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="dd5a3-119">Mots clés</span><span class="sxs-lookup"><span data-stu-id="dd5a3-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="dd5a3-120">Événements</span><span class="sxs-lookup"><span data-stu-id="dd5a3-120">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
