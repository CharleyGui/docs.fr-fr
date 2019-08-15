---
title: 'Procédure : réattribuer des contrôles existants à un autre parent'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: a65b3c2b596a2d88ce4236aeadd86993bb268aa6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039788"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="88993-102">Procédure : réattribuer des contrôles existants à un autre parent</span><span class="sxs-lookup"><span data-stu-id="88993-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="88993-103">Vous pouvez affecter des contrôles qui existent sur votre formulaire à un nouveau contrôle de conteneur.</span><span class="sxs-lookup"><span data-stu-id="88993-103">You can assign controls that exist on your form to a new container control.</span></span>

## <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="88993-104">Pour réaffecter des contrôles existants à un autre parent</span><span class="sxs-lookup"><span data-stu-id="88993-104">To reassign existing controls to a different parent</span></span>

1. <span data-ttu-id="88993-105">Faites glisser trois contrôles <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="88993-105">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>

     <span data-ttu-id="88993-106">Disposez-les près les uns des autres en les laissant non alignés.</span><span class="sxs-lookup"><span data-stu-id="88993-106">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="88993-107">Dans la **Boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="88993-107">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>

     <span data-ttu-id="88993-108">Ne faites pas glisser l’icône vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="88993-108">Do not drag the icon onto the form.</span></span>

3. <span data-ttu-id="88993-109">Déplacez le pointeur de la souris près des trois contrôles <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="88993-109">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

     <span data-ttu-id="88993-110">Le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="88993-110">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="88993-111">Cliquez et maintenez le bouton de la souris enfoncé.</span><span class="sxs-lookup"><span data-stu-id="88993-111">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="88993-112">Faites glisser le pointeur de la souris pour tracer le contour du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="88993-112">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="88993-113">Tracez le contour des trois contrôles <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="88993-113">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="88993-114">Relâchez le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="88993-114">Release the mouse button.</span></span>

     <span data-ttu-id="88993-115">Les trois contrôles <xref:System.Windows.Forms.Button> sont maintenant insérés dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="88993-115">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="88993-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88993-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="88993-117">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88993-117">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="88993-118">Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="88993-118">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="88993-119">Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide de lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="88993-119">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
