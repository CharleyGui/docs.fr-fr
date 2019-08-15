---
title: 'Procédure : créer des clés d’accès pour les contrôles Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039518"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a><span data-ttu-id="abcf7-102">Procédure : créer des clés d’accès pour les contrôles Windows Forms à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="abcf7-102">How to: Create Access Keys for Windows Forms Controls Using the Designer</span></span>
<span data-ttu-id="abcf7-103">Une *touche d’accès* est un caractère souligné dans le texte d’un menu, un élément de menu ou l’étiquette d’un contrôle tel qu’un bouton.</span><span class="sxs-lookup"><span data-stu-id="abcf7-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="abcf7-104">Il permet à l’utilisateur de «cliquer» sur un bouton en appuyant sur la touche ALT en combinaison avec la clé d’accès prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="abcf7-104">It enables the user to "click" a button by pressing the ALT key in combination with the predefined access key.</span></span> <span data-ttu-id="abcf7-105">Par exemple, si un bouton exécute une procédure pour imprimer un formulaire, sa `Text` propriété a donc la valeur «imprimer», en ajoutant une esperluette (&) avant la lettre «p», la lettre «p» est soulignée dans le texte du bouton au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="abcf7-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand (&) before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="abcf7-106">L’utilisateur peut exécuter la commande associée au bouton en appuyant sur ALT + P.</span><span class="sxs-lookup"><span data-stu-id="abcf7-106">The user can run the command associated with the button by pressing ALT+P.</span></span> <span data-ttu-id="abcf7-107">Vous ne pouvez pas avoir de clé d’accès pour un contrôle qui ne peut pas recevoir le focus.</span><span class="sxs-lookup"><span data-stu-id="abcf7-107">You cannot have an access key for a control that cannot receive focus.</span></span>

## <a name="to-create-an-access-key-for-a-control"></a><span data-ttu-id="abcf7-108">Pour créer une clé d’accès pour un contrôle</span><span class="sxs-lookup"><span data-stu-id="abcf7-108">To create an access key for a control</span></span>

1. <span data-ttu-id="abcf7-109">Dans la fenêtre **Propriétés** , affectez `Text` à la propriété une chaîne qui comprend une esperluette (&) avant la lettre qui sera la touche d’accès.</span><span class="sxs-lookup"><span data-stu-id="abcf7-109">In the **Properties** window, set the `Text` property to a string that includes an ampersand (&) before the letter that will be the access key.</span></span> <span data-ttu-id="abcf7-110">Par exemple, pour définir la lettre «P» comme touche d’accès, tapez **& imprimer** dans la grille.</span><span class="sxs-lookup"><span data-stu-id="abcf7-110">For example, to set the letter "P" as the access key, type **&Print** into the grid.</span></span>

## <a name="see-also"></a><span data-ttu-id="abcf7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abcf7-111">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="abcf7-112">Guide pratique pour Répondre à Windows Forms clics de bouton</span><span class="sxs-lookup"><span data-stu-id="abcf7-112">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="abcf7-113">Guide pratique pour Définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="abcf7-113">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="abcf7-114">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="abcf7-114">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
