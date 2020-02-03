---
title: ajuster des contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02f1c26dcb322a39c41781c83d8c820bd2fd27e0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745523"
---
# <a name="how-to-dock-controls-on-windows-forms"></a>Comment : ancrer des contrôles sur Windows Forms

Vous pouvez ancrer les contrôles aux bords de votre formulaire ou les faire remplir le conteneur du contrôle (un formulaire ou un contrôle conteneur). Par exemple, l’Explorateur Windows ancre son contrôle <xref:System.Windows.Forms.TreeView> sur le côté gauche de la fenêtre et son contrôle <xref:System.Windows.Forms.ListView> à droite de la fenêtre. Utilisez la propriété <xref:System.Windows.Forms.Control.Dock%2A> pour tous les contrôles Windows Forms visibles pour définir le mode d’ancrage.

> [!NOTE]
> Les contrôles sont ancrés dans l’ordre de plan inverse.

La propriété <xref:System.Windows.Forms.Control.Dock%2A> interagit avec la propriété <xref:System.Windows.Forms.Control.AutoSize%2A>. Pour plus d’informations, consultez [vue d’ensemble de la propriété AutoSize](autosize-property-overview.md).

## <a name="to-dock-a-control"></a>Pour ancrer un contrôle

1. Dans Visual Studio, sélectionnez le contrôle que vous souhaitez ancrer.

2. Dans la fenêtre **Propriétés** , cliquez sur la flèche à droite de la propriété <xref:System.Windows.Forms.Control.Dock%2A>.

   Un éditeur affiche une série de cases représentant les bords et le centre du formulaire.

3. Cliquez sur le bouton qui représente le bord du formulaire dans lequel vous souhaitez ancrer le contrôle. Pour remplir le contenu du contrôle de formulaire ou de conteneur du contrôle, cliquez sur la zone centrale. Cliquez sur **(aucun)** pour désactiver l’ancrage.

   Le contrôle est automatiquement redimensionné pour s’ajuster aux limites du bord ancré.

   > [!NOTE]
   > Les contrôles hérités doivent être `Protected` pour pouvoir être ancrés. Pour modifier le niveau d’accès d’un contrôle, définissez sa propriété **modifier** dans la fenêtre **Propriétés** .

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
- [Guide pratique pour ancrer des contrôles enfants dans un contrôle FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Guide pratique pour ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Vue d’ensemble de la propriété AutoSize](autosize-property-overview.md)
- [Guide pratique pour ancrer des contrôles sur des Windows Forms](how-to-anchor-controls-on-windows-forms.md)
