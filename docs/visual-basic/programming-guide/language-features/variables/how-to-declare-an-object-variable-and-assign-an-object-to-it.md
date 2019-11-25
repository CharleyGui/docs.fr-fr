---
title: 'How to: Declare an Object Variable and Assign an Object to It'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 4cfad1d820b584d4610d24c392b14ac3958471b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352902"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="aac04-102">Comment : déclarer une variable objet et lui affecter un objet dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aac04-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="aac04-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="aac04-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="aac04-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span><span class="sxs-lookup"><span data-stu-id="aac04-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="aac04-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="aac04-105">Example</span></span>

<span data-ttu-id="aac04-106">The following example declares an `Object` variable and assigns the current instance to it.</span><span class="sxs-lookup"><span data-stu-id="aac04-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="aac04-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span><span class="sxs-lookup"><span data-stu-id="aac04-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="aac04-108">The following example is equivalent to the preceding example.</span><span class="sxs-lookup"><span data-stu-id="aac04-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="aac04-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="aac04-109">Compiling the Code</span></span>

<span data-ttu-id="aac04-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="aac04-110">This example requires:</span></span>

- <span data-ttu-id="aac04-111">une référence à l'espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="aac04-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="aac04-112">A class, structure, or module in which to put the `Dim` statement.</span><span class="sxs-lookup"><span data-stu-id="aac04-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="aac04-113">A procedure in which to put the assignment statement.</span><span class="sxs-lookup"><span data-stu-id="aac04-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="aac04-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aac04-114">See also</span></span>

- [<span data-ttu-id="aac04-115">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="aac04-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="aac04-116">Variables objets</span><span class="sxs-lookup"><span data-stu-id="aac04-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="aac04-117">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="aac04-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="aac04-118">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="aac04-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="aac04-119">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="aac04-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="aac04-120">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="aac04-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="aac04-121">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="aac04-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
