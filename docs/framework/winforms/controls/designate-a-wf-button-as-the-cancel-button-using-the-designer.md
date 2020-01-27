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
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Comment : désigner un bouton Windows Forms comme bouton Annuler à l'aide du concepteur
Sur un formulaire Windows, vous pouvez désigner un contrôle de <xref:System.Windows.Forms.Button> comme bouton Annuler. Un clic est effectué sur un bouton Annuler chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quel que soit le contrôle du formulaire actif. Un tel bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.

## <a name="to-designate-the-cancel-button"></a>Pour désigner le bouton Annuler

1. Sélectionnez le formulaire sur lequel réside le bouton.

2. Dans la fenêtre **Propriétés** , définissez la propriété <xref:System.Windows.Forms.Form.CancelButton%2A> du formulaire sur le nom du contrôle <xref:System.Windows.Forms.Button>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Vue d'ensemble du contrôle Button](button-control-overview-windows-forms.md)
- [Méthodes de sélection du contrôle Button Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Guide pratique pour répondre à un clic du contrôle Button Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique pour désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Button, contrôle](button-control-windows-forms.md)
