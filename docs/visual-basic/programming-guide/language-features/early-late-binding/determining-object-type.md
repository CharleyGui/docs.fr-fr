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
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345201"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="7d2b4-102">Détermination du type Object (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d2b4-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="7d2b4-103">Les variables objets génériques (autrement dit, les variables que vous déclarez comme `Object`) peuvent contenir des objets de n’importe quelle classe.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="7d2b4-104">Lorsque vous utilisez des variables de type `Object`, vous devrez peut-être effectuer des actions différentes en fonction de la classe de l’objet. par exemple, certains objets peuvent ne pas prendre en charge une propriété ou une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="7d2b4-105">Visual Basic fournit deux méthodes pour déterminer le type d’objet qui est stocké dans une variable objet : la fonction `TypeName` et l’opérateur `TypeOf...Is`.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="7d2b4-106">TypeName et TypeOf... Non</span><span class="sxs-lookup"><span data-stu-id="7d2b4-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="7d2b4-107">La fonction `TypeName` retourne une chaîne et constitue le meilleur choix lorsque vous avez besoin de stocker ou d’afficher le nom de classe d’un objet, comme indiqué dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="7d2b4-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="7d2b4-108">L’opérateur `TypeOf...Is` est le meilleur choix pour tester le type d’un objet, car il est beaucoup plus rapide qu’une comparaison de chaînes équivalente à l’aide de `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="7d2b4-109">Le fragment de code suivant utilise `TypeOf...Is` dans une instruction `If...Then...Else` :</span><span class="sxs-lookup"><span data-stu-id="7d2b4-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="7d2b4-110">Un mot de prudence est dû ici.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-110">A word of caution is due here.</span></span> <span data-ttu-id="7d2b4-111">L’opérateur `TypeOf...Is` retourne `True` si un objet est d’un type spécifique ou s’il est dérivé d’un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="7d2b4-112">Presque tout ce que vous faites avec Visual Basic implique des objets, qui incluent certains éléments qui ne sont normalement pas considérés comme des objets, tels que les chaînes et les entiers.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="7d2b4-113">Ces objets sont dérivés de et héritent des méthodes de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="7d2b4-114">En cas de réussite d’une `Integer` et évaluée avec `Object`, l’opérateur `TypeOf...Is` retourne `True`.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="7d2b4-115">L’exemple suivant indique que le paramètre `InParam` est à la fois un `Object` et un `Integer`:</span><span class="sxs-lookup"><span data-stu-id="7d2b4-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="7d2b4-116">L’exemple suivant utilise à la fois `TypeOf...Is` et `TypeName` pour déterminer le type d’objet qui lui est passé dans l’argument `Ctrl`.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="7d2b4-117">La procédure `TestObject` appelle `ShowType` avec trois types différents de contrôles.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="7d2b4-118">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="7d2b4-118">To run the example</span></span>  
  
1. <span data-ttu-id="7d2b4-119">Créez un projet d’application Windows et ajoutez un contrôle de <xref:System.Windows.Forms.Button>, un contrôle <xref:System.Windows.Forms.CheckBox> et un <xref:System.Windows.Forms.RadioButton> contrôle au formulaire.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="7d2b4-120">À partir du bouton de votre formulaire, appelez la procédure `TestObject`.</span><span class="sxs-lookup"><span data-stu-id="7d2b4-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="7d2b4-121">Ajoutez le code suivant à votre formulaire :</span><span class="sxs-lookup"><span data-stu-id="7d2b4-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="7d2b4-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d2b4-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="7d2b4-123">Appel d’une propriété ou méthode à l’aide d’un nom de chaîne</span><span class="sxs-lookup"><span data-stu-id="7d2b4-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="7d2b4-124">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="7d2b4-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="7d2b4-125">If...Then...Else (instruction)</span><span class="sxs-lookup"><span data-stu-id="7d2b4-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="7d2b4-126">String (type de données)</span><span class="sxs-lookup"><span data-stu-id="7d2b4-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="7d2b4-127">Integer (type de données)</span><span class="sxs-lookup"><span data-stu-id="7d2b4-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
