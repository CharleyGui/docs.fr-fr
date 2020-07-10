---
title: Guide pratique pour créer des formulaires MDI parents
description: Découvrez comment créer un formulaire MDI parent par programme et à l’aide de l’Concepteur Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174703"
---
# <a name="how-to-create-mdi-parent-forms"></a><span data-ttu-id="70720-103">Guide pratique pour créer des formulaires MDI parents</span><span class="sxs-lookup"><span data-stu-id="70720-103">How to: Create MDI Parent Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="70720-104">Cette rubrique utilise le contrôle <xref:System.Windows.Forms.MainMenu>, qui a été remplacé par le contrôle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="70720-104">This topic uses the <xref:System.Windows.Forms.MainMenu> control, which has been replaced by the <xref:System.Windows.Forms.MenuStrip> control.</span></span> <span data-ttu-id="70720-105">Le contrôle <xref:System.Windows.Forms.MainMenu> est conservé pour la compatibilité descendante et une utilisation future, au besoin.</span><span class="sxs-lookup"><span data-stu-id="70720-105">The <xref:System.Windows.Forms.MainMenu> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="70720-106">Pour plus d’informations sur la création d’un formulaire MDI parent à l’aide d’un <xref:System.Windows.Forms.MenuStrip> , consultez Guide pratique [pour créer une liste de fenêtres MDI avec MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="70720-106">For information about creating a MDI parent Form by using a <xref:System.Windows.Forms.MenuStrip>, see [How to: Create an MDI Window List with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).</span></span>

<span data-ttu-id="70720-107">Le formulaire MDI parent constitue la base d'une application d'interface multidocument (MDI, Multiple-Document Interface).</span><span class="sxs-lookup"><span data-stu-id="70720-107">The foundation of a Multiple-Document Interface (MDI) application is the MDI parent form.</span></span> <span data-ttu-id="70720-108">Ce formulaire contient les fenêtres MDI enfants, c'est-à-dire les sous-fenêtres dans lesquelles l'utilisateur interagit avec l'application MDI.</span><span class="sxs-lookup"><span data-stu-id="70720-108">This is the form that contains the MDI child windows, which are the sub-windows wherein the user interacts with the MDI application.</span></span> <span data-ttu-id="70720-109">Il est facile de créer un formulaire MDI parent, que ce soit par programmation ou dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="70720-109">Creating an MDI parent form is easy, both in the Windows Forms Designer and programmatically.</span></span>

## <a name="create-an-mdi-parent-form-at-design-time"></a><span data-ttu-id="70720-110">Créer un formulaire MDI parent au moment du design</span><span class="sxs-lookup"><span data-stu-id="70720-110">Create an MDI parent form at design time</span></span>

1. <span data-ttu-id="70720-111">Créez un projet d’application Windows dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="70720-111">Create a Windows Application project in Visual Studio.</span></span>

2. <span data-ttu-id="70720-112">Dans la fenêtre **Propriétés** , affectez <xref:System.Windows.Forms.Form.IsMdiContainer%2A> à la propriété la **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="70720-112">In the **Properties** window, set the <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to **true**.</span></span>

     <span data-ttu-id="70720-113">Ainsi, vous désignez le formulaire comme le conteneur MDI des fenêtres enfants.</span><span class="sxs-lookup"><span data-stu-id="70720-113">This designates the form as an MDI container for child windows.</span></span>

    > [!NOTE]
    > <span data-ttu-id="70720-114">Quand vous définissez des propriétés dans la fenêtre **Propriétés**, vous pouvez aussi si vous le souhaitez définir la propriété `WindowState` sur **Maximized**, car il est plus facile de manipuler des fenêtres enfants MDI quand le formulaire parent est agrandi au maximum.</span><span class="sxs-lookup"><span data-stu-id="70720-114">While setting properties in the **Properties** window, you can also set the `WindowState` property to **Maximized**, if you like, as it is easiest to manipulate MDI child windows when the parent form is maximized.</span></span> <span data-ttu-id="70720-115">Sachez par ailleurs que le contour du formulaire MDI parent prend la couleur système (définie dans le Panneau de configuration Système Windows), et non la couleur d'arrière-plan que vous avez définie avec la propriété <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70720-115">Additionally, be aware that the edge of the MDI parent form will pick up the system color (set in the Windows System Control Panel), rather than the back color you set using the <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> property.</span></span>

3. <span data-ttu-id="70720-116">Dans la **Boîte à outils**, faites glisser un contrôle **MenuStrip** sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="70720-116">From the **Toolbox**, drag a **MenuStrip** control to the form.</span></span> <span data-ttu-id="70720-117">Créez un élément de menu de plus haut niveau en définissant la propriété **Text** sur **&File** avec des éléments de sous-menu appelés **&New** et **&Close**.</span><span class="sxs-lookup"><span data-stu-id="70720-117">Create a top-level menu item with the **Text** property set to **&File** with submenu items called **&New** and **&Close**.</span></span> <span data-ttu-id="70720-118">Créez également un menu de plus haut niveau appelé **&Window**.</span><span class="sxs-lookup"><span data-stu-id="70720-118">Also create a top-level menu item called **&Window**.</span></span>

     <span data-ttu-id="70720-119">Le premier menu crée et masque les éléments de menu au moment de l'exécution, alors que le deuxième menu garde la trace des fenêtres MDI enfants ouvertes.</span><span class="sxs-lookup"><span data-stu-id="70720-119">The first menu will create and hide menu items at run time, and the second menu will keep track of the open MDI child windows.</span></span> <span data-ttu-id="70720-120">À ce stade, vous avez créé une fenêtre MDI parente.</span><span class="sxs-lookup"><span data-stu-id="70720-120">At this point, you have created an MDI parent window.</span></span>

4. <span data-ttu-id="70720-121">Appuyez sur **F5** pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="70720-121">Press **F5** to run the application.</span></span> <span data-ttu-id="70720-122">Pour plus d’informations sur la création de fenêtres MDI enfants qui fonctionnent dans un formulaire MDI parent, consultez [Guide pratique pour créer des formulaires MDI enfants](how-to-create-mdi-child-forms.md).</span><span class="sxs-lookup"><span data-stu-id="70720-122">For information about creating MDI child windows that operate within the MDI parent form, see [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70720-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70720-123">See also</span></span>

- [<span data-ttu-id="70720-124">Applications d’interface multidocument (MDI, Multiple Document Interface)</span><span class="sxs-lookup"><span data-stu-id="70720-124">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="70720-125">Comment : créer des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="70720-125">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="70720-126">Comment : déterminer l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="70720-126">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="70720-127">Comment : envoyer des données à l'enfant MDI actif</span><span class="sxs-lookup"><span data-stu-id="70720-127">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="70720-128">Guide pratique pour réorganiser des formulaires MDI enfants</span><span class="sxs-lookup"><span data-stu-id="70720-128">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
