---
title: Héberger un contrôle de Windows Forms dans WPF
description: Découvrez comment héberger des contrôles de Windows Forms dans Windows Presentation Foundation, qui fournit déjà de nombreux contrôles avec un ensemble de fonctionnalités enrichi.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164975"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit de nombreux contrôles avec un ensemble complet de fonctionnalités. Toutefois, vous souhaiterez peut-être parfois utiliser des contrôles de Windows Forms dans vos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages. Par exemple, vous pouvez avoir un investissement important dans les contrôles de Windows Forms existants, ou vous pouvez avoir un contrôle Windows Forms qui fournit des fonctionnalités uniques.

Cette procédure pas à pas vous montre comment héberger un <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> contrôle de Windows Forms sur une [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page à l’aide de code.

Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle de Windows Forms dans l’exemple WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="hosting-the-windows-forms-control"></a>Hébergement d’un contrôle Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>Pour héberger le contrôle MaskedTextBox

1. Créez un projet d’application WPF nommé `HostingWfInWpf` .

2. Ajoutez les références aux assemblys suivants.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Ouvrez MainWindow. xaml dans le Concepteur WPF.

4. Nommez l' <xref:System.Windows.Controls.Grid> élément `grid1` .

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. En Mode Création ou en mode XAML, sélectionnez l' <xref:System.Windows.Window> élément.

6. Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .

7. Double-cliquez sur l' <xref:System.Windows.FrameworkElement.Loaded> événement.

8. Insérez le code suivant pour gérer l' <xref:System.Windows.FrameworkElement.Loaded> événement.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. En haut du fichier, ajoutez l' `Imports` instruction ou suivante `using` .

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Appuyez sur **F5** pour générer et exécuter l’application.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF à l’aide de XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Procédure pas à pas : hébergement d’un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : hébergement d’un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Contrôles Windows Forms et contrôles WPF équivalents](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hébergement d’un contrôle Windows Forms dans WPF, exemple](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
