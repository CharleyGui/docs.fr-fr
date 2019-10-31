---
title: 'Comment : copier et coller un contrôle ElementHost au moment du design'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197482"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Comment : copier et coller un contrôle ElementHost

Cette procédure vous montre comment copier un contrôle Windows Presentation Foundation (WPF) sur un Windows Form dans Visual Studio.

1. Dans Visual Studio, ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF à un projet Windows Forms. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [procédure pas à pas : création de contenu WPF sur Windows Forms au moment du design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. Dans la fenêtre **Propriétés** , définissez la valeur des propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> de `UserControl1` sur **200**.

3. Affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur **Blue**.

4. Générez le projet.

5. Ouvrez `Form1` dans le Concepteur Windows Forms.

6. À partir de la **boîte à outils**, faites glisser une instance de `UserControl1` vers le formulaire.

   Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

7. Avec `elementHost1` sélectionné, appuyez sur **Ctrl**+**C** pour le copier dans le presse-papiers.

8. Appuyez sur **Ctrl**+**V** pour coller le contrôle copié dans le formulaire.

   Un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost2` est créé sur le formulaire.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
