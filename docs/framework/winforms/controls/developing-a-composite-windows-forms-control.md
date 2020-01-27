---
title: Développement d’un contrôle composite
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
ms.openlocfilehash: d80564c71dad57ce9145fbedd45a1396df1ddfec
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746033"
---
# <a name="develop-a-composite-windows-forms-control"></a><span data-ttu-id="761d9-102">Développer un contrôle de Windows Forms composite</span><span class="sxs-lookup"><span data-stu-id="761d9-102">Develop a composite Windows Forms control</span></span>

<span data-ttu-id="761d9-103">Vous pouvez développer un contrôle Windows Forms composite en combinant d'autres contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="761d9-103">You can develop a composite Windows Forms control by combining other Windows Forms controls.</span></span> <span data-ttu-id="761d9-104">Les contrôles composites qui dérivent de <xref:System.Web.UI.UserControl> sont appelés contrôles utilisateur.</span><span class="sxs-lookup"><span data-stu-id="761d9-104">Composite controls that derive from <xref:System.Web.UI.UserControl> are called user controls.</span></span> <span data-ttu-id="761d9-105">La classe de base, <xref:System.Windows.Forms.UserControl>, fournit le routage clavier pour les contrôles enfants, ce qui permet de garantir que les contrôles enfants peuvent recevoir le focus.</span><span class="sxs-lookup"><span data-stu-id="761d9-105">The base class, <xref:System.Windows.Forms.UserControl>, provides keyboard routing for the child controls, thus ensuring that child controls can receive focus.</span></span> <span data-ttu-id="761d9-106">Pour obtenir un exemple de contrôle utilisateur, consultez l’exemple <xref:System.Windows.Forms.UserControl> dans [Comment : appliquer des attributs dans des contrôles Windows Forms](how-to-apply-attributes-in-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="761d9-106">For an example of a user control, see the <xref:System.Windows.Forms.UserControl> sample in [How to: Apply Attributes in Windows Forms Controls](how-to-apply-attributes-in-windows-forms-controls.md).</span></span>

<span data-ttu-id="761d9-107">Le concepteur de Windows Forms dans Visual Studio fournit une prise en charge enrichie au moment du design pour la création de contrôles utilisateur.</span><span class="sxs-lookup"><span data-stu-id="761d9-107">The Windows Forms designer in Visual Studio provides rich design-time support for authoring user controls.</span></span>

- [<span data-ttu-id="761d9-108">Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils</span><span class="sxs-lookup"><span data-stu-id="761d9-108">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)

- [<span data-ttu-id="761d9-109">Procédure pas à pas : sérialisation des collections de types standard avec DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="761d9-109">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)

- [<span data-ttu-id="761d9-110">Procédure pas à pas : héritage d’un contrôle Windows Forms à l’aide de Visual C#</span><span class="sxs-lookup"><span data-stu-id="761d9-110">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)

- [<span data-ttu-id="761d9-111">Comment : fournir une bitmap pour un contrôle en vue de l'afficher dans la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="761d9-111">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)

- [<span data-ttu-id="761d9-112">Guide pratique pour hériter de contrôles Windows Forms existants</span><span class="sxs-lookup"><span data-stu-id="761d9-112">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)

- [<span data-ttu-id="761d9-113">Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design</span><span class="sxs-lookup"><span data-stu-id="761d9-113">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)

- [<span data-ttu-id="761d9-114">Guide pratique pour hériter de la classe du contrôle</span><span class="sxs-lookup"><span data-stu-id="761d9-114">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)

- [<span data-ttu-id="761d9-115">Guide pratique pour tester le comportement d’un UserControl au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="761d9-115">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)

- [<span data-ttu-id="761d9-116">Guide pratique pour aligner un contrôle sur les bords des formulaires au moment du design</span><span class="sxs-lookup"><span data-stu-id="761d9-116">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)

- [<span data-ttu-id="761d9-117">Guide pratique pour hériter de la classe UserControl</span><span class="sxs-lookup"><span data-stu-id="761d9-117">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)

- [<span data-ttu-id="761d9-118">Guide pratique pour créer des contrôles pour des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="761d9-118">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)

- [<span data-ttu-id="761d9-119">Guide pratique pour créer des contrôles composites</span><span class="sxs-lookup"><span data-stu-id="761d9-119">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)

- [<span data-ttu-id="761d9-120">Procédure pas à pas : création d’un contrôle composite à l’aide de Visual C#</span><span class="sxs-lookup"><span data-stu-id="761d9-120">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)

- [<span data-ttu-id="761d9-121">Procédure pas à pas : création d’un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="761d9-121">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

- <span data-ttu-id="761d9-122">[Comment : créer un contrôle Windows Forms qui bénéficie des fonctionnalités au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="761d9-122">[How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))</span></span>

## <a name="see-also"></a><span data-ttu-id="761d9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="761d9-123">See also</span></span>

- [<span data-ttu-id="761d9-124">Guide pratique pour appliquer des attributs dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="761d9-124">How to: Apply Attributes in Windows Forms Controls</span></span>](how-to-apply-attributes-in-windows-forms-controls.md)
- [<span data-ttu-id="761d9-125">Développement de contrôles Windows Forms personnalisés avec le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="761d9-125">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="761d9-126">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="761d9-126">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
