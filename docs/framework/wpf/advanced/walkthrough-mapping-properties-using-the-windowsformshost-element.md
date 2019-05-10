---
title: 'Procédure pas à pas : mappage de propriétés à l’aide de l’élément WindowsFormsHost'
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: a7c36e8fc150fe3268120ed728f1bed87d24e800
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623585"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Procédure pas à pas : mappage de propriétés à l’aide de l’élément WindowsFormsHost

Cette procédure pas à pas vous montre comment utiliser le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> propriété à mapper [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés aux propriétés correspondantes dans un hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du projet.

- Définition de la disposition de l’application.

- Définition d’un nouveau mappage de propriété.

- Suppression d’un mappage de propriété par défaut.

- Remplacement d’un mappage de propriété par défaut.

- Extension d’un mappage de propriété par défaut.

Pour l’intégralité du code des tâches illustrées dans cette procédure pas à pas, consultez [propriétés de mappage à l’aide de l’exemple d’élément WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).

Lorsque vous avez terminé, vous serez en mesure de mapper [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés aux propriétés correspondantes dans un hébergé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Créer et configurer le projet

1. Créer un **application WPF** projet nommé `PropertyMappingWithWfhSample`.

2. Dans **l’Explorateur de solutions**, ajoutez une référence à l’assembly WindowsFormsIntegration, nommé WindowsFormsIntegration.dll.

3. Dans **l’Explorateur de solutions**, ajoutez des références aux assemblys System.Drawing et System.Windows.Forms.

## <a name="defining-the-application-layout"></a>Définition de la disposition de l’application

Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-application utilise le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément pour héberger un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] contrôle.

### <a name="to-define-the-application-layout"></a>Pour définir la disposition de l’application

1. Ouvrez Window1.xaml dans le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].

2. Remplacez le code existant par le code ci-dessous.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. Ouvrez Window1.xaml.cs dans l’éditeur de code.

4. En haut du fichier, importez les espaces de noms suivants.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Définition d’un nouveau mappage de propriété

Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément fournit par défaut plusieurs mappages de propriété. Vous ajoutez un nouveau mappage de propriété en appelant le <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> méthode sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-define-a-new-property-mapping"></a>Pour définir un nouveau mappage de propriété

- Copiez le code suivant dans la définition de la `Window1` classe.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     Le `AddClipMapping` méthode ajoute un nouveau mappage pour le <xref:System.Windows.UIElement.Clip%2A> propriété.

     Le `OnClipChange` méthode se traduit par la <xref:System.Windows.UIElement.Clip%2A> propriété le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.Region%2A> propriété.

     Le `Window1_SizeChanged` méthode gère la fenêtre <xref:System.Windows.FrameworkElement.SizeChanged> événements et de la taille de la zone de découpage pour s’ajuster à la fenêtre d’application.

## <a name="removing-a-default-property-mapping"></a>Suppression d’un mappage de propriété par défaut

Supprimer un mappage de propriété par défaut en appelant le <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> méthode sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-remove-a-default-property-mapping"></a>Pour supprimer un mappage de propriété par défaut

- Copiez le code suivant dans la définition de la `Window1` classe.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     Le `RemoveCursorMapping` méthode supprime le mappage par défaut pour le <xref:System.Windows.FrameworkElement.Cursor%2A> propriété.

## <a name="replacing-a-default-property-mapping"></a>Remplacement d’un mappage de propriété par défaut

Remplacez un mappage de propriété par défaut en supprimant le mappage par défaut et en appelant le <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> méthode sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>.

### <a name="to-replace-a-default-property-mapping"></a>Pour remplacer un mappage de propriété par défaut

- Copiez le code suivant dans la définition de la `Window1` classe.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     Le `ReplaceFlowDirectionMapping` méthode remplace le mappage par défaut pour le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété.

     Le `OnFlowDirectionChange` méthode se traduit par la <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.Control.RightToLeft%2A> propriété.

     Le `cb_CheckedChanged` méthode gère le <xref:System.Windows.Forms.CheckBox.CheckedChanged> événement sur le <xref:System.Windows.Forms.CheckBox> contrôle. Il assigne le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété basée sur la valeur de la <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété

## <a name="extending-a-default-property-mapping"></a>Extension d’un mappage de propriété par défaut

Vous pouvez utiliser un mappage de propriété par défaut et l’étendre avec votre propre mappage.

### <a name="to-extend-a-default-property-mapping"></a>Pour étendre un mappage de propriété par défaut

- Copiez le code suivant dans la définition de la `Window1` classe.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     Le `ExtendBackgroundMapping` méthode ajoute un traducteur de propriété personnalisée à l’objet existant <xref:System.Windows.Controls.Control.Background%2A> mappage de propriété.

     Le `OnBackgroundChange` méthode assigne une image spécifique du contrôle hébergé <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriété. Le `OnBackgroundChange` méthode est appelée une fois que le mappage de propriété par défaut est appliqué.

## <a name="initializing-your-property-mappings"></a>Initialisation de vos mappages de propriétés

Définissez vos mappages de propriété en appelant les méthodes décrites précédemment le <xref:System.Windows.FrameworkElement.Loaded> Gestionnaire d’événements.

### <a name="to-initialize-your-property-mappings"></a>Pour initialiser vos mappages de propriétés

1. Copiez le code suivant dans la définition de la `Window1` classe.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     Le `WindowLoaded` méthode gère le <xref:System.Windows.FrameworkElement.Loaded> événement et effectue l’initialisation suivante.

    - Crée un [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.CheckBox> contrôle.

    - Appelle les méthodes que vous avez définies précédemment dans la procédure pas à pas pour configurer les mappages de propriétés.

    - Assigne les valeurs initiales aux propriétés mappées.

2. Appuyez sur **F5** pour générer et exécuter l’application. Cliquez sur la case à cocher pour voir l’effet de la <xref:System.Windows.FrameworkElement.FlowDirection%2A> mappage. Quand vous cliquez sur la case à cocher, la disposition inverse son orientation de gauche à droite.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Procédure pas à pas : Hébergement d’un contrôle de formulaires Windows dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)