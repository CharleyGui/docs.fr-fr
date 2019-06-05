---
title: 'Procédure : créer un contrôle à liaison simple dans un formulaire Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 5c92b7bfd5026b0569397dc05cca216fbdab0753
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689304"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="33f8d-102">Procédure : créer un contrôle à liaison simple dans un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="33f8d-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>

<span data-ttu-id="33f8d-103">Avec *liaison simple*, vous pouvez afficher un seul élément de données, telle qu’une valeur de colonne à partir d’une table de dataset dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="33f8d-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="33f8d-104">Vous pouvez créer une liaison simple n’importe quelle propriété d’un contrôle à une valeur de données.</span><span class="sxs-lookup"><span data-stu-id="33f8d-104">You can simple-bind any property of a control to a data value.</span></span>

> [!NOTE]
> <span data-ttu-id="33f8d-105">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="33f8d-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="33f8d-106">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="33f8d-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="33f8d-107">Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="33f8d-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

### <a name="to-simple-bind-a-control"></a><span data-ttu-id="33f8d-108">Pour un contrôle à liaison simple</span><span class="sxs-lookup"><span data-stu-id="33f8d-108">To simple-bind a control</span></span>

1. <span data-ttu-id="33f8d-109">Connectez-vous à une source de données.</span><span class="sxs-lookup"><span data-stu-id="33f8d-109">Connect to a data source.</span></span> <span data-ttu-id="33f8d-110">Pour plus d’informations, consultez [connexion à une Source de données](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="33f8d-110">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="33f8d-111">Dans le formulaire, sélectionnez le contrôle et affichez la **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="33f8d-111">In the form, select the control and display the **Properties** window.</span></span>

3. <span data-ttu-id="33f8d-112">Développez le **(DataBindings)** propriété.</span><span class="sxs-lookup"><span data-stu-id="33f8d-112">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="33f8d-113">Les propriétés les plus souvent liées sont affichées sous la **(DataBindings)** propriété.</span><span class="sxs-lookup"><span data-stu-id="33f8d-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="33f8d-114">Par exemple, dans la plupart des contrôles, le **texte** propriété est liée plus fréquemment.</span><span class="sxs-lookup"><span data-stu-id="33f8d-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="33f8d-115">Si la propriété dont vous souhaitez lier ne fait pas partie des propriétés couramment liées, cliquez sur le **points de suspension** bouton (![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) dans le **() Avancé)** à cocher pour afficher le **mise en forme et liaison avancée** boîte de dialogue avec une liste complète des propriétés pour ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="33f8d-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="33f8d-116">Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur la flèche déroulante sous **liaison**.</span><span class="sxs-lookup"><span data-stu-id="33f8d-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="33f8d-117">Une liste des sources de données disponibles s'affiche.</span><span class="sxs-lookup"><span data-stu-id="33f8d-117">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="33f8d-118">Développez la source de données avec laquelle vous voulez établir une liaison jusqu’à trouver l’élément de données souhaité.</span><span class="sxs-lookup"><span data-stu-id="33f8d-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="33f8d-119">Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.</span><span class="sxs-lookup"><span data-stu-id="33f8d-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="33f8d-120">Cliquez sur le nom d'un élément avec lequel établir une liaison.</span><span class="sxs-lookup"><span data-stu-id="33f8d-120">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="33f8d-121">Si vous travailliez le **mise en forme et liaison avancée** boîte de dialogue, cliquez sur **OK** pour revenir à la **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="33f8d-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="33f8d-122">Si vous souhaitez lier d’autres propriétés du contrôle, répétez les étapes 3 à 7.</span><span class="sxs-lookup"><span data-stu-id="33f8d-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="33f8d-123">Étant donné que les contrôles de liaison simple affichent uniquement un seul élément de données, il est très courant d’inclure une logique de navigation dans un formulaire Windows avec des contrôles de liaison simple.</span><span class="sxs-lookup"><span data-stu-id="33f8d-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="33f8d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33f8d-124">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="33f8d-125">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33f8d-125">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="33f8d-126">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="33f8d-126">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
