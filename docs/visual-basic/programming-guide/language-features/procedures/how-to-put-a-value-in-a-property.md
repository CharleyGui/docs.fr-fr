---
title: 'Comment : placer une valeur dans une propriété'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: c0fb3e137010390097a68aea161efcff93839d94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414335"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="54e5e-102">Comment : placer une valeur dans une propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54e5e-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="54e5e-103">Vous stockez une valeur dans une propriété en plaçant le nom de la propriété sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="54e5e-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="54e5e-104">La procédure de la propriété `Set` stocke une valeur, mais vous ne l’appelez pas explicitement par nom.</span><span class="sxs-lookup"><span data-stu-id="54e5e-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="54e5e-105">Vous utilisez la propriété de la même façon que vous utilisez une variable.</span><span class="sxs-lookup"><span data-stu-id="54e5e-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="54e5e-106">Visual Basic effectue les appels aux procédures de la propriété.</span><span class="sxs-lookup"><span data-stu-id="54e5e-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="54e5e-107">Pour stocker une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="54e5e-107">To store a value in a property</span></span>  
  
1. <span data-ttu-id="54e5e-108">Utilisez le nom de la propriété sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="54e5e-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="54e5e-109">L’exemple suivant définit la valeur de la `TimeOfDay` propriété Visual Basic sur midi, en appelant implicitement sa `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="54e5e-109">The following example sets the value of the Visual Basic `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="54e5e-110">Si la propriété accepte des arguments, placez le nom de la propriété entre parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="54e5e-110">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="54e5e-111">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="54e5e-111">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="54e5e-112">Placez les arguments dans la liste d’arguments entre parenthèses, séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="54e5e-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="54e5e-113">Veillez à fournir les arguments dans l’ordre dans lequel la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="54e5e-113">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4. <span data-ttu-id="54e5e-114">La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="54e5e-114">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54e5e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54e5e-115">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>
- [<span data-ttu-id="54e5e-116">Procédures Property</span><span class="sxs-lookup"><span data-stu-id="54e5e-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="54e5e-117">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="54e5e-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="54e5e-118">Property Statement</span><span class="sxs-lookup"><span data-stu-id="54e5e-118">Property Statement</span></span>](../../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="54e5e-119">Différences entre les propriétés et les variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54e5e-119">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="54e5e-120">Comment : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="54e5e-120">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="54e5e-121">Comment : déclarer une propriété avec des niveaux d'accès mixtes</span><span class="sxs-lookup"><span data-stu-id="54e5e-121">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="54e5e-122">Comment : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="54e5e-122">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="54e5e-123">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54e5e-123">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="54e5e-124">Comment : obtenir une valeur d'une propriété</span><span class="sxs-lookup"><span data-stu-id="54e5e-124">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
