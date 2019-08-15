---
title: 'Procédure : lier des contrôles Windows Forms au composant BindingSource à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040015"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="58266-102">Procédure : lier des contrôles Windows Forms au composant BindingSource à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="58266-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="58266-103">Une fois que vous avez ajouté des contrôles à votre formulaire et déterminé l’interface utilisateur de votre application, vous pouvez lier les contrôles à une source de données, de sorte qu’au moment de l’exécution, les utilisateurs puissent modifier et enregistrer des données relatives à l’application.</span><span class="sxs-lookup"><span data-stu-id="58266-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>

 <span data-ttu-id="58266-104">La liaison d’un contrôle ou d’une série de contrôles dans Windows Forms est plus <xref:System.Windows.Forms.BindingSource> facile à effectuer à l’aide du contrôle comme un pont entre les contrôles sur le formulaire et la source de données.</span><span class="sxs-lookup"><span data-stu-id="58266-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>

 <span data-ttu-id="58266-105">Un ou plusieurs contrôles d’un formulaire peuvent être liés à des données; dans la procédure suivante, un <xref:System.Windows.Forms.TextBox> contrôle est lié à une source de données.</span><span class="sxs-lookup"><span data-stu-id="58266-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>

 <span data-ttu-id="58266-106">Pour terminer la procédure, il est supposé que vous allez établir une liaison avec une source de données dérivée d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="58266-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="58266-107">Pour plus d’informations sur la création de sources de données à partir d’autres magasins de données, consultez [ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="58266-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>

## <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="58266-108">Pour lier un contrôle au moment du design</span><span class="sxs-lookup"><span data-stu-id="58266-108">To bind a control at design time</span></span>

1. <span data-ttu-id="58266-109">Faites glisser <xref:System.Windows.Forms.TextBox> un contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="58266-109">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>

2. <span data-ttu-id="58266-110">Dans la fenêtre **Propriétés** :</span><span class="sxs-lookup"><span data-stu-id="58266-110">In the **Properties** window:</span></span>

    1. <span data-ttu-id="58266-111">Développez le nœud **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="58266-111">Expand the **(DataBindings)** node.</span></span>

    2. <span data-ttu-id="58266-112">Cliquez sur la flèche en regard <xref:System.Windows.Forms.TextBox.Text%2A> de la propriété.</span><span class="sxs-lookup"><span data-stu-id="58266-112">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>

         <span data-ttu-id="58266-113">L’éditeur de types de l’interface utilisateur **DataSource** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="58266-113">The **DataSource** UI type editor opens.</span></span>

         <span data-ttu-id="58266-114">Si une source de données a déjà été configurée pour le projet ou le formulaire, elle s’affiche.</span><span class="sxs-lookup"><span data-stu-id="58266-114">If a data source has previously been configured for the project or form, it will appear.</span></span>

3. <span data-ttu-id="58266-115">Cliquez sur **Ajouter la source de données du projet** pour vous connecter aux données et créer une source de données.</span><span class="sxs-lookup"><span data-stu-id="58266-115">Click **Add Project Data Source** to connect to data and create a data source.</span></span>

4. <span data-ttu-id="58266-116">Sur la page d’accueil de l’**Assistant Configuration de source de données**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="58266-116">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>

5. <span data-ttu-id="58266-117">Dans la page **choisir un type de source de données** , sélectionnez **base de**données.</span><span class="sxs-lookup"><span data-stu-id="58266-117">On the **Choose a Data Source Type** page, select **Database**.</span></span>

6. <span data-ttu-id="58266-118">Sur la page **choisir votre connexion de données** , sélectionnez une connexion de données dans la liste des connexions disponibles.</span><span class="sxs-lookup"><span data-stu-id="58266-118">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="58266-119">Si la connexion de données souhaitée n’est pas disponible, sélectionnez **nouvelle connexion** pour créer une nouvelle connexion de données.</span><span class="sxs-lookup"><span data-stu-id="58266-119">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>

7. <span data-ttu-id="58266-120">Sélectionnez **Oui, enregistrer la connexion** pour enregistrer la chaîne de connexion dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="58266-120">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>

8. <span data-ttu-id="58266-121">Sélectionnez les objets de base de données à mettre dans votre application.</span><span class="sxs-lookup"><span data-stu-id="58266-121">Select the database objects to bring into your application.</span></span> <span data-ttu-id="58266-122">Dans ce cas, sélectionnez un champ dans une table que vous <xref:System.Windows.Forms.TextBox> souhaitez afficher.</span><span class="sxs-lookup"><span data-stu-id="58266-122">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>

9. <span data-ttu-id="58266-123">Remplacez le nom du jeu de données par défaut, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="58266-123">Replace the default dataset name if you want.</span></span>

10. <span data-ttu-id="58266-124">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="58266-124">Click **Finish**.</span></span>

11. <span data-ttu-id="58266-125">Dans la fenêtre **Propriétés** , cliquez à nouveau sur la flèche <xref:System.Windows.Forms.TextBox.Text%2A> à côté de la propriété.</span><span class="sxs-lookup"><span data-stu-id="58266-125">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="58266-126">Dans l’éditeur de types d’interface utilisateur **DataSource** , sélectionnez le nom du champ <xref:System.Windows.Forms.TextBox> auquel vous souhaitez lier.</span><span class="sxs-lookup"><span data-stu-id="58266-126">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>

     <span data-ttu-id="58266-127">L’éditeur de type d’interface utilisateur **DataSource** se ferme et <xref:System.Windows.Forms.BindingSource> le jeu de données, et l’adaptateur de table propre à cette connexion de données sont ajoutés à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="58266-127">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>

## <a name="see-also"></a><span data-ttu-id="58266-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58266-128">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="58266-129">Ajouter de nouvelles sources de données</span><span class="sxs-lookup"><span data-stu-id="58266-129">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="58266-130">[Fenêtre sources de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="58266-130">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>
