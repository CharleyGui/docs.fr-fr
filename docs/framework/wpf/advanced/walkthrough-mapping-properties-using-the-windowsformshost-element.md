---
title: "Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost"
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 74809167-bf8e-48b7-a2e7-b4ea08bc7d8c
ms.openlocfilehash: c076937d6431adf1750793d47ece88dc82edf95c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794098"
---
# <a name="walkthrough-mapping-properties-using-the-windowsformshost-element"></a>Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost

Cette procédure pas à pas vous montre comment utiliser la propriété <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> pour mapper des propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à des propriétés correspondantes sur un contrôle Windows Forms hébergé.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du projet.

- Définition de la disposition de l’application.

- Définition d’un nouveau mappage de propriété.

- Suppression d’un mappage de propriété par défaut.

- Remplacement d’un mappage de propriété par défaut.

- Extension d’un mappage de propriété par défaut.

Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [mappage de propriétés à l’aide de l’exemple d’élément WindowsFormsHost](https://go.microsoft.com/fwlink/?LinkID=160019).

Lorsque vous avez terminé, vous pouvez mapper [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés aux propriétés correspondantes sur un contrôle Windows Forms hébergé.

## <a name="prerequisites"></a>Prerequisites

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Visual Studio 2017

## <a name="create-and-set-up-the-project"></a>Créer et configurer le projet

1. Créez un projet d' **application WPF** nommé `PropertyMappingWithWfhSample`.

2. Dans **Explorateur de solutions**, ajoutez une référence à l’assembly windowsformsintegration, nommé windowsformsintegration. dll.

3. Dans **Explorateur de solutions**, ajoutez des références aux assemblys System. Drawing et System. Windows. Forms.

## <a name="defining-the-application-layout"></a>Définition de la disposition de l’application

L’application basée sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]utilise l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> pour héberger un contrôle Windows Forms.

### <a name="to-define-the-application-layout"></a>Pour définir la disposition de l’application

1. Ouvrez Window1. xaml dans le Concepteur WPF.

2. Remplacez le code existant par le code ci-dessous.

     [!code-xaml[PropertyMappingWithWfhSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml#1)]

3. Ouvrez Window1.xaml.cs dans l’éditeur de code.

4. En haut du fichier, importez les espaces de noms suivants.

     [!code-csharp[PropertyMappingWithWfhSample#20](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#20)]
     [!code-vb[PropertyMappingWithWfhSample#20](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#20)]

## <a name="defining-a-new-property-mapping"></a>Définition d’un nouveau mappage de propriété

L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> fournit plusieurs mappages de propriété par défaut. Vous ajoutez un nouveau mappage de propriété en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-define-a-new-property-mapping"></a>Pour définir un nouveau mappage de propriété

- Copiez le code suivant dans la définition de la classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#14)]
     [!code-vb[PropertyMappingWithWfhSample#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#14)]

     La méthode `AddClipMapping` ajoute un nouveau mappage pour la propriété <xref:System.Windows.UIElement.Clip%2A>.

     La méthode `OnClipChange` convertit la propriété <xref:System.Windows.UIElement.Clip%2A> en propriété<xref:System.Windows.Forms.Control.Region%2A> Windows Forms.

     La méthode `Window1_SizeChanged` gère l’événement de <xref:System.Windows.FrameworkElement.SizeChanged> de la fenêtre et dimensionne la zone de découpage pour l’adapter à la fenêtre d’application.

## <a name="removing-a-default-property-mapping"></a>Suppression d’un mappage de propriété par défaut

Supprimez un mappage de propriété par défaut en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-remove-a-default-property-mapping"></a>Pour supprimer un mappage de propriété par défaut

- Copiez le code suivant dans la définition de la classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#13)]
     [!code-vb[PropertyMappingWithWfhSample#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#13)]

     La méthode `RemoveCursorMapping` supprime le mappage par défaut pour la propriété <xref:System.Windows.FrameworkElement.Cursor%2A>.

## <a name="replacing-a-default-property-mapping"></a>Remplacement d’un mappage de propriété par défaut

Remplacez un mappage de propriété par défaut en supprimant le mappage par défaut et en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> sur le <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A>de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.

### <a name="to-replace-a-default-property-mapping"></a>Pour remplacer un mappage de propriété par défaut

- Copiez le code suivant dans la définition de la classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#12)]
     [!code-vb[PropertyMappingWithWfhSample#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#12)]

     La méthode `ReplaceFlowDirectionMapping` remplace le mappage par défaut pour la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A>.

     La méthode `OnFlowDirectionChange` convertit la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> en propriété<xref:System.Windows.Forms.Control.RightToLeft%2A> Windows Forms.

     La méthode `cb_CheckedChanged` gère l’événement <xref:System.Windows.Forms.CheckBox.CheckedChanged> sur le contrôle <xref:System.Windows.Forms.CheckBox>. Elle assigne la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> en fonction de la valeur de la propriété <xref:System.Windows.Forms.CheckBox.CheckState%2A>

## <a name="extending-a-default-property-mapping"></a>Extension d’un mappage de propriété par défaut

Vous pouvez utiliser un mappage de propriété par défaut et l’étendre avec votre propre mappage.

### <a name="to-extend-a-default-property-mapping"></a>Pour étendre un mappage de propriété par défaut

- Copiez le code suivant dans la définition de la classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#15)]
     [!code-vb[PropertyMappingWithWfhSample#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#15)]

     La méthode `ExtendBackgroundMapping` ajoute un traducteur de propriétés personnalisées au mappage de propriété de <xref:System.Windows.Controls.Control.Background%2A> existant.

     La méthode `OnBackgroundChange` assigne une image spécifique à la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du contrôle hébergé. La méthode `OnBackgroundChange` est appelée après l’application du mappage de propriété par défaut.

## <a name="initializing-your-property-mappings"></a>Initialisation de vos mappages de propriétés

Configurez vos mappages de propriétés en appelant les méthodes décrites précédemment dans le gestionnaire d’événements <xref:System.Windows.FrameworkElement.Loaded>.

### <a name="to-initialize-your-property-mappings"></a>Pour initialiser vos mappages de propriétés

1. Copiez le code suivant dans la définition de la classe `Window1`.

     [!code-csharp[PropertyMappingWithWfhSample#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithWfhSample/CSharp/PropertyMappingWithWfh/Window1.xaml.cs#11)]
     [!code-vb[PropertyMappingWithWfhSample#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithWfhSample/VisualBasic/PropertyMappingWithWfh/Window1.xaml.vb#11)]

     La méthode `WindowLoaded` gère l’événement <xref:System.Windows.FrameworkElement.Loaded> et effectue l’initialisation suivante.

    - Crée un contrôle de<xref:System.Windows.Forms.CheckBox> Windows Forms.

    - Appelle les méthodes que vous avez définies précédemment dans la procédure pas à pas pour configurer les mappages de propriétés.

    - Assigne les valeurs initiales aux propriétés mappées.

2. Appuyez sur **F5** pour générer et exécuter l’application. Activez la case à cocher pour voir l’effet du mappage de <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Quand vous cliquez sur la case à cocher, la disposition inverse son orientation de gauche à droite.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Procédure pas à pas : hébergement d’un contrôle Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
