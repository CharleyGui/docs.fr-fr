---
title: 'Procédure pas à pas : Sérialisation des collections de types standard avec DesignerSerializationVisibilityAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2fbb0715d148b443b1eca8f400e4ad43eb51fa43
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015733"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a><span data-ttu-id="134e7-102">Procédure pas à pas : Sérialiser des collections de types standard</span><span class="sxs-lookup"><span data-stu-id="134e7-102">Walkthrough: Serialize collections of standard types</span></span>

<span data-ttu-id="134e7-103">Vos contrôles personnalisés exposent parfois une collection en tant que propriété.</span><span class="sxs-lookup"><span data-stu-id="134e7-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="134e7-104">Cette procédure pas à pas montre comment <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> utiliser la classe pour contrôler la façon dont une collection est sérialisée au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="134e7-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="134e7-105">L’application <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> de la valeur à votre propriété de collection garantit que la propriété sera sérialisée.</span><span class="sxs-lookup"><span data-stu-id="134e7-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="134e7-106">Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Sérialiser des collections de types standard avec DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="134e7-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="134e7-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="134e7-107">Prerequisites</span></span>

<span data-ttu-id="134e7-108">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="134e7-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="134e7-109">Créer un contrôle avec une collection sérialisable</span><span class="sxs-lookup"><span data-stu-id="134e7-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="134e7-110">La première étape consiste à créer un contrôle qui a une collection sérialisable en tant que propriété.</span><span class="sxs-lookup"><span data-stu-id="134e7-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="134e7-111">Vous pouvez modifier le contenu de cette collection à l’aide de l' **éditeur de collections**, auquel vous pouvez accéder à partir de la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="134e7-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="134e7-112">Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="134e7-112">In Visual Studio, create a Windows Control Library project, and name it **SerializationDemoControlLib**.</span></span>

2. <span data-ttu-id="134e7-113">`UserControl1` Renommez `SerializationDemoControl`-le.</span><span class="sxs-lookup"><span data-stu-id="134e7-113">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="134e7-114">Pour plus d’informations, consultez [Renommer un symbole de code](/visualstudio/ide/reference/rename)refactorisation.</span><span class="sxs-lookup"><span data-stu-id="134e7-114">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="134e7-115">Dans la fenêtre **Propriétés** , affectez à la <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> propriété la valeur **10**.</span><span class="sxs-lookup"><span data-stu-id="134e7-115">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to **10**.</span></span>

4. <span data-ttu-id="134e7-116">Placez un <xref:System.Windows.Forms.TextBox> contrôle dans le `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="134e7-116">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="134e7-117">Sélectionnez le contrôle <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="134e7-117">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="134e7-118">Dans la fenêtre **Propriétés** , définissez les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="134e7-118">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="134e7-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="134e7-119">Property</span></span>|<span data-ttu-id="134e7-120">Remplacer par</span><span class="sxs-lookup"><span data-stu-id="134e7-120">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="134e7-121">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="134e7-121">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="134e7-122">**Sa**</span><span class="sxs-lookup"><span data-stu-id="134e7-122">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="134e7-123">**ScrollBars**</span><span class="sxs-lookup"><span data-stu-id="134e7-123">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="134e7-124">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="134e7-124">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="134e7-125">Dans l' **éditeur de code**, déclarez un champ de `stringsValue` tableau `SerializationDemoControl`de chaînes nommé dans.</span><span class="sxs-lookup"><span data-stu-id="134e7-125">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="134e7-126">Définissez la `Strings` propriété sur le `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="134e7-126">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="134e7-127">La <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valeur est utilisée pour activer la sérialisation de la collection.</span><span class="sxs-lookup"><span data-stu-id="134e7-127">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="134e7-128">Appuyez sur **F5** pour générer le projet et exécuter votre contrôle dans le **conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="134e7-128">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="134e7-129">Recherchez la propriété Strings dans <xref:System.Windows.Forms.PropertyGrid> le du **conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="134e7-129">Find the **Strings** property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="134e7-130">Sélectionnez la **propriété chaînes** , puis cliquez sur le bouton![de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png)) pour ouvrir l' **éditeur de collections String**.</span><span class="sxs-lookup"><span data-stu-id="134e7-130">Select the **Strings** property, then select the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="134e7-131">Entrez plusieurs chaînes dans l **'éditeur de collections String**.</span><span class="sxs-lookup"><span data-stu-id="134e7-131">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="134e7-132">Séparez-les en appuyant sur la touche **entrée** à la fin de chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="134e7-132">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="134e7-133">Cliquez sur **OK** lorsque vous avez terminé d’entrer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="134e7-133">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="134e7-134">Les chaînes que vous avez tapées <xref:System.Windows.Forms.TextBox> apparaissent dans `SerializationDemoControl`le de.</span><span class="sxs-lookup"><span data-stu-id="134e7-134">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serialize-a-collection-property"></a><span data-ttu-id="134e7-135">Sérialiser une propriété de collection</span><span class="sxs-lookup"><span data-stu-id="134e7-135">Serialize a collection property</span></span>

<span data-ttu-id="134e7-136">Pour tester le comportement de sérialisation de votre contrôle, vous devez le placer dans un formulaire et modifier le contenu de la collection à l’aide de l' **éditeur de collections**.</span><span class="sxs-lookup"><span data-stu-id="134e7-136">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="134e7-137">Vous pouvez voir l’état de la collection sérialisée en examinant un fichier de concepteur spécial dans lequel le **Concepteur Windows Forms** émet du code.</span><span class="sxs-lookup"><span data-stu-id="134e7-137">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

1. <span data-ttu-id="134e7-138">Ajoutez un projet d’application Windows à la solution.</span><span class="sxs-lookup"><span data-stu-id="134e7-138">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="134e7-139">Attribuez un nom au projet `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="134e7-139">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="134e7-140">Dans la **boîte à outils**, recherchez l’onglet **Composants SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="134e7-140">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="134e7-141">Dans cet onglet, vous trouverez le `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="134e7-141">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="134e7-142">Pour plus d’informations, consultez [Procédure pas à pas : Remplissage automatique de la boîte à outils](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)avec des composants personnalisés.</span><span class="sxs-lookup"><span data-stu-id="134e7-142">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="134e7-143">Placez un `SerializationDemoControl` sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="134e7-143">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="134e7-144">Recherchez la `Strings` propriété dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="134e7-144">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="134e7-145">Cliquez sur `Strings` la propriété, puis sur le![bouton de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) pour ouvrir l' **éditeur de collections String**.</span><span class="sxs-lookup"><span data-stu-id="134e7-145">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="134e7-146">Tapez plusieurs chaînes dans l **'éditeur de collections String**.</span><span class="sxs-lookup"><span data-stu-id="134e7-146">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="134e7-147">Séparez-les en appuyant sur **entrée** à la fin de chaque chaîne.</span><span class="sxs-lookup"><span data-stu-id="134e7-147">Separate them by pressing **Enter** at the end of each string.</span></span> <span data-ttu-id="134e7-148">Cliquez sur **OK** lorsque vous avez terminé d’entrer des chaînes.</span><span class="sxs-lookup"><span data-stu-id="134e7-148">Click **OK** when you are finished entering strings.</span></span>

> [!NOTE]
> <span data-ttu-id="134e7-149">Les chaînes que vous avez tapées <xref:System.Windows.Forms.TextBox> apparaissent dans `SerializationDemoControl`le de.</span><span class="sxs-lookup"><span data-stu-id="134e7-149">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

6. <span data-ttu-id="134e7-150">Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="134e7-150">In **Solution Explorer**, click the **Show All Files** button.</span></span>

7. <span data-ttu-id="134e7-151">Ouvrez le nœud **Form1** .</span><span class="sxs-lookup"><span data-stu-id="134e7-151">Open the **Form1** node.</span></span> <span data-ttu-id="134e7-152">En dessous, il s’agit d’un fichier nommé **Form1.Designer.cs** ou **Form1. Designer. vb**.</span><span class="sxs-lookup"><span data-stu-id="134e7-152">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="134e7-153">Il s’agit du fichier dans lequel le **Concepteur Windows Forms** émet du code représentant l’État au moment du design de votre formulaire et de ses contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="134e7-153">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="134e7-154">Ouvrez ce fichier dans **l’éditeur de code**.</span><span class="sxs-lookup"><span data-stu-id="134e7-154">Open this file in the **Code Editor**.</span></span>

8. <span data-ttu-id="134e7-155">Ouvrez la région appelée **code généré par le Concepteur Windows Form** et recherchez la section intitulée **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="134e7-155">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="134e7-156">Sous cette étiquette se trouve le code qui représente l’État sérialisé de votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="134e7-156">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="134e7-157">Les chaînes que vous avez tapées à l’étape 5 apparaissent dans `Strings` une assignation à la propriété.</span><span class="sxs-lookup"><span data-stu-id="134e7-157">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="134e7-158">Les exemples de code suivants C# dans et Visual Basic, montrent un code similaire à ce que vous verrez si vous avez tapé les chaînes «Red», «orange» et «Yellow».</span><span class="sxs-lookup"><span data-stu-id="134e7-158">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. <span data-ttu-id="134e7-159">Dans l' **éditeur de code**, affectez à <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>la `Strings` propriété de la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="134e7-159">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. <span data-ttu-id="134e7-160">Régénérez la solution et répétez les étapes 3 et 4.</span><span class="sxs-lookup"><span data-stu-id="134e7-160">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="134e7-161">Dans ce cas, le **Concepteur Windows Forms** n’émet aucune assignation à `Strings` la propriété.</span><span class="sxs-lookup"><span data-stu-id="134e7-161">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="134e7-162">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="134e7-162">Next steps</span></span>

<span data-ttu-id="134e7-163">Une fois que vous savez comment sérialiser une collection de types standard, envisagez d’intégrer vos contrôles personnalisés plus profondément dans l’environnement au moment du Design.</span><span class="sxs-lookup"><span data-stu-id="134e7-163">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="134e7-164">Les rubriques suivantes décrivent comment améliorer l’intégration au moment du design de vos contrôles personnalisés:</span><span class="sxs-lookup"><span data-stu-id="134e7-164">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="134e7-165">[Architecture au moment du design](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="134e7-165">[Design-Time Architecture](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="134e7-166">Attributs dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="134e7-166">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="134e7-167">[Vue d’ensemble de la sérialisation du concepteur](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="134e7-167">[Designer Serialization Overview](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="134e7-168">Procédure pas à pas : Création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="134e7-168">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="134e7-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="134e7-169">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [<span data-ttu-id="134e7-170">Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="134e7-170">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
