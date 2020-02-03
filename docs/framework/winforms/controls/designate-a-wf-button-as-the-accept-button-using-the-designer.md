---
title: Désigner un bouton comme bouton accepter à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27a5de51f8c5b2c84cc205e09ac1a2179c315752
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746065"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="69840-102">Comment : désigner un bouton Windows Forms comme bouton Accepter à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="69840-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="69840-103">Sur un formulaire Windows, vous pouvez désigner un contrôle de <xref:System.Windows.Forms.Button> comme bouton accepter, également appelé bouton par défaut.</span><span class="sxs-lookup"><span data-stu-id="69840-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="69840-104">Chaque fois que l’utilisateur appuie sur la touche entrée, le bouton par défaut est activé, quel que soit l’autre contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="69840-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="69840-105">Les exceptions sont les cas où le contrôle ayant le focus est un autre bouton, dans ce cas, le bouton sur lequel le focus sera activé, ou une zone de texte multiligne, ou un contrôle personnalisé qui intercepte la touche entrée.</span><span class="sxs-lookup"><span data-stu-id="69840-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>

## <a name="to-designate-the-accept-button"></a><span data-ttu-id="69840-106">Pour désigner le bouton accepter</span><span class="sxs-lookup"><span data-stu-id="69840-106">To designate the accept button</span></span>

1. <span data-ttu-id="69840-107">Sélectionnez le formulaire sur lequel réside le bouton.</span><span class="sxs-lookup"><span data-stu-id="69840-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="69840-108">Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Windows.Forms.Form.AcceptButton%2A> du formulaire sur le nom du contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="69840-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="69840-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69840-109">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="69840-110">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="69840-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="69840-111">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69840-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="69840-112">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="69840-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="69840-113">Guide pratique pour désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="69840-113">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [<span data-ttu-id="69840-114">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="69840-114">Button Control</span></span>](button-control-windows-forms.md)
