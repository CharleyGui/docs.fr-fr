---
title: 'Procédure : arrimer des contrôles dans des Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58b61af306385a245bedf16e370e6830c370a622
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987486"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="fcae3-102">Procédure : Ancrer les contrôles sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcae3-102">How to: Dock controls on Windows Forms</span></span>

<span data-ttu-id="fcae3-103">Vous pouvez ancrer les contrôles aux bords de votre formulaire ou les faire remplir le conteneur du contrôle (un formulaire ou un contrôle conteneur).</span><span class="sxs-lookup"><span data-stu-id="fcae3-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="fcae3-104">Par exemple, l’Explorateur Windows ancre son <xref:System.Windows.Forms.TreeView> contrôle sur le côté gauche de la fenêtre et son <xref:System.Windows.Forms.ListView> contrôle sur le côté droit de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="fcae3-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="fcae3-105">Utilisez la <xref:System.Windows.Forms.Control.Dock%2A> propriété pour tous les contrôles Windows Forms visibles pour définir le mode d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="fcae3-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>

> [!NOTE]
> <span data-ttu-id="fcae3-106">Les contrôles sont ancrés dans l’ordre de plan inverse.</span><span class="sxs-lookup"><span data-stu-id="fcae3-106">Controls are docked in reverse z-order.</span></span>

<span data-ttu-id="fcae3-107">La <xref:System.Windows.Forms.Control.Dock%2A> propriété interagit avec la <xref:System.Windows.Forms.Control.AutoSize%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="fcae3-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="fcae3-108">Pour plus d’informations, consultez [vue d’ensemble](autosize-property-overview.md)de la propriété AutoSize.</span><span class="sxs-lookup"><span data-stu-id="fcae3-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="to-dock-a-control"></a><span data-ttu-id="fcae3-109">Pour ancrer un contrôle</span><span class="sxs-lookup"><span data-stu-id="fcae3-109">To dock a control</span></span>

1. <span data-ttu-id="fcae3-110">Dans Visual Studio, sélectionnez le contrôle que vous souhaitez ancrer.</span><span class="sxs-lookup"><span data-stu-id="fcae3-110">In Visual Studio, select the control that you want to dock.</span></span>

2. <span data-ttu-id="fcae3-111">Dans la fenêtre **Propriétés** , cliquez sur la flèche à droite de la <xref:System.Windows.Forms.Control.Dock%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="fcae3-111">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

   <span data-ttu-id="fcae3-112">Un éditeur affiche une série de cases représentant les bords et le centre du formulaire.</span><span class="sxs-lookup"><span data-stu-id="fcae3-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>

3. <span data-ttu-id="fcae3-113">Cliquez sur le bouton qui représente le bord du formulaire dans lequel vous souhaitez ancrer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="fcae3-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="fcae3-114">Pour remplir le contenu du contrôle de formulaire ou de conteneur du contrôle, cliquez sur la zone centrale.</span><span class="sxs-lookup"><span data-stu-id="fcae3-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="fcae3-115">Cliquez sur **(aucun)** pour désactiver l’ancrage.</span><span class="sxs-lookup"><span data-stu-id="fcae3-115">Click **(none)** to disable docking.</span></span>

   <span data-ttu-id="fcae3-116">Le contrôle est automatiquement redimensionné pour s’ajuster aux limites du bord ancré.</span><span class="sxs-lookup"><span data-stu-id="fcae3-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>

   > [!NOTE]
   > <span data-ttu-id="fcae3-117">Les contrôles hérités `Protected` doivent être en mesure d’être ancrés.</span><span class="sxs-lookup"><span data-stu-id="fcae3-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="fcae3-118">Pour modifier le niveau d’accès d’un contrôle, définissez sa propriété **modifier** dans la fenêtre **Propriétés** .</span><span class="sxs-lookup"><span data-stu-id="fcae3-118">To change the access level of a control, set its **Modifier** property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcae3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcae3-119">See also</span></span>

- [<span data-ttu-id="fcae3-120">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcae3-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="fcae3-121">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcae3-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="fcae3-122">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcae3-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="fcae3-123">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcae3-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="fcae3-124">Guide pratique : Ancrer et ancrer des contrôles enfants dans un contrôle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="fcae3-124">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="fcae3-125">Guide pratique pour Ancrer et ancrer des contrôles enfants dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="fcae3-125">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="fcae3-126">Vue d’ensemble de la propriété AutoSize</span><span class="sxs-lookup"><span data-stu-id="fcae3-126">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="fcae3-127">Guide pratique pour Contrôles d’ancrage sur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fcae3-127">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
