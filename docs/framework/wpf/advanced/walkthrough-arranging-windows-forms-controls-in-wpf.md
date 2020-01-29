---
title: Organiser les contrôles Windows Forms dans WPF
titleSuffix: ''
ms.date: 04/03/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- arranging controls [WPF]
ms.assetid: a1db8049-15c7-45d6-ae3d-36a6735cb848
ms.openlocfilehash: 5e7544dfdbee234bb968c9a7f39814e8749ece15
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735284"
---
# <a name="walkthrough-arranging-windows-forms-controls-in-wpf"></a>Procédure pas à pas : organisation des contrôles Windows Forms dans WPF

Cette procédure pas à pas vous montre comment utiliser [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalités de disposition pour organiser des contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans une application hybride.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du projet.
- Utilisation des paramètres de disposition par défaut
- Dimensionnement en fonction du contenu
- Utilisation du positionnement absolu
- Spécification explicite de la taille
- Définition des propriétés de disposition
- Présentation des limitations dans l’ordre de plan
- Ancrage
- Définition de la visibilité
- Hébergement d’un contrôle qui ne s’étire pas
- Scaling (mise à l'échelle).
- Rotation
- Définition d’une marge intérieure et de marges
- Utilisation de conteneurs de présentation dynamiques

Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [réorganisation des contrôles de Windows Forms dans l’exemple WPF](https://go.microsoft.com/fwlink/?LinkID=159971).

Lorsque vous aurez terminé, vous aurez une compréhension des fonctionnalités de disposition [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] dans les applications basées sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

## <a name="prerequisites"></a>Prerequisites

Cette procédure pas à pas nécessite Visual Studio.

## <a name="creating-the-project"></a>Création du projet

Pour créer et configurer le projet, procédez comme suit :

1. Créez un projet d’application WPF nommé `WpfLayoutHostingWf`.

2. Dans Explorateur de solutions, ajoutez des références aux assemblys suivants :

    - WindowsFormsIntegration
    - System.Windows.Forms
    - System.Drawing

3. Double-cliquez sur *MainWindow. Xaml* pour l’ouvrir en mode XAML.

4. Dans l’élément <xref:System.Windows.Window>, ajoutez le mappage d’espace de noms [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] suivant.

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. Dans l’élément <xref:System.Windows.Controls.Grid> affectez à la propriété <xref:System.Windows.Controls.Grid.ShowGridLines%2A> la valeur `true` et définissez cinq lignes et trois colonnes.

     [!code-xaml[WpfLayoutHostingWfWithXaml#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#2)]

## <a name="using-default-layout-settings"></a>Utilisation des paramètres de disposition par défaut

Par défaut, l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> gère la disposition du contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé.

Pour utiliser les paramètres de disposition par défaut, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#3)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. Le contrôle de <xref:System.Windows.Forms.Button?displayProperty=nameWithType> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] s’affiche dans le <xref:System.Windows.Controls.Canvas>. Le contrôle hébergé est dimensionné en fonction de son contenu, et l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est dimensionné pour s’adapter au contrôle hébergé.

## <a name="sizing-to-content"></a>Dimensionnement en fonction du contenu

L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> garantit que le contrôle hébergé est dimensionné pour afficher correctement son contenu.

Pour ajuster au contenu, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#4)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. Les deux contrôles de bouton sont dimensionnés pour afficher la chaîne de texte la plus longue et la taille de police supérieure correctement, et les éléments de <xref:System.Windows.Forms.Integration.WindowsFormsHost> sont redimensionnés pour s’adapter aux contrôles hébergés.

## <a name="using-absolute-positioning"></a>Utilisation du positionnement absolu

Vous pouvez utiliser le positionnement absolu pour placer l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> n’importe où dans l’interface utilisateur.

Pour utiliser le positionnement absolu, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#5)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est placé à 20 pixels du bord supérieur de la cellule de la grille et à 20 pixels à partir de la gauche.

## <a name="specifying-size-explicitly"></a>Spécification explicite de la taille

Vous pouvez spécifier la taille de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> à l’aide des propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.

Pour spécifier explicitement la taille, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#6)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est défini sur une taille de 50 pixels de large par 70 pixels de haut, ce qui est plus petit que les paramètres de disposition par défaut. Le contenu du contrôle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est réorganisé en conséquence.

## <a name="setting-layout-properties"></a>Définition des propriétés de disposition

Définissez toujours les propriétés relatives à la disposition sur le contrôle hébergé à l’aide des propriétés de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Si vous définissez les propriétés de disposition directement sur le contrôle hébergé, vous obtiendrez des résultats inattendus.

 La définition des propriétés relatives à la disposition sur le contrôle hébergé dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] n’a aucun effet.

Pour voir les effets de la définition des propriétés sur le contrôle hébergé, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#7)]

2. Dans **Explorateur de solutions**, double-cliquez sur *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs* pour l’ouvrir dans l’éditeur de code.

3. Copiez le code suivant dans la définition de classe `MainWindow` :

     [!code-csharp[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#101)]
     [!code-vb[WpfLayoutHostingWfWithXaml#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#101)]

4. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.

5. Cliquez sur le bouton **cliquez sur moi** . Le gestionnaire d’événements `button1_Click` définit les propriétés de <xref:System.Windows.Forms.Control.Top%2A> et de <xref:System.Windows.Forms.Control.Left%2A> sur le contrôle hébergé. Le contrôle hébergé est alors repositionné dans l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>. L’hôte conserve la même zone d’écran, mais le contrôle hébergé est découpé. Au lieu de cela, le contrôle hébergé doit toujours remplir l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

## <a name="understanding-z-order-limitations"></a>Présentation des limitations dans l’ordre de plan

Les éléments <xref:System.Windows.Forms.Integration.WindowsFormsHost> visibles sont toujours dessinés par-dessus d’autres éléments WPF et ne sont pas affectés par l’ordre de plan. Pour voir ce comportement de l’ordre de plan, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#8)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est peint sur l’élément label.

## <a name="docking"></a>Docking

<xref:System.Windows.Forms.Integration.WindowsFormsHost> élément prend en charge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ancrage. Définissez la <xref:System.Windows.Controls.DockPanel.Dock%2A> propriété jointe pour ancrer le contrôle hébergé dans un élément <xref:System.Windows.Controls.DockPanel>.

Pour ancrer un contrôle hébergé, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#9](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#9)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est ancré à droite de l’élément <xref:System.Windows.Controls.DockPanel>.

## <a name="setting-visibility"></a>Définition de la visibilité

Vous pouvez rendre votre contrôle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] invisible ou le réduire en définissant la propriété <xref:System.Windows.UIElement.Visibility%2A> sur l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>. Quand un contrôle est invisible, il n’est pas affiché, mais il occupe l’espace de disposition. Quand un contrôle est réduit, il n’est pas affiché et n’occupe pas l’espace de disposition.

Pour définir la visibilité d’un contrôle hébergé, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#10](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#10)]

2. Dans *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs*, copiez le code suivant dans la définition de classe :

     [!code-csharp[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#102)]
     [!code-vb[WpfLayoutHostingWfWithXaml#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#102)]

3. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application.

4. Cliquez sur le bouton **Cliquer pour rendre invisible** pour rendre l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> invisible.

5. Cliquez sur le bouton **Cliquer pour réduire** pour masquer complètement l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> de la disposition. Lorsque le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] est réduit, les éléments environnants sont réorganisés pour occuper l’espace.

## <a name="hosting-a-control-that-does-not-stretch"></a>Hébergement d’un contrôle qui ne s’étire pas

Certains contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ont une taille fixe et ne sont pas étirés pour remplir l’espace disponible dans la disposition. Par exemple, le contrôle <xref:System.Windows.Forms.MonthCalendar> affiche un mois dans un espace fixe.

Pour héberger un contrôle qui ne s’étire pas, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#11)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> est centré dans la ligne de la grille, mais il n’est pas étiré pour remplir l’espace disponible. Si la fenêtre est suffisamment grande, vous pouvez voir deux mois ou plus affichés par le contrôle <xref:System.Windows.Forms.MonthCalendar> hébergé, mais ceux-ci sont centrés sur la ligne. Le moteur de disposition [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Centre les éléments qui ne peuvent pas être dimensionnés pour remplir l’espace disponible.

## <a name="scaling"></a>Mise à l'échelle

Contrairement aux éléments WPF, la plupart des contrôles Windows Forms ne sont pas continuellement évolutifs. Pour fournir une mise à l’échelle personnalisée, vous devez substituer la méthode <xref:System.Windows.Forms.Integration.WindowsFormsHost.ScaleChild%2A?displayProperty=nameWithType>.

Pour mettre à l’échelle un contrôle hébergé à l’aide du comportement par défaut, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#12)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. Le contrôle hébergé et ses éléments voisins sont mis à l’échelle par un facteur de 0,5. Toutefois, la police du contrôle hébergé n’est pas mise à l’échelle.

<!-- This could use an example of custom scaling. -->

## <a name="rotating"></a>Rotation

Contrairement aux éléments WPF, les contrôles Windows Forms ne prennent pas en charge la rotation. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> ne pivote pas avec d’autres éléments WPF lorsqu’une transformation de rotation est appliquée. Toute valeur de rotation autre que 180 degrés déclenche l’événement <xref:System.Windows.Forms.Integration.WindowsFormsHost.LayoutError>.

Pour voir l’effet de la rotation dans une application hybride, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#13)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. Le contrôle hébergé ne pivote pas, mais ses éléments voisins subissent une rotation de 180 degrés. Vous devrez peut-être redimensionner la fenêtre pour apercevoir les éléments.

## <a name="setting-padding-and-margins"></a>Définition d’une marge intérieure et de marges

La marge intérieure et les marges dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] disposition sont similaires à la marge intérieure et aux marges dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]. Définissez simplement les propriétés <xref:System.Windows.Controls.Control.Padding%2A> et <xref:System.Windows.FrameworkElement.Margin%2A> sur l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

Pour définir le remplissage et les marges d’un contrôle hébergé, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#14)]
    [!code-xaml[WpfLayoutHostingWfWithXaml#15](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#15)]

2. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. Les paramètres de marge intérieure et de marge sont appliqués aux contrôles [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergés de la même façon que dans [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].

## <a name="using-dynamic-layout-containers"></a>Utilisation de conteneurs de disposition dynamiques

[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] fournit deux conteneurs de disposition dynamique, <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel>. Vous pouvez également utiliser ces conteneurs dans des dispositions de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Pour utiliser un conteneur de disposition dynamique, procédez comme suit :

1. Copiez le code XAML suivant dans l’élément <xref:System.Windows.Controls.Grid> :

     [!code-xaml[WpfLayoutHostingWfWithXaml#16](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml#16)]

2. Dans *MainWindow. Xaml. vb* ou *MainWindow.Xaml.cs*, copiez le code suivant dans la définition de classe :

     [!code-csharp[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#103)]
     [!code-vb[WpfLayoutHostingWfWithXaml#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#103)]

3. Ajoutez un appel à la méthode `InitializeFlowLayoutPanel` dans le constructeur :

     [!code-csharp[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/csharp/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/CSharp/Window1.xaml.cs#104)]
     [!code-vb[WpfLayoutHostingWfWithXaml#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WpfLayoutHostingWfWithXaml/VisualBasic/Window1.xaml.vb#104)]

4. Appuyez sur <kbd>F5</kbd> pour générer et exécuter l’application. L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> remplit le <xref:System.Windows.Controls.DockPanel>et <xref:System.Windows.Forms.FlowLayoutPanel> réorganise ses contrôles enfants dans le <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>par défaut.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Considérations sur la disposition de l’élément WindowsFormsHost](layout-considerations-for-the-windowsformshost-element.md)
- [Organiser des contrôles de Windows Forms dans WPF, exemple](https://go.microsoft.com/fwlink/?LinkID=159971)
- [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
