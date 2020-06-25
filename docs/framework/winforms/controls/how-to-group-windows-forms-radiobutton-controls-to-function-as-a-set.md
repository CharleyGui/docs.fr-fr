---
title: Grouper des contrôles RadioButton pour qu’ils fonctionnent comme un ensemble
description: Découvrez comment regrouper Windows Forms contrôles RadioButton pour fonctionner indépendamment des autres jeux.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325923"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="084c3-103">Comment : grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment</span><span class="sxs-lookup"><span data-stu-id="084c3-103">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="084c3-104">Les <xref:System.Windows.Forms.RadioButton> contrôles Windows Forms sont conçus pour permettre aux utilisateurs de choisir entre plusieurs paramètres, dont un seul peut être assigné à une procédure ou à un objet.</span><span class="sxs-lookup"><span data-stu-id="084c3-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="084c3-105">Par exemple, un groupe de <xref:System.Windows.Forms.RadioButton> contrôles peut afficher un choix de porte-lots pour une commande, mais un seul de ces opérateurs sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="084c3-105">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="084c3-106">Par conséquent, un seul <xref:System.Windows.Forms.RadioButton> élément à la fois peut être sélectionné, même s’il fait partie d’un groupe fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="084c3-106">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="084c3-107">Vous regroupez des cases d’option en les dessinant à l’intérieur d’un conteneur tel qu’un <xref:System.Windows.Forms.Panel> contrôle, un <xref:System.Windows.Forms.GroupBox> contrôle ou un formulaire.</span><span class="sxs-lookup"><span data-stu-id="084c3-107">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="084c3-108">Toutes les cases d’option ajoutées directement à un formulaire deviennent un groupe.</span><span class="sxs-lookup"><span data-stu-id="084c3-108">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="084c3-109">Pour ajouter des groupes distincts, vous devez les placer à l’intérieur de panneaux ou de zones de groupe.</span><span class="sxs-lookup"><span data-stu-id="084c3-109">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="084c3-110">Pour plus d’informations sur les panneaux ou les zones de groupe, consultez [vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md) ou [vue d’ensemble du contrôle GroupBox](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="084c3-110">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="084c3-111">Pour regrouper des contrôles RadioButton comme un jeu pour fonctionner indépendamment d’autres jeux</span><span class="sxs-lookup"><span data-stu-id="084c3-111">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="084c3-112">Faites glisser <xref:System.Windows.Forms.GroupBox> un <xref:System.Windows.Forms.Panel> contrôle ou de l’onglet **Windows Forms** de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="084c3-112">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="084c3-113">Dessinez <xref:System.Windows.Forms.RadioButton> des contrôles sur le <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> contrôle ou.</span><span class="sxs-lookup"><span data-stu-id="084c3-113">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084c3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="084c3-114">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="084c3-115">Vue d’ensemble du contrôle RadioButton</span><span class="sxs-lookup"><span data-stu-id="084c3-115">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="084c3-116">Vue d’ensemble du contrôle Panel</span><span class="sxs-lookup"><span data-stu-id="084c3-116">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="084c3-117">Vue d'ensemble du contrôle GroupBox</span><span class="sxs-lookup"><span data-stu-id="084c3-117">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="084c3-118">Vue d’ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="084c3-118">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="084c3-119">RadioButton, contrôle</span><span class="sxs-lookup"><span data-stu-id="084c3-119">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
