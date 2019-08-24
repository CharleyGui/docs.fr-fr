---
title: 'Procédure : arrimer des contrôles dans des Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 58b61af306385a245bedf16e370e6830c370a622
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987486"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Procédure : Ancrer les contrôles sur Windows Forms

Vous pouvez ancrer les contrôles aux bords de votre formulaire ou les faire remplir le conteneur du contrôle (un formulaire ou un contrôle conteneur). Par exemple, l’Explorateur Windows ancre son <xref:System.Windows.Forms.TreeView> contrôle sur le côté gauche de la fenêtre et son <xref:System.Windows.Forms.ListView> contrôle sur le côté droit de la fenêtre. Utilisez la <xref:System.Windows.Forms.Control.Dock%2A> propriété pour tous les contrôles Windows Forms visibles pour définir le mode d’ancrage.

> [!NOTE]
> Les contrôles sont ancrés dans l’ordre de plan inverse.

La <xref:System.Windows.Forms.Control.Dock%2A> propriété interagit avec la <xref:System.Windows.Forms.Control.AutoSize%2A> propriété. Pour plus d’informations, consultez [vue d’ensemble](autosize-property-overview.md)de la propriété AutoSize.

## <a name="to-dock-a-control"></a>Pour ancrer un contrôle

1. Dans Visual Studio, sélectionnez le contrôle que vous souhaitez ancrer.

2. Dans la fenêtre **Propriétés** , cliquez sur la flèche à droite de la <xref:System.Windows.Forms.Control.Dock%2A> propriété.

   Un éditeur affiche une série de cases représentant les bords et le centre du formulaire.

3. Cliquez sur le bouton qui représente le bord du formulaire dans lequel vous souhaitez ancrer le contrôle. Pour remplir le contenu du contrôle de formulaire ou de conteneur du contrôle, cliquez sur la zone centrale. Cliquez sur **(aucun)** pour désactiver l’ancrage.

   Le contrôle est automatiquement redimensionné pour s’ajuster aux limites du bord ancré.

   > [!NOTE]
   > Les contrôles hérités `Protected` doivent être en mesure d’être ancrés. Pour modifier le niveau d’accès d’un contrôle, définissez sa propriété **modifier** dans la fenêtre **Propriétés** .

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
- [Guide pratique : Ancrer et ancrer des contrôles enfants dans un contrôle FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Guide pratique pour Ancrer et ancrer des contrôles enfants dans un contrôle TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Vue d’ensemble de la propriété AutoSize](autosize-property-overview.md)
- [Guide pratique pour Contrôles d’ancrage sur Windows Forms](how-to-anchor-controls-on-windows-forms.md)
