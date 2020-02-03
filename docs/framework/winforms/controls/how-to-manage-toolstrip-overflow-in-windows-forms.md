---
title: 'Comment : gérer le dépassement de capacité de contrôles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736145"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="3dddf-102">Comment : Gérer le dépassement de capacité de contrôles ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3dddf-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>

<span data-ttu-id="3dddf-103">Lorsque tous les éléments d’un contrôle <xref:System.Windows.Forms.ToolStrip> ne tiennent pas dans l’espace alloué, vous pouvez activer la fonctionnalité de dépassement de capacité sur le <xref:System.Windows.Forms.ToolStrip> et déterminer le comportement de dépassement de <xref:System.Windows.Forms.ToolStripItem>spécifiques.</span><span class="sxs-lookup"><span data-stu-id="3dddf-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>

<span data-ttu-id="3dddf-104">Lorsque vous ajoutez des <xref:System.Windows.Forms.ToolStripItem>qui requièrent plus d’espace que ce qui est alloué à la <xref:System.Windows.Forms.ToolStrip> en fonction de la taille actuelle du formulaire, un <xref:System.Windows.Forms.ToolStripOverflowButton> s’affiche automatiquement sur le <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="3dddf-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="3dddf-105">Le <xref:System.Windows.Forms.ToolStripOverflowButton> s’affiche, et les éléments avec dépassement de capacité sont déplacés dans le menu déroulant de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="3dddf-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="3dddf-106">Cela vous permet de personnaliser et de hiérarchiser la façon dont vos éléments de <xref:System.Windows.Forms.ToolStrip> s’ajustent correctement à différentes tailles de formulaire.</span><span class="sxs-lookup"><span data-stu-id="3dddf-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="3dddf-107">Vous pouvez également modifier l’apparence de vos éléments lorsqu’ils entrent dans le débordement à l’aide des propriétés <xref:System.Windows.Forms.ToolStripItem.Placement%2A> et <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> et de l’événement <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>.</span><span class="sxs-lookup"><span data-stu-id="3dddf-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="3dddf-108">Si vous agrandissez le formulaire au moment de la conception ou de l’exécution, davantage de <xref:System.Windows.Forms.ToolStripItem>s peuvent être affichés sur le <xref:System.Windows.Forms.ToolStrip> principal et le <xref:System.Windows.Forms.ToolStripOverflowButton> peut même disparaître jusqu’à ce que vous réduisiez la taille du formulaire.</span><span class="sxs-lookup"><span data-stu-id="3dddf-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>

## <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="3dddf-109">Pour activer le dépassement de capacité sur un contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3dddf-109">To enable overflow on a ToolStrip control</span></span>

- <span data-ttu-id="3dddf-110">Assurez-vous que la propriété <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> n’est pas définie sur `false` pour le <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="3dddf-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="3dddf-111">Par défaut, il s’agit de `True`.</span><span class="sxs-lookup"><span data-stu-id="3dddf-111">The default is `True`.</span></span>

     <span data-ttu-id="3dddf-112">Lorsque <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> est `True` (valeur par défaut), un <xref:System.Windows.Forms.ToolStripItem> est envoyé au menu déroulant de dépassement de capacité lorsque le contenu du <xref:System.Windows.Forms.ToolStripItem> dépasse la largeur d’un <xref:System.Windows.Forms.ToolStrip> horizontal ou la hauteur d’un <xref:System.Windows.Forms.ToolStrip>vertical.</span><span class="sxs-lookup"><span data-stu-id="3dddf-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="3dddf-113">Pour spécifier le comportement de dépassement de capacité d’un ToolStripItem spécifique</span><span class="sxs-lookup"><span data-stu-id="3dddf-113">To specify overflow behavior of a specific ToolStripItem</span></span>

- <span data-ttu-id="3dddf-114">Affectez la valeur souhaitée à la propriété <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> du <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="3dddf-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="3dddf-115">Les possibilités sont `Always`, `Never`et `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="3dddf-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="3dddf-116">Par défaut, il s’agit de `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="3dddf-116">The default is `AsNeeded`.</span></span>

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a><span data-ttu-id="3dddf-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3dddf-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="3dddf-118">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3dddf-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="3dddf-119">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3dddf-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="3dddf-120">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3dddf-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
