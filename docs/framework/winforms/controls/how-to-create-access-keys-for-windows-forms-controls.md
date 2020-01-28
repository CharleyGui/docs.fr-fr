---
title: Créer des clés d’accès pour les contrôles
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 7f6b0a5838cacfc1189fba819a54b3423d567ea0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731174"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a><span data-ttu-id="26ce1-102">Comment : créer des clés d’accès pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ce1-102">How to: Create access keys for Windows Forms controls</span></span>

<span data-ttu-id="26ce1-103">Une *touche d’accès* est un caractère souligné dans le texte d’un menu, un élément de menu ou l’étiquette d’un contrôle tel qu’un bouton.</span><span class="sxs-lookup"><span data-stu-id="26ce1-103">An *access key* is an underlined character in the text of a menu, menu item, or the label of a control such as a button.</span></span> <span data-ttu-id="26ce1-104">Avec une clé d’accès, l’utilisateur peut « cliquer » sur un bouton en appuyant sur la touche Alt en combinaison avec la clé d’accès prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="26ce1-104">With an access key, the user can "click" a button by pressing the Alt key in combination with the predefined access key.</span></span> <span data-ttu-id="26ce1-105">Par exemple, si un bouton exécute une procédure pour imprimer un formulaire, et que sa propriété `Text` est donc définie sur « imprimer », l’ajout d’une esperluette avant la lettre « P » entraîne la soulignement de la lettre « P » dans le texte du bouton au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="26ce1-105">For example, if a button runs a procedure to print a form, and therefore its `Text` property is set to "Print," adding an ampersand before the letter "P" causes the letter "P" to be underlined in the button text at run time.</span></span> <span data-ttu-id="26ce1-106">L’utilisateur peut exécuter la commande associée au bouton en appuyant sur ALT + P.</span><span class="sxs-lookup"><span data-stu-id="26ce1-106">The user can run the command associated with the button by pressing Alt+P.</span></span>

<span data-ttu-id="26ce1-107">Les contrôles qui ne peuvent pas recevoir le focus ne peuvent pas avoir de clés d’accès.</span><span class="sxs-lookup"><span data-stu-id="26ce1-107">Controls that cannot receive focus can't have access keys.</span></span>

## <a name="programmatic"></a><span data-ttu-id="26ce1-108">Par programme</span><span class="sxs-lookup"><span data-stu-id="26ce1-108">Programmatic</span></span>

<span data-ttu-id="26ce1-109">Définissez la propriété `Text` sur une chaîne qui comprend une esperluette (&) avant la lettre qui sera le raccourci.</span><span class="sxs-lookup"><span data-stu-id="26ce1-109">Set the `Text` property to a string that includes an ampersand (&) before the letter that will be the shortcut.</span></span>

```vb
' Set the letter "P" as an access key.
Button1.Text = "&Print"
```

```csharp
// Set the letter "P" as an access key.
button1.Text = "&Print";
```

```cpp
// Set the letter "P" as an access key.
button1->Text = "&Print";
```

> [!NOTE]
> <span data-ttu-id="26ce1-110">Pour utiliser une esperluette dans une légende sans créer de clé d’accès, incluez deux signes & (& &).</span><span class="sxs-lookup"><span data-stu-id="26ce1-110">To use an ampersand in a caption without creating an access key, include two ampersands (&&).</span></span> <span data-ttu-id="26ce1-111">Une esperluette unique est affichée dans la légende et aucun caractère n’est souligné.</span><span class="sxs-lookup"><span data-stu-id="26ce1-111">A single ampersand is displayed in the caption and no characters are underlined.</span></span>

## <a name="designer"></a><span data-ttu-id="26ce1-112">Designer</span><span class="sxs-lookup"><span data-stu-id="26ce1-112">Designer</span></span>

<span data-ttu-id="26ce1-113">Dans la fenêtre **Propriétés** de Visual Studio, définissez la propriété **Text** sur une chaîne qui comprend une esperluette (' & ') avant la lettre qui sera la touche d’accès.</span><span class="sxs-lookup"><span data-stu-id="26ce1-113">In the **Properties** window of Visual Studio, set the **Text** property to a string that includes an ampersand ('&') before the letter that will be the access key.</span></span> <span data-ttu-id="26ce1-114">Par exemple, pour définir la lettre « P » comme touche d’accès, entrez **& imprimer**.</span><span class="sxs-lookup"><span data-stu-id="26ce1-114">For example, to set the letter "P" as the access key, enter **&Print**.</span></span>

## <a name="see-also"></a><span data-ttu-id="26ce1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26ce1-115">See also</span></span>

- <xref:System.Windows.Forms.Button>
- [<span data-ttu-id="26ce1-116">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ce1-116">How to: Respond to Windows Forms Button Clicks</span></span>](how-to-respond-to-windows-forms-button-clicks.md)
- [<span data-ttu-id="26ce1-117">Guide pratique pour définir le texte affiché par un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ce1-117">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="26ce1-118">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26ce1-118">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
