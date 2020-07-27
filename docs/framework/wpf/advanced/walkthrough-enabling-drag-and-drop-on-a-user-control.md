---
title: 'Procédure pas à pas : activation de Glisser-déplacer sur un contrôle utilisateur'
description: Découvrez comment créer un contrôle utilisateur personnalisé qui peut participer au transfert de données par glisser-déplacer dans Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 12ad47035a09995094014841b083062743fc2574
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168276"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="605f8-103">Procédure pas à pas : activation de Glisser-déplacer sur un contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="605f8-103">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="605f8-104">Cette procédure pas à pas montre comment créer un contrôle utilisateur personnalisé qui peut participer à un transfert de données par glisser-déplacer dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="605f8-104">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="605f8-105">Dans cette procédure pas à pas, vous allez créer un WPF personnalisé <xref:System.Windows.Controls.UserControl> qui représente une forme de cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-105">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="605f8-106">Vous implémentez la fonctionnalité sur le contrôle pour activer le transfert de données par glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="605f8-106">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="605f8-107">Par exemple, si vous faites glisser un contrôle de cercle sur un autre, les données de couleur de remplissage sont copiées du cercle source vers la cible.</span><span class="sxs-lookup"><span data-stu-id="605f8-107">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="605f8-108">Si vous faites glisser un contrôle Circle vers un <xref:System.Windows.Controls.TextBox> , la représentation sous forme de chaîne de la couleur de remplissage est copiée dans le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-108">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="605f8-109">Vous allez également créer une petite application qui contient deux contrôles de panneau et un <xref:System.Windows.Controls.TextBox> pour tester la fonctionnalité de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="605f8-109">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="605f8-110">Vous écrivez du code qui permet aux panneaux de traiter les données de cercle déplacées, ce qui vous permet de déplacer ou copier des cercles de la collection d’enfants d’un panneau à l’autre.</span><span class="sxs-lookup"><span data-stu-id="605f8-110">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="605f8-111">Cette procédure pas à pas décrit les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-111">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="605f8-112">Créer un contrôle utilisateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="605f8-112">Create a custom user control.</span></span>

- <span data-ttu-id="605f8-113">Permettre au contrôle utilisateur d’être une source de glissement.</span><span class="sxs-lookup"><span data-stu-id="605f8-113">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="605f8-114">Permettre au contrôle utilisateur d’être une cible de déplacement.</span><span class="sxs-lookup"><span data-stu-id="605f8-114">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="605f8-115">Permettre à un panneau de recevoir des données déplacées à partir du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="605f8-115">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="605f8-116">Prérequis</span><span class="sxs-lookup"><span data-stu-id="605f8-116">Prerequisites</span></span>

<span data-ttu-id="605f8-117">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="605f8-117">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="605f8-118">Créer le projet d’application</span><span class="sxs-lookup"><span data-stu-id="605f8-118">Create the Application Project</span></span>
 <span data-ttu-id="605f8-119">Dans cette section, vous allez créer l’infrastructure de l’application, qui comprend une page principale avec deux panneaux et un <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-119">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="605f8-120">Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="605f8-120">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="605f8-121">Pour plus d’informations, consultez [Procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="605f8-121">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="605f8-122">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="605f8-122">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="605f8-123">Ajoutez le balisage suivant entre les balises d’ouverture et de fermeture <xref:System.Windows.Controls.Grid> .</span><span class="sxs-lookup"><span data-stu-id="605f8-123">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="605f8-124">Ce balisage crée l’interface utilisateur pour l’application de test.</span><span class="sxs-lookup"><span data-stu-id="605f8-124">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="605f8-125">Ajouter un nouveau contrôle utilisateur au projet</span><span class="sxs-lookup"><span data-stu-id="605f8-125">Add a New User Control to the Project</span></span>
 <span data-ttu-id="605f8-126">Dans cette section, vous ajoutez un nouveau contrôle utilisateur au projet.</span><span class="sxs-lookup"><span data-stu-id="605f8-126">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="605f8-127">Dans le menu Projet, sélectionnez **Ajouter un contrôle utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="605f8-127">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="605f8-128">Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le nom par `Circle.xaml` , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="605f8-128">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="605f8-129">Circle.XAML et son code-behind sont ajoutés au projet.</span><span class="sxs-lookup"><span data-stu-id="605f8-129">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="605f8-130">Ouvrez Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="605f8-130">Open Circle.xaml.</span></span>

     <span data-ttu-id="605f8-131">Ce fichier doit contenir les éléments d’interface utilisateur du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="605f8-131">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="605f8-132">Ajoutez le balisage suivant à la racine <xref:System.Windows.Controls.Grid> pour créer un contrôle utilisateur simple dont l’interface utilisateur est un cercle bleu.</span><span class="sxs-lookup"><span data-stu-id="605f8-132">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="605f8-133">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="605f8-133">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="605f8-134">En C#, ajoutez le code suivant après le constructeur sans paramètre pour créer un constructeur de copie.</span><span class="sxs-lookup"><span data-stu-id="605f8-134">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="605f8-135">Dans Visual Basic, ajoutez le code suivant pour créer un constructeur sans paramètre et un constructeur de copie.</span><span class="sxs-lookup"><span data-stu-id="605f8-135">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="605f8-136">Pour que le contrôle utilisateur puisse être copié, vous ajoutez une méthode de constructeur de copie dans le fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="605f8-136">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="605f8-137">Dans le contrôle utilisateur de cercle simplifié, vous copiez uniquement les valeurs de remplissage et de taille du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="605f8-137">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="605f8-138">Ajouter le contrôle utilisateur à la fenêtre principale</span><span class="sxs-lookup"><span data-stu-id="605f8-138">Add the user control to the main window</span></span>

1. <span data-ttu-id="605f8-139">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="605f8-139">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="605f8-140">Ajoutez le code XAML suivant à la <xref:System.Windows.Window> balise d’ouverture pour créer une référence d’espace de noms XML à l’application actuelle.</span><span class="sxs-lookup"><span data-stu-id="605f8-140">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="605f8-141">Dans le premier <xref:System.Windows.Controls.StackPanel> , ajoutez le code XAML suivant pour créer deux instances du contrôle utilisateur Circle dans le premier panneau.</span><span class="sxs-lookup"><span data-stu-id="605f8-141">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="605f8-142">Le code XAML complet pour le panneau ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="605f8-142">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="605f8-143">Implémenter les événements de source de glissement dans le contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="605f8-143">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="605f8-144">Dans cette section, vous allez substituer la <xref:System.Windows.UIElement.OnMouseMove%2A> méthode et lancer l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="605f8-144">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="605f8-145">Si un glisser-déplacer est démarré (un bouton de la souris est enfoncé et que la souris est déplacée), vous allez empaqueter les données à transférer dans un <xref:System.Windows.DataObject> .</span><span class="sxs-lookup"><span data-stu-id="605f8-145">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="605f8-146">Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.</span><span class="sxs-lookup"><span data-stu-id="605f8-146">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="605f8-147">Pour lancer une opération de glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="605f8-147">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="605f8-148">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="605f8-148">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="605f8-149">Ajoutez la <xref:System.Windows.UIElement.OnMouseMove%2A> substitution suivante pour fournir la gestion de classe pour l' <xref:System.Windows.UIElement.MouseMove> événement.</span><span class="sxs-lookup"><span data-stu-id="605f8-149">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="605f8-150">Ce <xref:System.Windows.UIElement.OnMouseMove%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-150">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="605f8-151">Vérifie si le bouton gauche de la souris est enfoncé quand la souris se déplace.</span><span class="sxs-lookup"><span data-stu-id="605f8-151">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="605f8-152">Empaquette les données de cercle dans un <xref:System.Windows.DataObject> .</span><span class="sxs-lookup"><span data-stu-id="605f8-152">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="605f8-153">Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.</span><span class="sxs-lookup"><span data-stu-id="605f8-153">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="605f8-154">Appelle la <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> méthode statique pour initier l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="605f8-154">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="605f8-155">Vous transmettez les trois paramètres suivants à la <xref:System.Windows.DragDrop.DoDragDrop%2A> méthode :</span><span class="sxs-lookup"><span data-stu-id="605f8-155">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="605f8-156">`dragSource` : Référence à ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="605f8-156">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="605f8-157">`data`: Le <xref:System.Windows.DataObject> créé dans le code précédent.</span><span class="sxs-lookup"><span data-stu-id="605f8-157">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="605f8-158">`allowedEffects`: Les opérations de glisser-déplacer autorisées, qui sont <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="605f8-158">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="605f8-159">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="605f8-159">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="605f8-160">Cliquez sur l’un des contrôles de cercle et faites-le glisser sur les panneaux, l’autre cercle et le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-160">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="605f8-161">Lorsque vous faites glisser le pointeur de la souris sur le <xref:System.Windows.Controls.TextBox> , le curseur change pour indiquer un déplacement.</span><span class="sxs-lookup"><span data-stu-id="605f8-161">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="605f8-162">Tout en faisant glisser un cercle sur le <xref:System.Windows.Controls.TextBox> , appuyez sur la touche **CTRL** .</span><span class="sxs-lookup"><span data-stu-id="605f8-162">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="605f8-163">Notez que le curseur change pour indiquer une copie.</span><span class="sxs-lookup"><span data-stu-id="605f8-163">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="605f8-164">Glissez-déposez un cercle sur le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-164">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="605f8-165">La représentation sous forme de chaîne de la couleur de remplissage du cercle est ajoutée à <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-165">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="605f8-166">![Représentation sous forme de chaîne de la couleur de remplissage du cercle](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="605f8-166">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="605f8-167">Par défaut, le curseur change pendant une opération de glisser-déplacer pour indiquer l’effet du déplacement des données.</span><span class="sxs-lookup"><span data-stu-id="605f8-167">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="605f8-168">Vous pouvez personnaliser les commentaires donnés à l’utilisateur en gérant l' <xref:System.Windows.UIElement.GiveFeedback> événement et en définissant un autre curseur.</span><span class="sxs-lookup"><span data-stu-id="605f8-168">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="605f8-169">Envoyer des commentaires à l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="605f8-169">Give feedback to the user</span></span>

1. <span data-ttu-id="605f8-170">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="605f8-170">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="605f8-171">Ajoutez la <xref:System.Windows.UIElement.OnGiveFeedback%2A> substitution suivante pour fournir la gestion de classe pour l' <xref:System.Windows.UIElement.GiveFeedback> événement.</span><span class="sxs-lookup"><span data-stu-id="605f8-171">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="605f8-172">Ce <xref:System.Windows.UIElement.OnGiveFeedback%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-172">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="605f8-173">Vérifie les <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valeurs qui sont définies dans le gestionnaire d’événements de la cible de déplacement <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="605f8-173">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="605f8-174">Définit un curseur personnalisé en fonction de la <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valeur.</span><span class="sxs-lookup"><span data-stu-id="605f8-174">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="605f8-175">Le curseur a pour objectif de fournir des commentaires visuels à l’utilisateur sur l’effet du déplacement des données.</span><span class="sxs-lookup"><span data-stu-id="605f8-175">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="605f8-176">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="605f8-176">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="605f8-177">Faites glisser l’un des contrôles de cercle sur les panneaux, l’autre cercle et le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-177">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="605f8-178">Notez que les curseurs sont maintenant les curseurs personnalisés que vous avez spécifiés dans le <xref:System.Windows.UIElement.OnGiveFeedback%2A> remplacement.</span><span class="sxs-lookup"><span data-stu-id="605f8-178">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="605f8-179">![Glisser-déplacer avec des curseurs personnalisés](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="605f8-179">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="605f8-180">Sélectionnez le texte `green` à partir du <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-180">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="605f8-181">Faites glisser le texte `green` sur un contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-181">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="605f8-182">Notez que les curseurs par défaut sont affichés pour indiquer les effets de l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="605f8-182">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="605f8-183">Le curseur de commentaire est toujours défini par la source de glissement.</span><span class="sxs-lookup"><span data-stu-id="605f8-183">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="605f8-184">Implémenter les événements cible de déplacement dans le contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="605f8-184">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="605f8-185">Dans cette section, vous indiquez que le contrôle utilisateur est une cible de déplacement, vous substituez les méthodes qui permettent au contrôle utilisateur d’être une cible de déplacement et vous traitez les données qui sont déplacées sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="605f8-185">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="605f8-186">Pour permettre au contrôle utilisateur d’être une cible de déplacement</span><span class="sxs-lookup"><span data-stu-id="605f8-186">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="605f8-187">Ouvrez Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="605f8-187">Open Circle.xaml.</span></span>

2. <span data-ttu-id="605f8-188">Dans la <xref:System.Windows.Controls.UserControl> balise d’ouverture, ajoutez la <xref:System.Windows.UIElement.AllowDrop%2A> propriété et affectez-lui la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="605f8-188">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="605f8-189">La <xref:System.Windows.UIElement.OnDrop%2A> méthode est appelée lorsque la <xref:System.Windows.UIElement.AllowDrop%2A> propriété a la valeur `true` et que les données de la source de glissement sont déplacées sur le contrôle utilisateur Circle.</span><span class="sxs-lookup"><span data-stu-id="605f8-189">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="605f8-190">Dans cette méthode, vous traitez les données qui ont été déplacées et appliquez les données au cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-190">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="605f8-191">Pour traiter les données déplacées</span><span class="sxs-lookup"><span data-stu-id="605f8-191">To process the dropped data</span></span>

1. <span data-ttu-id="605f8-192">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="605f8-192">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="605f8-193">Ajoutez la <xref:System.Windows.UIElement.OnDrop%2A> substitution suivante pour fournir la gestion de classe pour l' <xref:System.Windows.UIElement.Drop> événement.</span><span class="sxs-lookup"><span data-stu-id="605f8-193">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="605f8-194">Ce <xref:System.Windows.UIElement.OnDrop%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-194">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="605f8-195">Utilise la <xref:System.Windows.DataObject.GetDataPresent%2A> méthode pour vérifier si les données glissées contiennent un objet String.</span><span class="sxs-lookup"><span data-stu-id="605f8-195">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="605f8-196">Utilise la <xref:System.Windows.DataObject.GetData%2A> méthode pour extraire les données de chaîne si elles sont présentes.</span><span class="sxs-lookup"><span data-stu-id="605f8-196">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="605f8-197">Utilise un <xref:System.Windows.Media.BrushConverter> pour essayer de convertir la chaîne en <xref:System.Windows.Media.Brush> .</span><span class="sxs-lookup"><span data-stu-id="605f8-197">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="605f8-198">Si la conversion réussit, applique le pinceau au <xref:System.Windows.Shapes.Shape.Fill%2A> du <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-198">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="605f8-199">Marque l' <xref:System.Windows.UIElement.Drop> événement comme géré.</span><span class="sxs-lookup"><span data-stu-id="605f8-199">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="605f8-200">Vous devez marquer l’événement de déplacement comme étant géré pour que les autres éléments qui reçoivent cet événement sachent que le contrôle utilisateur de cercle l’a géré.</span><span class="sxs-lookup"><span data-stu-id="605f8-200">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="605f8-201">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="605f8-201">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="605f8-202">Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-202">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="605f8-203">Faites glisser le texte vers un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="605f8-203">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="605f8-204">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="605f8-204">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="605f8-205">![Convertir une chaîne en pinceau](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="605f8-205">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="605f8-206">Tapez le texte `green` dans le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-206">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="605f8-207">Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-207">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="605f8-208">Faites le glisser vers un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="605f8-208">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="605f8-209">Notez que le curseur change pour indiquer que le déplacement est autorisé, mais la couleur du cercle ne change pas, car `gre` n’est pas une couleur valide.</span><span class="sxs-lookup"><span data-stu-id="605f8-209">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="605f8-210">Faites glisser le contrôle de cercle vert et déplacez-le sur le contrôle de cercle bleu.</span><span class="sxs-lookup"><span data-stu-id="605f8-210">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="605f8-211">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="605f8-211">The Circle changes from blue to green.</span></span> <span data-ttu-id="605f8-212">Notez que le curseur affiché varie selon que le <xref:System.Windows.Controls.TextBox> ou le cercle est la source du glissement.</span><span class="sxs-lookup"><span data-stu-id="605f8-212">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="605f8-213">Le fait <xref:System.Windows.UIElement.AllowDrop%2A> de définir la propriété sur `true` et de traiter les données déplacées est tout ce qui est nécessaire pour permettre à un élément d’être une cible de déplacement.</span><span class="sxs-lookup"><span data-stu-id="605f8-213">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="605f8-214">Toutefois, pour offrir une meilleure expérience utilisateur, vous devez également gérer les <xref:System.Windows.UIElement.DragEnter> <xref:System.Windows.UIElement.DragLeave> événements, et <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="605f8-214">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="605f8-215">Dans ces événements, vous pouvez effectuer des vérifications et fournir des commentaires supplémentaires à l’utilisateur avant de déplacer les données.</span><span class="sxs-lookup"><span data-stu-id="605f8-215">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="605f8-216">Quand les données sont glissées sur le contrôle utilisateur de cercle, le contrôle doit notifier la source de glissement si elle peut ou non traiter les données en cours de glissement.</span><span class="sxs-lookup"><span data-stu-id="605f8-216">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="605f8-217">Si le contrôle ne sait pas comment traiter les données, il doit refuser le déplacement.</span><span class="sxs-lookup"><span data-stu-id="605f8-217">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="605f8-218">Pour ce faire, vous allez gérer l' <xref:System.Windows.UIElement.DragOver> événement et définir la <xref:System.Windows.DragEventArgs.Effects%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="605f8-218">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="605f8-219">Pour vérifier que le déplacement de données est autorisé</span><span class="sxs-lookup"><span data-stu-id="605f8-219">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="605f8-220">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="605f8-220">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="605f8-221">Ajoutez la <xref:System.Windows.UIElement.OnDragOver%2A> substitution suivante pour fournir la gestion de classe pour l' <xref:System.Windows.UIElement.DragOver> événement.</span><span class="sxs-lookup"><span data-stu-id="605f8-221">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="605f8-222">Ce <xref:System.Windows.UIElement.OnDragOver%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-222">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="605f8-223">Affecte la valeur <xref:System.Windows.DragEventArgs.Effects%2A> à la propriété <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="605f8-223">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="605f8-224">Effectue les mêmes vérifications que celles effectuées dans la <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si le contrôle utilisateur Circle peut traiter les données glissées.</span><span class="sxs-lookup"><span data-stu-id="605f8-224">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="605f8-225">Si le contrôle utilisateur peut traiter les données, affecte <xref:System.Windows.DragEventArgs.Effects%2A> à la propriété la valeur <xref:System.Windows.DragDropEffects.Copy> ou <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="605f8-225">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="605f8-226">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="605f8-226">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="605f8-227">Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-227">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="605f8-228">Faites glisser le texte vers un contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-228">Drag the text to a Circle control.</span></span> <span data-ttu-id="605f8-229">Notez que le curseur change à présent pour indiquer que le déplacement n’est pas autorisé, car `gre` n’est pas une couleur valide.</span><span class="sxs-lookup"><span data-stu-id="605f8-229">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="605f8-230">Vous pouvez améliorer l’expérience utilisateur en appliquant un aperçu de l’opération de déplacement.</span><span class="sxs-lookup"><span data-stu-id="605f8-230">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="605f8-231">Pour le contrôle utilisateur Circle, vous allez substituer les <xref:System.Windows.UIElement.OnDragEnter%2A> <xref:System.Windows.UIElement.OnDragLeave%2A> méthodes et.</span><span class="sxs-lookup"><span data-stu-id="605f8-231">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="605f8-232">Lorsque les données sont glissées sur le contrôle, l’arrière-plan actuel <xref:System.Windows.Shapes.Shape.Fill%2A> est enregistré dans une variable d’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="605f8-232">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="605f8-233">La chaîne est ensuite convertie en pinceau et appliquée au <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-233">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="605f8-234">Si les données sont déplacées en dehors du cercle sans être supprimées, la valeur d’origine <xref:System.Windows.Shapes.Shape.Fill%2A> est réappliquée au cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-234">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="605f8-235">Pour afficher un aperçu du résultat de l’opération de glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="605f8-235">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="605f8-236">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="605f8-236">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="605f8-237">Dans la classe Circle, déclarez une <xref:System.Windows.Media.Brush> variable privée nommée `_previousFill` et initialisez-la sur `null` .</span><span class="sxs-lookup"><span data-stu-id="605f8-237">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="605f8-238">Ajoutez la <xref:System.Windows.UIElement.OnDragEnter%2A> substitution suivante pour fournir la gestion de classe pour l' <xref:System.Windows.UIElement.DragEnter> événement.</span><span class="sxs-lookup"><span data-stu-id="605f8-238">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="605f8-239">Ce <xref:System.Windows.UIElement.OnDragEnter%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-239">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="605f8-240">Enregistre la <xref:System.Windows.Shapes.Shape.Fill%2A> propriété de <xref:System.Windows.Shapes.Ellipse> dans la `_previousFill` variable.</span><span class="sxs-lookup"><span data-stu-id="605f8-240">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="605f8-241">Effectue les mêmes vérifications que celles effectuées dans la <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si les données peuvent être converties en <xref:System.Windows.Media.Brush> .</span><span class="sxs-lookup"><span data-stu-id="605f8-241">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="605f8-242">Si les données sont converties en valides <xref:System.Windows.Media.Brush> , l’applique à l’objet <xref:System.Windows.Shapes.Shape.Fill%2A> de l’objet <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="605f8-242">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="605f8-243">Ajoutez la <xref:System.Windows.UIElement.OnDragLeave%2A> substitution suivante pour fournir la gestion de classe pour l' <xref:System.Windows.UIElement.DragLeave> événement.</span><span class="sxs-lookup"><span data-stu-id="605f8-243">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="605f8-244">Ce <xref:System.Windows.UIElement.OnDragLeave%2A> remplacement effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-244">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="605f8-245">Applique l' <xref:System.Windows.Media.Brush> enregistrement dans la `_previousFill` variable au <xref:System.Windows.Shapes.Shape.Fill%2A> du <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du contrôle utilisateur de cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-245">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="605f8-246">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="605f8-246">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="605f8-247">Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-247">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="605f8-248">Faites glisser le texte sur un contrôle de cercle sans le déplacer.</span><span class="sxs-lookup"><span data-stu-id="605f8-248">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="605f8-249">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="605f8-249">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="605f8-250">![Prévisualiser les effets d’une opération de glisser-déplacer&#45;et&#45;](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="605f8-250">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="605f8-251">Faites glisser le texte en dehors du contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="605f8-251">Drag the text away from the Circle control.</span></span> <span data-ttu-id="605f8-252">Le cercle passe du vert au bleu.</span><span class="sxs-lookup"><span data-stu-id="605f8-252">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="605f8-253">Permettre à un panneau de recevoir des données déplacées</span><span class="sxs-lookup"><span data-stu-id="605f8-253">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="605f8-254">Dans cette section, vous allez activer les panneaux qui hébergent les contrôles utilisateur de cercle pour agir en tant que cibles de dépôt pour les données de cercle glissées.</span><span class="sxs-lookup"><span data-stu-id="605f8-254">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="605f8-255">Vous allez implémenter le code qui vous permet de déplacer un cercle d’un panneau à un autre, ou de faire une copie d’un contrôle de cercle en maintenant la touche **CTRL** enfoncée tout en faisant glisser un cercle et en le déposant.</span><span class="sxs-lookup"><span data-stu-id="605f8-255">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="605f8-256">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="605f8-256">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="605f8-257">Comme indiqué dans le code XAML suivant, dans chacun des <xref:System.Windows.Controls.StackPanel> contrôles, ajoutez des gestionnaires pour les <xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop> événements et.</span><span class="sxs-lookup"><span data-stu-id="605f8-257">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="605f8-258">Nommez le <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements, `panel_DragOver` et nommez le <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements, `panel_Drop` .</span><span class="sxs-lookup"><span data-stu-id="605f8-258">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="605f8-259">Ouvrez MainWindows.xaml.cs ou MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="605f8-259">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="605f8-260">Ajoutez le code suivant pour le <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="605f8-260">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="605f8-261">Ce <xref:System.Windows.UIElement.DragOver> Gestionnaire d’événements effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-261">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="605f8-262">Vérifie que les données déplacées contiennent les données d’objet qui ont été empaquetées dans le <xref:System.Windows.DataObject> par le contrôle utilisateur Circle et passées dans l’appel à <xref:System.Windows.DragDrop.DoDragDrop%2A> .</span><span class="sxs-lookup"><span data-stu-id="605f8-262">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="605f8-263">Si les données d’objet sont présentes, vérifie si la touche **CTRL** est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="605f8-263">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="605f8-264">Si la touche **CTRL** est enfoncée, affecte la <xref:System.Windows.DragEventArgs.Effects%2A> valeur à la propriété <xref:System.Windows.DragDropEffects.Copy> .</span><span class="sxs-lookup"><span data-stu-id="605f8-264">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="605f8-265">Sinon, affectez <xref:System.Windows.DragEventArgs.Effects%2A> à la propriété la valeur <xref:System.Windows.DragDropEffects.Move> .</span><span class="sxs-lookup"><span data-stu-id="605f8-265">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="605f8-266">Ajoutez le code suivant pour le <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="605f8-266">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="605f8-267">Ce <xref:System.Windows.UIElement.Drop> Gestionnaire d’événements effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="605f8-267">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="605f8-268">Vérifie si l' <xref:System.Windows.UIElement.Drop> événement a déjà été géré.</span><span class="sxs-lookup"><span data-stu-id="605f8-268">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="605f8-269">Par exemple, si un cercle est déposé sur un autre cercle qui gère l' <xref:System.Windows.UIElement.Drop> événement, vous ne souhaitez pas que le panneau qui contient le cercle le gère également.</span><span class="sxs-lookup"><span data-stu-id="605f8-269">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="605f8-270">Si l' <xref:System.Windows.UIElement.Drop> événement n’est pas géré, vérifie si la touche **CTRL** est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="605f8-270">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="605f8-271">Si la touche **CTRL** est enfoncée lorsque le <xref:System.Windows.UIElement.Drop> se produit, effectue une copie du contrôle Circle et l’ajoute à la <xref:System.Windows.Controls.Panel.Children%2A> collection de <xref:System.Windows.Controls.StackPanel> .</span><span class="sxs-lookup"><span data-stu-id="605f8-271">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="605f8-272">Si la touche **CTRL** n’est pas enfoncée, déplace le cercle de la <xref:System.Windows.Controls.Panel.Children%2A> collection de son panneau parent vers la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau sur lequel il a été déposé.</span><span class="sxs-lookup"><span data-stu-id="605f8-272">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="605f8-273">Définit la <xref:System.Windows.DragEventArgs.Effects%2A> propriété pour indiquer à la <xref:System.Windows.DragDrop.DoDragDrop%2A> méthode si une opération de déplacement ou de copie a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="605f8-273">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="605f8-274">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="605f8-274">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="605f8-275">Sélectionnez le texte `green` à partir du <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="605f8-275">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="605f8-276">Faites glisser le texte sur un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="605f8-276">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="605f8-277">Faites glisser un contrôle de cercle du panneau gauche vers le panneau droit et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="605f8-277">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="605f8-278">Le cercle est supprimé de la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau gauche et ajouté à la collection Children du panneau droit.</span><span class="sxs-lookup"><span data-stu-id="605f8-278">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="605f8-279">Faites glisser un contrôle Circle du panneau dans lequel il se trouve et déposez-le tout en appuyant sur la touche **CTRL** .</span><span class="sxs-lookup"><span data-stu-id="605f8-279">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="605f8-280">Le cercle est copié et la copie est ajoutée à la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau de réception.</span><span class="sxs-lookup"><span data-stu-id="605f8-280">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="605f8-281">![Glissement d'un cercle tout en appuyant sur la touche CTRL](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="605f8-281">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="605f8-282">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="605f8-282">See also</span></span>

- [<span data-ttu-id="605f8-283">Vue d'ensemble du glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="605f8-283">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
