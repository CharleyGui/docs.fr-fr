---
title: Grouper des contrôles RadioButton pour qu’ils fonctionnent comme un ensemble
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: c4b37c84bf0f93837b91c743c7681d39fd83a659
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732952"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="58025-102">Comment : grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment</span><span class="sxs-lookup"><span data-stu-id="58025-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="58025-103">Les contrôles Windows Forms <xref:System.Windows.Forms.RadioButton> sont conçus pour permettre aux utilisateurs de choisir entre plusieurs paramètres, dont un seul peut être assigné à une procédure ou à un objet.</span><span class="sxs-lookup"><span data-stu-id="58025-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="58025-104">Par exemple, un groupe de <xref:System.Windows.Forms.RadioButton> contrôles peut afficher un choix de porte-packages pour une commande, mais un seul de ces opérateurs sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="58025-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="58025-105">Par conséquent, vous ne pouvez sélectionner qu’un seul <xref:System.Windows.Forms.RadioButton> à la fois, même s’il fait partie d’un groupe fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="58025-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="58025-106">Vous regroupez des cases d’option en les dessinant à l’intérieur d’un conteneur tel qu’un contrôle <xref:System.Windows.Forms.Panel>, un contrôle <xref:System.Windows.Forms.GroupBox> ou un formulaire.</span><span class="sxs-lookup"><span data-stu-id="58025-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="58025-107">Toutes les cases d’option ajoutées directement à un formulaire deviennent un groupe.</span><span class="sxs-lookup"><span data-stu-id="58025-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="58025-108">Pour ajouter des groupes distincts, vous devez les placer à l’intérieur de panneaux ou de zones de groupe.</span><span class="sxs-lookup"><span data-stu-id="58025-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="58025-109">Pour plus d’informations sur les panneaux ou les zones de groupe, consultez [vue d’ensemble du contrôle Panel](panel-control-overview-windows-forms.md) ou [vue d’ensemble du contrôle GroupBox](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="58025-109">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="58025-110">Pour regrouper des contrôles RadioButton comme un jeu pour fonctionner indépendamment d’autres jeux</span><span class="sxs-lookup"><span data-stu-id="58025-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="58025-111">Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel> de l’onglet **Windows Forms** de la **boîte à outils** vers le formulaire.</span><span class="sxs-lookup"><span data-stu-id="58025-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="58025-112">Dessinez <xref:System.Windows.Forms.RadioButton> contrôles sur le contrôle <xref:System.Windows.Forms.GroupBox> ou <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="58025-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58025-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58025-113">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="58025-114">Vue d’ensemble du contrôle RadioButton</span><span class="sxs-lookup"><span data-stu-id="58025-114">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="58025-115">Vue d’ensemble du contrôle Panel</span><span class="sxs-lookup"><span data-stu-id="58025-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="58025-116">Vue d’ensemble du contrôle GroupBox</span><span class="sxs-lookup"><span data-stu-id="58025-116">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="58025-117">Vue d'ensemble du contrôle CheckBox</span><span class="sxs-lookup"><span data-stu-id="58025-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="58025-118">RadioButton, contrôle</span><span class="sxs-lookup"><span data-stu-id="58025-118">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
