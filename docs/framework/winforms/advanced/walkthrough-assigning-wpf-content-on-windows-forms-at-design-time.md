---
title: Sélectionner des contrôles WPF pour Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19f1dfec282b025f5a1fa367ec5fa9a52472c691
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746808"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="16e1c-102">Procédure pas à pas : assigner du contenu WPF sur Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="16e1c-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="16e1c-103">Cet article vous montre comment sélectionner les types de contrôle Windows Presentation Foundation (WPF) que vous souhaitez afficher dans votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="16e1c-103">This article show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="16e1c-104">Vous pouvez sélectionner n’importe quel type de contrôle WPF inclus dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="16e1c-104">You can select any WPF control types that are included in your project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16e1c-105">Composants requis</span><span class="sxs-lookup"><span data-stu-id="16e1c-105">Prerequisites</span></span>

<span data-ttu-id="16e1c-106">Cette procédure pas à pas nécessite Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="16e1c-106">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="16e1c-107">Créer le projet</span><span class="sxs-lookup"><span data-stu-id="16e1c-107">Create the project</span></span>

<span data-ttu-id="16e1c-108">Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel nommé `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="16e1c-108">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="16e1c-109">Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="16e1c-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="16e1c-110">Créer les types de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="16e1c-110">Create the WPF control types</span></span>

<span data-ttu-id="16e1c-111">Après avoir ajouté des types de contrôles WPF au projet, vous pouvez les héberger dans différents contrôles <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="16e1c-111">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

1. <span data-ttu-id="16e1c-112">Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution.</span><span class="sxs-lookup"><span data-stu-id="16e1c-112">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="16e1c-113">Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="16e1c-113">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="16e1c-114">Pour plus d’informations, consultez [procédure pas à pas : création de contenu WPF sur Windows Forms au moment du design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="16e1c-114">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="16e1c-115">En mode Design, assurez-vous que `UserControl1` est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="16e1c-115">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="16e1c-116">Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="16e1c-116">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="16e1c-117">Ajoutez un contrôle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> au <xref:System.Windows.Controls.UserControl> et définissez la valeur de la propriété <xref:System.Windows.Controls.TextBox.Text%2A> sur le **contenu hébergé**.</span><span class="sxs-lookup"><span data-stu-id="16e1c-117">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="16e1c-118">Ajoutez un deuxième <xref:System.Windows.Controls.UserControl> WPF au projet.</span><span class="sxs-lookup"><span data-stu-id="16e1c-118">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="16e1c-119">Utilisez le nom par défaut pour le type de contrôle, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="16e1c-119">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="16e1c-120">Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="16e1c-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

7. <span data-ttu-id="16e1c-121">Ajoutez un contrôle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> au <xref:System.Windows.Controls.UserControl> et définissez la valeur de la propriété <xref:System.Windows.Controls.TextBox.Text%2A> sur le **contenu hébergé 2**.</span><span class="sxs-lookup"><span data-stu-id="16e1c-121">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="16e1c-122">En général, vous devez héberger du contenu WPF plus sophistiqué.</span><span class="sxs-lookup"><span data-stu-id="16e1c-122">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="16e1c-123">Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> est utilisé ici uniquement à titre d'illustration.</span><span class="sxs-lookup"><span data-stu-id="16e1c-123">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

8. <span data-ttu-id="16e1c-124">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="16e1c-124">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="16e1c-125">Sélectionner des contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="16e1c-125">Select WPF controls</span></span>

<span data-ttu-id="16e1c-126">Vous pouvez assigner du contenu WPF différent à un contrôle <xref:System.Windows.Forms.Integration.ElementHost> qui héberge déjà du contenu.</span><span class="sxs-lookup"><span data-stu-id="16e1c-126">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="16e1c-127">Ouvrez `Form1` dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="16e1c-127">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="16e1c-128">Dans la **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="16e1c-128">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="16e1c-129">Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="16e1c-129">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="16e1c-130">Dans le panneau des balises actives pour `elementHost1`, ouvrez la liste déroulante **Sélectionner le contenu hébergé** .</span><span class="sxs-lookup"><span data-stu-id="16e1c-130">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="16e1c-131">Sélectionnez **UserControl2** dans la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="16e1c-131">Select **UserControl2** from the drop-down list box.</span></span>

   <span data-ttu-id="16e1c-132">Le contrôle `elementHost1` héberge maintenant une instance du type `UserControl2`.</span><span class="sxs-lookup"><span data-stu-id="16e1c-132">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="16e1c-133">Dans la fenêtre **Propriétés** , vérifiez que la propriété <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> a la valeur **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="16e1c-133">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="16e1c-134">À partir de la **boîte à outils**, dans le groupe **interopérabilité WPF** , faites glisser un contrôle <xref:System.Windows.Forms.Integration.ElementHost> sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="16e1c-134">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

   <span data-ttu-id="16e1c-135">Le nom par défaut du nouveau contrôle est `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="16e1c-135">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="16e1c-136">Dans le panneau des balises actives pour `elementHost2`, ouvrez la liste déroulante **Sélectionner le contenu hébergé** .</span><span class="sxs-lookup"><span data-stu-id="16e1c-136">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="16e1c-137">Sélectionnez **UserControl1** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="16e1c-137">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="16e1c-138">Le contrôle `elementHost2` héberge maintenant une instance du type `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="16e1c-138">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="16e1c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16e1c-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="16e1c-140">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="16e1c-140">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="16e1c-141">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="16e1c-141">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="16e1c-142">Concevoir en XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="16e1c-142">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
