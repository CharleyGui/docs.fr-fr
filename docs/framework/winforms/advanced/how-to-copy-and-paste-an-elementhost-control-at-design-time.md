---
title: 'Procédure : copier et coller un contrôle ElementHost au moment du design'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 0f3367deaaec04744a3f812d7f2d08047d7eb588
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211387"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a>Procédure : copier et coller un contrôle ElementHost au moment du design

Cette procédure vous montre comment copier un contrôle Windows Presentation Foundation (WPF) sur un formulaire Windows dans Visual Studio.

## <a name="copy-and-paste-an-elementhost-control-at-design-time"></a>Copiez et collez un contrôle ElementHost au moment du design

1. Ajoutez un nouveau WPF <xref:System.Windows.Controls.UserControl> à votre projet Windows Forms. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [Procédure pas à pas : Création de contenu WPF dans les Windows Forms au moment du Design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés de `UserControl1` à `200`.

3. Affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur `Blue`.

4. Générez le projet.

5. Ouvrez `Form1` dans le Concepteur Windows Forms.

6. À partir de la **boîte à outils**, faites glisser une instance de `UserControl1` vers le formulaire.

   Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

7. `elementHost1` étant sélectionné, appuyez sur Ctrl+C pour le copier dans le Presse-papiers.

8. Appuyez sur CTRL + V pour coller le contrôle copié vers le formulaire.

   Un nouveau <xref:System.Windows.Forms.Integration.ElementHost> contrôle nommé `elementHost2` est créé sur le formulaire.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
