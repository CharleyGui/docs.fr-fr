---
title: Définition de classes
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: bd3f6e5cff41551240d9904ab93af8758eb104d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346076"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="3c999-102">Procédure pas à pas : définition des classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c999-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="3c999-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span><span class="sxs-lookup"><span data-stu-id="3c999-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="3c999-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span><span class="sxs-lookup"><span data-stu-id="3c999-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="3c999-105">To define a class</span><span class="sxs-lookup"><span data-stu-id="3c999-105">To define a class</span></span>
  
1. <span data-ttu-id="3c999-106">Create a project by clicking **New Project** on the **File** menu.</span><span class="sxs-lookup"><span data-stu-id="3c999-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="3c999-107">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="3c999-107">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="3c999-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span><span class="sxs-lookup"><span data-stu-id="3c999-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="3c999-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span><span class="sxs-lookup"><span data-stu-id="3c999-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="3c999-110">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="3c999-110">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="3c999-111">Select the **Class** template.</span><span class="sxs-lookup"><span data-stu-id="3c999-111">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="3c999-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span><span class="sxs-lookup"><span data-stu-id="3c999-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="3c999-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span><span class="sxs-lookup"><span data-stu-id="3c999-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="3c999-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span><span class="sxs-lookup"><span data-stu-id="3c999-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="3c999-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span><span class="sxs-lookup"><span data-stu-id="3c999-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="3c999-116">Declaring the field as `Private` means it can be used only within the class.</span><span class="sxs-lookup"><span data-stu-id="3c999-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="3c999-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span><span class="sxs-lookup"><span data-stu-id="3c999-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="3c999-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3c999-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="3c999-119">Define a property for the class by adding the following code:</span><span class="sxs-lookup"><span data-stu-id="3c999-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="3c999-120">Define a method for the class by adding the following code:</span><span class="sxs-lookup"><span data-stu-id="3c999-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="3c999-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="3c999-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="3c999-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span><span class="sxs-lookup"><span data-stu-id="3c999-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="3c999-123">This constructor sets the value of the field that holds the user name.</span><span class="sxs-lookup"><span data-stu-id="3c999-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="3c999-124">To create a button to test the class</span><span class="sxs-lookup"><span data-stu-id="3c999-124">To create a button to test the class</span></span>
  
1. <span data-ttu-id="3c999-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span><span class="sxs-lookup"><span data-stu-id="3c999-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="3c999-126">By default, the startup form for Windows Application projects is named Form1.vb.</span><span class="sxs-lookup"><span data-stu-id="3c999-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="3c999-127">The main form will then appear.</span><span class="sxs-lookup"><span data-stu-id="3c999-127">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="3c999-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span><span class="sxs-lookup"><span data-stu-id="3c999-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="3c999-129">Add the following code to call the test procedure:</span><span class="sxs-lookup"><span data-stu-id="3c999-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="3c999-130">Pour exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="3c999-130">To run your application</span></span>
  
1. <span data-ttu-id="3c999-131">Run your application by pressing F5.</span><span class="sxs-lookup"><span data-stu-id="3c999-131">Run your application by pressing F5.</span></span> <span data-ttu-id="3c999-132">Click the button on the form to call the test procedure.</span><span class="sxs-lookup"><span data-stu-id="3c999-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="3c999-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span><span class="sxs-lookup"><span data-stu-id="3c999-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="3c999-134">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="3c999-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="3c999-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span><span class="sxs-lookup"><span data-stu-id="3c999-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c999-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c999-136">See also</span></span>

- [<span data-ttu-id="3c999-137">Programmation orientée objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c999-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="3c999-138">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="3c999-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
