---
title: Héberger un contrôle de Windows Forms dans WPF à l’aide de XAML
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 2c5764ac2dfd9f5747087cc76e3971c002f12b90
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794189"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a>Procédure pas à pas : hébergement d'un contrôle Windows Forms dans WPF avec XAML
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit de nombreux contrôles avec un ensemble complet de fonctionnalités. Toutefois, vous souhaiterez peut-être parfois utiliser des contrôles de Windows Forms sur vos pages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Par exemple, vous pouvez avoir un investissement important dans les contrôles de Windows Forms existants, ou vous pouvez avoir un contrôle Windows Forms qui fournit des fonctionnalités uniques.  
  
 Cette procédure pas à pas vous montre comment héberger un contrôle Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> sur une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [hébergement d’un contrôle de Windows Forms dans WPF à l’aide de l’exemple XAML](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWpfWithXaml).
  
## <a name="prerequisites"></a>Prerequisites  

Cette procédure pas à pas nécessite Visual Studio.  
  
## <a name="hosting-the-windows-forms-control"></a>Hébergement d’un contrôle Windows Forms  
  
#### <a name="to-host-the-maskedtextbox-control"></a>Pour héberger le contrôle MaskedTextBox  
  
1. Créez un projet d’application WPF nommé `HostingWfInWpfWithXaml`.  
  
2. Ajoutez les références aux assemblys suivants.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. Ouvrez MainWindow. xaml dans le Concepteur WPF.  
  
4. Dans l’élément <xref:System.Windows.Window>, ajoutez le mappage d’espace de noms suivant. Le mappage d’espace de noms `wf` établit une référence à l’assembly qui contient le contrôle Windows Forms.  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5. Dans l’élément <xref:System.Windows.Controls.Grid>, ajoutez le code XAML suivant.  
  
     Le contrôle <xref:System.Windows.Forms.MaskedTextBox> est créé en tant qu’enfant du contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6. Appuyez sur F5 pour générer et exécuter l'application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Contrôles Windows Forms et contrôles WPF équivalents](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Hébergement d’un contrôle de Windows Forms dans WPF à l’aide de XAML, exemple](https://go.microsoft.com/fwlink/?LinkID=160000)
