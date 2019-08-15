---
title: 'Procédure : désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: cc352f15fb1e8b531cd0f9b298b2db4ce649d3cf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039648"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="0728b-102">Procédure : désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="0728b-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="0728b-103">Sur un formulaire Windows, vous pouvez désigner un <xref:System.Windows.Forms.Button> contrôle comme bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="0728b-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="0728b-104">Un clic est effectué sur un bouton Annuler chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quel que soit le contrôle du formulaire actif.</span><span class="sxs-lookup"><span data-stu-id="0728b-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="0728b-105">Un tel bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.</span><span class="sxs-lookup"><span data-stu-id="0728b-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="0728b-106">Pour désigner le bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="0728b-106">To designate the cancel button</span></span>

1. <span data-ttu-id="0728b-107">Sélectionnez le formulaire sur lequel réside le bouton.</span><span class="sxs-lookup"><span data-stu-id="0728b-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="0728b-108">Dans la fenêtre **Propriétés** , affectez à la <xref:System.Windows.Forms.Form.CancelButton%2A> propriété du formulaire <xref:System.Windows.Forms.Button> le nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="0728b-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="0728b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0728b-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="0728b-110">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="0728b-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="0728b-111">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0728b-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="0728b-112">Guide pratique : Répondre à Windows Forms clics de bouton</span><span class="sxs-lookup"><span data-stu-id="0728b-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="0728b-113">Guide pratique pour Désigner un bouton Windows Forms comme bouton accepter à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="0728b-113">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="0728b-114">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="0728b-114">Button Control</span></span>](button-control-windows-forms.md)
