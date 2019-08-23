---
title: Définition des classes (Visual Basic)
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
ms.openlocfilehash: 679f4fd55f142c2c4bb63a556feb95c074960b12
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914731"
---
# <a name="walkthrough-defining-classes-visual-basic"></a><span data-ttu-id="92ebf-102">Procédure pas à pas : Définition des classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92ebf-102">Walkthrough: Defining Classes (Visual Basic)</span></span>

<span data-ttu-id="92ebf-103">Cette procédure pas à pas montre comment définir des classes, que vous pouvez ensuite utiliser pour créer des objets.</span><span class="sxs-lookup"><span data-stu-id="92ebf-103">This walkthrough demonstrates how to define classes, which you can then use to create objects.</span></span> <span data-ttu-id="92ebf-104">Elle vous montre également comment ajouter des propriétés et des méthodes à la nouvelle classe, et montre comment initialiser un objet.</span><span class="sxs-lookup"><span data-stu-id="92ebf-104">It also shows you how to add properties and methods to the new class, and demonstrates how to initialize an object.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a><span data-ttu-id="92ebf-105">Pour définir une classe</span><span class="sxs-lookup"><span data-stu-id="92ebf-105">To define a class</span></span>
  
1. <span data-ttu-id="92ebf-106">Créez un projet en cliquant sur **nouveau projet** dans le menu **fichier** .</span><span class="sxs-lookup"><span data-stu-id="92ebf-106">Create a project by clicking **New Project** on the **File** menu.</span></span> <span data-ttu-id="92ebf-107">La boîte de dialogue **Nouveau projet** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="92ebf-107">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="92ebf-108">Sélectionnez application Windows dans la liste des modèles de projet de Visual Basic pour afficher le nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="92ebf-108">Select Windows Application from the list of Visual Basic project templates to display the new project.</span></span>  
  
3. <span data-ttu-id="92ebf-109">Ajoutez une nouvelle classe au projet en cliquant sur **Ajouter une classe** dans le menu **projet** .</span><span class="sxs-lookup"><span data-stu-id="92ebf-109">Add a new class to the project by clicking **Add Class** on the **Project** menu.</span></span> <span data-ttu-id="92ebf-110">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="92ebf-110">The **Add New Item** dialog box appears.</span></span>  
  
4. <span data-ttu-id="92ebf-111">Sélectionnez le modèle de **classe** .</span><span class="sxs-lookup"><span data-stu-id="92ebf-111">Select the **Class** template.</span></span>  
  
5. <span data-ttu-id="92ebf-112">Nommez la nouvelle `UserNameInfo.vb`classe, puis cliquez sur **Ajouter** pour afficher le code de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="92ebf-112">Name the new class `UserNameInfo.vb`, and then click **Add** to display the code for the new class.</span></span>  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > <span data-ttu-id="92ebf-113">Vous pouvez utiliser l' **éditeur de code** Visual Basic pour ajouter une classe à votre formulaire de démarrage en `Class` tapant le mot clé suivi du nom de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="92ebf-113">You can use the Visual Basic **Code Editor** to add a class to your startup form by typing the `Class` keyword followed by the name of the new class.</span></span> <span data-ttu-id="92ebf-114">L' **éditeur de code** fournit une `End Class` instruction correspondante.</span><span class="sxs-lookup"><span data-stu-id="92ebf-114">The **Code Editor** provides a corresponding `End Class` statement for you.</span></span>  
  
6. <span data-ttu-id="92ebf-115">Définissez un champ privé pour la classe en ajoutant le code suivant entre les `Class` instructions `End Class` et:</span><span class="sxs-lookup"><span data-stu-id="92ebf-115">Define a private field for the class by adding the following code between the `Class` and `End Class` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     <span data-ttu-id="92ebf-116">La déclaration du champ comme `Private` signifie qu’il peut être utilisé uniquement dans la classe.</span><span class="sxs-lookup"><span data-stu-id="92ebf-116">Declaring the field as `Private` means it can be used only within the class.</span></span> <span data-ttu-id="92ebf-117">Vous pouvez rendre les champs disponibles à l’extérieur d’une classe en utilisant des modificateurs d’accès tels `Public` que qui fournissent plus d’accès.</span><span class="sxs-lookup"><span data-stu-id="92ebf-117">You can make fields available from outside a class by using access modifiers such as `Public` that provide more access.</span></span> <span data-ttu-id="92ebf-118">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="92ebf-118">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
7. <span data-ttu-id="92ebf-119">Définissez une propriété pour la classe en ajoutant le code suivant:</span><span class="sxs-lookup"><span data-stu-id="92ebf-119">Define a property for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. <span data-ttu-id="92ebf-120">Définissez une méthode pour la classe en ajoutant le code suivant:</span><span class="sxs-lookup"><span data-stu-id="92ebf-120">Define a method for the class by adding the following code:</span></span>  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. <span data-ttu-id="92ebf-121">Définissez un constructeur paramétrable pour la nouvelle classe en ajoutant une procédure nommée `Sub New`:</span><span class="sxs-lookup"><span data-stu-id="92ebf-121">Define a parameterized constructor for the new class by adding a procedure named `Sub New`:</span></span>  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     <span data-ttu-id="92ebf-122">Le `Sub New` constructeur est appelé automatiquement lorsqu’un objet basé sur cette classe est créé.</span><span class="sxs-lookup"><span data-stu-id="92ebf-122">The `Sub New` constructor is called automatically when an object based on this class is created.</span></span> <span data-ttu-id="92ebf-123">Ce constructeur définit la valeur du champ qui contient le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="92ebf-123">This constructor sets the value of the field that holds the user name.</span></span>  
  
## <a name="to-create-a-button-to-test-the-class"></a><span data-ttu-id="92ebf-124">Pour créer un bouton pour tester la classe</span><span class="sxs-lookup"><span data-stu-id="92ebf-124">To create a button to test the class</span></span>
  
1. <span data-ttu-id="92ebf-125">Modifiez le formulaire de démarrage en mode Design en cliquant avec le bouton droit sur son nom dans **Explorateur de solutions** puis en cliquant sur **Concepteur de vues**.</span><span class="sxs-lookup"><span data-stu-id="92ebf-125">Change the startup form to design mode by right-clicking its name in **Solution Explorer** and then clicking **View Designer**.</span></span> <span data-ttu-id="92ebf-126">Par défaut, le formulaire de démarrage pour les projets d’application Windows est nommé Form1. vb.</span><span class="sxs-lookup"><span data-stu-id="92ebf-126">By default, the startup form for Windows Application projects is named Form1.vb.</span></span> <span data-ttu-id="92ebf-127">Le formulaire principal s’affiche alors.</span><span class="sxs-lookup"><span data-stu-id="92ebf-127">The main form will then appear.</span></span>  
  
2. <span data-ttu-id="92ebf-128">Ajoutez un bouton au formulaire principal et double-cliquez dessus pour afficher le code du gestionnaire d' `Button1_Click` événements.</span><span class="sxs-lookup"><span data-stu-id="92ebf-128">Add a button to the main form and double-click it to display the code for the `Button1_Click` event handler.</span></span> <span data-ttu-id="92ebf-129">Ajoutez le code suivant pour appeler la procédure de test:</span><span class="sxs-lookup"><span data-stu-id="92ebf-129">Add the following code to call the test procedure:</span></span>  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a><span data-ttu-id="92ebf-130">Pour exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="92ebf-130">To run your application</span></span>
  
1. <span data-ttu-id="92ebf-131">Exécutez votre application en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="92ebf-131">Run your application by pressing F5.</span></span> <span data-ttu-id="92ebf-132">Cliquez sur le bouton du formulaire pour appeler la procédure de test.</span><span class="sxs-lookup"><span data-stu-id="92ebf-132">Click the button on the form to call the test procedure.</span></span> <span data-ttu-id="92ebf-133">Il affiche un message indiquant que l’original `UserName` est «Moore, Bobby», parce que la procédure a `Capitalize` appelé la méthode de l’objet.</span><span class="sxs-lookup"><span data-stu-id="92ebf-133">It displays a message stating that the original `UserName` is "MOORE, BOBBY", because the procedure called the `Capitalize` method of the object.</span></span>  
  
2. <span data-ttu-id="92ebf-134">Cliquez sur **OK** pour fermer la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="92ebf-134">Click **OK** to dismiss the message box.</span></span> <span data-ttu-id="92ebf-135">La `Button1 Click` procédure modifie la valeur de la `UserName` propriété et affiche un message indiquant que la nouvelle valeur de `UserName` est «worden, Joe».</span><span class="sxs-lookup"><span data-stu-id="92ebf-135">The `Button1 Click` procedure changes the value of the `UserName` property and displays a message stating that the new value of `UserName` is "Worden, Joe".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ebf-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92ebf-136">See also</span></span>

- [<span data-ttu-id="92ebf-137">Programmation orientée objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92ebf-137">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
- [<span data-ttu-id="92ebf-138">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="92ebf-138">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
