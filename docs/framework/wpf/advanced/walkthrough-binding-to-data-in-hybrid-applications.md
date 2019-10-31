---
title: 'Procédure pas à pas : liaison de données dans des applications hybrides'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 99f0e621c7dd56c0a26b51b4725f9fb96ab3cbf9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197904"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a><span data-ttu-id="5c7eb-102">Procédure pas à pas : liaison de données dans des applications hybrides</span><span class="sxs-lookup"><span data-stu-id="5c7eb-102">Walkthrough: Binding to Data in Hybrid Applications</span></span>

<span data-ttu-id="5c7eb-103">La liaison d’une source de données à un contrôle est essentielle pour permettre aux utilisateurs d’accéder aux données sous-jacentes, que vous utilisiez [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c7eb-103">Binding a data source to a control is essential for providing users with access to underlying data, whether you are using [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] or [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="5c7eb-104">Cette procédure pas à pas montre comment vous pouvez utiliser la liaison de données dans des applications hybrides qui incluent à la fois des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c7eb-104">This walkthrough shows how you can use data binding in hybrid applications that include both [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls.</span></span>

<span data-ttu-id="5c7eb-105">Cette procédure pas à pas décrit notamment les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="5c7eb-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="5c7eb-106">Création du projet</span><span class="sxs-lookup"><span data-stu-id="5c7eb-106">Creating the project.</span></span>

- <span data-ttu-id="5c7eb-107">Définition du modèle de données.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-107">Defining the data template.</span></span>

- <span data-ttu-id="5c7eb-108">Spécification de la disposition du formulaire.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-108">Specifying the form layout.</span></span>

- <span data-ttu-id="5c7eb-109">Spécification des liaisons de données.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-109">Specifying data bindings.</span></span>

- <span data-ttu-id="5c7eb-110">Affichage des données à l’aide de l’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-110">Displaying data by using interoperation.</span></span>

- <span data-ttu-id="5c7eb-111">Ajout de la source de données au projet.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-111">Adding the data source to the project.</span></span>

- <span data-ttu-id="5c7eb-112">Liaison à la source de données.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-112">Binding to the data source.</span></span>

<span data-ttu-id="5c7eb-113">Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez la rubrique [exemple de liaison de données dans des applications hybrides](https://go.microsoft.com/fwlink/?LinkID=159983).</span><span class="sxs-lookup"><span data-stu-id="5c7eb-113">For a complete code listing of the tasks illustrated in this walkthrough, see [Data Binding in Hybrid Applications Sample](https://go.microsoft.com/fwlink/?LinkID=159983).</span></span>

<span data-ttu-id="5c7eb-114">À l’issue de cette procédure, vous aurez une meilleure compréhension des fonctionnalités de liaison de données dans les applications hybrides.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-114">When you are finished, you will have an understanding of data binding features in hybrid applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5c7eb-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5c7eb-115">Prerequisites</span></span>

<span data-ttu-id="5c7eb-116">Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :</span><span class="sxs-lookup"><span data-stu-id="5c7eb-116">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="5c7eb-117">Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-117">Visual Studio.</span></span>

- <span data-ttu-id="5c7eb-118">Accès à l’exemple de base de données Northwind s’exécutant sur Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-118">Access to the Northwind sample database running on Microsoft SQL Server.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="5c7eb-119">Création du projet</span><span class="sxs-lookup"><span data-stu-id="5c7eb-119">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="5c7eb-120">Pour créer et configurer le projet</span><span class="sxs-lookup"><span data-stu-id="5c7eb-120">To create and set up the project</span></span>

1. <span data-ttu-id="5c7eb-121">Créez un projet d’application WPF nommé `WPFWithWFAndDatabinding`.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-121">Create a WPF Application project named `WPFWithWFAndDatabinding`.</span></span>

2. <span data-ttu-id="5c7eb-122">Dans l’Explorateur de solutions, ajoutez des références aux assemblys suivants.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-122">In Solution Explorer, add references to the following assemblies.</span></span>

    - <span data-ttu-id="5c7eb-123">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="5c7eb-123">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="5c7eb-124">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="5c7eb-124">System.Windows.Forms</span></span>

3. <span data-ttu-id="5c7eb-125">Ouvrez MainWindow. xaml dans la [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c7eb-125">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

4. <span data-ttu-id="5c7eb-126">Dans l’élément <xref:System.Windows.Window>, ajoutez le mappage d’espaces de noms [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] suivant.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-126">In the <xref:System.Windows.Window> element, add the following [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] namespaces mapping.</span></span>

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. <span data-ttu-id="5c7eb-127">Nommez l’élément <xref:System.Windows.Controls.Grid> par défaut `mainGrid` en affectant la propriété <xref:System.Windows.FrameworkElement.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-127">Name the default <xref:System.Windows.Controls.Grid> element `mainGrid` by assigning the <xref:System.Windows.FrameworkElement.Name%2A> property.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a><span data-ttu-id="5c7eb-128">Définition du modèle de données</span><span class="sxs-lookup"><span data-stu-id="5c7eb-128">Defining the Data Template</span></span>

<span data-ttu-id="5c7eb-129">La liste principale des clients s’affiche dans un contrôle de <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-129">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="5c7eb-130">L’exemple de code suivant définit un objet <xref:System.Windows.DataTemplate> nommé `ListItemsTemplate` qui contrôle l’arborescence d’éléments visuels du contrôle <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-130">The following code example defines a <xref:System.Windows.DataTemplate> object named `ListItemsTemplate` that controls the visual tree of the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="5c7eb-131">Cette <xref:System.Windows.DataTemplate> est assignée à la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> du contrôle <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-131">This <xref:System.Windows.DataTemplate> is assigned to the <xref:System.Windows.Controls.ListBox> control's <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> property.</span></span>

### <a name="to-define-the-data-template"></a><span data-ttu-id="5c7eb-132">Pour définir le modèle de données</span><span class="sxs-lookup"><span data-stu-id="5c7eb-132">To define the data template</span></span>

- <span data-ttu-id="5c7eb-133">Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-133">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a><span data-ttu-id="5c7eb-134">Spécification de la disposition du formulaire</span><span class="sxs-lookup"><span data-stu-id="5c7eb-134">Specifying the Form Layout</span></span>

<span data-ttu-id="5c7eb-135">La disposition du formulaire est définie par une grille de trois lignes et trois colonnes.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-135">The layout of the form is defined by a grid with three rows and three columns.</span></span> <span data-ttu-id="5c7eb-136">des contrôles de <xref:System.Windows.Controls.Label> sont fournis pour identifier chaque colonne dans la table Customers.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-136"><xref:System.Windows.Controls.Label> controls are provided to identify each column in the Customers table.</span></span>

### <a name="to-set-up-the-grid-layout"></a><span data-ttu-id="5c7eb-137">Pour configurer la disposition de la grille</span><span class="sxs-lookup"><span data-stu-id="5c7eb-137">To set up the Grid layout</span></span>

- <span data-ttu-id="5c7eb-138">Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-138">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a><span data-ttu-id="5c7eb-139">Pour configurer les contrôles Label</span><span class="sxs-lookup"><span data-stu-id="5c7eb-139">To set up the Label controls</span></span>

- <span data-ttu-id="5c7eb-140">Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-140">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a><span data-ttu-id="5c7eb-141">Spécification des liaisons de données</span><span class="sxs-lookup"><span data-stu-id="5c7eb-141">Specifying Data Bindings</span></span>

<span data-ttu-id="5c7eb-142">La liste principale des clients s’affiche dans un contrôle de <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-142">The master list of customers is displayed in a <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="5c7eb-143">Le `ListItemsTemplate` attaché lie un contrôle <xref:System.Windows.Controls.TextBlock> au champ `ContactName` de la base de données.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-143">The attached `ListItemsTemplate` binds a <xref:System.Windows.Controls.TextBlock> control to the `ContactName` field from the database.</span></span>

<span data-ttu-id="5c7eb-144">Les détails de chaque enregistrement de client s’affichent dans plusieurs contrôles de <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-144">The details of each customer record are displayed in several <xref:System.Windows.Controls.TextBox> controls.</span></span>

### <a name="to-specify-data-bindings"></a><span data-ttu-id="5c7eb-145">Pour spécifier des liaisons de données</span><span class="sxs-lookup"><span data-stu-id="5c7eb-145">To specify data bindings</span></span>

- <span data-ttu-id="5c7eb-146">Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-146">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     <span data-ttu-id="5c7eb-147">La classe <xref:System.Windows.Data.Binding> lie les contrôles <xref:System.Windows.Controls.TextBox> aux champs appropriés dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-147">The <xref:System.Windows.Data.Binding> class binds the <xref:System.Windows.Controls.TextBox> controls to the appropriate fields in the database.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a><span data-ttu-id="5c7eb-148">Affichage des données à l’aide de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="5c7eb-148">Displaying Data by Using Interoperation</span></span>

<span data-ttu-id="5c7eb-149">Les commandes correspondant au client sélectionné s’affichent dans un contrôle de <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> nommé `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-149">The orders corresponding to the selected customer are displayed in a <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> control named `dataGridView1`.</span></span> <span data-ttu-id="5c7eb-150">Le contrôle `dataGridView1` est lié à la source de données dans le fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-150">The `dataGridView1` control is bound to the data source in the code-behind file.</span></span> <span data-ttu-id="5c7eb-151">Un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> est le parent de ce contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c7eb-151">A <xref:System.Windows.Forms.Integration.WindowsFormsHost> control is the parent of this [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control.</span></span>

### <a name="to-display-data-in-the-datagridview-control"></a><span data-ttu-id="5c7eb-152">Pour afficher des données dans le contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="5c7eb-152">To display data in the DataGridView control</span></span>

- <span data-ttu-id="5c7eb-153">Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-153">Copy the following XAML into the <xref:System.Windows.Controls.Grid> element's declaration.</span></span>

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a><span data-ttu-id="5c7eb-154">Ajout de la source de données au projet</span><span class="sxs-lookup"><span data-stu-id="5c7eb-154">Adding the Data Source to the Project</span></span>

<span data-ttu-id="5c7eb-155">Avec Visual Studio, vous pouvez facilement ajouter une source de données à votre projet.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-155">With Visual Studio, you can easily add a data source to your project.</span></span> <span data-ttu-id="5c7eb-156">Cette procédure ajoute un jeu de données fortement typé à votre projet.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-156">This procedure adds a strongly typed data set to your project.</span></span> <span data-ttu-id="5c7eb-157">Plusieurs autres classes de prise en charge, comme les adaptateurs de table pour chacune des tables choisies, sont également ajoutées.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-157">Several other support classes, such as table adapters for each of the chosen tables, are also added.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="5c7eb-158">Pour ajouter la source de données</span><span class="sxs-lookup"><span data-stu-id="5c7eb-158">To add the data source</span></span>

1. <span data-ttu-id="5c7eb-159">Dans le menu **données** , sélectionnez **Ajouter une nouvelle source de données**.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-159">From the **Data** menu, select **Add New Data Source**.</span></span>

2. <span data-ttu-id="5c7eb-160">Dans l **'Assistant Configuration de source de données**, créez une connexion à la base de données Northwind à l’aide d’un jeu de données.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-160">In the **Data Source Configuration Wizard**, create a connection to the Northwind database by using a dataset.</span></span> <span data-ttu-id="5c7eb-161">Pour plus d'informations, consultez [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="5c7eb-161">For more information, see [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).</span></span>

3. <span data-ttu-id="5c7eb-162">Lorsque l' **Assistant Configuration de source de données**vous y invite, enregistrez la chaîne de connexion en tant que `NorthwindConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-162">When you are prompted by the **Data Source Configuration Wizard**, save the connection string as `NorthwindConnectionString`.</span></span>

4. <span data-ttu-id="5c7eb-163">Lorsque vous êtes invité à choisir vos objets de base de données, sélectionnez les tables `Customers` et `Orders`, puis nommez le jeu de données généré `NorthwindDataSet`.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-163">When you are prompted to choose your database objects, select the `Customers` and `Orders` tables, and name the generated data set `NorthwindDataSet`.</span></span>

## <a name="binding-to-the-data-source"></a><span data-ttu-id="5c7eb-164">Liaison à la source de données</span><span class="sxs-lookup"><span data-stu-id="5c7eb-164">Binding to the Data Source</span></span>

<span data-ttu-id="5c7eb-165">Le composant <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> fournit une interface uniforme pour la source de données de l’application.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-165">The <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> component provides a uniform interface for the application's data source.</span></span> <span data-ttu-id="5c7eb-166">La liaison à la source de données est implémentée dans le fichier code-behind.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-166">Binding to the data source is implemented in the code-behind file.</span></span>

### <a name="to-bind-to-the-data-source"></a><span data-ttu-id="5c7eb-167">Pour effectuer la liaison à la source de données</span><span class="sxs-lookup"><span data-stu-id="5c7eb-167">To bind to the data source</span></span>

1. <span data-ttu-id="5c7eb-168">Ouvrez le fichier code-behind nommé MainWindow.xaml.vb ou MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-168">Open the code-behind file, which is named MainWindow.xaml.vb or MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="5c7eb-169">Copiez le code suivant dans la définition de classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-169">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="5c7eb-170">Ce code déclare le composant <xref:System.Windows.Forms.BindingSource> et les classes d’assistance associées qui se connectent à la base de données.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-170">This code declares the <xref:System.Windows.Forms.BindingSource> component and associated helper classes that connect to the database.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. <span data-ttu-id="5c7eb-171">Copiez le code suivant dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-171">Copy the following code into the constructor.</span></span>

     <span data-ttu-id="5c7eb-172">Ce code crée et initialise le composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-172">This code creates and initializes the <xref:System.Windows.Forms.BindingSource> component.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. <span data-ttu-id="5c7eb-173">Ouvrez MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-173">Open MainWindow.xaml.</span></span>

5. <span data-ttu-id="5c7eb-174">En Mode Création ou en mode XAML, sélectionnez l’élément <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-174">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="5c7eb-175">Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .</span><span class="sxs-lookup"><span data-stu-id="5c7eb-175">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="5c7eb-176">Double-cliquez sur l’événement <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-176">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="5c7eb-177">Copiez le code suivant dans le gestionnaire d’événements <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-177">Copy the following code into the <xref:System.Windows.FrameworkElement.Loaded> event handler.</span></span>

     <span data-ttu-id="5c7eb-178">Ce code assigne le composant <xref:System.Windows.Forms.BindingSource> comme contexte de données et remplit les objets `Customers` et `Orders` adaptateur.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-178">This code assigns the <xref:System.Windows.Forms.BindingSource> component as the data context and populates the `Customers` and `Orders` adapter objects.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. <span data-ttu-id="5c7eb-179">Copiez le code suivant dans la définition de classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-179">Copy the following code into the `MainWindow` class definition.</span></span>

     <span data-ttu-id="5c7eb-180">Cette méthode gère l’événement <xref:System.Windows.Data.CollectionView.CurrentChanged> et met à jour l’élément actuel de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-180">This method handles the <xref:System.Windows.Data.CollectionView.CurrentChanged> event and updates the current item of the data binding.</span></span>

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. <span data-ttu-id="5c7eb-181">Appuyez sur F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="5c7eb-181">Press F5 to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c7eb-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c7eb-182">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="5c7eb-183">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5c7eb-183">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="5c7eb-184">Exemple de liaison de données dans des applications hybrides</span><span class="sxs-lookup"><span data-stu-id="5c7eb-184">Data Binding in Hybrid Applications Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159983)
- [<span data-ttu-id="5c7eb-185">Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF</span><span class="sxs-lookup"><span data-stu-id="5c7eb-185">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="5c7eb-186">Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5c7eb-186">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
