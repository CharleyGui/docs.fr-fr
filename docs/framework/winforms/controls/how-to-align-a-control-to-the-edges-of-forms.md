---
title: 'Procédure : aligner un contrôle sur les bords des formulaires'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015943"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Procédure : aligner un contrôle sur les bords des formulaires

Vous pouvez aligner un contrôle sur le bord de vos formulaires en définissant la propriété <xref:System.Windows.Forms.Control.Dock%2A>. Cette propriété désigne l’emplacement de votre contrôle dans le formulaire. La propriété <xref:System.Windows.Forms.Control.Dock%2A> peut avoir les valeurs suivantes :

|Paramètre|Effet sur le contrôle|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|S'ancre en bas du formulaire.|
|<xref:System.Windows.Forms.DockStyle.Fill>|Remplit tout l'espace restant dans le formulaire.|
|<xref:System.Windows.Forms.DockStyle.Left>|S'ancre sur le côté gauche du formulaire.|
|<xref:System.Windows.Forms.DockStyle.None>|Ne s'ancre nulle part et apparaît à l'emplacement spécifié par sa propriété <xref:System.Windows.Forms.Control.Location%2A>.|
|<xref:System.Windows.Forms.DockStyle.Right>|S'ancre sur le côté droit du formulaire.|
|<xref:System.Windows.Forms.DockStyle.Top>|S'ancre en haut du formulaire.|

Cette fonctionnalité est prise en charge au moment du design dans Visual Studio.

## <a name="set-the-dock-property-for-your-control-at-run-time"></a>Définir la propriété Dock pour votre contrôle au moment de l’exécution

Affectez la valeur appropriée à la propriété <xref:System.Windows.Forms.Control.Dock%2A> dans le code.

```vb
' To set the Dock property internally.
Me.Dock = DockStyle.Top
' To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top
```

```csharp
// To set the Dock property internally.
this.Dock = DockStyle.Top;
// To set the Dock property from another object.
UserControl1.Dock = DockStyle.Top;
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
- [Guide pratique : Ancrer et ancrer des contrôles enfants dans un contrôle FlowLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [Guide pratique : Ancrer et ancrer des contrôles enfants dans un contrôle TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Vue d’ensemble de la propriété AutoSize](autosize-property-overview.md)
