---
title: 'Procédure : définir le texte affiché par un contrôle Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], setting caption
- Windows Forms, setting the text displayed
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
ms.openlocfilehash: 37ab3823a41cca2eeea550c90e92e90bc364c759
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960349"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer"></a>Procédure : définir le texte affiché par un contrôle Windows Forms à l’aide du concepteur

Contrôles Windows Forms affichent généralement un texte qui est lié à la fonction principale du contrôle. Par exemple, un <xref:System.Windows.Forms.Button> contrôle affiche habituellement une légende qui indique quelle action sera effectuée lorsque le bouton est activé. Pour tous les contrôles, vous pouvez définir ou retourner le texte à l'aide de la propriété <xref:System.Windows.Forms.Control.Text%2A>. Vous pouvez modifier la police en utilisant la propriété <xref:System.Windows.Forms.Control.Font%2A>.

### <a name="to-set-the-text-and-font-with-the-designer"></a>Pour définir le texte et la police avec le Concepteur

1. Dans la fenêtre Propriétés, définissez la <xref:System.Windows.Forms.Control.Text%2A> propriété du contrôle à une chaîne appropriée.

     Pour créer une touche de raccourci soulignée, incluez une esperluette (&) avant la lettre qui sera la touche de raccourci.

2. Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) à côté du <xref:System.Windows.Forms.Control.Font%2A> propriété.

     Dans la boîte de dialogue Police standard, sélectionnez la police, le style de police, taille, effets (tels que barré ou soulignement) et script que vous souhaitez.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Définir le texte affiché par un Windows Forms de contrôle](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Utilisation de polices et de texte](../advanced/using-fonts-and-text.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
