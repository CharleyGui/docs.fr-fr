---
title: Détermination du type Object
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 3b1c4ad0ab4fd8d2897aff6ad9097cdc81272455
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410642"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="74d72-102">Détermination du type Object (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74d72-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="74d72-103">Les variables objets génériques (autrement dit, les variables que vous déclarez comme `Object` ) peuvent contenir des objets de n’importe quelle classe.</span><span class="sxs-lookup"><span data-stu-id="74d72-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="74d72-104">Lorsque vous utilisez des variables de type `Object` , vous devrez peut-être effectuer des actions différentes en fonction de la classe de l’objet ; par exemple, certains objets peuvent ne pas prendre en charge une propriété ou une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="74d72-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="74d72-105">Visual Basic fournit deux méthodes pour déterminer le type d’objet qui est stocké dans une variable objet : la `TypeName` fonction et l' `TypeOf...Is` opérateur.</span><span class="sxs-lookup"><span data-stu-id="74d72-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="74d72-106">TypeName et TypeOf... Non</span><span class="sxs-lookup"><span data-stu-id="74d72-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="74d72-107">La `TypeName` fonction retourne une chaîne et constitue le meilleur choix lorsque vous avez besoin de stocker ou d’afficher le nom de classe d’un objet, comme indiqué dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="74d72-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="74d72-108">L' `TypeOf...Is` opérateur est le meilleur choix pour tester le type d’un objet, car il est beaucoup plus rapide qu’une comparaison de chaînes équivalente à l’aide de `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="74d72-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="74d72-109">Le fragment de code suivant utilise `TypeOf...Is` dans une `If...Then...Else` instruction :</span><span class="sxs-lookup"><span data-stu-id="74d72-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="74d72-110">Un mot de prudence est dû ici.</span><span class="sxs-lookup"><span data-stu-id="74d72-110">A word of caution is due here.</span></span> <span data-ttu-id="74d72-111">L' `TypeOf...Is` opérateur retourne `True` si un objet est d’un type spécifique ou s’il est dérivé d’un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="74d72-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="74d72-112">Presque tout ce que vous faites avec Visual Basic implique des objets, qui incluent certains éléments qui ne sont normalement pas considérés comme des objets, tels que les chaînes et les entiers.</span><span class="sxs-lookup"><span data-stu-id="74d72-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="74d72-113">Ces objets sont dérivés de et héritent des méthodes de <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="74d72-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="74d72-114">Lorsqu’il reçoit un `Integer` et évalué avec `Object` , l' `TypeOf...Is` opérateur retourne `True` .</span><span class="sxs-lookup"><span data-stu-id="74d72-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="74d72-115">L’exemple suivant indique que le paramètre `InParam` est à la fois un `Object` et un `Integer` :</span><span class="sxs-lookup"><span data-stu-id="74d72-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="74d72-116">L’exemple suivant utilise à la fois `TypeOf...Is` et `TypeName` pour déterminer le type de l’objet qui lui est passé dans l' `Ctrl` argument.</span><span class="sxs-lookup"><span data-stu-id="74d72-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="74d72-117">La `TestObject` procédure appelle `ShowType` avec trois types différents de contrôles.</span><span class="sxs-lookup"><span data-stu-id="74d72-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="74d72-118">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="74d72-118">To run the example</span></span>  
  
1. <span data-ttu-id="74d72-119">Créez un nouveau projet d’application Windows et ajoutez un contrôle <xref:System.Windows.Forms.Button> , un contrôle <xref:System.Windows.Forms.CheckBox> et un <xref:System.Windows.Forms.RadioButton> contrôle au formulaire.</span><span class="sxs-lookup"><span data-stu-id="74d72-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="74d72-120">À partir du bouton de votre formulaire, appelez la `TestObject` procédure.</span><span class="sxs-lookup"><span data-stu-id="74d72-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="74d72-121">Ajoutez le code suivant à votre formulaire :</span><span class="sxs-lookup"><span data-stu-id="74d72-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="74d72-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74d72-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="74d72-123">Appel d'une propriété ou méthode à l'aide d'un nom de chaîne</span><span class="sxs-lookup"><span data-stu-id="74d72-123">Calling a Property or Method Using a String Name</span></span>](calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="74d72-124">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="74d72-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="74d72-125">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="74d72-125">If...Then...Else Statement</span></span>](../../../language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="74d72-126">String, type de données</span><span class="sxs-lookup"><span data-stu-id="74d72-126">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="74d72-127">Entier (type de données)</span><span class="sxs-lookup"><span data-stu-id="74d72-127">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)
