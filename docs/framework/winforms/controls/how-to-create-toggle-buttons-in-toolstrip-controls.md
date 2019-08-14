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
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>Procédure : créer des boutons bascule dans des contrôles ToolStrip

Lorsqu’un utilisateur clique sur un bouton bascule, il apparaît en 3D enfoncé et conserve l’apparence enfoncée jusqu’à ce que l’utilisateur clique à nouveau sur le bouton.

## <a name="to-create-a-toggling-toolstripbutton"></a>Pour créer un ToolStripButton à bascule

- Utilisez un code tel que l’exemple de code suivant. Ce code suppose que votre formulaire contient <xref:System.Windows.Forms.ToolStrip> un contrôle et que sa <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contient une <xref:System.Windows.Forms.ToolStripButton> appelée `toolStripButton1`. Elle suppose également que vous avez un gestionnaire d’événements appelé `toolStripButton1_CheckedChanged`.

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

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStripButton>
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
