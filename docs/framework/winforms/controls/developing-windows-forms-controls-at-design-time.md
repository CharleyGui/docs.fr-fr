---
title: Développer des contrôles au moment du design
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7626e1efbb30ef3bfe9b5b1278c0adb18dd5944b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628707"
---
# <a name="develop-windows-forms-controls-at-design-time"></a><span data-ttu-id="ee1d6-102">Développer des contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="ee1d6-102">Develop Windows Forms controls at design time</span></span>

<span data-ttu-id="ee1d6-103">Pour les auteurs de contrôles, le .NET Framework fournit une multitude de technologies de création de contrôles.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="ee1d6-104">Les auteurs ne sont plus contraints de concevoir des contrôles composites qui agissent en tant que collection de contrôles préexistants.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="ee1d6-105">À travers l’héritage, vous pouvez créer vos propres contrôles à partir de contrôles composites ou de contrôles Windows Forms préexistants.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="ee1d6-106">Vous pouvez également concevoir vos propres contrôles qui implémentent un dessin personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="ee1d6-107">Ces options permettent une grande souplesse dans la conception et les fonctionnalités de l’interface visuelle.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="ee1d6-108">Pour tirer parti de ces fonctionnalités, vous devez bien connaître les concepts de la programmation orientée objet.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="ee1d6-109">Il n’est pas nécessaire d’avoir une compréhension approfondie de l’héritage, mais il peut être utile de faire référence aux [notions de base de l’héritage (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ee1d6-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

<span data-ttu-id="ee1d6-110">Si vous voulez créer des contrôle personnalisés à utiliser sur des Web Forms, consultez [Développement de contrôles serveur ASP.NET personnalisés](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ee1d6-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ee1d6-111">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="ee1d6-111">In this section</span></span>

<span data-ttu-id="ee1d6-112">[Procédure pas à pas : création d’un contrôle composite](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-112">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="ee1d6-113">Montre comment créer un contrôle composite simple dans C#.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-113">Shows how to create a simple composite control in C#.</span></span>

<span data-ttu-id="ee1d6-114">[Procédure pas à pas : héritage d’un contrôle de Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-114">[Walkthrough: Inheriting from a Windows Forms Control](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="ee1d6-115">Montre comment créer un contrôle Windows Forms simple à l’aide de l’héritage dans C#.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-115">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>

<span data-ttu-id="ee1d6-116">[Procédure pas à pas : effectuer des tâches courantes à l’aide d’actions de concepteur](perform-common-tasks-design-actions.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-116">[Walkthrough: Perform common tasks using designer actions](perform-common-tasks-design-actions.md)</span></span>\
<span data-ttu-id="ee1d6-117">Montre comment utiliser la fonctionnalité de balise active sur les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-117">Shows how to use the smart tag feature on Windows Forms controls.</span></span>

<span data-ttu-id="ee1d6-118">[Procédure pas à pas : sérialisation de collections de types standard avec DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-118">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span></span>\
<span data-ttu-id="ee1d6-119">Montre comment utiliser l’attribut <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> pour sérialiser une collection.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-119">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>

<span data-ttu-id="ee1d6-120">[Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-120">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="ee1d6-121">Montre comment déboguer le comportement au moment du design de votre contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-121">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>

<span data-ttu-id="ee1d6-122">[Procédure pas à pas : création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-122">[Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md)</span></span>\
<span data-ttu-id="ee1d6-123">Montre comment intégrer étroitement un contrôle composite dans l’environnement de conception.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-123">Shows how to tightly integrate a composite control into the design environment.</span></span>

<span data-ttu-id="ee1d6-124">[Comment : créer des contrôles pour des Windows Forms](how-to-author-controls-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-124">[How to: Author Controls for Windows Forms](how-to-author-controls-for-windows-forms.md)</span></span>\
<span data-ttu-id="ee1d6-125">Fournit une vue d’ensemble des considérations pour l’implémentation d’un contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-125">Provides an overview of considerations for implementing a Windows Forms control.</span></span>

<span data-ttu-id="ee1d6-126">[Comment : créer des contrôles composites](how-to-author-composite-controls.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-126">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>\
<span data-ttu-id="ee1d6-127">Montre comment créer un contrôle en héritant d’un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-127">Shows how to create a control by inheriting from a composite control.</span></span>

<span data-ttu-id="ee1d6-128">[Comment : hériter de la classe UserControl](how-to-inherit-from-the-usercontrol-class.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-128">[How to: Inherit from the UserControl Class](how-to-inherit-from-the-usercontrol-class.md)</span></span>\
<span data-ttu-id="ee1d6-129">Fournit une vue d’ensemble de la procédure de création d’un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-129">Provides an overview of the procedure for creating a composite control.</span></span>

<span data-ttu-id="ee1d6-130">[Comment : hériter de contrôles Windows Forms existants](how-to-inherit-from-existing-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-130">[How to: Inherit from Existing Windows Forms Controls](how-to-inherit-from-existing-windows-forms-controls.md)</span></span>\
<span data-ttu-id="ee1d6-131">Montre comment créer un contrôle étendu en héritant de la classe de contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-131">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>

<span data-ttu-id="ee1d6-132">[Comment : hériter de la classe du contrôle](how-to-inherit-from-the-control-class.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-132">[How to: Inherit from the Control Class](how-to-inherit-from-the-control-class.md)</span></span>\
<span data-ttu-id="ee1d6-133">Fournit une vue d’ensemble de la création d’un contrôle étendu.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-133">Provides an overview of creating an extended control.</span></span>

<span data-ttu-id="ee1d6-134">[Comment : aligner un contrôle sur les bords des formulaires au moment du Design](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-134">[How to: Align a Control to the Edges of Forms at Design Time](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span></span>\
<span data-ttu-id="ee1d6-135">Montre comment utiliser la propriété <xref:System.Windows.Forms.Control.Dock%2A> pour aligner votre contrôle sur le bord du formulaire qu’il occupe.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-135">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="ee1d6-136">[Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>\
<span data-ttu-id="ee1d6-137">Montre la procédure d’installation de votre contrôle afin qu’il apparaisse dans la boîte de dialogue **Personnaliser la boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-137">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>

<span data-ttu-id="ee1d6-138">[Comment : fournir une bitmap de boîte à outils pour un contrôle](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-138">[How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span></span>\
<span data-ttu-id="ee1d6-139">Montre comment utiliser la <xref:System.Drawing.ToolboxBitmapAttribute> pour afficher une icône en regard de votre contrôle personnalisé dans la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-139">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="ee1d6-140">[Comment : tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-140">[How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span></span>\
<span data-ttu-id="ee1d6-141">Montre comment utiliser le **conteneur de test UserControl** pour tester le comportement d’un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-141">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>

<span data-ttu-id="ee1d6-142">[Erreurs au moment du design dans le Concepteur Windows Forms](design-time-errors-in-the-windows-forms-designer.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-142">[Design-Time Errors in the Windows Forms Designer](design-time-errors-in-the-windows-forms-designer.md)</span></span>\
<span data-ttu-id="ee1d6-143">Explique la signification et l’utilisation de la liste d’erreurs au moment du design qui apparaît dans Microsoft Visual Studio en cas d’échec du chargement du Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-143">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>

<span data-ttu-id="ee1d6-144">[Dépannage de la création de contrôles et de composants](troubleshooting-control-and-component-authoring.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-144">[Troubleshooting Control and Component Authoring](troubleshooting-control-and-component-authoring.md)</span></span>\
<span data-ttu-id="ee1d6-145">Montre comment diagnostiquer et résoudre les problèmes courants qui peuvent se produire quand vous créez un composant ou un contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-145">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>

## <a name="reference"></a><span data-ttu-id="ee1d6-146">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="ee1d6-146">Reference</span></span>

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a><span data-ttu-id="ee1d6-147">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="ee1d6-147">Related sections</span></span>

<span data-ttu-id="ee1d6-148">[Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-148">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="ee1d6-149">Explique comment créer vos propres contrôles personnalisés avec le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-149">Discusses how to create your own custom controls with the .NET Framework.</span></span>

<span data-ttu-id="ee1d6-150">[Indépendance du langage et composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-150">[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)</span></span>\
<span data-ttu-id="ee1d6-151">Présente le common language runtime, qui est conçu pour simplifier la création et l’utilisation des composants.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-151">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="ee1d6-152">Un aspect important de cette simplification est l’interopérabilité améliorée entre les composants écrits à l’aide de différents langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-152">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="ee1d6-153">La Common Language Specification (CLS) permet de créer des outils et composants fonctionnant avec plusieurs langages de programmation.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-153">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>

<span data-ttu-id="ee1d6-154">[Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span><span class="sxs-lookup"><span data-stu-id="ee1d6-154">[Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span></span>\
<span data-ttu-id="ee1d6-155">Décrit comment activer l’affichage de votre composant ou de votre contrôle dans la boîte de dialogue **Personnaliser la boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="ee1d6-155">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>
