---
title: 'Procédure : créer une interface de style Explorateur Windows dans un formulaire Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
ms.openlocfilehash: db2c5431dfb0156c1508a18ef13d2af80eb4981b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039535"
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a><span data-ttu-id="09044-102">Procédure : créer une interface de style Explorateur Windows dans un formulaire Windows</span><span class="sxs-lookup"><span data-stu-id="09044-102">How to: Create a Windows Explorer–Style Interface on a Windows Form</span></span>
<span data-ttu-id="09044-103">L’Explorateur Windows est un choix d’interface utilisateur courant pour les applications en raison de sa familiarité.</span><span class="sxs-lookup"><span data-stu-id="09044-103">Windows Explorer is a common user-interface choice for applications because of its ready familiarity.</span></span>

 <span data-ttu-id="09044-104">L’Explorateur Windows est, essentiellement, <xref:System.Windows.Forms.TreeView> un contrôle et <xref:System.Windows.Forms.ListView> un contrôle sur des panneaux distincts.</span><span class="sxs-lookup"><span data-stu-id="09044-104">Windows Explorer is, essentially, a <xref:System.Windows.Forms.TreeView> control and a <xref:System.Windows.Forms.ListView> control on separate panels.</span></span> <span data-ttu-id="09044-105">Les panneaux sont rendus redimensionnables par un séparateur.</span><span class="sxs-lookup"><span data-stu-id="09044-105">The panels are made resizable by a splitter.</span></span> <span data-ttu-id="09044-106">Cette organisation des contrôles est très efficace pour l’affichage et la navigation dans les informations.</span><span class="sxs-lookup"><span data-stu-id="09044-106">This arrangement of controls is very effective for displaying and browsing information.</span></span>

 <span data-ttu-id="09044-107">Les étapes suivantes montrent comment organiser les contrôles dans un formulaire de type Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="09044-107">The following steps show how to arrange controls in a Windows Explorer-like form.</span></span> <span data-ttu-id="09044-108">Ils n’indiquent pas comment ajouter la fonctionnalité de navigation de fichiers de l’application de l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="09044-108">They do not show how to add the file-browsing functionality of the Windows Explorer application.</span></span>

## <a name="to-create-a-windows-explorer-style-windows-form"></a><span data-ttu-id="09044-109">Pour créer un Windows Form de style Explorateur Windows</span><span class="sxs-lookup"><span data-stu-id="09044-109">To create a Windows Explorer-style Windows Form</span></span>

1. <span data-ttu-id="09044-110">Créer un nouveau projet d’application Windows (**fichier** > **nouveau** > **projet** >  **C# visuel** ou **Visual Basic** > **Bureau classique**  >  **Windows Forms application**).</span><span class="sxs-lookup"><span data-stu-id="09044-110">Create a new Windows Application project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>

2. <span data-ttu-id="09044-111">À partir de la **boîte à outils**:</span><span class="sxs-lookup"><span data-stu-id="09044-111">From the **Toolbox**:</span></span>

    1. <span data-ttu-id="09044-112">Faites glisser <xref:System.Windows.Forms.SplitContainer> un contrôle sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="09044-112">Drag a <xref:System.Windows.Forms.SplitContainer> control onto your form.</span></span>

    2. <span data-ttu-id="09044-113">Faites glisser <xref:System.Windows.Forms.TreeView> un contrôle dans **splitterPanel1** ( <xref:System.Windows.Forms.SplitContainer> le panneau du contrôle marqué **Panel1**).</span><span class="sxs-lookup"><span data-stu-id="09044-113">Drag a <xref:System.Windows.Forms.TreeView> control into **SplitterPanel1** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel1**).</span></span>

    3. <span data-ttu-id="09044-114">Faites glisser <xref:System.Windows.Forms.ListView> un contrôle dans **SplitterPanel2** ( <xref:System.Windows.Forms.SplitContainer> le panneau du contrôle marqué **Panel2**).</span><span class="sxs-lookup"><span data-stu-id="09044-114">Drag a <xref:System.Windows.Forms.ListView> control into **SplitterPanel2** (the panel of the <xref:System.Windows.Forms.SplitContainer> control marked **Panel2**).</span></span>

3. <span data-ttu-id="09044-115">Sélectionnez les trois contrôles en appuyant sur la touche CTRL et en cliquant successivement sur eux.</span><span class="sxs-lookup"><span data-stu-id="09044-115">Select all three controls by pressing the CTRL key and clicking them in turn.</span></span> <span data-ttu-id="09044-116">Lorsque vous sélectionnez le <xref:System.Windows.Forms.SplitContainer> contrôle, cliquez sur la barre de fractionnement, plutôt que sur les panneaux.</span><span class="sxs-lookup"><span data-stu-id="09044-116">When you select the <xref:System.Windows.Forms.SplitContainer> control, click the splitter bar, rather than the panels.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="09044-117">N’utilisez pas la commande **Sélectionner tout** du menu **Edition** .</span><span class="sxs-lookup"><span data-stu-id="09044-117">Do not use the **Select All** command on the **Edit** menu.</span></span> <span data-ttu-id="09044-118">Dans ce cas, la propriété nécessaire à l’étape suivante n’apparaîtra pas dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="09044-118">If you do so, the property needed in the next step will not appear in the **Properties** window.</span></span>

4. <span data-ttu-id="09044-119">Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> sur <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="09044-119">In the **Properties** window, set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

5. <span data-ttu-id="09044-120">Appuyez sur F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="09044-120">Press F5 to run the application.</span></span>

     <span data-ttu-id="09044-121">Le formulaire affiche une interface utilisateur en deux parties, similaire à celle de l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="09044-121">The form displays a two-part user interface, similar to that of the Windows Explorer.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="09044-122">Lorsque vous faites glisser le séparateur, les panneaux sont redimensionnés eux-mêmes.</span><span class="sxs-lookup"><span data-stu-id="09044-122">When you drag the splitter, the panels resize themselves.</span></span>

## <a name="see-also"></a><span data-ttu-id="09044-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09044-123">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="09044-124">Guide pratique : Créer une interface utilisateur à volets avec Windows Forms</span><span class="sxs-lookup"><span data-stu-id="09044-124">How to: Create a Multipane User Interface with Windows Forms</span></span>](how-to-create-a-multipane-user-interface-with-windows-forms.md)
- [<span data-ttu-id="09044-125">Guide pratique pour Définir le comportement de redimensionnement et de positionnement dans une fenêtre fractionnée</span><span class="sxs-lookup"><span data-stu-id="09044-125">How to: Define Resize and Positioning Behavior in a Split Window</span></span>](how-to-define-resize-and-positioning-behavior-in-a-split-window.md)
- [<span data-ttu-id="09044-126">Guide pratique : Fractionner une fenêtre horizontalement</span><span class="sxs-lookup"><span data-stu-id="09044-126">How to: Split a Window Horizontally</span></span>](how-to-split-a-window-horizontally.md)
- [<span data-ttu-id="09044-127">SplitContainer, contrôle</span><span class="sxs-lookup"><span data-stu-id="09044-127">SplitContainer Control</span></span>](splitcontainer-control-windows-forms.md)
