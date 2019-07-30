---
title: 'Procédure : Déclarez une variable objet et assignez-lui un objet dans Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630871"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="614ec-102">Procédure : Déclarez une variable objet et assignez-lui un objet dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="614ec-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="614ec-103">Vous déclarez une variable du [type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) en `As Object` spécifiant dans une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="614ec-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="614ec-104">Vous assignez un objet à une telle variable en plaçant l’objet après le signe`=`égal () dans une instruction d’assignation ou une clause d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="614ec-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="614ec-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="614ec-105">Example</span></span>

<span data-ttu-id="614ec-106">L’exemple suivant déclare une `Object` variable et lui assigne l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="614ec-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="614ec-107">Vous pouvez combiner la déclaration et l’assignation en initialisant la variable dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="614ec-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="614ec-108">L’exemple suivant est équivalent à l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="614ec-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="614ec-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="614ec-109">Compiling the Code</span></span>

<span data-ttu-id="614ec-110">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="614ec-110">This example requires:</span></span>

- <span data-ttu-id="614ec-111">une référence à l'espace de noms <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="614ec-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="614ec-112">Classe, structure ou module dans lequel placer l' `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="614ec-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="614ec-113">Procédure dans laquelle placer l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="614ec-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="614ec-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="614ec-114">See also</span></span>

- [<span data-ttu-id="614ec-115">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="614ec-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="614ec-116">Variables objets</span><span class="sxs-lookup"><span data-stu-id="614ec-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="614ec-117">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="614ec-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="614ec-118">Object (type de données)</span><span class="sxs-lookup"><span data-stu-id="614ec-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="614ec-119">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="614ec-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="614ec-120">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="614ec-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="614ec-121">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="614ec-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
