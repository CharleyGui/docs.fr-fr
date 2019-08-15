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
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a>Procédure : désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur
Sur un formulaire Windows, vous pouvez désigner un <xref:System.Windows.Forms.Button> contrôle comme bouton Annuler. Un clic est effectué sur un bouton Annuler chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quel que soit le contrôle du formulaire actif. Un tel bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.

## <a name="to-designate-the-cancel-button"></a>Pour désigner le bouton Annuler

1. Sélectionnez le formulaire sur lequel réside le bouton.

2. Dans la fenêtre **Propriétés** , affectez à la <xref:System.Windows.Forms.Form.CancelButton%2A> propriété du formulaire <xref:System.Windows.Forms.Button> le nom du contrôle.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Vue d'ensemble du contrôle Button](button-control-overview-windows-forms.md)
- [Méthodes de sélection du contrôle Button Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Guide pratique : Répondre à Windows Forms clics de bouton](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique pour Désigner un bouton Windows Forms comme bouton accepter à l’aide du concepteur](designate-a-wf-button-as-the-accept-button-using-the-designer.md)
- [Button, contrôle](button-control-windows-forms.md)
