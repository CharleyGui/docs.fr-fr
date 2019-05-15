---
title: 'Procédure : Créer une application Windows Forms à partir de la ligne de commande'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72195dd49c163b26a5bcfa739768718f2a32f346
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588981"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="a643a-102">Procédure : Créer une application Windows Forms à partir de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="a643a-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="a643a-103">Les procédures suivantes décrivent les étapes de base que vous devez effectuer pour créer et exécuter une application Windows Forms à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a643a-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="a643a-104">Ces procédures sont très bien prises en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a643a-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="a643a-105">Consultez également [procédure pas à pas : Hébergement d’un Windows contrôle Forms dans WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a643a-105">Also see [Walkthrough: Hosting a Windows Forms Control in WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a643a-106">Procédure</span><span class="sxs-lookup"><span data-stu-id="a643a-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="a643a-107">Pour créer le formulaire</span><span class="sxs-lookup"><span data-stu-id="a643a-107">To create the form</span></span>  
  
1. <span data-ttu-id="a643a-108">Dans un fichier de code vide, tapez les instructions import ou using suivantes :</span><span class="sxs-lookup"><span data-stu-id="a643a-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="a643a-109">Déclarez une classe nommée `Form1` qui hérite de la classe Form.</span><span class="sxs-lookup"><span data-stu-id="a643a-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. <span data-ttu-id="a643a-110">Créez un constructeur par défaut pour `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a643a-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="a643a-111">Vous ajouterez du code au constructeur lors d'une procédure ultérieure.</span><span class="sxs-lookup"><span data-stu-id="a643a-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="a643a-112">Ajoutez une méthode `Main` à la classe.</span><span class="sxs-lookup"><span data-stu-id="a643a-112">Add a `Main` method to the class.</span></span>  
  
    1. <span data-ttu-id="a643a-113">Appliquer le <xref:System.STAThreadAttribute> c# `Main` méthode pour spécifier votre application Windows Forms est un thread unique cloisonné.</span><span class="sxs-lookup"><span data-stu-id="a643a-113">Apply the <xref:System.STAThreadAttribute> to the C# `Main` method to specify your Windows Forms application is a single-threaded apartment.</span></span> <span data-ttu-id="a643a-114">(L’attribut n’est pas nécessaire en Visual Basic, dans la mesure où Windows forms applications développées avec Visual Basic utilisez un modèle de thread unique cloisonné par défaut.)</span><span class="sxs-lookup"><span data-stu-id="a643a-114">(The attribute is not necessary in Visual Basic, since Windows forms applications developed with Visual Basic use a single-threaded apartment model by default.)</span></span>  
  
    2. <span data-ttu-id="a643a-115">Appelez <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> pour appliquer des styles de système d’exploitation à votre application.</span><span class="sxs-lookup"><span data-stu-id="a643a-115">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to apply operating system styles to your application.</span></span>  
  
    3. <span data-ttu-id="a643a-116">Créez une instance du formulaire et exécutez-la.</span><span class="sxs-lookup"><span data-stu-id="a643a-116">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="a643a-117">Pour compiler et exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="a643a-117">To compile and run the application</span></span>  
  
1. <span data-ttu-id="a643a-118">À l'invite de commandes .NET Framework, accédez au répertoire où vous avez créé la classe `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a643a-118">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2. <span data-ttu-id="a643a-119">Compilez le formulaire.</span><span class="sxs-lookup"><span data-stu-id="a643a-119">Compile the form.</span></span>  
  
    - <span data-ttu-id="a643a-120">Si vous utilisez c#, tapez : `csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="a643a-120">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    - <span data-ttu-id="a643a-121">Si vous utilisez Visual Basic, tapez : `vbc form1.vb`</span><span class="sxs-lookup"><span data-stu-id="a643a-121">If you are using Visual Basic, type: `vbc form1.vb`</span></span>  
  
3. <span data-ttu-id="a643a-122">À l’invite de commandes, tapez : `Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="a643a-122">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="a643a-123">Ajout d'un contrôle et gestion d'un événement</span><span class="sxs-lookup"><span data-stu-id="a643a-123">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="a643a-124">Les étapes de la procédure précédente illustrent simplement comment créer un Windows Form de base qui se compile et s'exécute.</span><span class="sxs-lookup"><span data-stu-id="a643a-124">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="a643a-125">La procédure suivante illustre comment créer et ajouter un contrôle au formulaire et comment gérer un événement pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="a643a-125">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="a643a-126">Pour plus d’informations sur les contrôles que vous pouvez ajouter aux Windows Forms, consultez [des contrôles Windows Forms](./controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="a643a-126">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](./controls/index.md).</span></span>  
  
 <span data-ttu-id="a643a-127">Outre la création d’applications Windows Forms, vous devez comprendre la programmation basée sur les événements et comment gérer l’entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a643a-127">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="a643a-128">Pour plus d’informations, consultez [création de gestionnaires d’événements dans les Windows Forms](creating-event-handlers-in-windows-forms.md), et [gestion des entrées utilisateur](./controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="a643a-128">For more information, see [Creating Event Handlers in Windows Forms](creating-event-handlers-in-windows-forms.md), and [Handling User Input](./controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="a643a-129">Pour déclarer un contrôle bouton et gérer son événement click</span><span class="sxs-lookup"><span data-stu-id="a643a-129">To declare a button control and handle its click event</span></span>  
  
1. <span data-ttu-id="a643a-130">Déclarez un contrôle bouton nommé `button1`.</span><span class="sxs-lookup"><span data-stu-id="a643a-130">Declare a button control named `button1`.</span></span>  
  
2. <span data-ttu-id="a643a-131">Dans le constructeur, créez le bouton et définissez ses propriétés <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> et <xref:System.Windows.Forms.Control.Text%2A>.</span><span class="sxs-lookup"><span data-stu-id="a643a-131">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3. <span data-ttu-id="a643a-132">Ajoutez le bouton au formulaire.</span><span class="sxs-lookup"><span data-stu-id="a643a-132">Add the button to the form.</span></span>  
  
     <span data-ttu-id="a643a-133">L'exemple de code suivant montre comment déclarer le contrôle bouton.</span><span class="sxs-lookup"><span data-stu-id="a643a-133">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="a643a-134">Créez une méthode pour gérer l'événement <xref:System.Windows.Forms.Control.Click> pour le bouton.</span><span class="sxs-lookup"><span data-stu-id="a643a-134">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5. <span data-ttu-id="a643a-135">Dans le gestionnaire d'événements click, affichez un <xref:System.Windows.Forms.MessageBox> avec le message « Hello World ».</span><span class="sxs-lookup"><span data-stu-id="a643a-135">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="a643a-136">L'exemple de code suivant montre comment gérer l'événement click du contrôle bouton.</span><span class="sxs-lookup"><span data-stu-id="a643a-136">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <span data-ttu-id="a643a-137">Associez l'événement <xref:System.Windows.Forms.Control.Click> à la méthode que vous avez créée.</span><span class="sxs-lookup"><span data-stu-id="a643a-137">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="a643a-138">L'exemple de code suivant montre comment associer l'événement à la méthode.</span><span class="sxs-lookup"><span data-stu-id="a643a-138">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. <span data-ttu-id="a643a-139">Compilez et exécutez l'application comme décrit dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="a643a-139">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a643a-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="a643a-140">Example</span></span>  
 <span data-ttu-id="a643a-141">L'exemple de code suivant constitue l'exemple complet des procédures précédentes.</span><span class="sxs-lookup"><span data-stu-id="a643a-141">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a643a-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a643a-142">See also</span></span>

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [<span data-ttu-id="a643a-143">Modification de l'apparence des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a643a-143">Changing the Appearance of Windows Forms</span></span>](changing-the-appearance-of-windows-forms.md)
- [<span data-ttu-id="a643a-144">Amélioration des applications Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a643a-144">Enhancing Windows Forms Applications</span></span>](./advanced/index.md)
- [<span data-ttu-id="a643a-145">Bien démarrer avec Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a643a-145">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
