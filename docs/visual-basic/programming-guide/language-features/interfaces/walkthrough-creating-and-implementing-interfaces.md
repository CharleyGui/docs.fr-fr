---
title: Création et implémentation d’interfaces
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 89e8f91a04b25b84bc783d5c4f4b91cf12426f72
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405065"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a><span data-ttu-id="483f7-102">Procédure pas à pas : création et implémentation d'interfaces (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="483f7-102">Walkthrough: Creating and Implementing Interfaces (Visual Basic)</span></span>

<span data-ttu-id="483f7-103">Les interfaces décrivent les caractéristiques des propriétés, des méthodes et des événements, mais laissent les détails de l’implémentation à des structures ou des classes.</span><span class="sxs-lookup"><span data-stu-id="483f7-103">Interfaces describe the characteristics of properties, methods, and events, but leave the implementation details up to structures or classes.</span></span>  
  
 <span data-ttu-id="483f7-104">Cette procédure pas à pas montre comment déclarer et implémenter une interface.</span><span class="sxs-lookup"><span data-stu-id="483f7-104">This walkthrough demonstrates how to declare and implement an interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="483f7-105">Cette procédure pas à pas ne fournit pas d’informations sur la création d’une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="483f7-105">This walkthrough doesn't provide information about how to create a user interface.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a><span data-ttu-id="483f7-106">Pour définir une interface</span><span class="sxs-lookup"><span data-stu-id="483f7-106">To define an interface</span></span>
  
1. <span data-ttu-id="483f7-107">Ouvrez un nouveau projet d’application Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="483f7-107">Open a new Visual Basic Windows Application project.</span></span>  
  
2. <span data-ttu-id="483f7-108">Ajoutez un nouveau module au projet en cliquant sur **Ajouter un module** dans le menu **projet** .</span><span class="sxs-lookup"><span data-stu-id="483f7-108">Add a new module to the project by clicking **Add Module** on the **Project** menu.</span></span>  
  
3. <span data-ttu-id="483f7-109">Nommez le nouveau module `Module1.vb` , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="483f7-109">Name the new module `Module1.vb` and click **Add**.</span></span> <span data-ttu-id="483f7-110">Le code du nouveau module s’affiche.</span><span class="sxs-lookup"><span data-stu-id="483f7-110">The code for the new module is displayed.</span></span>  
  
4. <span data-ttu-id="483f7-111">Définissez une interface nommée `TestInterface` dans `Module1` en tapant `Interface TestInterface` entre les `Module` `End Module` instructions et, puis en appuyant sur entrée.</span><span class="sxs-lookup"><span data-stu-id="483f7-111">Define an interface named `TestInterface` within `Module1` by typing `Interface TestInterface` between the `Module` and `End Module` statements, and then pressing ENTER.</span></span> <span data-ttu-id="483f7-112">L' **éditeur de code** met en retrait le `Interface` mot clé et ajoute une `End Interface` instruction pour former un bloc de code.</span><span class="sxs-lookup"><span data-stu-id="483f7-112">The **Code Editor** indents the `Interface` keyword and adds an `End Interface` statement to form a code block.</span></span>  
  
5. <span data-ttu-id="483f7-113">Définissez une propriété, une méthode et un événement pour l’interface en plaçant le code suivant entre `Interface` les `End Interface` instructions et :</span><span class="sxs-lookup"><span data-stu-id="483f7-113">Define a property, method, and event for the interface by placing the following code between the `Interface` and `End Interface` statements:</span></span>  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a><span data-ttu-id="483f7-114">Implémentation</span><span class="sxs-lookup"><span data-stu-id="483f7-114">Implementation</span></span>

 <span data-ttu-id="483f7-115">Vous pouvez remarquer que la syntaxe utilisée pour déclarer des membres d’interface est différente de la syntaxe utilisée pour déclarer des membres de classe.</span><span class="sxs-lookup"><span data-stu-id="483f7-115">You may notice that the syntax used to declare interface members is different from the syntax used to declare class members.</span></span> <span data-ttu-id="483f7-116">Cette différence reflète le fait que les interfaces ne peuvent pas contenir de code d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="483f7-116">This difference reflects the fact that interfaces cannot contain implementation code.</span></span>  
  
### <a name="to-implement-the-interface"></a><span data-ttu-id="483f7-117">Pour implémenter l’interface</span><span class="sxs-lookup"><span data-stu-id="483f7-117">To implement the interface</span></span>
  
1. <span data-ttu-id="483f7-118">Ajoutez une classe nommée `ImplementationClass` en ajoutant l’instruction suivante à `Module1` , après l' `End Interface` instruction mais avant l' `End Module` instruction, puis en appuyant sur entrée :</span><span class="sxs-lookup"><span data-stu-id="483f7-118">Add a class named `ImplementationClass` by adding the following statement to `Module1`, after the `End Interface` statement but before the `End Module` statement, and then pressing ENTER:</span></span>  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     <span data-ttu-id="483f7-119">Si vous travaillez dans l’environnement de développement intégré, l' **éditeur de code** fournit une `End Class` instruction correspondante lorsque vous appuyez sur entrée.</span><span class="sxs-lookup"><span data-stu-id="483f7-119">If you are working within the integrated development environment, the **Code Editor** supplies a matching `End Class` statement when you press ENTER.</span></span>  
  
2. <span data-ttu-id="483f7-120">Ajoutez l' `Implements` instruction suivante à `ImplementationClass` , qui nomme l’interface que la classe implémente :</span><span class="sxs-lookup"><span data-stu-id="483f7-120">Add the following `Implements` statement to `ImplementationClass`, which names the interface the class implements:</span></span>  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     <span data-ttu-id="483f7-121">En cas de liste distincte des autres éléments en haut d’une classe ou d’une structure, l' `Implements` instruction indique que la classe ou la structure implémente une interface.</span><span class="sxs-lookup"><span data-stu-id="483f7-121">When listed separately from other items at the top of a class or structure, the `Implements` statement indicates that the class or structure implements an interface.</span></span>  
  
     <span data-ttu-id="483f7-122">Si vous travaillez dans l’environnement de développement intégré, l' **éditeur de code** implémente les membres de classe requis par `TestInterface` lorsque vous appuyez sur entrée, et vous pouvez ignorer l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="483f7-122">If you are working within the integrated development environment, the **Code Editor** implements the class members required by `TestInterface` when you press ENTER, and you can skip the next step.</span></span>  
  
3. <span data-ttu-id="483f7-123">Si vous ne travaillez pas dans l’environnement de développement intégré, vous devez implémenter tous les membres de l’interface `MyInterface` .</span><span class="sxs-lookup"><span data-stu-id="483f7-123">If you are not working within the integrated development environment, you must implement all the members of the interface `MyInterface`.</span></span> <span data-ttu-id="483f7-124">Ajoutez le code suivant à `ImplementationClass` pour implémenter `Event1` , `Method1` et `Prop1` :</span><span class="sxs-lookup"><span data-stu-id="483f7-124">Add the following code to `ImplementationClass` to implement `Event1`, `Method1`, and `Prop1`:</span></span>  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     <span data-ttu-id="483f7-125">L' `Implements` instruction nomme l’interface et le membre d’interface en cours d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="483f7-125">The `Implements` statement names the interface and interface member being implemented.</span></span>  
  
4. <span data-ttu-id="483f7-126">Terminez la définition de `Prop1` en ajoutant un champ privé à la classe qui a stocké la valeur de la propriété :</span><span class="sxs-lookup"><span data-stu-id="483f7-126">Complete the definition of `Prop1` by adding a private field to the class that stored the property value:</span></span>  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     <span data-ttu-id="483f7-127">Retourne la valeur de `pval` à partir de l’accesseur Get de la propriété.</span><span class="sxs-lookup"><span data-stu-id="483f7-127">Return the value of the `pval` from the property get accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     <span data-ttu-id="483f7-128">Définissez la valeur de `pval` dans l’accesseur Set de propriété.</span><span class="sxs-lookup"><span data-stu-id="483f7-128">Set the value of `pval` in the property set accessor.</span></span>  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. <span data-ttu-id="483f7-129">Terminez la définition de `Method1` en ajoutant le code suivant.</span><span class="sxs-lookup"><span data-stu-id="483f7-129">Complete the definition of `Method1` by adding the following code.</span></span>  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a><span data-ttu-id="483f7-130">Pour tester l’implémentation de l’interface</span><span class="sxs-lookup"><span data-stu-id="483f7-130">To test the implementation of the interface</span></span>
  
1. <span data-ttu-id="483f7-131">Cliquez avec le bouton droit sur le formulaire de démarrage de votre projet dans la **Explorateur de solutions**, puis cliquez sur **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="483f7-131">Right-click the startup form for your project in the **Solution Explorer**, and click **View Code**.</span></span> <span data-ttu-id="483f7-132">L’éditeur affiche la classe pour votre formulaire de démarrage.</span><span class="sxs-lookup"><span data-stu-id="483f7-132">The editor displays the class for your startup form.</span></span> <span data-ttu-id="483f7-133">Par défaut, le formulaire de démarrage est appelé `Form1` .</span><span class="sxs-lookup"><span data-stu-id="483f7-133">By default, the startup form is called `Form1`.</span></span>  
  
2. <span data-ttu-id="483f7-134">Ajoutez le `testInstance` champ suivant à la `Form1` classe :</span><span class="sxs-lookup"><span data-stu-id="483f7-134">Add the following `testInstance` field to the `Form1` class:</span></span>  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     <span data-ttu-id="483f7-135">En déclarant `testInstance` en tant que `WithEvents` , la `Form1` classe peut gérer ses événements.</span><span class="sxs-lookup"><span data-stu-id="483f7-135">By declaring `testInstance` as `WithEvents`, the `Form1` class can handle its events.</span></span>  
  
3. <span data-ttu-id="483f7-136">Ajoutez le gestionnaire d’événements suivant à la `Form1` classe pour gérer les événements déclenchés par `testInstance` :</span><span class="sxs-lookup"><span data-stu-id="483f7-136">Add the following event handler to the `Form1` class to handle events raised by `testInstance`:</span></span>  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. <span data-ttu-id="483f7-137">Ajoutez une sous-routine nommée `Test` à la `Form1` classe pour tester la classe d’implémentation :</span><span class="sxs-lookup"><span data-stu-id="483f7-137">Add a subroutine named `Test` to the `Form1` class to test the implementation class:</span></span>  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     <span data-ttu-id="483f7-138">La `Test` procédure crée une instance de la classe qui implémente `MyInterface` , assigne cette instance au `testInstance` champ, définit une propriété et exécute une méthode par le biais de l’interface.</span><span class="sxs-lookup"><span data-stu-id="483f7-138">The `Test` procedure creates an instance of the class that implements `MyInterface`, assigns that instance to the `testInstance` field, sets a property, and runs a method through the interface.</span></span>  
  
5. <span data-ttu-id="483f7-139">Ajoutez du code pour appeler la `Test` procédure à partir de la `Form1 Load` procédure de votre formulaire de démarrage :</span><span class="sxs-lookup"><span data-stu-id="483f7-139">Add code to call the `Test` procedure from the `Form1 Load` procedure of your startup form:</span></span>  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. <span data-ttu-id="483f7-140">Exécutez la `Test` procédure en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="483f7-140">Run the `Test` procedure by pressing F5.</span></span> <span data-ttu-id="483f7-141">Le message « Prop1 a été défini sur 9 » s’affiche.</span><span class="sxs-lookup"><span data-stu-id="483f7-141">The message "Prop1 was set to 9" is displayed.</span></span> <span data-ttu-id="483f7-142">Une fois que vous avez cliqué sur OK, le message « le paramètre X pour méthode1 est 5 » s’affiche.</span><span class="sxs-lookup"><span data-stu-id="483f7-142">After you click OK, the message "The X parameter for Method1 is 5" is displayed.</span></span> <span data-ttu-id="483f7-143">Cliquez sur OK. le message « le gestionnaire d’événements a intercepté l’événement » s’affiche.</span><span class="sxs-lookup"><span data-stu-id="483f7-143">Click OK, and the message "The event handler caught the event" is displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483f7-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="483f7-144">See also</span></span>

- [<span data-ttu-id="483f7-145">Implements, instruction</span><span class="sxs-lookup"><span data-stu-id="483f7-145">Implements Statement</span></span>](../../../language-reference/statements/implements-statement.md)
- [<span data-ttu-id="483f7-146">Interfaces</span><span class="sxs-lookup"><span data-stu-id="483f7-146">Interfaces</span></span>](index.md)
- [<span data-ttu-id="483f7-147">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="483f7-147">Interface Statement</span></span>](../../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="483f7-148">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="483f7-148">Event Statement</span></span>](../../../language-reference/statements/event-statement.md)
