---
title: 'Procédure pas à pas : hébergement d’un contrôle ActiveX dans WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 0181093de1c40889110ab7eae75a3847a17845a9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859934"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Procédure pas à pas : hébergement d’un contrôle ActiveX dans WPF
Pour permettre une interaction améliorée avec les navigateurs, vous pouvez utiliser des contrôles Microsoft ActiveX dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur. Cette procédure pas à pas montre comment vous pouvez héberger le [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] en tant que contrôle sur une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.

 Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du projet

- Création du contrôle ActiveX.

- Hébergement du contrôle ActiveX sur une Page WPF.

 Lorsque vous avez terminé cette procédure pas à pas, vous comprendrez comment utiliser des contrôles Microsoft ActiveX dans votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application basée sur.

## <a name="prerequisites"></a>Prérequis
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] installé sur l’ordinateur où Visual Studio est installé.

- Visual Studio 2010.

## <a name="creating-the-project"></a>Création du projet

### <a name="to-create-and-set-up-the-project"></a>Pour créer et configurer le projet

1. Créez un projet d’Application WPF nommé `HostingAxInWpf`.

2. Ajouter un projet de bibliothèque de contrôles Windows Forms à la solution, puis nommez le projet `WmpAxLib`.

3. Dans le projet WmpAxLib, ajoutez une référence à l’assembly Windows Media Player, nommé wmp.dll.

4. Ouvrez le **boîte à outils**.

5. Avec le bouton droit dans le **boîte à outils**, puis cliquez sur **choisir des éléments de**.

6. Cliquez sur le **composants COM** onglet, sélectionnez le **Windows Media Player** contrôler, puis cliquez sur **OK**.

     Le contrôle Windows Media Player est ajouté à la **boîte à outils**.

7. Dans l’Explorateur de solutions, cliquez sur le **UserControl1** de fichiers, puis cliquez sur **renommer**.

8. Remplacez le nom par `WmpAxControl.vb` ou `WmpAxControl.cs`, selon le langage.

9. Si vous êtes invité à renommer toutes les références, cliquez sur **Oui**.

## <a name="creating-the-activex-control"></a>Création du contrôle ActiveX
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] génère automatiquement un <xref:System.Windows.Forms.AxHost> classe wrapper pour un contrôle Microsoft ActiveX lorsque le contrôle est ajouté à une aire de conception. La procédure suivante crée un assembly managé nommé AxInterop.WMPLib.dll.

### <a name="to-create-the-activex-control"></a>Pour créer le contrôle ActiveX

1. Ouvrez WmpAxControl.cs ou WmpAxControl.vb dans le Concepteur de formulaires Windows.

2. À partir de la **boîte à outils**, ajoutez le contrôle Windows Media Player à l’aire de conception.

3. Dans la fenêtre Propriétés, définissez la valeur du contrôle Windows Media Player <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.

4. Générez le projet de bibliothèque de contrôle WmpAxLib.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Hébergement du contrôle ActiveX sur une Page WPF

### <a name="to-host-the-activex-control"></a>Pour héberger le contrôle ActiveX

1. Dans le projet HostingAxInWpf, ajoutez une référence à l’assembly d’interopérabilité ActiveX généré.

     Cet assembly est nommé AxInterop.WMPLib.dll et a été ajouté au dossier Debug du projet WmpAxLib lorsque vous avez importé le contrôle Windows Media Player.

2. Ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.

3. Ajoutez une référence à la [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly nommé System.Windows.Forms.dll.

4. Ouvrez MainWindow.xaml dans le Concepteur WPF.

5. Nom de la <xref:System.Windows.Controls.Grid> élément `grid1`.

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. Dans le mode Création ou XAML, sélectionnez le <xref:System.Windows.Window> élément.

7. Dans la fenêtre Propriétés, cliquez sur le **événements** onglet.

8. Double-cliquez sur le <xref:System.Windows.FrameworkElement.Loaded> événement.

9. Insérez le code suivant pour gérer les <xref:System.Windows.FrameworkElement.Loaded> événement.

     Ce code crée une instance de la <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôler et ajoute une instance de la `AxWindowsMediaPlayer` contrôle en tant qu’enfant.

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Appuyez sur F5 pour générer et exécuter l'application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Procédure pas à pas : Hébergement d’un contrôle Composite de formulaires Windows dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d’un contrôle Composite WPF dans les Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
