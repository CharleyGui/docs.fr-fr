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
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Comment : désigner un bouton Windows Forms comme bouton Accepter à l'aide du concepteur
Sur un formulaire Windows, vous pouvez désigner un contrôle de <xref:System.Windows.Forms.Button> comme bouton accepter, également appelé bouton par défaut. Chaque fois que l’utilisateur appuie sur la touche entrée, le bouton par défaut est activé, quel que soit l’autre contrôle sur le formulaire. Les exceptions sont les cas où le contrôle ayant le focus est un autre bouton, dans ce cas, le bouton sur lequel le focus sera activé, ou une zone de texte multiligne, ou un contrôle personnalisé qui intercepte la touche entrée.

## <a name="to-designate-the-accept-button"></a>Pour désigner le bouton accepter

1. Sélectionnez le formulaire sur lequel réside le bouton.

2. Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Windows.Forms.Form.AcceptButton%2A> du formulaire sur le nom du contrôle <xref:System.Windows.Forms.Button>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Vue d'ensemble du contrôle Button](button-control-overview-windows-forms.md)
- [Méthodes de sélection du contrôle Button Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique pour désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button, contrôle](button-control-windows-forms.md)
