---
title: 'Procédure : désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: 27ecb26c493232bcfb996d012f9760b7ef91e5b2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039655"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Procédure : désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur
Sur un formulaire Windows, vous pouvez désigner un <xref:System.Windows.Forms.Button> contrôle comme bouton d’acceptation, également appelé bouton par défaut. Chaque fois que l’utilisateur appuie sur la touche entrée, le bouton par défaut est activé, quel que soit l’autre contrôle sur le formulaire. Les exceptions sont les cas où le contrôle ayant le focus est un autre bouton, dans ce cas, le bouton sur lequel le focus sera activé, ou une zone de texte multiligne, ou un contrôle personnalisé qui intercepte la touche entrée.

## <a name="to-designate-the-accept-button"></a>Pour désigner le bouton accepter

1. Sélectionnez le formulaire sur lequel réside le bouton.

2. Dans la fenêtre **Propriétés** , affectez à la <xref:System.Windows.Forms.Form.AcceptButton%2A> propriété du formulaire <xref:System.Windows.Forms.Button> le nom du contrôle.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Vue d'ensemble du contrôle Button](button-control-overview-windows-forms.md)
- [Méthodes de sélection du contrôle Button Windows Forms](ways-to-select-a-windows-forms-button-control.md)
- [Guide pratique pour Répondre à Windows Forms clics de bouton](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique : Désigner un bouton Windows Forms comme bouton Annuler à l’aide du concepteur](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Button, contrôle](button-control-windows-forms.md)
