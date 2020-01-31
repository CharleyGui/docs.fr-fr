---
title: 'Comment : activer des styles visuels dans une application hybride'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
ms.openlocfilehash: dd52313e9100f9c6a1141b53ccc5a23a4b54410a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789918"
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a>Comment : activer des styles visuels dans une application hybride
Cette rubrique montre comment activer des styles visuels sur un contrôle de Windows Forms hébergé dans une application basée sur des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Si votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>, la plupart de vos contrôles Windows Forms utiliseront automatiquement les styles visuels. Pour plus d’informations, consultez [Rendu des contrôles avec les styles visuels](../../winforms/controls/rendering-controls-with-visual-styles.md).  
  
 Pour obtenir le code complet des tâches illustrées dans cette rubrique, consultez [activation de styles visuels dans un exemple d’application hybride](https://go.microsoft.com/fwlink/?LinkID=159986).  
  
## <a name="enabling-windows-forms-visual-styles"></a>Activation de styles visuels Windows Forms  
  
#### <a name="to-enable-windows-forms-visual-styles"></a>Pour activer les styles visuels Windows Forms  
  
1. Créez un projet d’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nommé `HostingWfWithVisualStyles`.  
  
2. Dans l’Explorateur de solutions, ajoutez des références aux assemblys suivants.  
  
    - WindowsFormsIntegration  
  
    - System.Windows.Forms  
  
3. Dans la boîte à outils, double-cliquez sur l’icône <xref:System.Windows.Controls.Grid> pour placer un élément <xref:System.Windows.Controls.Grid> sur l’aire de conception.  
  
4. Dans la Fenêtre Propriétés, définissez les valeurs des propriétés <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> sur **auto**.  
  
5. Dans Mode Création ou la vue XAML, sélectionnez l' <xref:System.Windows.Window>.  
  
6. Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .  
  
7. Double-cliquez sur l’événement <xref:System.Windows.FrameworkElement.Loaded>.
  
8. Dans MainWindow. Xaml. vb ou MainWindow.xaml.cs, insérez le code suivant pour gérer l’événement <xref:System.Windows.FrameworkElement.Loaded>.  
  
     [!code-csharp[HostingWfWithVisualStyles#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. Appuyez sur F5 pour générer et exécuter l'application.  
  
     Le contrôle Windows Forms est peint avec les styles visuels.  
  
## <a name="disabling-windows-forms-visual-styles"></a>Désactivation de styles visuels Windows Forms  
 Pour désactiver les styles visuels, supprimez simplement l’appel à la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
#### <a name="to-disable-windows-forms-visual-styles"></a>Pour désactiver les styles visuels Windows Forms  
  
1. Ouvrez MainWindow.xaml.vb ou MainWindow.xaml.cs dans l’éditeur de code.  
  
2. Commentez l’appel à la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  
  
3. Appuyez sur F5 pour générer et exécuter l'application.  
  
     Le contrôle Windows Forms est peint avec le style système par défaut.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>
- <xref:System.Windows.Forms.VisualStyles>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Rendu des contrôles avec les styles visuels](../../winforms/controls/rendering-controls-with-visual-styles.md)
- [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
