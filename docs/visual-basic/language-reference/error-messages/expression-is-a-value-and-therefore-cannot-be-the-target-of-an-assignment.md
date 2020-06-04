---
title: Cette expression est une valeur et ne peut donc pas être la cible d'une assignation
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 9e4dbaf2f2800454c673cd58ddec4cf0f6e5c6b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409505"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="dff35-102">Cette expression est une valeur et ne peut donc pas être la cible d'une assignation</span><span class="sxs-lookup"><span data-stu-id="dff35-102">Expression is a value and therefore cannot be the target of an assignment</span></span>

<span data-ttu-id="dff35-103">Une instruction tente d’affecter une valeur à une expression.</span><span class="sxs-lookup"><span data-stu-id="dff35-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="dff35-104">Vous pouvez assigner une valeur uniquement à une variable, une propriété ou un élément de tableau accessible en écriture au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dff35-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="dff35-105">L’exemple suivant illustre la façon dont cette erreur peut se produire.</span><span class="sxs-lookup"><span data-stu-id="dff35-105">The following example illustrates how this error can occur.</span></span>

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

<span data-ttu-id="dff35-106">Des exemples similaires peuvent s’appliquer aux propriétés et aux éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="dff35-106">Similar examples could apply to properties and array elements.</span></span>

<span data-ttu-id="dff35-107">**Accès indirect.**</span><span class="sxs-lookup"><span data-stu-id="dff35-107">**Indirect Access.**</span></span> <span data-ttu-id="dff35-108">L’accès indirect via un type valeur peut également générer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="dff35-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="dff35-109">Prenons l’exemple de code suivant, qui tente de définir la valeur de <xref:System.Drawing.Point> en y accédant indirectement par le biais de <xref:System.Windows.Forms.Control.Location%2A> .</span><span class="sxs-lookup"><span data-stu-id="dff35-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

<span data-ttu-id="dff35-110">La dernière instruction de l’exemple précédent échoue, car elle crée uniquement une allocation temporaire pour la <xref:System.Drawing.Point> structure retournée par la <xref:System.Windows.Forms.Control.Location%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="dff35-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="dff35-111">Une structure est un type valeur, et la structure temporaire n’est pas conservée après l’exécution de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="dff35-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="dff35-112">Le problème est résolu en déclarant et en utilisant une variable pour <xref:System.Windows.Forms.Control.Location%2A> , ce qui crée une allocation plus permanente pour la <xref:System.Drawing.Point> structure.</span><span class="sxs-lookup"><span data-stu-id="dff35-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="dff35-113">L’exemple suivant montre le code qui peut remplacer la dernière instruction de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="dff35-113">The following example shows code that can replace the last statement of the preceding example.</span></span>

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

<span data-ttu-id="dff35-114">**ID d’erreur :** BC30068</span><span class="sxs-lookup"><span data-stu-id="dff35-114">**Error ID:** BC30068</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="dff35-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="dff35-115">To correct this error</span></span>

- <span data-ttu-id="dff35-116">Si l’instruction assigne une valeur à une expression, remplacez l’expression par une variable, une propriété ou un élément de tableau accessible en écriture unique.</span><span class="sxs-lookup"><span data-stu-id="dff35-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>

- <span data-ttu-id="dff35-117">Si l’instruction fait un accès indirect par le biais d’un type valeur (généralement une structure), créez une variable qui contiendra le type valeur.</span><span class="sxs-lookup"><span data-stu-id="dff35-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>

- <span data-ttu-id="dff35-118">Assignez la structure appropriée (ou un autre type de valeur) à la variable.</span><span class="sxs-lookup"><span data-stu-id="dff35-118">Assign the appropriate structure (or other value type) to the variable.</span></span>

- <span data-ttu-id="dff35-119">Utilisez la variable pour accéder à la propriété afin de lui assigner une valeur.</span><span class="sxs-lookup"><span data-stu-id="dff35-119">Use the variable to access the property to assign it a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="dff35-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dff35-120">See also</span></span>

- [<span data-ttu-id="dff35-121">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="dff35-121">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="dff35-122">Instructions</span><span class="sxs-lookup"><span data-stu-id="dff35-122">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="dff35-123">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="dff35-123">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
