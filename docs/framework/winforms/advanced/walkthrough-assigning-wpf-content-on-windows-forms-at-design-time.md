---
title: Sélectionner des contrôles WPF pour Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19f1dfec282b025f5a1fa367ec5fa9a52472c691
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746808"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Procédure pas à pas : assigner du contenu WPF sur Windows Forms au moment du design

Cet article vous montre comment sélectionner les types de contrôle Windows Presentation Foundation (WPF) que vous souhaitez afficher dans votre formulaire. Vous pouvez sélectionner n’importe quel type de contrôle WPF inclus dans votre projet.

## <a name="prerequisites"></a>Composants requis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-project"></a>Créer le projet

Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel nommé `SelectingWpfContent`.

> [!NOTE]
> Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.

## <a name="create-the-wpf-control-types"></a>Créer les types de contrôles WPF

Après avoir ajouté des types de contrôles WPF au projet, vous pouvez les héberger dans différents contrôles <xref:System.Windows.Forms.Integration.ElementHost>.

1. Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [procédure pas à pas : création de contenu WPF sur Windows Forms au moment du design](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).

2. En mode Design, assurez-vous que `UserControl1` est sélectionné.

3. Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.

4. Ajoutez un contrôle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> au <xref:System.Windows.Controls.UserControl> et définissez la valeur de la propriété <xref:System.Windows.Controls.TextBox.Text%2A> sur le **contenu hébergé**.

5. Ajoutez un deuxième <xref:System.Windows.Controls.UserControl> WPF au projet. Utilisez le nom par défaut pour le type de contrôle, `UserControl2.xaml`.

6. Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.

7. Ajoutez un contrôle de <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> au <xref:System.Windows.Controls.UserControl> et définissez la valeur de la propriété <xref:System.Windows.Controls.TextBox.Text%2A> sur le **contenu hébergé 2**.

   > [!NOTE]
   > En général, vous devez héberger du contenu WPF plus sophistiqué. Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> est utilisé ici uniquement à titre d'illustration.

8. créer le projet ;

## <a name="select-wpf-controls"></a>Sélectionner des contrôles WPF

Vous pouvez assigner du contenu WPF différent à un contrôle <xref:System.Windows.Forms.Integration.ElementHost> qui héberge déjà du contenu.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

2. Dans la **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` sur le formulaire.

   Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

3. Dans le panneau des balises actives pour `elementHost1`, ouvrez la liste déroulante **Sélectionner le contenu hébergé** .

4. Sélectionnez **UserControl2** dans la zone de liste déroulante.

   Le contrôle `elementHost1` héberge maintenant une instance du type `UserControl2`.

5. Dans la fenêtre **Propriétés** , vérifiez que la propriété <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> a la valeur **UserControl2**.

6. À partir de la **boîte à outils**, dans le groupe **interopérabilité WPF** , faites glisser un contrôle <xref:System.Windows.Forms.Integration.ElementHost> sur le formulaire.

   Le nom par défaut du nouveau contrôle est `elementHost2`.

7. Dans le panneau des balises actives pour `elementHost2`, ouvrez la liste déroulante **Sélectionner le contenu hébergé** .

8. Sélectionnez **UserControl1** dans la liste déroulante.

9. Le contrôle `elementHost2` héberge maintenant une instance du type `UserControl1`.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
