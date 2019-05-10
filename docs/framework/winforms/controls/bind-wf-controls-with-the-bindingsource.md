---
title: 'Procédure : lier des contrôles Windows Forms au composant BindingSource à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: f8c268c816975fa9b00725d317365c147312b950
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593455"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a><span data-ttu-id="c48de-102">Procédure : lier des contrôles Windows Forms au composant BindingSource à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="c48de-102">How to: Bind Windows Forms Controls with the BindingSource Component Using the Designer</span></span>
<span data-ttu-id="c48de-103">Après avoir ajouté des contrôles à votre formulaire et de déterminer l’interface utilisateur pour votre application, vous pouvez lier les contrôles à une source de données, afin que, au moment de l’exécution, les utilisateurs peuvent modifier et enregistrer des données relatives à l’application.</span><span class="sxs-lookup"><span data-stu-id="c48de-103">After you have added controls to your form and determined the user interface for your application, you can bind the controls to a data source, so that, at run time, users can alter and save data related to the application.</span></span>  
  
 <span data-ttu-id="c48de-104">Liaison d’un contrôle ou une série de contrôles dans les Windows Forms plus simple consiste à l’aide de la <xref:System.Windows.Forms.BindingSource> contrôle comme un pont entre les contrôles sur le formulaire et la source de données.</span><span class="sxs-lookup"><span data-stu-id="c48de-104">Binding a control or series of controls in Windows Forms is most easily accomplished using the <xref:System.Windows.Forms.BindingSource> control as a bridge between the controls on the form and the data source.</span></span>  
  
 <span data-ttu-id="c48de-105">Un ou plusieurs contrôles sur un formulaire peuvent être liés aux données ; dans la procédure suivante, un <xref:System.Windows.Forms.TextBox> contrôle est lié à une source de données.</span><span class="sxs-lookup"><span data-stu-id="c48de-105">One or more controls on a form can be bound to data; in the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to a data source.</span></span>  
  
 <span data-ttu-id="c48de-106">Pour terminer la procédure, il est supposé que vous créerez une liaison à une source de données dérivée d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="c48de-106">To complete the procedure, it is assumed that you will bind to a data source derived from a database.</span></span> <span data-ttu-id="c48de-107">Pour plus d’informations sur la création de sources de données à partir d’autres magasins de données, consultez [ajouter de nouvelles sources de données](/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="c48de-107">For more information on creating data sources from other stores of data, see [Add new data sources](/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c48de-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="c48de-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c48de-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="c48de-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c48de-110">Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="c48de-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-at-design-time"></a><span data-ttu-id="c48de-111">Pour lier un contrôle au moment du design</span><span class="sxs-lookup"><span data-stu-id="c48de-111">To bind a control at design time</span></span>  
  
1. <span data-ttu-id="c48de-112">Faites glisser un <xref:System.Windows.Forms.TextBox> contrôle au formulaire.</span><span class="sxs-lookup"><span data-stu-id="c48de-112">Drag a <xref:System.Windows.Forms.TextBox> control on to the form.</span></span>  
  
2. <span data-ttu-id="c48de-113">Dans le **propriétés** fenêtre :</span><span class="sxs-lookup"><span data-stu-id="c48de-113">In the **Properties** window:</span></span>  
  
    1. <span data-ttu-id="c48de-114">Développez le **(DataBindings)** nœud.</span><span class="sxs-lookup"><span data-stu-id="c48de-114">Expand the **(DataBindings)** node.</span></span>  
  
    2. <span data-ttu-id="c48de-115">Cliquez sur la flèche en regard du <xref:System.Windows.Forms.TextBox.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c48de-115">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
         <span data-ttu-id="c48de-116">Le **DataSource** éditeur de type d’interface utilisateur s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="c48de-116">The **DataSource** UI type editor opens.</span></span>  
  
         <span data-ttu-id="c48de-117">Si une source de données a été précédemment configurée pour le projet ou d’un formulaire, il apparaît.</span><span class="sxs-lookup"><span data-stu-id="c48de-117">If a data source has previously been configured for the project or form, it will appear.</span></span>  
  
3. <span data-ttu-id="c48de-118">Cliquez sur **Ajouter la source de données du projet** pour vous connecter aux données et créer une source de données.</span><span class="sxs-lookup"><span data-stu-id="c48de-118">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
4. <span data-ttu-id="c48de-119">Sur la page d’accueil de l’**Assistant Configuration de source de données**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="c48de-119">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
5. <span data-ttu-id="c48de-120">Sur le **choisir un Type de Source de données** page, sélectionnez **base de données**.</span><span class="sxs-lookup"><span data-stu-id="c48de-120">On the **Choose a Data Source Type** page, select **Database**.</span></span>  
  
6. <span data-ttu-id="c48de-121">Sur le **choisir votre connexion de données** , sélectionnez une connexion de données à partir de la liste des connexions disponibles.</span><span class="sxs-lookup"><span data-stu-id="c48de-121">On the **Choose Your Data Connection** page, select a data connection from the list of available connections.</span></span> <span data-ttu-id="c48de-122">Si votre connexion de données souhaitée n’est pas disponible select **nouvelle connexion** pour créer une connexion de données.</span><span class="sxs-lookup"><span data-stu-id="c48de-122">If your desired data connection is not available select **New Connection** to create a new data connection.</span></span>  
  
7. <span data-ttu-id="c48de-123">Sélectionnez **Oui, enregistrer la connexion** pour enregistrer la chaîne de connexion dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="c48de-123">Select **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
8. <span data-ttu-id="c48de-124">Sélectionnez les objets de base de données à mettre dans votre application.</span><span class="sxs-lookup"><span data-stu-id="c48de-124">Select the database objects to bring into your application.</span></span> <span data-ttu-id="c48de-125">Dans ce cas, sélectionnez un champ dans une table que vous souhaitez que le <xref:System.Windows.Forms.TextBox> à afficher.</span><span class="sxs-lookup"><span data-stu-id="c48de-125">In this case, select a field in a table that you would like the <xref:System.Windows.Forms.TextBox> to display.</span></span>  
  
9. <span data-ttu-id="c48de-126">Remplacez le nom du jeu de données par défaut, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="c48de-126">Replace the default dataset name if you want.</span></span>  
  
10. <span data-ttu-id="c48de-127">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="c48de-127">Click **Finish**.</span></span>  
  
11. <span data-ttu-id="c48de-128">Dans le **propriétés** fenêtre, cliquez sur la flèche en regard du <xref:System.Windows.Forms.TextBox.Text%2A> propriété à nouveau.</span><span class="sxs-lookup"><span data-stu-id="c48de-128">In the **Properties** window, click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property again.</span></span> <span data-ttu-id="c48de-129">Dans le **DataSource** éditeur de type d’interface utilisateur, sélectionnez le nom du champ à lier le <xref:System.Windows.Forms.TextBox> à.</span><span class="sxs-lookup"><span data-stu-id="c48de-129">In the **DataSource** UI type editor, select the name of the field to bind the <xref:System.Windows.Forms.TextBox> to.</span></span>  
  
     <span data-ttu-id="c48de-130">Le **DataSource** se ferme l’éditeur et le jeu de données, type d’interface utilisateur <xref:System.Windows.Forms.BindingSource> et l’adaptateur de table spécifique pour que la connexion de données sont ajoutés à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="c48de-130">The **DataSource** UI type editor closes and the data set, <xref:System.Windows.Forms.BindingSource> and table adapter specific to that data connection are added to your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c48de-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c48de-131">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="c48de-132">Ajouter de nouvelles sources de données</span><span class="sxs-lookup"><span data-stu-id="c48de-132">Add new data sources</span></span>](/visualstudio/data-tools/add-new-data-sources)
- <span data-ttu-id="c48de-133">[Fenêtre Sources de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c48de-133">[Data Sources Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))</span></span>
