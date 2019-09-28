---
title: 'Procédure pas à pas : hébergement d’un contrôle composite WPF 3D dans Windows Forms'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting WPF content in Windows Forms [WPF]
- composite controls [WPF], hosting WPF in
ms.assetid: 486369a9-606a-4a3b-b086-a06f2119c7b0
ms.openlocfilehash: a35f2b4062edb18914c55046a69dcd9b8825d778
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353843"
---
# <a name="walkthrough-hosting-a-3-d-wpf-composite-control-in-windows-forms"></a>Procédure pas à pas : hébergement d’un contrôle composite WPF 3D dans Windows Forms

Cette procédure pas à pas montre comment vous pouvez créer un contrôle composite [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et l’héberger dans des contrôles et des formulaires [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l’aide du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.

Dans cette procédure pas à pas, vous allez implémenter une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> qui contient deux contrôles enfants. La <xref:System.Windows.Controls.UserControl> affiche un cône tridimensionnel (3d). Le rendu des objets 3D est beaucoup plus facile avec le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qu’avec [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Par conséquent, il est logique d’héberger une classe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl> pour créer des graphiques 3D dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

- Création du projet Windows Forms Host.

- Hébergement du [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.UserControl>.

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Visual Studio 2017

<a name="To_Create_the_UserControl"></a>
## <a name="create-the-usercontrol"></a>Créer le UserControl

1. Créez un projet de **bibliothèque de contrôles utilisateur WPF** nommé `HostingWpfUserControlInWf`.

2. Ouvrez UserControl1. xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

3. Remplacez le code généré par le code suivant :

     [!code-xaml[HostingWpfUserControlInWf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]

     Ce code définit un <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType> qui contient deux contrôles enfants. Le premier contrôle enfant est un contrôle <xref:System.Windows.Controls.Label?displayProperty=nameWithType> ; le deuxième est un contrôle <xref:System.Windows.Controls.Viewport3D> qui affiche un cône 3D.

<a name="To_Create_the_Windows_Forms_Host_Project"></a>
## <a name="create-the-host-project"></a>Créer le projet hôte

1. Ajoutez un projet **Windows Forms App (.NET Framework)** nommé `WpfUserControlHost` à la solution.

2. Dans **Explorateur de solutions**, ajoutez une référence à l’assembly windowsformsintegration, nommé windowsformsintegration. dll.

3. Ajoutez des références aux assemblys [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivants :

    - PresentationCore

    - PresentationFramework

    - WindowsBase

4. Ajoutez au projet une référence à `HostingWpfUserControlInWf`.

5. Dans Explorateur de solutions, définissez le projet `WpfUserControlHost` comme projet de démarrage.

<a name="To_Host_the_Windows_Presentation_Foundation"></a>
## <a name="host-the-usercontrol"></a>Héberger le UserControl

1. Dans le Concepteur Windows Forms, ouvrez Form1.

2. Dans l’Fenêtre Propriétés, cliquez sur **événements**, puis double-cliquez sur l’événement <xref:System.Windows.Forms.Form.Load> pour créer un gestionnaire d’événements.

     L’éditeur de code s’ouvre sur le gestionnaire d’événements `Form1_Load` qui vient d’être généré.

3. Remplacez le code dans Form1.cs par le code suivant.

     Le gestionnaire d’événements `Form1_Load` crée une instance de `UserControl1` et ajoute afin à la collection de contrôles enfants du contrôle <xref:System.Windows.Forms.Integration.ElementHost>. Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> est ajouté à la collection de contrôles enfants du formulaire.

     [!code-csharp[HostingWpfUserControlInWf#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/WpfUserControlHost/Form1.cs#10)]
     [!code-vb[HostingWpfUserControlInWf#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWpfUserControlInWf/VisualBasic/WpfUserControlHost/Form1.vb#10)]

4. Appuyez sur **F5** pour générer et exécuter l’application.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Procédure pas à pas : Hébergement d’un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Procédure pas à pas : Hébergement d’un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Hébergement d’un contrôle composite WPF dans Windows Forms exemple](https://go.microsoft.com/fwlink/?LinkID=160001)
