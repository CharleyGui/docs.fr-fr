---
title: 'Procédure pas à pas : organiser le contenu WPF dans Windows Forms au moment du design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658527"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a>Procédure pas à pas : Organiser le contenu WPF sur Windows Forms au moment du design

Cet article explique comment utiliser les fonctionnalités de disposition Windows Forms, telles que l’ancrage et les lignes d’alignement, pour réorganiser les contrôles Windows Presentation Foundation (WPF).

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-project"></a>Créer le projet

Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel `ArrangeElementHost`nommé.

> [!NOTE]
> Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.

## <a name="create-the-wpf-control"></a>Créer le contrôle WPF

Après avoir ajouté un contrôle WPF au projet, vous pouvez le disposer sur le formulaire.

1. Ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF au projet. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un contenu WPF sur Windows Forms au moment](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de la conception.

2. En mode Design, assurez-vous que `UserControl1` est sélectionné.

3. Dans la fenêtre **Propriétés** , affectez à la valeur <xref:System.Windows.FrameworkElement.Width%2A> des <xref:System.Windows.FrameworkElement.Height%2A> propriétés et la valeur **200**.

4. Affectez à la <xref:System.Windows.Controls.Control.Background%2A> propriété la valeur **Blue**.

5. Générez le projet.

## <a name="host-wpf-controls-in-a-layout-panel"></a>Héberger des contrôles WPF dans un panneau de disposition

Vous pouvez utiliser des contrôles WPF dans des panneaux de disposition de la même façon que vous utilisez d'autres contrôles Windows Forms.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

2. Dans la **boîte à outils**, <xref:System.Windows.Forms.TableLayoutPanel> faites glisser un contrôle sur le formulaire.

3. Dans le <xref:System.Windows.Forms.TableLayoutPanel> panneau des balises actives du contrôle, sélectionnez **Supprimer la dernière ligne**.

4. Augmentez la largeur et la hauteur du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

5. Dans la **boîte à outils**, double `UserControl1` -cliquez sur pour créer `UserControl1` une instance de dans la première <xref:System.Windows.Forms.TableLayoutPanel> cellule du contrôle.

   L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

6. Dans la **boîte à outils**, double `UserControl1` -cliquez sur pour créer une autre instance dans la <xref:System.Windows.Forms.TableLayoutPanel> deuxième cellule du contrôle.

7. Dans la fenêtre **structure du document** , `tableLayoutPanel1`sélectionnez.

8. Dans la fenêtre **Propriétés** , affectez à la <xref:System.Windows.Forms.Control.Padding%2A> propriété la valeur **10, 10,** 10, 10.

   Les deux contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés pour s'adapter à la nouvelle disposition.

## <a name="use-snaplines-to-align-wpf-controls"></a>Utiliser des lignes d’alignement pour aligner les contrôles WPF

Les lignes d'alignement permettent d'aligner facilement les contrôles sur un formulaire. Vous pouvez aussi utiliser des lignes d'alignement pour aligner vos contrôles WPF. Pour plus d’informations, consultez [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)l’aide des lignes d’alignement.

1. À partir de la **boîte à outils**, `UserControl1` faites glisser une instance de sur le formulaire, puis placez- <xref:System.Windows.Forms.TableLayoutPanel> la dans l’espace sous le contrôle.

   L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost3`.

2. À l'aide des lignes d'alignement, alignez le bord gauche de `elementHost3` avec le bord gauche du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

3. À l'aide des lignes d'alignement, affectez à `elementHost3` la même largeur que celle du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

4. Déplacez `elementHost3` vers le contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce qu'une ligne d'alignement centrale apparaisse entre les contrôles.

5. Dans la fenêtre **Propriétés** , affectez à la propriété Margin la valeur **20, 20, 20, 20**.

6. Déplacez le `elementHost3` hors du contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce que la ligne d'alignement centrale réapparaisse. La ligne d'alignement centrale indique maintenant une marge de 20.

7. Se `elementHost3` déplacer vers la droite jusqu’à ce que son bord gauche s’aligne avec `elementHost1`le bord gauche de.

8. Modifiez la largeur de `elementHost3` jusqu'à ce que son bord droit soit aligné avec le bord droit de `elementHost2`.

## <a name="anchor-and-dock-wpf-controls"></a>Ancrer et ancrer des contrôles WPF

Un contrôle WPF hébergé sur un formulaire a le même comportement d'ancrage que d'autres contrôles Windows Forms.

1. Sélectionnez `elementHost1`.

2. Dans la fenêtre **Propriétés** , affectez <xref:System.Windows.Forms.Control.Anchor%2A> à la propriété la valeur **haut, bas, gauche, droite**.

3. Agrandissez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

   Le contrôle `elementHost1` est redimensionné pour remplir la cellule.

4. Sélectionnez `elementHost2`.

5. Dans la fenêtre **Propriétés** , affectez à <xref:System.Windows.Forms.Control.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill>la propriété la valeur.

   Le contrôle `elementHost2` est redimensionné pour remplir la cellule.

6. Sélectionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

7. Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Top>.

8. Sélectionnez `elementHost3`.

9. Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.

   Le contrôle `elementHost3` est redimensionné pour remplir l'espace restant sur le formulaire.

10. Redimensionnez le formulaire.

    Les trois contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés correctement.

    Pour plus d'informations, voir [Procédure : Ancrer et ancrer des contrôles enfants dans](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)un contrôle TableLayoutPanel.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Guide pratique pour Ancrer et ancrer des contrôles enfants dans un contrôle TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Guide pratique pour Aligner un contrôle sur les bords des formulaires au moment du design](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide de lignes d’alignement](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
