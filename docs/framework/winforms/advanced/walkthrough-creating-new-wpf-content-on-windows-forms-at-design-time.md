---
title: Créer un contenu WPF sur Windows Forms
titleSuffix: ''
ms.date: 08/18/2018
helpviewer_keywords:
- interoperability [Windows Forms], WPF and Windows Forms
- WPF content [Windows Forms], hosting in Windows Forms
- hosting WPF content in Windows Forms
- ElementHost control
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 2e92d8e8-f0e4-4df7-9f07-2acf35cd798c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 69a0598b05d1b2bff84b203317d6d5a166ce109d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746390"
---
# <a name="walkthrough-create-new-wpf-content-on-windows-forms-at-design-time"></a>Procédure pas à pas : création d’un contenu WPF sur Windows Forms au moment du design

Cet article vous montre comment créer un contrôle Windows Presentation Foundation (WPF) à utiliser dans vos applications basées sur Windows Forms.

## <a name="prerequisites"></a>Prerequisites

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-project"></a>Créer le projet

Ouvrez Visual Studio et créez un projet d' **application Windows Forms (.NET Framework)** dans Visual Basic ou visual C# nommé `HostingWpf`.

> [!NOTE]
> Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.

## <a name="create-a-new-wpf-control"></a>Créer un contrôle WPF

La création d'un contrôle WPF et son ajout à votre projet sont des tâches aussi simples que l'ajout de tout autre élément à votre projet. Le Concepteur Windows Forms fonctionne avec un type particulier de contrôle nommé contrôle *composite*ou *contrôle utilisateur*. Pour plus d'informations sur les contrôles utilisateur WPF, consultez <xref:System.Windows.Controls.UserControl>.

> [!NOTE]
> Le type <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> pour WPF est distinct du type de contrôle utilisateur fourni par Windows Forms, également nommé <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>.

Pour créer un contrôle WPF :

1. Dans **Explorateur de solutions**, ajoutez un nouveau projet de **bibliothèque de contrôles utilisateur (.NET Framework) WPF** à la solution. Utilisez le nom par défaut pour la bibliothèque de contrôles, `WpfControlLibrary1`. Le nom du contrôle par défaut est `UserControl1.xaml`.

   L’ajout du nouveau contrôle a les effets suivants :

   - Le fichier UserControl1.xaml est ajouté.

   - Le fichier UserControl1.xaml.cs (ou UserControl1. Xaml. vb) est ajouté. Ce fichier contient le code-behind pour les gestionnaires d'événements et autre implémentation.

   - Les références aux assemblys WPF sont ajoutées.

   - Le fichier UserControl1. xaml s’ouvre dans le Concepteur WPF pour Visual Studio.

2. En mode Design, assurez-vous que `UserControl1` est sélectionné.

3. Dans la fenêtre **Propriétés** , affectez la valeur **200**aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.

4. À partir de la **boîte à outils**, faites glisser un contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> sur l’aire de conception.

5. Dans la fenêtre **Propriétés** , affectez la valeur **contenu hébergé**à la propriété <xref:System.Windows.Controls.TextBox.Text%2A>.

   > [!NOTE]
   > En général, vous devez héberger du contenu WPF plus sophistiqué. Le contrôle <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> est utilisé ici uniquement à titre d'illustration.

6. créer le projet ;

## <a name="add-a-wpf-control-to-a-windows-form"></a>Ajouter un contrôle WPF à un Windows Form

Votre nouveau contrôle WPF est prêt à être utilisé sur le formulaire. Windows Forms utilise le contrôle <xref:System.Windows.Forms.Integration.ElementHost> pour héberger du contenu WPF.

Pour ajouter un contrôle WPF à un Windows Form :

1. Ouvrez `Form1` dans le Concepteur Windows Forms.

2. Dans la **boîte à outils**, recherchez l’onglet nommé **contrôles utilisateur WPF WPFUserControlLibrary**.

3. Faites glisser une instance de `UserControl1` sur le formulaire.

    - Un contrôle <xref:System.Windows.Forms.Integration.ElementHost> est créé automatiquement sur le formulaire pour héberger le contrôle WPF.

    - Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> est nommé `elementHost1` et, dans la fenêtre **Propriétés** , vous pouvez voir que sa propriété <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> est définie sur **UserControl1**.

    - des références aux assemblys WPF sont ajoutées au projet.

    - Le contrôle `elementHost1` a un panneau de Smart Tags qui affiche les options d’hébergement disponibles.

4. Dans le panneau des balises actives des **Tâches ElementHost** , sélectionnez **ancrer dans le conteneur parent**.

5. Appuyez sur **F5** pour générer et exécuter l’application.

## <a name="next-steps"></a>Étapes suivantes :

Windows Forms et WPF sont des technologies différentes, mais elles sont conçues pour interagir étroitement. Pour fournir une apparence et un comportement plus riches dans vos applications, essayez ce qui suit :

- Hébergez un contrôle Windows Forms dans une page WPF. Pour plus d’informations, consultez [procédure pas à pas : Hébergement d’un contrôle de Windows Forms dans WPF](../../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).

- Appliquez des styles visuels Windows Forms à votre contenu WPF. Pour plus d’informations, consultez [Guide pratique pour activer des styles visuels dans une application hybride](../../wpf/advanced/how-to-enable-visual-styles-in-a-hybrid-application.md).

- Modifiez le style de votre contenu WPF. Pour plus d’informations, consultez [procédure pas à pas : stylisation du contenu WPF](walkthrough-styling-wpf-content.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Migration et interopérabilité](../../wpf/advanced/migration-and-interoperability.md)
- [Utilisation de contrôles WPF](using-wpf-controls.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
