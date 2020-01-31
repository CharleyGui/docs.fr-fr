---
title: Héberger un contrôle ActiveX dans WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: f2d9345eaaba7b85a217e6b230ae202f27ad3af8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742626"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Procédure pas à pas : hébergement d'un contrôle ActiveX dans WPF
Pour permettre une meilleure interaction avec les navigateurs, vous pouvez utiliser les contrôles Microsoft ActiveX dans votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette procédure pas à pas montre comment vous pouvez héberger le lecteur Microsoft Windows Media comme un contrôle sur une page de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du projet.

- Création du contrôle ActiveX.

- Hébergement du contrôle ActiveX sur une page WPF.

 Une fois cette procédure pas à pas terminée, vous comprendrez comment utiliser les contrôles Microsoft ActiveX dans votre application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

## <a name="prerequisites"></a>Prerequisites
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Lecteur Microsoft Windows Media installé sur l’ordinateur sur lequel Visual Studio est installé.

- Visual Studio 2010.

## <a name="creating-the-project"></a>Création du projet

### <a name="to-create-and-set-up-the-project"></a>Pour créer et configurer le projet

1. Créez un projet d’application WPF nommé `HostingAxInWpf`.

2. Ajoutez un projet de bibliothèque de contrôles Windows Forms à la solution et nommez le projet `WmpAxLib`.

3. Dans le projet WmpAxLib, ajoutez une référence à l’assembly du lecteur Windows Media, nommé wmp. dll.

4. Ouvrez la **boîte à outils**.

5. Cliquez avec le bouton droit dans la **boîte à outils**, puis cliquez sur **choisir les éléments**.

6. Cliquez sur l’onglet **composants com** , sélectionnez le contrôle du **lecteur Windows Media** , puis cliquez sur **OK**.

     Le contrôle du lecteur Windows Media est ajouté à la **boîte à outils**.

7. Dans Explorateur de solutions, cliquez avec le bouton droit sur le fichier **UserControl1** , puis cliquez sur **Renommer**.

8. Remplacez le nom par `WmpAxControl.vb` ou `WmpAxControl.cs`, en fonction de la langue.

9. Si vous êtes invité à renommer toutes les références, cliquez sur **Oui**.

## <a name="creating-the-activex-control"></a>Création du contrôle ActiveX
Visual Studio génère automatiquement une classe wrapper <xref:System.Windows.Forms.AxHost> pour un contrôle Microsoft ActiveX lorsque le contrôle est ajouté à une aire de conception. La procédure suivante crée un assembly managé nommé AxInterop. WMPLib. dll.

### <a name="to-create-the-activex-control"></a>Pour créer le contrôle ActiveX

1. Ouvrez WmpAxControl. vb ou WmpAxControl.cs dans le Concepteur Windows Forms.

2. À partir de la **boîte à outils**, ajoutez le contrôle du lecteur Windows Media à l’aire de conception.

3. Dans la Fenêtre Propriétés, définissez la valeur de la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle du lecteur Windows Media sur <xref:System.Windows.Forms.DockStyle.Fill>.

4. Générez le projet de bibliothèque de contrôles WmpAxLib.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hébergement du contrôle ActiveX sur une page WPF

### <a name="to-host-the-activex-control"></a>Pour héberger le contrôle ActiveX

1. Dans le projet HostingAxInWpf, ajoutez une référence à l’assembly d’interopérabilité ActiveX généré.

     Cet assembly se nomme AxInterop. WMPLib. dll et a été ajouté au dossier de débogage du projet WmpAxLib lorsque vous avez importé le contrôle du lecteur Windows Media.

2. Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration. dll.

3. Ajoutez une référence à l’assembly [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], nommé System. Windows. Forms. dll.

4. Ouvrez MainWindow. xaml dans le Concepteur WPF.

5. Nommez l’élément <xref:System.Windows.Controls.Grid> `grid1`.

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. En Mode Création ou en mode XAML, sélectionnez l’élément <xref:System.Windows.Window>.

7. Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .

8. Double-cliquez sur l’événement <xref:System.Windows.FrameworkElement.Loaded>.

9. Insérez le code suivant pour gérer l’événement <xref:System.Windows.FrameworkElement.Loaded>.

     Ce code crée une instance du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> et ajoute une instance du contrôle `AxWindowsMediaPlayer` en tant qu’enfant.

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Appuyez sur F5 pour générer et exécuter l'application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
