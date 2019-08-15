---
title: 'Procédure : désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039655"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a><span data-ttu-id="0b0e5-102">Procédure : désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="0b0e5-102">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>
<span data-ttu-id="0b0e5-103">Sur un formulaire Windows, vous pouvez désigner un <xref:System.Windows.Forms.Button> contrôle comme bouton d’acceptation, également appelé bouton par défaut.</span><span class="sxs-lookup"><span data-stu-id="0b0e5-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the accept button, also known as the default button.</span></span> <span data-ttu-id="0b0e5-104">Chaque fois que l’utilisateur appuie sur la touche entrée, le bouton par défaut est activé, quel que soit l’autre contrôle sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="0b0e5-104">Whenever the user presses the ENTER key, the default button is clicked regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="0b0e5-105">Les exceptions sont les cas où le contrôle ayant le focus est un autre bouton, dans ce cas, le bouton sur lequel le focus sera activé, ou une zone de texte multiligne, ou un contrôle personnalisé qui intercepte la touche entrée.</span><span class="sxs-lookup"><span data-stu-id="0b0e5-105">The exceptions to this are when the control with focus is another button — in that case, the button with the focus will be clicked — or a multiline text box, or a custom control that traps the ENTER key.</span></span>

## <a name="to-designate-the-accept-button"></a><span data-ttu-id="0b0e5-106">Pour désigner le bouton accepter</span><span class="sxs-lookup"><span data-stu-id="0b0e5-106">To designate the accept button</span></span>

1. <span data-ttu-id="0b0e5-107">Sélectionnez le formulaire sur lequel réside le bouton.</span><span class="sxs-lookup"><span data-stu-id="0b0e5-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="0b0e5-108">Dans la fenêtre **Propriétés** , affectez à la <xref:System.Windows.Forms.Form.AcceptButton%2A> propriété du formulaire <xref:System.Windows.Forms.Button> le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="0b0e5-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.AcceptButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b0e5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b0e5-109">See also</span></span>

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [<span data-ttu-id="0b0e5-110">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="0b0e5-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="0b0e5-111">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b0e5-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="0b0e5-112">Guide pratique pour Répondre à Windows Forms clics de bouton</span><span class="sxs-lookup"><span data-stu-id="0b0e5-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="0b0e5-113">Guide pratique : Désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="0b0e5-113">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [<span data-ttu-id="0b0e5-114">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="0b0e5-114">Button Control</span></span>](button-control-windows-forms.md)
