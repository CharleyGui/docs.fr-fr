---
title: 'Procédure : copier et coller un contrôle ElementHost au moment du design'
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
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666182"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a>Procédure : Copier et coller un contrôle ElementHost

Cette procédure vous montre comment copier un contrôle Windows Presentation Foundation (WPF) sur un Windows Form dans Visual Studio.

1. Dans Visual Studio, ajoutez un nouveau WPF <xref:System.Windows.Controls.UserControl> à un projet de Windows Forms. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un contenu WPF sur Windows Forms au moment](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de la conception.

2. Dans la fenêtre **Propriétés** , affectez à la valeur <xref:System.Windows.FrameworkElement.Width%2A> des <xref:System.Windows.FrameworkElement.Height%2A> propriétés et `UserControl1` de la valeur **200**.

3. Affectez à la <xref:System.Windows.Controls.Control.Background%2A> propriété la valeur **Blue**.

4. Générez le projet.

5. Ouvrez `Form1` dans le Concepteur Windows Forms.

6. À partir de la **boîte à outils**, `UserControl1` faites glisser une instance de sur le formulaire.

   Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

7. Avec `elementHost1` l’option sélectionné, appuyez sur **CTRL**+**C** pour le copier dans le presse-papiers.

8. Appuyez sur **CTRL**+**V** pour coller le contrôle copié dans le formulaire.

   Un nouveau <xref:System.Windows.Forms.Integration.ElementHost> contrôle nommé `elementHost2` est créé sur le formulaire.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
