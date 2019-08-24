---
title: 'Procédure : créer un contrôle à liaison simple dans un formulaire Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: df87f00e6e03de67c3fb1adc28472c96f4a47ef4
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015632"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="74ea6-102">Procédure : Créer un contrôle à liaison simple dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="74ea6-102">How to: Create a simple-bound control on a Windows Form</span></span>

<span data-ttu-id="74ea6-103">Avec une *liaison simple*, vous pouvez afficher un élément de données unique, tel qu’une valeur de colonne à partir d’une table de DataSet, dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="74ea6-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="74ea6-104">Vous pouvez facilement lier n’importe quelle propriété d’un contrôle à une valeur de données.</span><span class="sxs-lookup"><span data-stu-id="74ea6-104">You can simple-bind any property of a control to a data value.</span></span>

## <a name="to-simple-bind-a-control"></a><span data-ttu-id="74ea6-105">Pour lier un contrôle de façon simple</span><span class="sxs-lookup"><span data-stu-id="74ea6-105">To simple-bind a control</span></span>

1. <span data-ttu-id="74ea6-106">Connectez-vous à une source de données.</span><span class="sxs-lookup"><span data-stu-id="74ea6-106">Connect to a data source.</span></span> <span data-ttu-id="74ea6-107">Pour plus d’informations, consultez [connexion à une source de données](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="74ea6-107">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="74ea6-108">Dans Visual Studio, sélectionnez le contrôle dans le formulaire et affichez la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="74ea6-108">In Visual Studio, select the control on the form and display the **Properties** window.</span></span>

3. <span data-ttu-id="74ea6-109">Développez la propriété **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="74ea6-109">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="74ea6-110">Les propriétés les plus souvent liées sont affichées sous la propriété **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="74ea6-110">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="74ea6-111">Par exemple, dans la plupart des contrôles, la propriété **Text** est la plus souvent liée.</span><span class="sxs-lookup"><span data-stu-id="74ea6-111">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="74ea6-112">Si la propriété que vous souhaitez lier ne fait pas partie des propriétés couramment liées, cliquez sur le bouton de![sélection (le bouton de sélection (...) dans la fenêtre Propriétés de](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)Visual Studio). dans la zone **(avancé)** pour afficher la  **Boîte de dialogue mise en forme et liaison avancée** avec la liste complète des propriétés de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="74ea6-112">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="74ea6-113">Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur la flèche déroulante sous **liaison**.</span><span class="sxs-lookup"><span data-stu-id="74ea6-113">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="74ea6-114">Une liste des sources de données disponibles s'affiche.</span><span class="sxs-lookup"><span data-stu-id="74ea6-114">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="74ea6-115">Développez la source de données avec laquelle vous voulez établir une liaison jusqu’à trouver l’élément de données souhaité.</span><span class="sxs-lookup"><span data-stu-id="74ea6-115">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="74ea6-116">Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.</span><span class="sxs-lookup"><span data-stu-id="74ea6-116">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="74ea6-117">Cliquez sur le nom d'un élément avec lequel établir une liaison.</span><span class="sxs-lookup"><span data-stu-id="74ea6-117">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="74ea6-118">Si vous travailliez dans la boîte de dialogue **mise en forme et liaison avancée** , cliquez sur **OK** pour revenir à la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="74ea6-118">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="74ea6-119">Si vous souhaitez lier des propriétés supplémentaires du contrôle, répétez les étapes 3 à 7.</span><span class="sxs-lookup"><span data-stu-id="74ea6-119">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="74ea6-120">Étant donné que les contrôles à liaison simple n’affichent qu’un seul élément de données, il est très courant d’inclure la logique de navigation dans un Windows Form avec des contrôles à liaison simple.</span><span class="sxs-lookup"><span data-stu-id="74ea6-120">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="74ea6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74ea6-121">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="74ea6-122">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74ea6-122">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="74ea6-123">Liaison de données et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74ea6-123">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
