---
title: "Comment : activer l'affichage en mosaïque dans un contrôle ListView Windows Forms à l'aide du concepteur"
ms.date: 03/30/2017
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
ms.openlocfilehash: 4f51d3a596bc3358942cdfd654b3e4515d96cd07
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960100"
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="8d12b-102">Comment : activer l'affichage en mosaïque dans un contrôle ListView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="8d12b-102">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="8d12b-103">La fonctionnalité d’affichage en mosaïque du contrôle <xref:System.Windows.Forms.ListView> vous permet de fournir un équilibre visuel entre les informations graphiques et textuelles.</span><span class="sxs-lookup"><span data-stu-id="8d12b-103">The tile view feature of the <xref:System.Windows.Forms.ListView> control enables you to provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="8d12b-104">Les informations textuelles affichées pour un élément dans l'affichage en mosaïque sont identiques aux informations de colonne définies pour le mode Détails.</span><span class="sxs-lookup"><span data-stu-id="8d12b-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="8d12b-105">L’affichage en mosaïque fonctionne en association avec les fonctionnalités de regroupement ou de marque d’insertion dans le contrôle <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="8d12b-105">Tile view functions in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>

 <span data-ttu-id="8d12b-106">L’affichage en mosaïque utilise une icône 32 x 32 et plusieurs lignes de texte, comme illustré dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="8d12b-106">The tile view uses a 32 x 32 icon and several lines of text, as shown in the following image.</span></span>

 <span data-ttu-id="8d12b-107">![Affichage en mosaïque dans un contrôle ListView](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Texte et icônes de l'affichage en mosaïque")</span><span class="sxs-lookup"><span data-stu-id="8d12b-107">![Tile View in a ListView Control](./media/enable-tile-view-in-a-wf-listview-control-using-the-designer/tile-view-in-listview-control.gif "Tile view icons and text")</span></span>

 <span data-ttu-id="8d12b-108">Les propriétés et les méthodes de l’affichage en mosaïque vous permettent de spécifier les champs de colonne à afficher pour chaque élément, et de contrôler collectivement la taille et l’apparence de tous les éléments d’une fenêtre d’affichage en mosaïque.</span><span class="sxs-lookup"><span data-stu-id="8d12b-108">Tile view properties and methods enable you to specify which column fields to display for each item, and to collectively control the size and appearance of all items within a tile view window.</span></span> <span data-ttu-id="8d12b-109">Pour plus de clarté, la première ligne de texte dans une vignette est toujours le nom de l’élément ; elle ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="8d12b-109">For clarity, the first line of text in a tile is always the item's name; it cannot be changed.</span></span>

 <span data-ttu-id="8d12b-110">La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="8d12b-110">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="8d12b-111">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8d12b-111">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>

## <a name="to-set-tile-view-in-the-designer"></a><span data-ttu-id="8d12b-112">Pour définir l’affichage en mosaïque dans le concepteur</span><span class="sxs-lookup"><span data-stu-id="8d12b-112">To set tile view in the designer</span></span>

1. <span data-ttu-id="8d12b-113">Dans Visual Studio, sélectionnez le contrôle <xref:System.Windows.Forms.ListView> de votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="8d12b-113">In Visual Studio, select the <xref:System.Windows.Forms.ListView> control on your form.</span></span>

2. <span data-ttu-id="8d12b-114">Dans la fenêtre **Propriétés** , sélectionnez la propriété <xref:System.Windows.Forms.ListView.View%2A> et choisissez **mosaïque**.</span><span class="sxs-lookup"><span data-stu-id="8d12b-114">In the **Properties** window, select the <xref:System.Windows.Forms.ListView.View%2A> property and choose **Tile**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d12b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d12b-115">See also</span></span>

- <xref:System.Windows.Forms.ListView.TileSize%2A>
- [<span data-ttu-id="8d12b-116">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="8d12b-116">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
