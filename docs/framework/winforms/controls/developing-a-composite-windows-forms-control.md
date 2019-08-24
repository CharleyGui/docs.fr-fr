---
title: Développement d'un contrôle Windows Forms composite
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: 9ccbf3de3f5c65b99a06c29ffce4c96896d11fae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015957"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="7e7f2-102">Développer un contrôle de Windows Forms composite</span><span class="sxs-lookup"><span data-stu-id="7e7f2-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="7e7f2-103">Vous pouvez développer un contrôle Windows Forms composite en combinant d'autres contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="7e7f2-104">Les contrôles composites qui <xref:System.Web.UI.UserControl> dérivent de sont appelés contrôles utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="7e7f2-105">La classe de base, <xref:System.Windows.Forms.UserControl>, fournit le routage clavier pour les contrôles enfants, ce qui permet de garantir que les contrôles enfants peuvent recevoir le focus.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="7e7f2-106">Pour obtenir un exemple de contrôle utilisateur, consultez l' <xref:System.Windows.Forms.UserControl> exemple dans [How to: Appliquez des attributs dans les](how-to-apply-attributes-in-windows-forms-controls.md)contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="7e7f2-107">Le concepteur de Windows Forms dans Visual Studio fournit une prise en charge enrichie au moment du design pour la création de contrôles utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7e7f2-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="7e7f2-108">Guide pratique pour Afficher un contrôle dans la boîte de dialogue choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="7e7f2-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="7e7f2-109">Procédure pas à pas : Sérialisation des collections de types standard avec DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="7e7f2-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="7e7f2-110">Procédure pas à pas : Héritage à partir d’un contrôle Windows Forms avec VisualC#</span><span class="sxs-lookup"><span data-stu-id="7e7f2-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="7e7f2-111">Guide pratique : Fournir une bitmap de boîte à outils pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="7e7f2-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="7e7f2-112">Guide pratique pour Hériter de contrôles Windows Forms existants</span><span class="sxs-lookup"><span data-stu-id="7e7f2-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="7e7f2-113">Procédure pas à pas : Débogage des contrôles Windows Forms personnalisés au moment du design</span><span class="sxs-lookup"><span data-stu-id="7e7f2-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="7e7f2-114">Guide pratique : Hériter de la classe de contrôle</span><span class="sxs-lookup"><span data-stu-id="7e7f2-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="7e7f2-115">Guide pratique pour Tester le comportement d’un UserControl au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="7e7f2-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="7e7f2-116">Guide pratique pour Aligner un contrôle sur les bords des formulaires au moment du design</span><span class="sxs-lookup"><span data-stu-id="7e7f2-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="7e7f2-117">Guide pratique pour Hériter de la classe UserControl</span><span class="sxs-lookup"><span data-stu-id="7e7f2-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="7e7f2-118">Guide pratique pour Créer des contrôles pour Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e7f2-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="7e7f2-119">Guide pratique : Créer des contrôles composites</span><span class="sxs-lookup"><span data-stu-id="7e7f2-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="7e7f2-120">Procédure pas à pas : Création d’un contrôle composite à l’aide de VisualC#</span><span class="sxs-lookup"><span data-stu-id="7e7f2-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="7e7f2-121">Procédure pas à pas : Création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e7f2-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="7e7f2-122">[Guide pratique pour Créer un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="7e7f2-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="7e7f2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e7f2-123">See also</span></span>

- [<span data-ttu-id="7e7f2-124">Guide pratique : Appliquer des attributs dans des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e7f2-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="7e7f2-125">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7e7f2-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="7e7f2-126">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="7e7f2-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
