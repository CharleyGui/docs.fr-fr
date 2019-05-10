---
title: 'Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: af5a0d58e789e609a25aa828493a3b0722cc83e1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64605476"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit de nombreux contrôles avec un ensemble complet de fonctionnalités. Toutefois, vous souhaiterez parfois utiliser [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle sur votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages. Par exemple, avoir un investissement substantiel dans existant [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôles, ou vous pouvez avoir un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle qui fournit des fonctionnalités uniques.

Cette procédure pas à pas vous montre comment héberger un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control sur un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page à l’aide de code.

Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle de formulaires Windows dans WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=160057).

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="hosting-the-windows-forms-control"></a>Hébergement d’un contrôle Windows Forms

### <a name="to-host-the-maskedtextbox-control"></a>Pour héberger le contrôle MaskedTextBox

1. Créez un projet d’Application WPF nommé `HostingWfInWpf`.

2. Ajoutez les références aux assemblys suivants.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Ouvrez MainWindow.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

4. Nom de la <xref:System.Windows.Controls.Grid> élément `grid1`.

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. Dans le mode Création ou XAML, sélectionnez le <xref:System.Windows.Window> élément.

6. Dans la fenêtre Propriétés, cliquez sur le **événements** onglet.

7. Double-cliquez sur le <xref:System.Windows.FrameworkElement.Loaded> événement.

8. Insérez le code suivant pour gérer les <xref:System.Windows.FrameworkElement.Loaded> événement.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. En haut du fichier, ajoutez le code suivant `Imports` ou `using` instruction.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Appuyez sur **F5** pour générer et exécuter l’application.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Procédure pas à pas : Hébergement d’un contrôle de formulaires Windows dans WPF à l’aide de XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Procédure pas à pas : Hébergement d’un contrôle Composite de formulaires Windows dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d’un contrôle Composite WPF dans les Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Contrôles Windows Forms et contrôles WPF équivalents](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hébergement d’un contrôle Windows Forms dans WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=160057)
