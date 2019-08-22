---
title: 'Procédure pas à pas : Attribution de contenu WPF dans Windows Forms au moment du design'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5f5e2d8808c0a60df721bf2c0ed76b45ef49a0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666258"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>Procédure pas à pas : Assigner du contenu WPF sur Windows Forms au moment du design

Cet article vous montre comment sélectionner les types de contrôle Windows Presentation Foundation (WPF) que vous souhaitez afficher dans votre formulaire. Vous pouvez sélectionner tout type de contrôle WPF inclus dans votre projet.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-project"></a>Créer le projet

Ouvrez Visual Studio et créez un projet d’application Windows Forms dans Visual Basic ou un C# visuel `SelectingWpfContent`nommé.

> [!NOTE]
> Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.

## <a name="create-the-wpf-control-types"></a>Créer les types de contrôles WPF

Après avoir ajouté des types de contrôles WPF au projet, vous pouvez les héberger dans différents contrôles <xref:System.Windows.Forms.Integration.ElementHost>.

1. Ajoutez un nouveau projet <xref:System.Windows.Controls.UserControl> WPF à la solution. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [Procédure pas à pas : Création d’un contenu WPF sur Windows Forms au moment](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)de la conception.

2. En mode Design, assurez-vous que `UserControl1` est sélectionné.

3. Dans la fenêtre **Propriétés** , affectez à la valeur <xref:System.Windows.FrameworkElement.Width%2A> des <xref:System.Windows.FrameworkElement.Height%2A> propriétés et la valeur **200**.

4. Ajoutez un <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> <xref:System.Windows.Controls.UserControl> contrôle au et <xref:System.Windows.Controls.TextBox.Text%2A> affectez la valeur **contenu hébergé**à la propriété.

5. Ajoutez un deuxième <xref:System.Windows.Controls.UserControl> WPF au projet. Utilisez le nom par défaut pour le type de contrôle, `UserControl2.xaml`.

6. Dans la fenêtre **Propriétés** , affectez à la valeur <xref:System.Windows.FrameworkElement.Width%2A> des <xref:System.Windows.FrameworkElement.Height%2A> propriétés et la valeur **200**.

7. Ajoutez un <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> <xref:System.Windows.Controls.UserControl> contrôle au et <xref:System.Windows.Controls.TextBox.Text%2A> affectez la valeur **contenu hébergé 2**à la propriété.

   > [!NOTE]
   > En général, vous devez héberger du contenu WPF plus sophistiqué. Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> est utilisé ici uniquement à titre d'illustration.

8. Générez le projet.

## <a name="select-wpf-controls"></a>Sélectionner des contrôles WPF

Vous pouvez assigner du contenu WPF différent à un contrôle <xref:System.Windows.Forms.Integration.ElementHost> qui héberge déjà du contenu.

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

2. Dans la **boîte à outils**, double `UserControl1` -cliquez sur pour créer `UserControl1` une instance de sur le formulaire.

   Une instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.

3. Dans le panneau des balises `elementHost1`actives de, ouvrez la liste déroulante **Sélectionner le contenu hébergé** .

4. Sélectionnez **UserControl2** dans la zone de liste déroulante.

   Le contrôle `elementHost1` héberge maintenant une instance du type `UserControl2`.

5. Dans la fenêtre **Propriétés** , vérifiez que la <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> propriété a la valeur **UserControl2**.

6. À partir de la **boîte à outils**, dans le groupe interopérabilité <xref:System.Windows.Forms.Integration.ElementHost> **WPF** , faites glisser un contrôle sur le formulaire.

   Le nom par défaut du nouveau contrôle est `elementHost2`.

7. Dans le panneau des balises `elementHost2`actives de, ouvrez la liste déroulante **Sélectionner le contenu hébergé** .

8. Sélectionnez **UserControl1** dans la liste déroulante.

9. Le contrôle `elementHost2` héberge maintenant une instance du type `UserControl1`.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
