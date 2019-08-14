---
title: 'Procédure : créer des boutons bascule dans des contrôles ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972364"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="e84d1-102">Procédure : créer des boutons bascule dans des contrôles ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e84d1-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>

<span data-ttu-id="e84d1-103">Lorsqu’un utilisateur clique sur un bouton bascule, il apparaît en 3D enfoncé et conserve l’apparence enfoncée jusqu’à ce que l’utilisateur clique à nouveau sur le bouton.</span><span class="sxs-lookup"><span data-stu-id="e84d1-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>

## <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="e84d1-104">Pour créer un ToolStripButton à bascule</span><span class="sxs-lookup"><span data-stu-id="e84d1-104">To create a toggling ToolStripButton</span></span>

- <span data-ttu-id="e84d1-105">Utilisez un code tel que l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="e84d1-105">Use code such as the following code example.</span></span> <span data-ttu-id="e84d1-106">Ce code suppose que votre formulaire contient <xref:System.Windows.Forms.ToolStrip> un contrôle et que sa <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contient une <xref:System.Windows.Forms.ToolStripButton> appelée `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="e84d1-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="e84d1-107">Elle suppose également que vous avez un gestionnaire d’événements appelé `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="e84d1-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>

    ```vb
    toolStripButton1.CheckOnClick = True
    toolStripButton1.CheckedChanged AddressOf _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

    ```csharp
    toolStripButton1.CheckOnClick = true;
    toolStripButton1.CheckedChanged += new _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

## <a name="see-also"></a><span data-ttu-id="e84d1-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e84d1-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="e84d1-109">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="e84d1-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
