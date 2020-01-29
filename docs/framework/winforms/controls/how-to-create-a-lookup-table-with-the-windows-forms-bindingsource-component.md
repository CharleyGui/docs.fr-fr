---
title: Créer une table de correspondance avec le composant BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: ccf2bfa6cf3f56a38b55f8c87004c42a46172891
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736815"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="323b4-102">Comment : créer une table de correspondance avec le composant BindingSource Windows Forms</span><span class="sxs-lookup"><span data-stu-id="323b4-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="323b4-103">Une table de choix est une table de données ayant une colonne qui affiche les données des enregistrements situés dans une table liée.</span><span class="sxs-lookup"><span data-stu-id="323b4-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="323b4-104">Dans les procédures suivantes, un contrôle <xref:System.Windows.Forms.ComboBox> permet d'afficher le champ avec la relation de clé étrangère entre la table parent et la table enfant.</span><span class="sxs-lookup"><span data-stu-id="323b4-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="323b4-105">Pour mieux visualiser ces deux tables et cette relation, voici un exemple de table parent et de table enfant :</span><span class="sxs-lookup"><span data-stu-id="323b4-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="323b4-106">CustomersTable (table parent)</span><span class="sxs-lookup"><span data-stu-id="323b4-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="323b4-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="323b4-107">CustomerID</span></span>|<span data-ttu-id="323b4-108">CustomerName</span><span class="sxs-lookup"><span data-stu-id="323b4-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="323b4-109">712</span><span class="sxs-lookup"><span data-stu-id="323b4-109">712</span></span>|<span data-ttu-id="323b4-110">David Junca</span><span class="sxs-lookup"><span data-stu-id="323b4-110">Paul Koch</span></span>|  
|<span data-ttu-id="323b4-111">713</span><span class="sxs-lookup"><span data-stu-id="323b4-111">713</span></span>|<span data-ttu-id="323b4-112">Catherine Autier</span><span class="sxs-lookup"><span data-stu-id="323b4-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="323b4-113">OrdersTable (table enfant)</span><span class="sxs-lookup"><span data-stu-id="323b4-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="323b4-114">OrderID</span><span class="sxs-lookup"><span data-stu-id="323b4-114">OrderID</span></span>|<span data-ttu-id="323b4-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="323b4-115">OrderDate</span></span>|<span data-ttu-id="323b4-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="323b4-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="323b4-117">903</span><span class="sxs-lookup"><span data-stu-id="323b4-117">903</span></span>|<span data-ttu-id="323b4-118">12 février 2004</span><span class="sxs-lookup"><span data-stu-id="323b4-118">February 12, 2004</span></span>|<span data-ttu-id="323b4-119">712</span><span class="sxs-lookup"><span data-stu-id="323b4-119">712</span></span>|  
|<span data-ttu-id="323b4-120">904</span><span class="sxs-lookup"><span data-stu-id="323b4-120">904</span></span>|<span data-ttu-id="323b4-121">13 février 2004</span><span class="sxs-lookup"><span data-stu-id="323b4-121">February 13, 2004</span></span>|<span data-ttu-id="323b4-122">713</span><span class="sxs-lookup"><span data-stu-id="323b4-122">713</span></span>|  
  
 <span data-ttu-id="323b4-123">Dans ce scénario, une table, CustomersTable, stocke les informations réelles que vous souhaitez afficher et enregistrer.</span><span class="sxs-lookup"><span data-stu-id="323b4-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="323b4-124">Mais pour gagner de l'espace, la table délaisse les données qui ajoutent de la clarté.</span><span class="sxs-lookup"><span data-stu-id="323b4-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="323b4-125">L'autre table, OrdersTable, contient uniquement des informations relatives à l'apparence, notamment l'équivalence entre le numéro d'identification du client, l'ID de date et l'ID de commande.</span><span class="sxs-lookup"><span data-stu-id="323b4-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="323b4-126">Les noms des clients ne sont pas mentionnés.</span><span class="sxs-lookup"><span data-stu-id="323b4-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="323b4-127">Quatre propriétés importantes sont définies sur le contrôle [ComboBox](combobox-control-windows-forms.md) pour créer la table de choix.</span><span class="sxs-lookup"><span data-stu-id="323b4-127">Four important properties are set on the [ComboBox Control](combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
- <span data-ttu-id="323b4-128">La propriété <xref:System.Windows.Forms.ComboBox.DataSource%2A> contient le nom de la table.</span><span class="sxs-lookup"><span data-stu-id="323b4-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
- <span data-ttu-id="323b4-129">La propriété <xref:System.Windows.Forms.ListControl.DisplayMember%2A> contient la colonne de données de la table que vous souhaitez afficher pour le texte du contrôle (nom du client).</span><span class="sxs-lookup"><span data-stu-id="323b4-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
- <span data-ttu-id="323b4-130">La propriété <xref:System.Windows.Forms.ListControl.ValueMember%2A> contient la colonne de données de la table ayant les informations stockées (numéro d'identification dans la table parent).</span><span class="sxs-lookup"><span data-stu-id="323b4-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
- <span data-ttu-id="323b4-131">La propriété <xref:System.Windows.Forms.ListControl.SelectedValue%2A> fournit la valeur de recherche pour la table enfant, en fonction de <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="323b4-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="323b4-132">Les procédures ci-dessous vous montrent comment présenter votre formulaire sous forme de table de choix et lier les données aux contrôles qui s'y trouvent.</span><span class="sxs-lookup"><span data-stu-id="323b4-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="323b4-133">Pour mener à bien les procédures, vous devez disposer d'une source de données avec des tables parents et des tables enfants qui ont une relation de clé étrangère, comme indiqué précédemment.</span><span class="sxs-lookup"><span data-stu-id="323b4-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="323b4-134">Pour créer l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="323b4-134">To create the user interface</span></span>  
  
1. <span data-ttu-id="323b4-135">À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.ComboBox> sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="323b4-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="323b4-136">Ce contrôle affiche la colonne de la table parent.</span><span class="sxs-lookup"><span data-stu-id="323b4-136">This control will display the column from parent table.</span></span>  
  
2. <span data-ttu-id="323b4-137">Faites glisser d'autres contrôles pour afficher les détails de la table enfant.</span><span class="sxs-lookup"><span data-stu-id="323b4-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="323b4-138">Le format des données de la table doit déterminer votre choix des contrôles.</span><span class="sxs-lookup"><span data-stu-id="323b4-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="323b4-139">Pour plus d’informations, consultez [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="323b4-139">For more information, see [Windows Forms Controls by Function](windows-forms-controls-by-function.md).</span></span>  
  
3. <span data-ttu-id="323b4-140">Faites glisser un contrôle <xref:System.Windows.Forms.BindingNavigator> vers le formulaire. Cela vous permettra de naviguer parmi les données de la table enfant.</span><span class="sxs-lookup"><span data-stu-id="323b4-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="323b4-141">Pour se connecter aux données et les lier aux contrôles</span><span class="sxs-lookup"><span data-stu-id="323b4-141">To connect to the data and bind it to controls</span></span>  
  
1. <span data-ttu-id="323b4-142">Sélectionnez <xref:System.Windows.Forms.ComboBox>, puis cliquez sur le glyphe Tâche guidée pour afficher la boîte de dialogue Tâche guidée.</span><span class="sxs-lookup"><span data-stu-id="323b4-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2. <span data-ttu-id="323b4-143">Sélectionnez **Utilisez des éléments liés aux données**.</span><span class="sxs-lookup"><span data-stu-id="323b4-143">Select **Use data bound items**.</span></span>  
  
3. <span data-ttu-id="323b4-144">Cliquez sur la flèche à côté de la zone de liste déroulante **Source de données**.</span><span class="sxs-lookup"><span data-stu-id="323b4-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="323b4-145">Si une source de données a déjà été configurée pour le projet ou le formulaire, elle s'affiche. Sinon, procédez comme suit (cet exemple utilise les tables Customers et Orders de l'exemple de base de données Northwind et fait référence à celles-ci entre parenthèses).</span><span class="sxs-lookup"><span data-stu-id="323b4-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1. <span data-ttu-id="323b4-146">Cliquez sur **Ajouter la source de données du projet** pour vous connecter aux données et créer une source de données.</span><span class="sxs-lookup"><span data-stu-id="323b4-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2. <span data-ttu-id="323b4-147">Sur la page d’accueil de l’**Assistant Configuration de source de données**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="323b4-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3. <span data-ttu-id="323b4-148">Sélectionnez **Base de données** sur la page **Choisir un type de source de données**.</span><span class="sxs-lookup"><span data-stu-id="323b4-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4. <span data-ttu-id="323b4-149">Sélectionnez une connexion de données dans la liste des connexions disponibles sur la page **Choisir votre connexion de données**.</span><span class="sxs-lookup"><span data-stu-id="323b4-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="323b4-150">Si la connexion de données souhaitée n’est pas disponible, sélectionnez **Nouvelle connexion** pour créer une connexion de données.</span><span class="sxs-lookup"><span data-stu-id="323b4-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5. <span data-ttu-id="323b4-151">Cliquez sur **Oui, enregistrer la connexion en tant que** pour enregistrer la chaîne de connexion dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="323b4-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6. <span data-ttu-id="323b4-152">Sélectionnez les objets de base de données à mettre dans votre application.</span><span class="sxs-lookup"><span data-stu-id="323b4-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="323b4-153">Dans le cas présent, sélectionnez une table parent et une table enfant (par exemple Customers et Orders) avec une relation de clé étrangère.</span><span class="sxs-lookup"><span data-stu-id="323b4-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7. <span data-ttu-id="323b4-154">Remplacez le nom du jeu de données par défaut, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="323b4-154">Replace the default dataset name if you want.</span></span>  
  
    8. <span data-ttu-id="323b4-155">Cliquez sur **Finish**.</span><span class="sxs-lookup"><span data-stu-id="323b4-155">Click **Finish**.</span></span>  
  
4. <span data-ttu-id="323b4-156">Dans la zone de liste déroulante **Afficher le membre**, sélectionnez le nom de la colonne (par exemple ContactName) à afficher dans la zone de liste modifiable.</span><span class="sxs-lookup"><span data-stu-id="323b4-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5. <span data-ttu-id="323b4-157">Dans la zone de liste déroulante **Membre Value**, sélectionnez la colonne (par exemple, CustomerID) pour effectuer l’opération de recherche dans la table enfant.</span><span class="sxs-lookup"><span data-stu-id="323b4-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6. <span data-ttu-id="323b4-158">Dans la zone de liste déroulante **Valeur sélectionnée**, accédez à **Sources de données du projet** ainsi qu’au jeu de données que vous venez de créer et qui contient les tables parents et les tables enfants.</span><span class="sxs-lookup"><span data-stu-id="323b4-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="323b4-159">Sélectionnez la même propriété de la table enfant qui représente le membre Value de la table parent (par exemple Orders.CustomerID).</span><span class="sxs-lookup"><span data-stu-id="323b4-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="323b4-160">Les composants appropriés de <xref:System.Windows.Forms.BindingSource>, de jeu de données et d'adaptateur de table sont créés et ajoutés au formulaire.</span><span class="sxs-lookup"><span data-stu-id="323b4-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7. <span data-ttu-id="323b4-161">Liez le contrôle <xref:System.Windows.Forms.BindingNavigator> au <xref:System.Windows.Forms.BindingSource> de la table enfant (par exemple `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="323b4-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8. <span data-ttu-id="323b4-162">Liez les contrôles autres que <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.BindingNavigator> aux champs de détails du <xref:System.Windows.Forms.BindingSource> de la table enfant (par exemple `OrdersBindingSource`) à afficher.</span><span class="sxs-lookup"><span data-stu-id="323b4-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="323b4-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="323b4-163">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="323b4-164">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="323b4-164">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="323b4-165">ComboBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="323b4-165">ComboBox Control</span></span>](combobox-control-windows-forms.md)
- [<span data-ttu-id="323b4-166">Lier des contrôles à des données dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="323b4-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
