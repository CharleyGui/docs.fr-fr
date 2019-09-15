---
title: 'Procédure pas à pas : activation de Glisser-déplacer sur un contrôle utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 172e49c2c255db4d24d2180f919b1305326b5e82
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991808"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a><span data-ttu-id="c7f88-102">Procédure pas à pas : activation de Glisser-déplacer sur un contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="c7f88-102">Walkthrough: Enabling Drag and Drop on a User Control</span></span>

<span data-ttu-id="c7f88-103">Cette procédure pas à pas montre comment créer un contrôle utilisateur personnalisé qui peut participer à un transfert de données par glisser-déplacer dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7f88-103">This walkthrough demonstrates how to create a custom user control that can participate in drag-and-drop data transfer in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>

<span data-ttu-id="c7f88-104">Dans cette procédure pas à pas, vous allez créer <xref:System.Windows.Controls.UserControl> un WPF personnalisé qui représente une forme de cercle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-104">In this walkthrough, you will create a custom WPF <xref:System.Windows.Controls.UserControl> that represents a circle shape.</span></span> <span data-ttu-id="c7f88-105">Vous implémentez la fonctionnalité sur le contrôle pour activer le transfert de données par glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="c7f88-105">You will implement functionality on the control to enable data transfer through drag-and-drop.</span></span> <span data-ttu-id="c7f88-106">Par exemple, si vous faites glisser un contrôle de cercle sur un autre, les données de couleur de remplissage sont copiées du cercle source vers la cible.</span><span class="sxs-lookup"><span data-stu-id="c7f88-106">For example, if you drag from one Circle control to another, the Fill color data is copied from the source Circle to the target.</span></span> <span data-ttu-id="c7f88-107">Si vous faites glisser un contrôle Circle vers un <xref:System.Windows.Controls.TextBox>, la représentation sous forme de chaîne de la couleur de remplissage <xref:System.Windows.Controls.TextBox>est copiée dans le.</span><span class="sxs-lookup"><span data-stu-id="c7f88-107">If you drag from a Circle control to a <xref:System.Windows.Controls.TextBox>, the string representation of the Fill color is copied to the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7f88-108">Vous allez également créer une petite application qui contient deux contrôles de panneau et <xref:System.Windows.Controls.TextBox> un pour tester la fonctionnalité de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="c7f88-108">You will also create a small application that contains two panel controls and a <xref:System.Windows.Controls.TextBox> to test the drag-and-drop functionality.</span></span> <span data-ttu-id="c7f88-109">Vous écrivez du code qui permet aux panneaux de traiter les données de cercle déplacées, ce qui vous permet de déplacer ou copier des cercles de la collection d’enfants d’un panneau à l’autre.</span><span class="sxs-lookup"><span data-stu-id="c7f88-109">You will write code that enables the panels to process dropped Circle data, which will enable you to move or copy Circles from the Children collection of one panel to the other.</span></span>

<span data-ttu-id="c7f88-110">Cette procédure pas à pas décrit les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="c7f88-110">This walkthrough illustrates the following tasks:</span></span>

- <span data-ttu-id="c7f88-111">Créer un contrôle utilisateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c7f88-111">Create a custom user control.</span></span>

- <span data-ttu-id="c7f88-112">Permettre au contrôle utilisateur d’être une source de glissement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-112">Enable the user control to be a drag source.</span></span>

- <span data-ttu-id="c7f88-113">Permettre au contrôle utilisateur d’être une cible de déplacement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-113">Enable the user control to be a drop target.</span></span>

- <span data-ttu-id="c7f88-114">Permettre à un panneau de recevoir des données déplacées à partir du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7f88-114">Enable a panel to receive data dropped from the user control.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7f88-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="c7f88-115">Prerequisites</span></span>

<span data-ttu-id="c7f88-116">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7f88-116">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-application-project"></a><span data-ttu-id="c7f88-117">Créer le projet d’application</span><span class="sxs-lookup"><span data-stu-id="c7f88-117">Create the Application Project</span></span>
 <span data-ttu-id="c7f88-118">Dans cette section, vous allez créer l’infrastructure de l’application, qui comprend une page principale avec deux panneaux <xref:System.Windows.Controls.TextBox>et un.</span><span class="sxs-lookup"><span data-stu-id="c7f88-118">In this section, you will create the application infrastructure, which includes a main page with two panels and a <xref:System.Windows.Controls.TextBox>.</span></span>

1. <span data-ttu-id="c7f88-119">Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `DragDropExample`.</span><span class="sxs-lookup"><span data-stu-id="c7f88-119">Create a new WPF Application project in Visual Basic or Visual C# named `DragDropExample`.</span></span> <span data-ttu-id="c7f88-120">Pour plus d’informations, consultez [Procédure pas à pas : Ma première application](../getting-started/walkthrough-my-first-wpf-desktop-application.md)de bureau WPF.</span><span class="sxs-lookup"><span data-stu-id="c7f88-120">For more information, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

2. <span data-ttu-id="c7f88-121">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7f88-121">Open MainWindow.xaml.</span></span>

3. <span data-ttu-id="c7f88-122">Ajoutez le balisage suivant entre les balises <xref:System.Windows.Controls.Grid> d’ouverture et de fermeture.</span><span class="sxs-lookup"><span data-stu-id="c7f88-122">Add the following markup between the opening and closing <xref:System.Windows.Controls.Grid> tags.</span></span>

     <span data-ttu-id="c7f88-123">Ce balisage crée l’interface utilisateur pour l’application de test.</span><span class="sxs-lookup"><span data-stu-id="c7f88-123">This markup creates the user interface for the test application.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a><span data-ttu-id="c7f88-124">Ajouter un nouveau contrôle utilisateur au projet</span><span class="sxs-lookup"><span data-stu-id="c7f88-124">Add a New User Control to the Project</span></span>
 <span data-ttu-id="c7f88-125">Dans cette section, vous ajoutez un nouveau contrôle utilisateur au projet.</span><span class="sxs-lookup"><span data-stu-id="c7f88-125">In this section, you will add a new user control to the project.</span></span>

1. <span data-ttu-id="c7f88-126">Dans le menu Projet, sélectionnez **Ajouter un contrôle utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="c7f88-126">On the Project menu, select **Add User Control**.</span></span>

2. <span data-ttu-id="c7f88-127">Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le `Circle.xaml`nom par, puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c7f88-127">In the **Add New Item** dialog box, change the name to `Circle.xaml`, and click **Add**.</span></span>

     <span data-ttu-id="c7f88-128">Circle.XAML et son code-behind sont ajoutés au projet.</span><span class="sxs-lookup"><span data-stu-id="c7f88-128">Circle.xaml and its code-behind is added to the project.</span></span>

3. <span data-ttu-id="c7f88-129">Ouvrez Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7f88-129">Open Circle.xaml.</span></span>

     <span data-ttu-id="c7f88-130">Ce fichier doit contenir les éléments d’interface utilisateur du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7f88-130">This file will contain the user interface elements of the user control.</span></span>

4. <span data-ttu-id="c7f88-131">Ajoutez le balisage suivant à la <xref:System.Windows.Controls.Grid> racine pour créer un contrôle utilisateur simple dont l’interface utilisateur est un cercle bleu.</span><span class="sxs-lookup"><span data-stu-id="c7f88-131">Add the following markup to the root <xref:System.Windows.Controls.Grid> to create a simple user control that has a blue circle as its UI.</span></span>

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. <span data-ttu-id="c7f88-132">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c7f88-132">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

6. <span data-ttu-id="c7f88-133">Dans C#, ajoutez le code suivant après le constructeur sans paramètre pour créer un constructeur de copie.</span><span class="sxs-lookup"><span data-stu-id="c7f88-133">In C#, add the following code after the parameterless constructor to create a copy constructor.</span></span> <span data-ttu-id="c7f88-134">Dans Visual Basic, ajoutez le code suivant pour créer un constructeur sans paramètre et un constructeur de copie.</span><span class="sxs-lookup"><span data-stu-id="c7f88-134">In Visual Basic, add the following code to create both a parameterless constructor and a copy constructor.</span></span>

     <span data-ttu-id="c7f88-135">Pour que le contrôle utilisateur puisse être copié, vous ajoutez une méthode de constructeur de copie dans le fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="c7f88-135">In order to allow the user control to be copied, you add a copy constructor method in the code-behind file.</span></span> <span data-ttu-id="c7f88-136">Dans le contrôle utilisateur de cercle simplifié, vous copiez uniquement les valeurs de remplissage et de taille du contrôle utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7f88-136">In the simplified Circle user control, you will only copy the Fill and the size of the of the user control.</span></span>

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a><span data-ttu-id="c7f88-137">Ajouter le contrôle utilisateur à la fenêtre principale</span><span class="sxs-lookup"><span data-stu-id="c7f88-137">Add the user control to the main window</span></span>

1. <span data-ttu-id="c7f88-138">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7f88-138">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="c7f88-139">Ajoutez le code XAML suivant à la <xref:System.Windows.Window> balise d’ouverture pour créer une référence d’espace de noms XML à l’application actuelle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-139">Add the following XAML to the opening <xref:System.Windows.Window> tag to create an XML namespace reference to the current application.</span></span>

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. <span data-ttu-id="c7f88-140">Dans le premier <xref:System.Windows.Controls.StackPanel>, ajoutez le code XAML suivant pour créer deux instances du contrôle utilisateur Circle dans le premier panneau.</span><span class="sxs-lookup"><span data-stu-id="c7f88-140">In the first <xref:System.Windows.Controls.StackPanel>, add the following XAML to create two instances of the Circle user control in the first panel.</span></span>

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     <span data-ttu-id="c7f88-141">Le code XAML complet pour le panneau ressemble à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="c7f88-141">The full XAML for the panel looks like the following.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a><span data-ttu-id="c7f88-142">Implémenter les événements de source de glissement dans le contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="c7f88-142">Implement Drag Source Events in the User Control</span></span>
 <span data-ttu-id="c7f88-143">Dans cette section, vous allez substituer la <xref:System.Windows.UIElement.OnMouseMove%2A> méthode et lancer l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="c7f88-143">In this section, you will override the <xref:System.Windows.UIElement.OnMouseMove%2A> method and initiate the drag-and-drop operation.</span></span>

 <span data-ttu-id="c7f88-144">Si un glisser-déplacer est démarré (un bouton de la souris est enfoncé et que la souris est déplacée), vous allez empaqueter les données à transférer dans un <xref:System.Windows.DataObject>.</span><span class="sxs-lookup"><span data-stu-id="c7f88-144">If a drag is started (a mouse button is pressed and the mouse is moved), you will package the data to be transferred into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="c7f88-145">Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.</span><span class="sxs-lookup"><span data-stu-id="c7f88-145">In this case, the Circle control will package three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

### <a name="to-initiate-a-drag-and-drop-operation"></a><span data-ttu-id="c7f88-146">Pour lancer une opération de glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="c7f88-146">To initiate a drag-and-drop operation</span></span>

1. <span data-ttu-id="c7f88-147">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c7f88-147">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7f88-148">Ajoutez la substitution <xref:System.Windows.UIElement.OnMouseMove%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.MouseMove> l’événement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-148">Add the following <xref:System.Windows.UIElement.OnMouseMove%2A> override to provide class handling for the <xref:System.Windows.UIElement.MouseMove> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     <span data-ttu-id="c7f88-149">Ce <xref:System.Windows.UIElement.OnMouseMove%2A> remplacement effectue les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="c7f88-149">This <xref:System.Windows.UIElement.OnMouseMove%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7f88-150">Vérifie si le bouton gauche de la souris est enfoncé quand la souris se déplace.</span><span class="sxs-lookup"><span data-stu-id="c7f88-150">Checks whether the left mouse button is pressed while the mouse is moving.</span></span>

    - <span data-ttu-id="c7f88-151">Empaquette les données de <xref:System.Windows.DataObject>cercle dans un.</span><span class="sxs-lookup"><span data-stu-id="c7f88-151">Packages the Circle data into a <xref:System.Windows.DataObject>.</span></span> <span data-ttu-id="c7f88-152">Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.</span><span class="sxs-lookup"><span data-stu-id="c7f88-152">In this case, the Circle control packages three data items; a string representation of its Fill color, a double representation of its height, and a copy of itself.</span></span>

    - <span data-ttu-id="c7f88-153">Appelle la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> statique pour initier l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="c7f88-153">Calls the static <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> method to initiate the drag-and-drop operation.</span></span> <span data-ttu-id="c7f88-154">Vous transmettez les trois paramètres suivants à <xref:System.Windows.DragDrop.DoDragDrop%2A> la méthode:</span><span class="sxs-lookup"><span data-stu-id="c7f88-154">You pass the following three parameters to the <xref:System.Windows.DragDrop.DoDragDrop%2A> method:</span></span>

        - <span data-ttu-id="c7f88-155">`dragSource` : Référence à ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-155">`dragSource` – A reference to this control.</span></span>

        - <span data-ttu-id="c7f88-156">`data`: Le <xref:System.Windows.DataObject> créé dans le code précédent.</span><span class="sxs-lookup"><span data-stu-id="c7f88-156">`data` – The <xref:System.Windows.DataObject> created in the previous code.</span></span>

        - <span data-ttu-id="c7f88-157">`allowedEffects`: Les opérations de glisser-déplacer autorisées, qui sont <xref:System.Windows.DragDropEffects.Copy> ou. <xref:System.Windows.DragDropEffects.Move></span><span class="sxs-lookup"><span data-stu-id="c7f88-157">`allowedEffects` – The allowed drag-and-drop operations, which are <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="c7f88-158">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="c7f88-158">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="c7f88-159">Cliquez sur l’un des contrôles de cercle et faites-le glisser sur les panneaux, l’autre <xref:System.Windows.Controls.TextBox>cercle et le.</span><span class="sxs-lookup"><span data-stu-id="c7f88-159">Click one of the Circle controls and drag it over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7f88-160">Lorsque vous faites glisser le <xref:System.Windows.Controls.TextBox>pointeur de la souris sur le, le curseur change pour indiquer un déplacement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-160">When dragging over the <xref:System.Windows.Controls.TextBox>, the cursor changes to indicate a move.</span></span>

5. <span data-ttu-id="c7f88-161">Tout en faisant glisser un cercle sur <xref:System.Windows.Controls.TextBox>le, appuyez sur la touche **CTRL** .</span><span class="sxs-lookup"><span data-stu-id="c7f88-161">While dragging a Circle over the <xref:System.Windows.Controls.TextBox>, press the **Ctrl** key.</span></span> <span data-ttu-id="c7f88-162">Notez que le curseur change pour indiquer une copie.</span><span class="sxs-lookup"><span data-stu-id="c7f88-162">Notice how the cursor changes to indicate a copy.</span></span>

6. <span data-ttu-id="c7f88-163">Glissez-déposez un <xref:System.Windows.Controls.TextBox>cercle sur le.</span><span class="sxs-lookup"><span data-stu-id="c7f88-163">Drag and drop a Circle onto the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7f88-164">La représentation sous forme de chaîne de la couleur de remplissage du cercle est <xref:System.Windows.Controls.TextBox>ajoutée à.</span><span class="sxs-lookup"><span data-stu-id="c7f88-164">The string representation of the Circle’s fill color is appended to the <xref:System.Windows.Controls.TextBox>.</span></span>

     <span data-ttu-id="c7f88-165">![Représentation sous forme de chaîne de la couleur de remplissage du cercle](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span><span class="sxs-lookup"><span data-stu-id="c7f88-165">![String representation of Circle's fill color](./media/dragdrop-colorstring.png "DragDrop_ColorString")</span></span>

<span data-ttu-id="c7f88-166">Par défaut, le curseur change pendant une opération de glisser-déplacer pour indiquer l’effet du déplacement des données.</span><span class="sxs-lookup"><span data-stu-id="c7f88-166">By default, the cursor will change during a drag-and-drop operation to indicate what effect dropping the data will have.</span></span> <span data-ttu-id="c7f88-167">Vous pouvez personnaliser les commentaires donnés à l’utilisateur en gérant l' <xref:System.Windows.UIElement.GiveFeedback> événement et en définissant un autre curseur.</span><span class="sxs-lookup"><span data-stu-id="c7f88-167">You can customize the feedback given to the user by handling the <xref:System.Windows.UIElement.GiveFeedback> event and setting a different cursor.</span></span>

## <a name="give-feedback-to-the-user"></a><span data-ttu-id="c7f88-168">Envoyer des commentaires à l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="c7f88-168">Give feedback to the user</span></span>

1. <span data-ttu-id="c7f88-169">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c7f88-169">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7f88-170">Ajoutez la substitution <xref:System.Windows.UIElement.OnGiveFeedback%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.GiveFeedback> l’événement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-170">Add the following <xref:System.Windows.UIElement.OnGiveFeedback%2A> override to provide class handling for the <xref:System.Windows.UIElement.GiveFeedback> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     <span data-ttu-id="c7f88-171">Ce <xref:System.Windows.UIElement.OnGiveFeedback%2A> remplacement effectue les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="c7f88-171">This <xref:System.Windows.UIElement.OnGiveFeedback%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7f88-172">Vérifie les <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valeurs qui sont définies dans le gestionnaire d’événements <xref:System.Windows.UIElement.DragOver> de la cible de déplacement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-172">Checks the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> values that are set in the drop target's <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

    - <span data-ttu-id="c7f88-173">Définit un curseur personnalisé en fonction de <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> la valeur.</span><span class="sxs-lookup"><span data-stu-id="c7f88-173">Sets a custom cursor based on the <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> value.</span></span> <span data-ttu-id="c7f88-174">Le curseur a pour objectif de fournir des commentaires visuels à l’utilisateur sur l’effet du déplacement des données.</span><span class="sxs-lookup"><span data-stu-id="c7f88-174">The cursor is intended to give visual feedback to the user about what effect dropping the data will have.</span></span>

3. <span data-ttu-id="c7f88-175">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="c7f88-175">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="c7f88-176">Faites glisser l’un des contrôles de cercle sur les panneaux, l’autre cercle et <xref:System.Windows.Controls.TextBox>le.</span><span class="sxs-lookup"><span data-stu-id="c7f88-176">Drag one of the Circle controls over the panels, the other Circle, and the <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="c7f88-177">Notez que les curseurs sont maintenant les curseurs personnalisés que vous avez spécifiés <xref:System.Windows.UIElement.OnGiveFeedback%2A> dans le remplacement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-177">Notice that the cursors are now the custom cursors that you specified in the <xref:System.Windows.UIElement.OnGiveFeedback%2A> override.</span></span>

     <span data-ttu-id="c7f88-178">![Glisser-déplacer avec des curseurs personnalisés](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span><span class="sxs-lookup"><span data-stu-id="c7f88-178">![Drag and drop with custom cursors](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")</span></span>

5. <span data-ttu-id="c7f88-179">Sélectionnez le texte `green` <xref:System.Windows.Controls.TextBox>à partir du.</span><span class="sxs-lookup"><span data-stu-id="c7f88-179">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

6. <span data-ttu-id="c7f88-180">Faites glisser le texte `green` sur un contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-180">Drag the `green` text to a Circle control.</span></span> <span data-ttu-id="c7f88-181">Notez que les curseurs par défaut sont affichés pour indiquer les effets de l’opération de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="c7f88-181">Notice that the default cursors are shown to indicate the effects of the drag-and-drop operation.</span></span> <span data-ttu-id="c7f88-182">Le curseur de commentaire est toujours défini par la source de glissement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-182">The feedback cursor is always set by the drag source.</span></span>

## <a name="implement-drop-target-events-in-the-user-control"></a><span data-ttu-id="c7f88-183">Implémenter les événements cible de déplacement dans le contrôle utilisateur</span><span class="sxs-lookup"><span data-stu-id="c7f88-183">Implement Drop Target Events in the User Control</span></span>
 <span data-ttu-id="c7f88-184">Dans cette section, vous indiquez que le contrôle utilisateur est une cible de déplacement, vous substituez les méthodes qui permettent au contrôle utilisateur d’être une cible de déplacement et vous traitez les données qui sont déplacées sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c7f88-184">In this section, you will specify that the user control is a drop target, override the methods that enable the user control to be a drop target, and process the data that is dropped on it.</span></span>

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a><span data-ttu-id="c7f88-185">Pour permettre au contrôle utilisateur d’être une cible de déplacement</span><span class="sxs-lookup"><span data-stu-id="c7f88-185">To enable the user control to be a drop target</span></span>

1. <span data-ttu-id="c7f88-186">Ouvrez Circle.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7f88-186">Open Circle.xaml.</span></span>

2. <span data-ttu-id="c7f88-187">Dans la balise d’ouverture <xref:System.Windows.Controls.UserControl> , ajoutez la `true`propriété et affectez-lui la <xref:System.Windows.UIElement.AllowDrop%2A> valeur.</span><span class="sxs-lookup"><span data-stu-id="c7f88-187">In the opening <xref:System.Windows.Controls.UserControl> tag, add the <xref:System.Windows.UIElement.AllowDrop%2A> property and set it to `true`.</span></span>

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

<span data-ttu-id="c7f88-188">La <xref:System.Windows.UIElement.OnDrop%2A> méthode est appelée lorsque la <xref:System.Windows.UIElement.AllowDrop%2A> propriété a la valeur `true` et que les données de la source de glissement sont déplacées sur le contrôle utilisateur Circle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-188">The <xref:System.Windows.UIElement.OnDrop%2A> method is called when the <xref:System.Windows.UIElement.AllowDrop%2A> property is set to `true` and data from the drag source is dropped on the Circle user control.</span></span> <span data-ttu-id="c7f88-189">Dans cette méthode, vous traitez les données qui ont été déplacées et appliquez les données au cercle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-189">In this method, you will process the data that was dropped and apply the data to the Circle.</span></span>

### <a name="to-process-the-dropped-data"></a><span data-ttu-id="c7f88-190">Pour traiter les données déplacées</span><span class="sxs-lookup"><span data-stu-id="c7f88-190">To process the dropped data</span></span>

1. <span data-ttu-id="c7f88-191">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c7f88-191">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7f88-192">Ajoutez la substitution <xref:System.Windows.UIElement.OnDrop%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.Drop> l’événement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-192">Add the following <xref:System.Windows.UIElement.OnDrop%2A> override to provide class handling for the <xref:System.Windows.UIElement.Drop> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     <span data-ttu-id="c7f88-193">Ce <xref:System.Windows.UIElement.OnDrop%2A> remplacement effectue les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="c7f88-193">This <xref:System.Windows.UIElement.OnDrop%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7f88-194">Utilise la <xref:System.Windows.DataObject.GetDataPresent%2A> méthode pour vérifier si les données glissées contiennent un objet String.</span><span class="sxs-lookup"><span data-stu-id="c7f88-194">Uses the <xref:System.Windows.DataObject.GetDataPresent%2A> method to check if the dragged data contains a string object.</span></span>

    - <span data-ttu-id="c7f88-195">Utilise la <xref:System.Windows.DataObject.GetData%2A> méthode pour extraire les données de chaîne si elles sont présentes.</span><span class="sxs-lookup"><span data-stu-id="c7f88-195">Uses the <xref:System.Windows.DataObject.GetData%2A> method to extract the string data if it is present.</span></span>

    - <span data-ttu-id="c7f88-196">Utilise un <xref:System.Windows.Media.BrushConverter> pour essayer de convertir la chaîne <xref:System.Windows.Media.Brush>en.</span><span class="sxs-lookup"><span data-stu-id="c7f88-196">Uses a <xref:System.Windows.Media.BrushConverter> to try to convert the string to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="c7f88-197">Si la conversion réussit, applique le pinceau au <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> du qui fournit l’interface utilisateur du contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-197">If the conversion is successful, applies the brush to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle control.</span></span>

    - <span data-ttu-id="c7f88-198">Marque l' <xref:System.Windows.UIElement.Drop> événement comme géré.</span><span class="sxs-lookup"><span data-stu-id="c7f88-198">Marks the <xref:System.Windows.UIElement.Drop> event as handled.</span></span> <span data-ttu-id="c7f88-199">Vous devez marquer l’événement de déplacement comme étant géré pour que les autres éléments qui reçoivent cet événement sachent que le contrôle utilisateur de cercle l’a géré.</span><span class="sxs-lookup"><span data-stu-id="c7f88-199">You should mark the drop event as handled so that other elements that receive this event know that the Circle user control handled it.</span></span>

3. <span data-ttu-id="c7f88-200">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="c7f88-200">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="c7f88-201">Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7f88-201">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="c7f88-202">Faites glisser le texte vers un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="c7f88-202">Drag the text to a Circle control and drop it.</span></span> <span data-ttu-id="c7f88-203">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="c7f88-203">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="c7f88-204">![Convertir une chaîne en pinceau](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span><span class="sxs-lookup"><span data-stu-id="c7f88-204">![Convert a string to a brush](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")</span></span>

6. <span data-ttu-id="c7f88-205">Tapez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7f88-205">Type the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="c7f88-206">Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7f88-206">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="c7f88-207">Faites le glisser vers un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="c7f88-207">Drag it to a Circle control and drop it.</span></span> <span data-ttu-id="c7f88-208">Notez que le curseur change pour indiquer que le déplacement est autorisé, mais la couleur du cercle ne change pas, car `gre` n’est pas une couleur valide.</span><span class="sxs-lookup"><span data-stu-id="c7f88-208">Notice that the cursor changes to indicate that the drop is allowed, but the color of the Circle does not change because `gre` is not a valid color.</span></span>

9. <span data-ttu-id="c7f88-209">Faites glisser le contrôle de cercle vert et déplacez-le sur le contrôle de cercle bleu.</span><span class="sxs-lookup"><span data-stu-id="c7f88-209">Drag from the green Circle control and drop on the blue Circle control.</span></span> <span data-ttu-id="c7f88-210">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="c7f88-210">The Circle changes from blue to green.</span></span> <span data-ttu-id="c7f88-211">Notez que le curseur affiché varie selon que <xref:System.Windows.Controls.TextBox> le ou le cercle est la source du glissement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-211">Notice that which cursor is shown depends on whether the <xref:System.Windows.Controls.TextBox> or the Circle is the drag source.</span></span>

<span data-ttu-id="c7f88-212">Le fait <xref:System.Windows.UIElement.AllowDrop%2A> de définir `true` la propriété sur et de traiter les données déplacées est tout ce qui est nécessaire pour permettre à un élément d’être une cible de déplacement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-212">Setting the <xref:System.Windows.UIElement.AllowDrop%2A> property to `true` and processing the dropped data is all that is required to enable an element to be a drop target.</span></span> <span data-ttu-id="c7f88-213">Toutefois, pour offrir une meilleure expérience utilisateur, vous devez également gérer les <xref:System.Windows.UIElement.DragEnter>événements <xref:System.Windows.UIElement.DragLeave>, et <xref:System.Windows.UIElement.DragOver> .</span><span class="sxs-lookup"><span data-stu-id="c7f88-213">However, to provide a better user experience, you should also handle the <xref:System.Windows.UIElement.DragEnter>, <xref:System.Windows.UIElement.DragLeave>, and <xref:System.Windows.UIElement.DragOver> events.</span></span> <span data-ttu-id="c7f88-214">Dans ces événements, vous pouvez effectuer des vérifications et fournir des commentaires supplémentaires à l’utilisateur avant de déplacer les données.</span><span class="sxs-lookup"><span data-stu-id="c7f88-214">In these events, you can perform checks and provide additional feedback to the user before the data is dropped.</span></span>

<span data-ttu-id="c7f88-215">Quand les données sont glissées sur le contrôle utilisateur de cercle, le contrôle doit notifier la source de glissement si elle peut ou non traiter les données en cours de glissement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-215">When data is dragged over the Circle user control, the control should notify the drag source whether it can process the data that is being dragged.</span></span> <span data-ttu-id="c7f88-216">Si le contrôle ne sait pas comment traiter les données, il doit refuser le déplacement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-216">If the control does not know how to process the data, it should refuse the drop.</span></span> <span data-ttu-id="c7f88-217">Pour ce faire, vous allez gérer l' <xref:System.Windows.UIElement.DragOver> événement et définir la <xref:System.Windows.DragEventArgs.Effects%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c7f88-217">To do this, you will handle the <xref:System.Windows.UIElement.DragOver> event and set the <xref:System.Windows.DragEventArgs.Effects%2A> property.</span></span>

### <a name="to-verify-that-the-data-drop-is-allowed"></a><span data-ttu-id="c7f88-218">Pour vérifier que le déplacement de données est autorisé</span><span class="sxs-lookup"><span data-stu-id="c7f88-218">To verify that the data drop is allowed</span></span>

1. <span data-ttu-id="c7f88-219">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c7f88-219">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7f88-220">Ajoutez la substitution <xref:System.Windows.UIElement.OnDragOver%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.DragOver> l’événement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-220">Add the following <xref:System.Windows.UIElement.OnDragOver%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragOver> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     <span data-ttu-id="c7f88-221">Ce <xref:System.Windows.UIElement.OnDragOver%2A> remplacement effectue les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="c7f88-221">This <xref:System.Windows.UIElement.OnDragOver%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7f88-222">Affecte la valeur <xref:System.Windows.DragEventArgs.Effects%2A> à la propriété <xref:System.Windows.DragDropEffects.None>.</span><span class="sxs-lookup"><span data-stu-id="c7f88-222">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.None>.</span></span>

    - <span data-ttu-id="c7f88-223">Effectue les mêmes vérifications que celles effectuées dans la <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si le contrôle utilisateur Circle peut traiter les données glissées.</span><span class="sxs-lookup"><span data-stu-id="c7f88-223">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the Circle user control can process the dragged data.</span></span>

    - <span data-ttu-id="c7f88-224">Si le contrôle utilisateur peut traiter les données, affecte à <xref:System.Windows.DragEventArgs.Effects%2A> la propriété <xref:System.Windows.DragDropEffects.Copy> la <xref:System.Windows.DragDropEffects.Move>valeur ou.</span><span class="sxs-lookup"><span data-stu-id="c7f88-224">If the user control can process the data, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy> or <xref:System.Windows.DragDropEffects.Move>.</span></span>

3. <span data-ttu-id="c7f88-225">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="c7f88-225">Press **F5** to build and run the application.</span></span>

4. <span data-ttu-id="c7f88-226">Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7f88-226">Select the text `gre` in the <xref:System.Windows.Controls.TextBox>.</span></span>

5. <span data-ttu-id="c7f88-227">Faites glisser le texte vers un contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-227">Drag the text to a Circle control.</span></span> <span data-ttu-id="c7f88-228">Notez que le curseur change à présent pour indiquer que le déplacement n’est pas autorisé, car `gre` n’est pas une couleur valide.</span><span class="sxs-lookup"><span data-stu-id="c7f88-228">Notice that the cursor now changes to indicate that the drop is not allowed because `gre` is not a valid color.</span></span>

 <span data-ttu-id="c7f88-229">Vous pouvez améliorer l’expérience utilisateur en appliquant un aperçu de l’opération de déplacement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-229">You can further enhance the user experience by applying a preview of the drop operation.</span></span> <span data-ttu-id="c7f88-230">Pour le contrôle utilisateur Circle, vous allez substituer les <xref:System.Windows.UIElement.OnDragEnter%2A> méthodes <xref:System.Windows.UIElement.OnDragLeave%2A> et.</span><span class="sxs-lookup"><span data-stu-id="c7f88-230">For the Circle user control, you will override the <xref:System.Windows.UIElement.OnDragEnter%2A> and <xref:System.Windows.UIElement.OnDragLeave%2A> methods.</span></span> <span data-ttu-id="c7f88-231">Lorsque les données sont glissées sur le contrôle, l’arrière- <xref:System.Windows.Shapes.Shape.Fill%2A> plan actuel est enregistré dans une variable d’espace réservé.</span><span class="sxs-lookup"><span data-stu-id="c7f88-231">When the data is dragged over the control, the current background <xref:System.Windows.Shapes.Shape.Fill%2A> is saved in a placeholder variable.</span></span> <span data-ttu-id="c7f88-232">La chaîne est ensuite convertie en pinceau et appliquée au <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du cercle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-232">The string is then converted to a brush and applied to the <xref:System.Windows.Shapes.Ellipse> that provides the Circle's UI.</span></span> <span data-ttu-id="c7f88-233">Si les données sont déplacées en dehors du cercle sans être supprimées, <xref:System.Windows.Shapes.Shape.Fill%2A> la valeur d’origine est réappliquée au cercle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-233">If the data is dragged out of the Circle without being dropped, the original <xref:System.Windows.Shapes.Shape.Fill%2A> value is re-applied to the Circle.</span></span>

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a><span data-ttu-id="c7f88-234">Pour afficher un aperçu du résultat de l’opération de glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="c7f88-234">To preview the effects of the drag-and-drop operation</span></span>

1. <span data-ttu-id="c7f88-235">Ouvrez Circle.xaml.cs ou Circle.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c7f88-235">Open Circle.xaml.cs or Circle.xaml.vb.</span></span>

2. <span data-ttu-id="c7f88-236">Dans la classe Circle, déclarez une <xref:System.Windows.Media.Brush> variable privée `_previousFill` nommée et initialisez- `null`la sur.</span><span class="sxs-lookup"><span data-stu-id="c7f88-236">In the Circle class, declare a private <xref:System.Windows.Media.Brush> variable named `_previousFill` and initialize it to `null`.</span></span>

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. <span data-ttu-id="c7f88-237">Ajoutez la substitution <xref:System.Windows.UIElement.OnDragEnter%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.DragEnter> l’événement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-237">Add the following <xref:System.Windows.UIElement.OnDragEnter%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragEnter> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     <span data-ttu-id="c7f88-238">Ce <xref:System.Windows.UIElement.OnDragEnter%2A> remplacement effectue les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="c7f88-238">This <xref:System.Windows.UIElement.OnDragEnter%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7f88-239">Enregistre la <xref:System.Windows.Shapes.Shape.Fill%2A> propriété <xref:System.Windows.Shapes.Ellipse> de dans la `_previousFill` variable.</span><span class="sxs-lookup"><span data-stu-id="c7f88-239">Saves the <xref:System.Windows.Shapes.Shape.Fill%2A> property of the <xref:System.Windows.Shapes.Ellipse> in the `_previousFill` variable.</span></span>

    - <span data-ttu-id="c7f88-240">Effectue les mêmes vérifications que celles effectuées dans la <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si les données peuvent être converties <xref:System.Windows.Media.Brush>en.</span><span class="sxs-lookup"><span data-stu-id="c7f88-240">Performs the same checks that are performed in the <xref:System.Windows.UIElement.OnDrop%2A> method to determine whether the data can be converted to a <xref:System.Windows.Media.Brush>.</span></span>

    - <span data-ttu-id="c7f88-241">Si les données sont converties en <xref:System.Windows.Media.Brush>valides, l’applique <xref:System.Windows.Shapes.Shape.Fill%2A> à l' <xref:System.Windows.Shapes.Ellipse>objet de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c7f88-241">If the data is converted to a valid <xref:System.Windows.Media.Brush>, applies it to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse>.</span></span>

4. <span data-ttu-id="c7f88-242">Ajoutez la substitution <xref:System.Windows.UIElement.OnDragLeave%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.DragLeave> l’événement.</span><span class="sxs-lookup"><span data-stu-id="c7f88-242">Add the following <xref:System.Windows.UIElement.OnDragLeave%2A> override to provide class handling for the <xref:System.Windows.UIElement.DragLeave> event.</span></span>

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     <span data-ttu-id="c7f88-243">Ce <xref:System.Windows.UIElement.OnDragLeave%2A> remplacement effectue les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="c7f88-243">This <xref:System.Windows.UIElement.OnDragLeave%2A> override performs the following tasks:</span></span>

    - <span data-ttu-id="c7f88-244">Applique l' <xref:System.Windows.Media.Brush> enregistrement dans la `_previousFill` <xref:System.Windows.Shapes.Shape.Fill%2A>variableau du quifournitl’interfaceutilisateurducontrôleutilisateurdecercle.<xref:System.Windows.Shapes.Ellipse></span><span class="sxs-lookup"><span data-stu-id="c7f88-244">Applies the <xref:System.Windows.Media.Brush> saved in the `_previousFill` variable to the <xref:System.Windows.Shapes.Shape.Fill%2A> of the <xref:System.Windows.Shapes.Ellipse> that provides the UI of the Circle user control.</span></span>

5. <span data-ttu-id="c7f88-245">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="c7f88-245">Press **F5** to build and run the application.</span></span>

6. <span data-ttu-id="c7f88-246">Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="c7f88-246">Select the text `green` in the <xref:System.Windows.Controls.TextBox>.</span></span>

7. <span data-ttu-id="c7f88-247">Faites glisser le texte sur un contrôle de cercle sans le déplacer.</span><span class="sxs-lookup"><span data-stu-id="c7f88-247">Drag the text over a Circle control without dropping it.</span></span> <span data-ttu-id="c7f88-248">Le cercle passe du bleu au vert.</span><span class="sxs-lookup"><span data-stu-id="c7f88-248">The Circle changes from blue to green.</span></span>

     <span data-ttu-id="c7f88-249">![Prévisualiser les effets d’une opération de glisser-déplacer](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span><span class="sxs-lookup"><span data-stu-id="c7f88-249">![Preview the effects of a drag&#45;and&#45;drop operation](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")</span></span>

8. <span data-ttu-id="c7f88-250">Faites glisser le texte en dehors du contrôle de cercle.</span><span class="sxs-lookup"><span data-stu-id="c7f88-250">Drag the text away from the Circle control.</span></span> <span data-ttu-id="c7f88-251">Le cercle passe du vert au bleu.</span><span class="sxs-lookup"><span data-stu-id="c7f88-251">The Circle changes from green back to blue.</span></span>

## <a name="enable-a-panel-to-receive-dropped-data"></a><span data-ttu-id="c7f88-252">Permettre à un panneau de recevoir des données déplacées</span><span class="sxs-lookup"><span data-stu-id="c7f88-252">Enable a Panel to Receive Dropped Data</span></span>

<span data-ttu-id="c7f88-253">Dans cette section, vous allez activer les panneaux qui hébergent les contrôles utilisateur de cercle pour agir en tant que cibles de dépôt pour les données de cercle glissées.</span><span class="sxs-lookup"><span data-stu-id="c7f88-253">In this section, you enable the panels that host the Circle user controls to act as drop targets for dragged Circle data.</span></span> <span data-ttu-id="c7f88-254">Vous allez implémenter le code qui vous permet de déplacer un cercle d’un panneau à un autre, ou de faire une copie d’un contrôle de cercle en maintenant la touche **CTRL** enfoncée tout en faisant glisser un cercle et en le déposant.</span><span class="sxs-lookup"><span data-stu-id="c7f88-254">You will implement code that enables you to move a Circle from one panel to another, or to make a copy of a Circle control by holding down the **Ctrl** key while dragging and dropping a Circle.</span></span>

1. <span data-ttu-id="c7f88-255">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="c7f88-255">Open MainWindow.xaml.</span></span>

2. <span data-ttu-id="c7f88-256">Comme indiqué dans le code XAML suivant, dans chacun des <xref:System.Windows.Controls.StackPanel> contrôles, ajoutez des gestionnaires pour les <xref:System.Windows.UIElement.DragOver> événements <xref:System.Windows.UIElement.Drop> et.</span><span class="sxs-lookup"><span data-stu-id="c7f88-256">As shown in the following XAML, in each of the <xref:System.Windows.Controls.StackPanel> controls, add handlers for the <xref:System.Windows.UIElement.DragOver> and <xref:System.Windows.UIElement.Drop> events.</span></span> <span data-ttu-id="c7f88-257">Nommez <xref:System.Windows.UIElement.DragOver> le gestionnaire d' `panel_DragOver`événements, et nommez le <xref:System.Windows.UIElement.Drop> gestionnaire `panel_Drop`d’événements,.</span><span class="sxs-lookup"><span data-stu-id="c7f88-257">Name the <xref:System.Windows.UIElement.DragOver> event handler, `panel_DragOver`, and name the <xref:System.Windows.UIElement.Drop> event handler, `panel_Drop`.</span></span>

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. <span data-ttu-id="c7f88-258">Ouvrez MainWindows.xaml.cs ou MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c7f88-258">Open MainWindows.xaml.cs or MainWindow.xaml.vb.</span></span>

4. <span data-ttu-id="c7f88-259">Ajoutez le code suivant pour le <xref:System.Windows.UIElement.DragOver> gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="c7f88-259">Add the following code for the <xref:System.Windows.UIElement.DragOver> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     <span data-ttu-id="c7f88-260">Ce <xref:System.Windows.UIElement.DragOver> gestionnaire d’événements effectue les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="c7f88-260">This <xref:System.Windows.UIElement.DragOver> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="c7f88-261">Vérifie que les données déplacées contiennent les données d’objet qui ont été empaquetées dans le <xref:System.Windows.DataObject> par le contrôle utilisateur Circle et passées dans l’appel à. <xref:System.Windows.DragDrop.DoDragDrop%2A></span><span class="sxs-lookup"><span data-stu-id="c7f88-261">Checks that the dragged data contains the "Object" data that was packaged in the <xref:System.Windows.DataObject> by the Circle user control and passed in the call to <xref:System.Windows.DragDrop.DoDragDrop%2A>.</span></span>

    - <span data-ttu-id="c7f88-262">Si les données d’objet sont présentes, vérifie si la touche **CTRL** est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="c7f88-262">If the "Object" data is present, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="c7f88-263">Si la touche **CTRL** est enfoncée, <xref:System.Windows.DragEventArgs.Effects%2A> affecte la <xref:System.Windows.DragDropEffects.Copy>valeur à la propriété.</span><span class="sxs-lookup"><span data-stu-id="c7f88-263">If the **Ctrl** key is pressed, sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Copy>.</span></span> <span data-ttu-id="c7f88-264">Sinon, affectez <xref:System.Windows.DragEventArgs.Effects%2A> à <xref:System.Windows.DragDropEffects.Move>la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="c7f88-264">Otherwise, set the <xref:System.Windows.DragEventArgs.Effects%2A> property to <xref:System.Windows.DragDropEffects.Move>.</span></span>

5. <span data-ttu-id="c7f88-265">Ajoutez le code suivant pour le <xref:System.Windows.UIElement.Drop> gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="c7f88-265">Add the following code for the <xref:System.Windows.UIElement.Drop> event handler.</span></span>

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     <span data-ttu-id="c7f88-266">Ce <xref:System.Windows.UIElement.Drop> gestionnaire d’événements effectue les tâches suivantes:</span><span class="sxs-lookup"><span data-stu-id="c7f88-266">This <xref:System.Windows.UIElement.Drop> event handler performs the following tasks:</span></span>

    - <span data-ttu-id="c7f88-267">Vérifie si l' <xref:System.Windows.UIElement.Drop> événement a déjà été géré.</span><span class="sxs-lookup"><span data-stu-id="c7f88-267">Checks whether the <xref:System.Windows.UIElement.Drop> event has already been handled.</span></span> <span data-ttu-id="c7f88-268">Par exemple, si un cercle est déposé sur un autre cercle qui gère <xref:System.Windows.UIElement.Drop> l’événement, vous ne souhaitez pas que le panneau qui contient le cercle le gère également.</span><span class="sxs-lookup"><span data-stu-id="c7f88-268">For instance, if a Circle is dropped on another Circle which handles the <xref:System.Windows.UIElement.Drop> event, you do not want the panel that contains the Circle to also handle it.</span></span>

    - <span data-ttu-id="c7f88-269">Si l' <xref:System.Windows.UIElement.Drop> événement n’est pas géré, vérifie si la touche **CTRL** est enfoncée.</span><span class="sxs-lookup"><span data-stu-id="c7f88-269">If the <xref:System.Windows.UIElement.Drop> event is not handled, checks whether the **Ctrl** key is pressed.</span></span>

    - <span data-ttu-id="c7f88-270">Si la touche **CTRL** est enfoncée <xref:System.Windows.UIElement.Drop> lorsque le se produit, effectue une copie du contrôle Circle et l’ajoute <xref:System.Windows.Controls.Panel.Children%2A> à <xref:System.Windows.Controls.StackPanel>la collection de.</span><span class="sxs-lookup"><span data-stu-id="c7f88-270">If the **Ctrl** key is pressed when the <xref:System.Windows.UIElement.Drop> happens, makes a copy of the Circle control and add it to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the <xref:System.Windows.Controls.StackPanel>.</span></span>

    - <span data-ttu-id="c7f88-271">Si la touche **CTRL** n’est pas enfoncée, déplace le <xref:System.Windows.Controls.Panel.Children%2A> cercle de la collection de son panneau <xref:System.Windows.Controls.Panel.Children%2A> parent vers la collection du panneau sur lequel il a été déposé.</span><span class="sxs-lookup"><span data-stu-id="c7f88-271">If the **Ctrl** key is not pressed, moves the Circle from the <xref:System.Windows.Controls.Panel.Children%2A> collection of its parent panel to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the panel that it was dropped on.</span></span>

    - <span data-ttu-id="c7f88-272">Définit la <xref:System.Windows.DragEventArgs.Effects%2A> propriété pour indiquer à <xref:System.Windows.DragDrop.DoDragDrop%2A> la méthode si une opération de déplacement ou de copie a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="c7f88-272">Sets the <xref:System.Windows.DragEventArgs.Effects%2A> property to notify the <xref:System.Windows.DragDrop.DoDragDrop%2A> method whether a move or copy operation was performed.</span></span>

6. <span data-ttu-id="c7f88-273">Appuyez sur **F5** pour générer et exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="c7f88-273">Press **F5** to build and run the application.</span></span>

7. <span data-ttu-id="c7f88-274">Sélectionnez le texte `green` <xref:System.Windows.Controls.TextBox>à partir du.</span><span class="sxs-lookup"><span data-stu-id="c7f88-274">Select the text `green` from the <xref:System.Windows.Controls.TextBox>.</span></span>

8. <span data-ttu-id="c7f88-275">Faites glisser le texte sur un contrôle de cercle et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="c7f88-275">Drag the text over a Circle control and drop it.</span></span>

9. <span data-ttu-id="c7f88-276">Faites glisser un contrôle de cercle du panneau gauche vers le panneau droit et déplacez-le.</span><span class="sxs-lookup"><span data-stu-id="c7f88-276">Drag a Circle control from the left panel to the right panel and drop it.</span></span> <span data-ttu-id="c7f88-277">Le cercle est supprimé de la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau gauche et ajouté à la collection Children du panneau droit.</span><span class="sxs-lookup"><span data-stu-id="c7f88-277">The Circle is removed from the <xref:System.Windows.Controls.Panel.Children%2A> collection of the left panel and added to the Children collection of the right panel.</span></span>

10. <span data-ttu-id="c7f88-278">Faites glisser un contrôle Circle du panneau dans lequel il se trouve et déposez-le tout en appuyant sur la touche **CTRL** .</span><span class="sxs-lookup"><span data-stu-id="c7f88-278">Drag a Circle control from the panel it is in to the other panel and drop it while pressing the **Ctrl** key.</span></span> <span data-ttu-id="c7f88-279">Le cercle est copié et la copie est ajoutée à la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau de réception.</span><span class="sxs-lookup"><span data-stu-id="c7f88-279">The Circle is copied and the copy is added to the <xref:System.Windows.Controls.Panel.Children%2A> collection of the receiving panel.</span></span>

     <span data-ttu-id="c7f88-280">![Glissement d'un cercle en maintenant la touche CTRL enfoncée](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span><span class="sxs-lookup"><span data-stu-id="c7f88-280">![Dragging a Circle while pressing the CTRL key](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")</span></span>

## <a name="see-also"></a><span data-ttu-id="c7f88-281">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7f88-281">See also</span></span>

- [<span data-ttu-id="c7f88-282">Vue d'ensemble du glisser-déplacer</span><span class="sxs-lookup"><span data-stu-id="c7f88-282">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
