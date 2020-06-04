---
title: 'Guide pratique : déclarer une variable objet et lui affecter un objet'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410501"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="aae21-102">Comment : déclarer une variable objet et lui affecter un objet dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aae21-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="aae21-103">Vous déclarez une variable du [type de données Object](../../../language-reference/data-types/object-data-type.md) en spécifiant `As Object` dans une [instruction Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aae21-103">You declare a variable of the [Object Data Type](../../../language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="aae21-104">Vous assignez un objet à une telle variable en plaçant l’objet après le signe égal ( `=` ) dans une instruction d’assignation ou une clause d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="aae21-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="aae21-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="aae21-105">Example</span></span>

<span data-ttu-id="aae21-106">L’exemple suivant déclare une `Object` variable et lui assigne l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="aae21-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="aae21-107">Vous pouvez combiner la déclaration et l’assignation en initialisant la variable dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="aae21-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="aae21-108">L’exemple suivant est équivalent à l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="aae21-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="aae21-109">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="aae21-109">Compile the code</span></span>

<span data-ttu-id="aae21-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="aae21-110">This example requires:</span></span>

- <span data-ttu-id="aae21-111">une référence à l'espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="aae21-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="aae21-112">Classe, structure ou module dans lequel placer l' `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="aae21-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="aae21-113">Procédure dans laquelle placer l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="aae21-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="aae21-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aae21-114">See also</span></span>

- [<span data-ttu-id="aae21-115">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="aae21-115">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="aae21-116">Variables objets</span><span class="sxs-lookup"><span data-stu-id="aae21-116">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="aae21-117">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="aae21-117">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="aae21-118">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="aae21-118">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="aae21-119">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="aae21-119">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="aae21-120">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="aae21-120">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="aae21-121">Option Strict Statement</span><span class="sxs-lookup"><span data-stu-id="aae21-121">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
