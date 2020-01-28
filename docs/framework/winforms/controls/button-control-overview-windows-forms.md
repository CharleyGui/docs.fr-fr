---
title: Vue d'ensemble du contrôle Button
ms.date: 03/30/2017
f1_keywords:
- Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
ms.openlocfilehash: 4ba7b333e5414efb4814d64ce50c55e08b27f859
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747082"
---
# <a name="button-control-overview-windows-forms"></a>Vue d'ensemble du contrôle Button (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.Button> permet à l'utilisateur d'effectuer une action en cliquant dessus. Quand le bouton est activé, il donne l'impression d'être enfoncé puis relâché. Chaque fois que l’utilisateur clique sur un bouton, le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> est appelé. Vous placez le code dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> pour exécuter toute action de votre choix.  
  
 Le texte affiché sur le bouton est contenu dans la propriété <xref:System.Windows.Forms.Control.Text%2A>. Si votre texte dépasse la largeur du bouton, il est renvoyé à la ligne suivante. Toutefois, il est coupé si le contrôle ne peut pas prendre en charge sa hauteur globale. Pour plus d’informations, consultez [Comment : définir le texte affiché par un contrôle Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md). La propriété <xref:System.Windows.Forms.Control.Text%2A> peut contenir une clé d’accès, qui permet à un utilisateur de « cliquer » sur le contrôle en appuyant sur la touche ALT avec la touche d’accès. Pour plus d’informations, consultez [Comment : créer des clés d’accès pour les contrôles Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md). L’apparence du texte est contrôlée par la propriété <xref:System.Windows.Forms.Control.Font%2A> et la propriété <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>.  
  
 Le contrôle <xref:System.Windows.Forms.Button> peut également afficher des images à l’aide des propriétés <xref:System.Windows.Forms.ButtonBase.Image%2A> et <xref:System.Windows.Forms.ButtonBase.ImageList%2A>. Pour plus d’informations, consultez [Comment : définir l’image affichée par un contrôle Windows Forms](how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Button>
- [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Méthodes de sélection du contrôle Button Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Guide pratique pour désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Guide pratique pour désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button, contrôle](button-control-windows-forms.md)
