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
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Procédure : créer des clés d’accès pour les contrôles Windows Forms à l’aide du concepteur
Une *touche d’accès* est un caractère souligné dans le texte d’un menu, un élément de menu ou l’étiquette d’un contrôle tel qu’un bouton. Il permet à l’utilisateur de «cliquer» sur un bouton en appuyant sur la touche ALT en combinaison avec la clé d’accès prédéfinie. Par exemple, si un bouton exécute une procédure pour imprimer un formulaire, sa `Text` propriété a donc la valeur «imprimer», en ajoutant une esperluette (&) avant la lettre «p», la lettre «p» est soulignée dans le texte du bouton au moment de l’exécution. L’utilisateur peut exécuter la commande associée au bouton en appuyant sur ALT + P. Vous ne pouvez pas avoir de clé d’accès pour un contrôle qui ne peut pas recevoir le focus.

## <a name="to-create-an-access-key-for-a-control"></a>Pour créer une clé d’accès pour un contrôle

1. Dans la fenêtre **Propriétés** , affectez `Text` à la propriété une chaîne qui comprend une esperluette (&) avant la lettre qui sera la touche d’accès. Par exemple, pour définir la lettre «P» comme touche d’accès, tapez **& imprimer** dans la grille.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Button>
- [Guide pratique pour Répondre à Windows Forms clics de bouton](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique pour Définir le texte affiché par un contrôle Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
