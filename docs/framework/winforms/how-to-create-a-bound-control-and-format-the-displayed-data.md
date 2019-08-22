---
title: 'Procédure : créer un contrôle lié et mettre en forme les données affichées'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: b5ad85a9477ca32cd28f246abe4ece3cace43182
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666771"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="bcacc-102">Procédure : créer un contrôle lié et mettre en forme les données affichées</span><span class="sxs-lookup"><span data-stu-id="bcacc-102">How to: Create a Bound Control and Format the Displayed Data</span></span>

<span data-ttu-id="bcacc-103">Avec Windows Forms la liaison de données, vous pouvez mettre en forme les données affichées dans un contrôle lié aux données à l’aide de la boîte de dialogue **mise en forme et liaison avancée** .</span><span class="sxs-lookup"><span data-stu-id="bcacc-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>

### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="bcacc-104">Pour lier un contrôle et mettre en forme les données affichées</span><span class="sxs-lookup"><span data-stu-id="bcacc-104">To bind a control and format the displayed data</span></span>

1. <span data-ttu-id="bcacc-105">Connectez-vous à une source de données.</span><span class="sxs-lookup"><span data-stu-id="bcacc-105">Connect to a data source.</span></span>

     <span data-ttu-id="bcacc-106">Pour plus d’informations, consultez [connexion à une source de données](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="bcacc-106">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="bcacc-107">Dans le formulaire, sélectionnez le contrôle, puis ouvrez la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="bcacc-107">In the form, select the control, and then open the Properties window.</span></span>

3. <span data-ttu-id="bcacc-108">Développez la propriété **(DataBindings)** , puis dans la zone **(avancé)** , cliquez sur le bouton de![sélection (le bouton de sélection (...) dans le fenêtre Propriétés de](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)Visual Studio.) pour afficher les **options de mise en forme et avancé** La boîte de dialogue liaison, qui contient la liste complète des propriétés de ce contrôle.</span><span class="sxs-lookup"><span data-stu-id="bcacc-108">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>

4. <span data-ttu-id="bcacc-109">Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur la flèche **liaison** .</span><span class="sxs-lookup"><span data-stu-id="bcacc-109">Select the property you want to bind, and then click the **Binding** arrow.</span></span>

     <span data-ttu-id="bcacc-110">Une liste des sources de données disponibles s'affiche.</span><span class="sxs-lookup"><span data-stu-id="bcacc-110">A list of available data sources is displayed.</span></span>

5. <span data-ttu-id="bcacc-111">Développez la source de données avec laquelle vous voulez établir une liaison jusqu’à trouver l’élément de données souhaité.</span><span class="sxs-lookup"><span data-stu-id="bcacc-111">Expand the data source you want to bind to until you find the single data element you want.</span></span>

     <span data-ttu-id="bcacc-112">Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.</span><span class="sxs-lookup"><span data-stu-id="bcacc-112">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

6. <span data-ttu-id="bcacc-113">Cliquez sur le nom d'un élément avec lequel établir une liaison.</span><span class="sxs-lookup"><span data-stu-id="bcacc-113">Click the name of an element to bind to.</span></span>

7. <span data-ttu-id="bcacc-114">Dans la zone **type de format** , cliquez sur le format que vous souhaitez appliquer aux données affichées dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="bcacc-114">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>

     <span data-ttu-id="bcacc-115">Dans tous les cas, vous pouvez spécifier la valeur affichée dans le contrôle si la source de données contient <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="bcacc-115">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="bcacc-116">Sinon, les options varient légèrement en fonction du type de format que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="bcacc-116">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="bcacc-117">Le tableau suivant présente les options et les types de format.</span><span class="sxs-lookup"><span data-stu-id="bcacc-117">The following table shows the format types and options.</span></span>

    |<span data-ttu-id="bcacc-118">Type de format</span><span class="sxs-lookup"><span data-stu-id="bcacc-118">Format type</span></span>|<span data-ttu-id="bcacc-119">Option de mise en forme</span><span class="sxs-lookup"><span data-stu-id="bcacc-119">Formatting option</span></span>|
    |-----------------|-----------------------|
    |<span data-ttu-id="bcacc-120">Aucune mise en forme</span><span class="sxs-lookup"><span data-stu-id="bcacc-120">No Formatting</span></span>|<span data-ttu-id="bcacc-121">Aucune option.</span><span class="sxs-lookup"><span data-stu-id="bcacc-121">No options.</span></span>|
    |<span data-ttu-id="bcacc-122">Numeric</span><span class="sxs-lookup"><span data-stu-id="bcacc-122">Numeric</span></span>|<span data-ttu-id="bcacc-123">Spécifiez le nombre de décimales à l’aide du contrôle de nombre de décimales.</span><span class="sxs-lookup"><span data-stu-id="bcacc-123">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="bcacc-124">Devise</span><span class="sxs-lookup"><span data-stu-id="bcacc-124">Currency</span></span>|<span data-ttu-id="bcacc-125">Spécifiez le nombre de décimales à l’aide du contrôle de nombre de décimales.</span><span class="sxs-lookup"><span data-stu-id="bcacc-125">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="bcacc-126">Date et heure</span><span class="sxs-lookup"><span data-stu-id="bcacc-126">Date Time</span></span>|<span data-ttu-id="bcacc-127">Sélectionnez le mode d’affichage de la date et de l’heure en sélectionnant l’un des éléments dans la zone de sélection **type** .</span><span class="sxs-lookup"><span data-stu-id="bcacc-127">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|
    |<span data-ttu-id="bcacc-128">Scientifique</span><span class="sxs-lookup"><span data-stu-id="bcacc-128">Scientific</span></span>|<span data-ttu-id="bcacc-129">Spécifiez le nombre de décimales à l’aide du contrôle de nombre de décimales.</span><span class="sxs-lookup"><span data-stu-id="bcacc-129">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="bcacc-130">Personnalisé</span><span class="sxs-lookup"><span data-stu-id="bcacc-130">Custom</span></span>|<span data-ttu-id="bcacc-131">Spécifiez une chaîne de format personnalisée.</span><span class="sxs-lookup"><span data-stu-id="bcacc-131">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="bcacc-132">Pour plus d’informations, consultez [Mise en forme des types](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="bcacc-132">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="bcacc-133">**Remarque :**  Il n'est pas garanti que les chaînes de format personnalisées puissent effectuer un aller-retour entre la source de données et le contrôle dépendant.</span><span class="sxs-lookup"><span data-stu-id="bcacc-133">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="bcacc-134">Gérez plutôt l'événement <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> pour la liaison et appliquez la mise en forme personnalisée dans le code de gestion d'événements.</span><span class="sxs-lookup"><span data-stu-id="bcacc-134">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|

8. <span data-ttu-id="bcacc-135">Cliquez sur **OK** pour fermer la boîte de dialogue **mise en forme et liaison avancée** et revenir au fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="bcacc-135">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>

## <a name="see-also"></a><span data-ttu-id="bcacc-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcacc-136">See also</span></span>

- [<span data-ttu-id="bcacc-137">Guide pratique : Créer un contrôle à liaison simple dans un Windows Form</span><span class="sxs-lookup"><span data-stu-id="bcacc-137">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="bcacc-138">Validation des entrées d’utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bcacc-138">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="bcacc-139">Liaison de données Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bcacc-139">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
