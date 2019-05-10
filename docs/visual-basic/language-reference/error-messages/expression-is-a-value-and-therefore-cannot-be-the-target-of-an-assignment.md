---
title: Cette expression est une valeur et ne peut donc pas être la cible d'une assignation
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 1c7fb92c963ea7fa4129cddf060fe7c0b0261fc7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665140"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="47c2b-102">Cette expression est une valeur et ne peut donc pas être la cible d'une assignation</span><span class="sxs-lookup"><span data-stu-id="47c2b-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="47c2b-103">Une instruction tente d’assigner une valeur à une expression.</span><span class="sxs-lookup"><span data-stu-id="47c2b-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="47c2b-104">Vous pouvez affecter une valeur uniquement à une variable accessible en écriture, une propriété ou un élément de tableau en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="47c2b-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="47c2b-105">L’exemple suivant illustre comment cette erreur peut se produire.</span><span class="sxs-lookup"><span data-stu-id="47c2b-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="47c2b-106">Des exemples similaires pourraient s’appliquent aux propriétés et éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="47c2b-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="47c2b-107">**Accès indirect.**</span><span class="sxs-lookup"><span data-stu-id="47c2b-107">**Indirect Access.**</span></span> <span data-ttu-id="47c2b-108">Accès indirect via un type valeur peut également générer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="47c2b-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="47c2b-109">Prenons l’exemple de code suivant, qui tente de définir la valeur de <xref:System.Drawing.Point> en y accédant indirectement via <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="47c2b-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="47c2b-110">La dernière instruction de l’exemple précédent échoue, car il crée uniquement une allocation temporaire pour la <xref:System.Drawing.Point> structure retournée par le <xref:System.Windows.Forms.Control.Location%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="47c2b-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="47c2b-111">Une structure est un type valeur, et la structure temporaire n’est pas conservée après l’exécution de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="47c2b-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="47c2b-112">Le problème est résolu en déclarant et en utilisant une variable pour <xref:System.Windows.Forms.Control.Location%2A>, ce qui crée une allocation plus permanente pour le <xref:System.Drawing.Point> structure.</span><span class="sxs-lookup"><span data-stu-id="47c2b-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="47c2b-113">L’exemple suivant montre le code qui peut remplacer la dernière instruction de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="47c2b-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="47c2b-114">**ID d’erreur :** BC30068</span><span class="sxs-lookup"><span data-stu-id="47c2b-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="47c2b-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="47c2b-115">To correct this error</span></span>  
  
- <span data-ttu-id="47c2b-116">Si l’instruction assigne une valeur à une expression, remplacez l’expression par une variable accessible en écriture seule, une propriété ou un élément de tableau.</span><span class="sxs-lookup"><span data-stu-id="47c2b-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
- <span data-ttu-id="47c2b-117">Si l’instruction effectue un accès indirect via un type valeur (généralement une structure), créez une variable pour contenir le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="47c2b-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
- <span data-ttu-id="47c2b-118">Affectez la structure appropriée (ou autre type de valeur) à la variable.</span><span class="sxs-lookup"><span data-stu-id="47c2b-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
- <span data-ttu-id="47c2b-119">Utilisez la variable pour accéder à la propriété pour lui attribuer une valeur.</span><span class="sxs-lookup"><span data-stu-id="47c2b-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c2b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47c2b-120">See also</span></span>

- [<span data-ttu-id="47c2b-121">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="47c2b-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="47c2b-122">Instructions</span><span class="sxs-lookup"><span data-stu-id="47c2b-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="47c2b-123">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="47c2b-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
