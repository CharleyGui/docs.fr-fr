---
title: Organiser le contenu WPF sur Windows Forms au moment du design
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5a6b12def45052e117fb149555946ea42d6cd3c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746819"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>Procédure pas à pas : organisation du contenu WPF sur Windows Forms au moment du design

Cet article explique comment utiliser les fonctionnalités de disposition Windows Forms, telles que l’ancrage et les lignes d’alignement, pour réorganiser les contrôles Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Prerequisites

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-project"></a>Créer le projet

Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel nommé `ArrangeElementHost`.

> [!NOTE]
> Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.

## <a name="create-the-wpf-control"></a>Créer le contrôle WPF

Après avoir ajouté un contrôle WPF au projet, vous pouvez le disposer sur le formulaire.

1. Ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF au projet. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [procédure pas à pas : création de contenu WPF sur Windows Forms au moment du design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. En mode Design, assurez-vous que `UserControl1` est sélectionné.

3. Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.

4. Affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur **Blue**.

5. créer le projet ;

## <a name="host-wpf-controls-in-a-layout-panel"></a>Héberger des contrôles WPF dans un panneau de disposition

Vous pouvez utiliser des contrôles WPF dans des panneaux de disposition de la même façon que vous utilisez d'autres contrôles Windows Forms.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

2. Dans la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> sur le formulaire.

3. Dans le panneau des balises actives du contrôle <xref:System.Windows.Forms.TableLayoutPanel>, sélectionnez **Supprimer la dernière ligne**.

4. Augmentez la largeur et la hauteur du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

5. Dans la **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` dans la première cellule du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

   L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

6. Dans la **boîte à outils**, double-cliquez sur `UserControl1` pour créer une autre instance dans la deuxième cellule du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

7. Dans la fenêtre **structure du document** , sélectionnez `tableLayoutPanel1`.

8. Dans la fenêtre **Propriétés** , définissez la valeur de la propriété <xref:System.Windows.Forms.Control.Padding%2A> sur **10, 10,** 10, 10.

   Les deux contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés pour s'adapter à la nouvelle disposition.

## <a name="use-snaplines-to-align-wpf-controls"></a>Utiliser des lignes d’alignement pour aligner les contrôles WPF

Les lignes d'alignement permettent d'aligner facilement les contrôles sur un formulaire. Vous pouvez aussi utiliser des lignes d'alignement pour aligner vos contrôles WPF. Pour plus d’informations, consultez [procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide des lignes d’alignement](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

1. À partir de la **boîte à outils**, faites glisser une instance de `UserControl1` sur le formulaire, puis placez-la dans l’espace sous le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

   L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost3`.

2. À l'aide des lignes d'alignement, alignez le bord gauche de `elementHost3` avec le bord gauche du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

3. À l'aide des lignes d'alignement, affectez à `elementHost3` la même largeur que celle du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

4. Déplacez `elementHost3` vers le contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce qu'une ligne d'alignement centrale apparaisse entre les contrôles.

5. Dans la fenêtre **Propriétés** , affectez à la propriété Margin la valeur **20, 20, 20, 20**.

6. Déplacez le `elementHost3` hors du contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce que la ligne d'alignement centrale réapparaisse. La ligne d'alignement centrale indique maintenant une marge de 20.

7. Déplacer `elementHost3` vers la droite jusqu’à ce que son bord gauche s’aligne avec le bord gauche de `elementHost1`.

8. Modifiez la largeur de `elementHost3` jusqu'à ce que son bord droit soit aligné avec le bord droit de `elementHost2`.

## <a name="anchor-and-dock-wpf-controls"></a>Ancrer et ancrer des contrôles WPF

Un contrôle WPF hébergé sur un formulaire a le même comportement d'ancrage que d'autres contrôles Windows Forms.

1. Sélectionnez `elementHost1`.

2. Dans la fenêtre **Propriétés** , affectez à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> la valeur **haut, bas, gauche, droite**.

3. Agrandissez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

   Le contrôle `elementHost1` est redimensionné pour remplir la cellule.

4. Sélectionnez `elementHost2`.

5. Dans la fenêtre **Propriétés** , définissez la valeur de la propriété <xref:System.Windows.Forms.Control.Dock%2A> sur <xref:System.Windows.Forms.DockStyle.Fill>.

   Le contrôle `elementHost2` est redimensionné pour remplir la cellule.

6. Sélectionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

7. Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Top>.

8. Sélectionnez `elementHost3`.

9. Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.

   Le contrôle `elementHost3` est redimensionné pour remplir l'espace restant sur le formulaire.

10. Redimensionnez le formulaire.

    Les trois contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés correctement.

    Pour plus d’informations, consultez [Comment : ancrer et ancrer des contrôles enfants dans un contrôle TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Guide pratique pour ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Guide pratique pour aligner un contrôle sur les bords des formulaires au moment du design](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
