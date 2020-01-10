---
title: 'Comment : déclarer une variable objet et lui assigner un objet'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: eaaeda2a986584e6e1a2e0d2cda3890fb6187598
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344236"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="397b7-102">Comment : déclarer une variable objet et lui affecter un objet dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="397b7-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="397b7-103">Vous déclarez une variable du [type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) en spécifiant `As Object` dans une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="397b7-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="397b7-104">Vous assignez un objet à une telle variable en plaçant l’objet après le signe égal (`=`) dans une instruction d’assignation ou une clause d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="397b7-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="397b7-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="397b7-105">Example</span></span>

<span data-ttu-id="397b7-106">L’exemple suivant déclare une variable `Object` et lui affecte l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="397b7-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="397b7-107">Vous pouvez combiner la déclaration et l’assignation en initialisant la variable dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="397b7-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="397b7-108">L’exemple suivant est équivalent à l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="397b7-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a><span data-ttu-id="397b7-109">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="397b7-109">Compile the code</span></span>

<span data-ttu-id="397b7-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="397b7-110">This example requires:</span></span>

- <span data-ttu-id="397b7-111">une référence à l'espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="397b7-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="397b7-112">Classe, structure ou module dans lequel placer l’instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="397b7-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="397b7-113">Procédure dans laquelle placer l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="397b7-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="397b7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="397b7-114">See also</span></span>

- [<span data-ttu-id="397b7-115">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="397b7-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="397b7-116">Variables objets</span><span class="sxs-lookup"><span data-stu-id="397b7-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="397b7-117">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="397b7-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="397b7-118">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="397b7-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="397b7-119">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="397b7-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="397b7-120">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="397b7-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="397b7-121">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="397b7-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
