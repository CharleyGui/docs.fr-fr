---
title: 'Procédure : créer des clés d’accès pour les contrôles Windows Forms'
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
ms.openlocfilehash: ccec8bba9e01cbaa7bfef841af68a0fcaa720b90
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658377"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Procédure : Créer des clés d’accès pour les contrôles de Windows Forms

Une *touche d’accès* est un caractère souligné dans le texte d’un menu, un élément de menu ou l’étiquette d’un contrôle tel qu’un bouton. Avec une clé d’accès, l’utilisateur peut «cliquer» sur un bouton en appuyant sur la touche Alt en combinaison avec la clé d’accès prédéfinie. Par exemple, si un bouton exécute une procédure pour imprimer un formulaire et que sa `Text` propriété est donc définie sur «imprimer», l’ajout d’une esperluette avant la lettre «p» entraîne la soulignement de la lettre «p» dans le texte du bouton au moment de l’exécution. L’utilisateur peut exécuter la commande associée au bouton en appuyant sur ALT + P.

Les contrôles qui ne peuvent pas recevoir le focus ne peuvent pas avoir de clés d’accès.

## <a name="programmatic"></a>Par programme

Affectez `Text` à la propriété une chaîne qui comprend une esperluette (&) avant la lettre qui sera le raccourci.

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
> Pour utiliser une esperluette dans une légende sans créer de clé d’accès, incluez deux signes & (& &). Une esperluette unique est affichée dans la légende et aucun caractère n’est souligné.

## <a name="designer"></a>Designer

Dans la fenêtre **Propriétés** de Visual Studio, définissez la propriété **Text** sur une chaîne qui comprend une esperluette (' & ') avant la lettre qui sera la touche d’accès. Par exemple, pour définir la lettre «P» comme touche d’accès, entrez **& imprimer**.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Button>
- [Guide pratique pour Répondre à Windows Forms clics de bouton](how-to-respond-to-windows-forms-button-clicks.md)
- [Guide pratique pour Définir le texte affiché par un contrôle Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
