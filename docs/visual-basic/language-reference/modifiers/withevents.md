---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 48261e27de302c1809c9725e6e2fc0705a803930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386774"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="edd30-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edd30-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="edd30-103">Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.</span><span class="sxs-lookup"><span data-stu-id="edd30-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="edd30-104">Notes</span><span class="sxs-lookup"><span data-stu-id="edd30-104">Remarks</span></span>

<span data-ttu-id="edd30-105">Quand une variable est définie à l’aide `WithEvents` de, vous pouvez spécifier de façon déclarative qu’une méthode gère les événements de la variable à l’aide du `Handles` mot clé.</span><span class="sxs-lookup"><span data-stu-id="edd30-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="edd30-106">Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou du module.</span><span class="sxs-lookup"><span data-stu-id="edd30-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="edd30-107">Cela signifie que le contexte de déclaration pour une `WithEvents` variable doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="edd30-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="edd30-108">Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.</span><span class="sxs-lookup"><span data-stu-id="edd30-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="edd30-109">Vous pouvez déclarer uniquement des variables individuelles, et non des tableaux, avec `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="edd30-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="edd30-110">Règles</span><span class="sxs-lookup"><span data-stu-id="edd30-110">Rules</span></span>

<span data-ttu-id="edd30-111">**Types d’éléments.**</span><span class="sxs-lookup"><span data-stu-id="edd30-111">**Element Types.**</span></span> <span data-ttu-id="edd30-112">Vous devez déclarer des `WithEvents` variables en tant que variables d’objet afin qu’elles puissent accepter des instances de classe.</span><span class="sxs-lookup"><span data-stu-id="edd30-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="edd30-113">Toutefois, vous ne pouvez pas les déclarer en tant que `Object` .</span><span class="sxs-lookup"><span data-stu-id="edd30-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="edd30-114">Vous devez les déclarer en tant que classe spécifique qui peut déclencher les événements.</span><span class="sxs-lookup"><span data-stu-id="edd30-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="edd30-115">Le `WithEvents` modificateur peut être utilisé dans ce contexte : [instruction Dim](../statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="edd30-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="edd30-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="edd30-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="edd30-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edd30-117">See also</span></span>

- [<span data-ttu-id="edd30-118">Poignées</span><span class="sxs-lookup"><span data-stu-id="edd30-118">Handles</span></span>](../statements/handles-clause.md)
- [<span data-ttu-id="edd30-119">Mots clés</span><span class="sxs-lookup"><span data-stu-id="edd30-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="edd30-120">Événements</span><span class="sxs-lookup"><span data-stu-id="edd30-120">Events</span></span>](../../programming-guide/language-features/events/index.md)
