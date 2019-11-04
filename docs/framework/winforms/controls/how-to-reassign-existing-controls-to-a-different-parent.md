---
title: 'Comment : réassignation de contrôles existants à un parent différent'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459198"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="fe909-102">Comment : réassigner des contrôles existants à un autre parent</span><span class="sxs-lookup"><span data-stu-id="fe909-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="fe909-103">Vous pouvez affecter des contrôles qui existent sur votre formulaire à un nouveau contrôle de conteneur.</span><span class="sxs-lookup"><span data-stu-id="fe909-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="fe909-104">Dans Visual Studio, faites glisser trois contrôles <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="fe909-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="fe909-105">Disposez-les près les uns des autres en les laissant non alignés.</span><span class="sxs-lookup"><span data-stu-id="fe909-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="fe909-106">Dans la **Boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="fe909-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="fe909-107">(Ne faites pas glisser l’icône sur le formulaire.)</span><span class="sxs-lookup"><span data-stu-id="fe909-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="fe909-108">Déplacez le pointeur de la souris près des trois contrôles <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="fe909-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="fe909-109">Le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="fe909-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="fe909-110">Cliquez et maintenez le bouton de la souris enfoncé.</span><span class="sxs-lookup"><span data-stu-id="fe909-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="fe909-111">Faites glisser le pointeur de la souris pour tracer le contour du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="fe909-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="fe909-112">Tracez le contour des trois contrôles <xref:System.Windows.Forms.Button> .</span><span class="sxs-lookup"><span data-stu-id="fe909-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="fe909-113">Relâchez le bouton de la souris.</span><span class="sxs-lookup"><span data-stu-id="fe909-113">Release the mouse button.</span></span>

   <span data-ttu-id="fe909-114">Les trois contrôles <xref:System.Windows.Forms.Button> sont maintenant insérés dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="fe909-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe909-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe909-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="fe909-116">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="fe909-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="fe909-117">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="fe909-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
