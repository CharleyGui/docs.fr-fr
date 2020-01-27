---
title: Désigner un bouton comme bouton Annuler à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
ms.openlocfilehash: 95d1139b6e339055f944ad0b0967a6d91283d49e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746052"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="75bee-102">Comment : désigner un bouton Windows Forms comme bouton Annuler à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="75bee-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="75bee-103">Sur un formulaire Windows, vous pouvez désigner un contrôle de <xref:System.Windows.Forms.Button> comme bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="75bee-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="75bee-104">Un clic est effectué sur un bouton Annuler chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quel que soit le contrôle du formulaire actif.</span><span class="sxs-lookup"><span data-stu-id="75bee-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="75bee-105">Un tel bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.</span><span class="sxs-lookup"><span data-stu-id="75bee-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>

## <a name="to-designate-the-cancel-button"></a><span data-ttu-id="75bee-106">Pour désigner le bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="75bee-106">To designate the cancel button</span></span>

1. <span data-ttu-id="75bee-107">Sélectionnez le formulaire sur lequel réside le bouton.</span><span class="sxs-lookup"><span data-stu-id="75bee-107">Select the form on which the button resides.</span></span>

2. <span data-ttu-id="75bee-108">Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Windows.Forms.Form.CancelButton%2A> du formulaire sur le nom du contrôle <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="75bee-108">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>

## <a name="see-also"></a><span data-ttu-id="75bee-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75bee-109">See also</span></span>

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [<span data-ttu-id="75bee-110">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="75bee-110">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="75bee-111">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75bee-111">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="75bee-112">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="75bee-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="75bee-113">Guide pratique pour désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="75bee-113">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [<span data-ttu-id="75bee-114">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="75bee-114">Button Control</span></span>](button-control-windows-forms.md)
