---
title: Méthodes de sélection d’un contrôle Button
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740005"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a><span data-ttu-id="579f7-102">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="579f7-102">Ways to Select a Windows Forms Button Control</span></span>
<span data-ttu-id="579f7-103">Un bouton de Windows Forms peut être sélectionné des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="579f7-103">A Windows Forms button can be selected in the following ways:</span></span>  
  
- <span data-ttu-id="579f7-104">Utilisez la souris pour cliquer sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="579f7-104">Use a mouse to click the button.</span></span>  
  
- <span data-ttu-id="579f7-105">Appelez l’événement <xref:System.Windows.Forms.Control.Click> du bouton dans le code.</span><span class="sxs-lookup"><span data-stu-id="579f7-105">Invoke the button's <xref:System.Windows.Forms.Control.Click> event in code.</span></span>  
  
- <span data-ttu-id="579f7-106">Déplacez le focus sur le bouton en appuyant sur la touche TAB, puis choisissez le bouton en appuyant sur la barre d’espace ou sur entrée.</span><span class="sxs-lookup"><span data-stu-id="579f7-106">Move the focus to the button by pressing the TAB key, and then choose the button by pressing the SPACEBAR or ENTER.</span></span>  
  
- <span data-ttu-id="579f7-107">Appuyez sur la touche d’accès (ALT + la lettre soulignée) pour le bouton.</span><span class="sxs-lookup"><span data-stu-id="579f7-107">Press the access key (ALT + the underlined letter) for the button.</span></span> <span data-ttu-id="579f7-108">Pour plus d’informations sur les clés d’accès, consultez [How to : Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="579f7-108">For more information about access keys, see [How to: Create Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
- <span data-ttu-id="579f7-109">Si le bouton est le bouton « accepter » du formulaire, le fait d’appuyer sur entrée choisit le bouton, même si un autre contrôle a le focus, sauf s’il s’agit d’un autre bouton, d’une zone de texte multiligne ou d’un contrôle personnalisé qui intercepte la touche entrée.</span><span class="sxs-lookup"><span data-stu-id="579f7-109">If the button is the "accept" button of the form, pressing ENTER chooses the button, even if another control has the focus — except if that other control is another button, a multi-line text box, or a custom control that traps the enter key.</span></span>  
  
- <span data-ttu-id="579f7-110">Si le bouton est le bouton « Annuler » du formulaire, le fait d’appuyer sur la touche Échap choisit le bouton, même si un autre contrôle a le focus.</span><span class="sxs-lookup"><span data-stu-id="579f7-110">If the button is the "cancel" button of the form, pressing ESC chooses the button, even if another control has the focus.</span></span>  
  
- <span data-ttu-id="579f7-111">Appelez la méthode <xref:System.Windows.Forms.Button.PerformClick%2A> pour sélectionner le bouton par programmation.</span><span class="sxs-lookup"><span data-stu-id="579f7-111">Call the <xref:System.Windows.Forms.Button.PerformClick%2A> method to select the button programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="579f7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="579f7-112">See also</span></span>

- [<span data-ttu-id="579f7-113">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="579f7-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="579f7-114">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="579f7-114">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="579f7-115">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="579f7-115">Button Control</span></span>](button-control-windows-forms.md)
