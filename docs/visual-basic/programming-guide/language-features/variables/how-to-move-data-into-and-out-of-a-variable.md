---
title: "Comment : placer des données dans et en dehors d'une variable"
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: fe19a6160623aa9ea867becdf7a15b51319abf45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410436"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="139ff-102">Comment : placer des données dans et en dehors d'une variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="139ff-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="139ff-103">Vous stockez une valeur dans une variable en plaçant le nom de la variable sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="139ff-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="139ff-104">Ajout de données dans une variable</span><span class="sxs-lookup"><span data-stu-id="139ff-104">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="139ff-105">Pour stocker une valeur dans une variable</span><span class="sxs-lookup"><span data-stu-id="139ff-105">To store a value in a variable</span></span>

- <span data-ttu-id="139ff-106">Utilisez le nom de la variable sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="139ff-106">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="139ff-107">L’exemple suivant définit la valeur de la variable `alpha` .</span><span class="sxs-lookup"><span data-stu-id="139ff-107">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="139ff-108">La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la variable.</span><span class="sxs-lookup"><span data-stu-id="139ff-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="139ff-109">Obtention de données à partir d’une variable</span><span class="sxs-lookup"><span data-stu-id="139ff-109">Getting Data from a Variable</span></span>

<span data-ttu-id="139ff-110">Vous récupérez la valeur d’une variable en incluant le nom de la variable dans une expression.</span><span class="sxs-lookup"><span data-stu-id="139ff-110">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="139ff-111">Pour récupérer une valeur d’une variable</span><span class="sxs-lookup"><span data-stu-id="139ff-111">To retrieve a value from a variable</span></span>

- <span data-ttu-id="139ff-112">Utilisez le nom de la variable dans une expression.</span><span class="sxs-lookup"><span data-stu-id="139ff-112">Use the variable name in an expression.</span></span> <span data-ttu-id="139ff-113">Vous pouvez utiliser une variable partout où vous pouvez utiliser une constante ou un littéral, sauf dans une expression qui définit la valeur d’une constante.</span><span class="sxs-lookup"><span data-stu-id="139ff-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="139ff-114">\- ou -</span><span class="sxs-lookup"><span data-stu-id="139ff-114">\-or-</span></span>

- <span data-ttu-id="139ff-115">Utilisez le nom de variable après le signe égal ( `=` ) dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="139ff-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="139ff-116">L’exemple suivant lit la valeur de la variable `startValue` , puis utilise la valeur de la variable `counter` dans une expression.</span><span class="sxs-lookup"><span data-stu-id="139ff-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="139ff-117">La valeur de la variable participe à l’expression de la même manière qu’une constante, puis elle est stockée dans la variable ou la propriété à gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="139ff-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="139ff-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="139ff-118">See also</span></span>

- [<span data-ttu-id="139ff-119">Variables</span><span class="sxs-lookup"><span data-stu-id="139ff-119">Variables</span></span>](index.md)
- [<span data-ttu-id="139ff-120">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="139ff-120">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="139ff-121">Variables objets</span><span class="sxs-lookup"><span data-stu-id="139ff-121">Object Variables</span></span>](object-variables.md)
