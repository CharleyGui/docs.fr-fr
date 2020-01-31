---
title: "Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost"
ms.date: 08/18/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mapping properties [WPF]
- ElementHost control [WPF], mapping properties
ms.assetid: bccd6e0d-2272-4924-9107-ff8ed58b88aa
ms.openlocfilehash: 7ff4ff607ab70b55cda1e2c4736ff773d4907a22
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794115"
---
# <a name="walkthrough-mapping-properties-using-the-elementhost-control"></a>Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost

Cette procédure pas à pas vous montre comment utiliser la propriété <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> pour mapper des propriétés Windows Forms à des propriétés correspondantes sur un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hébergé.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du projet.

- Définition d’un nouveau mappage de propriété.

- Suppression d’un mappage de propriété par défaut.

- Extension d’un mappage de propriété par défaut.

Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez [mappage de propriétés à l’aide de l’exemple de contrôle ElementHost](https://go.microsoft.com/fwlink/?LinkID=160018).

Lorsque vous avez terminé, vous pouvez mapper les propriétés de Windows Forms aux propriétés de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondantes sur un élément hébergé.

## <a name="prerequisites"></a>Prerequisites

Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :

- Visual Studio 2017

## <a name="creating-the-project"></a>Création du projet

### <a name="to-create-the-project"></a>Pour créer le projet

1. Créez un projet d' **application Windows Forms** nommé `PropertyMappingWithElementHost`.

2. Dans **Explorateur de solutions**, ajoutez des références aux assemblys de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] suivants.

    - PresentationCore

    - PresentationFramework

    - WindowsBase

    - WindowsFormsIntegration

3. Copiez le code suivant en haut du fichier de code `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#10](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#10)]
     [!code-vb[PropertyMappingWithElementHost#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#10)]

4. Ouvrez `Form1` dans le Concepteur Windows Forms. Double-cliquez sur le formulaire pour ajouter un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Form.Load>.

5. Revenez à la Concepteur Windows Forms et ajoutez un gestionnaire d’événements pour l’événement <xref:System.Windows.Forms.Control.Resize> du formulaire. Pour plus d’informations, consultez [Comment : créer des gestionnaires d’événements à l’aide du concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

6. Déclarez un champ <xref:System.Windows.Forms.Integration.ElementHost> dans la classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#16](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#16)]
     [!code-vb[PropertyMappingWithElementHost#16](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#16)]

## <a name="defining-new-property-mappings"></a>Définition de nouveaux mappages de propriétés

Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> fournit plusieurs mappages de propriété par défaut. Vous ajoutez un nouveau mappage de propriété en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Add%2A> sur le <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.

### <a name="to-define-new-property-mappings"></a>Pour définir de nouveaux mappages de propriétés

1. Copiez le code suivant dans la définition de la classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#12](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#12)]
     [!code-vb[PropertyMappingWithElementHost#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#12)]

     La méthode `AddMarginMapping` ajoute un nouveau mappage pour la propriété <xref:System.Windows.Forms.Control.Margin%2A>.

     La méthode `OnMarginChange` convertit la propriété <xref:System.Windows.Forms.Control.Margin%2A> en propriété <xref:System.Windows.FrameworkElement.Margin%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

2. Copiez le code suivant dans la définition de la classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#14](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#14)]
     [!code-vb[PropertyMappingWithElementHost#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#14)]

     La méthode `AddRegionMapping` ajoute un nouveau mappage pour la propriété <xref:System.Windows.Forms.Control.Region%2A>.

     La méthode `OnRegionChange` convertit la propriété <xref:System.Windows.Forms.Control.Region%2A> en propriété <xref:System.Windows.UIElement.Clip%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

     La méthode `Form1_Resize` gère l’événement <xref:System.Windows.Forms.Control.Resize> du formulaire et dimensionne la zone de découpage pour l’adapter à l’élément hébergé.

## <a name="removing-a-default-property-mapping"></a>Suppression d’un mappage de propriété par défaut

Supprimez un mappage de propriété par défaut en appelant la méthode <xref:System.Windows.Forms.Integration.PropertyMap.Remove%2A> sur le <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A>du contrôle <xref:System.Windows.Forms.Integration.ElementHost>.

### <a name="to-remove-a-default-property-mapping"></a>Pour supprimer un mappage de propriété par défaut

- Copiez le code suivant dans la définition de la classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#13](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#13)]
     [!code-vb[PropertyMappingWithElementHost#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#13)]

     La méthode `RemoveCursorMapping` supprime le mappage par défaut pour la propriété <xref:System.Windows.Forms.Control.Cursor%2A>.

## <a name="extending-a-default-property-mapping"></a>Extension d’un mappage de propriété par défaut

Vous pouvez utiliser un mappage de propriété par défaut et l’étendre avec votre propre mappage.

### <a name="to-extend-a-default-property-mapping"></a>Pour étendre un mappage de propriété par défaut

- Copiez le code suivant dans la définition de la classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#15](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#15)]
     [!code-vb[PropertyMappingWithElementHost#15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#15)]

     La méthode `ExtendBackColorMapping` ajoute un traducteur de propriétés personnalisées au mappage de propriété de <xref:System.Windows.Forms.Control.BackColor%2A> existant.

     La méthode `OnBackColorChange` assigne une image spécifique à la propriété <xref:System.Windows.Controls.Control.Background%2A> du contrôle hébergé. La méthode `OnBackColorChange` est appelée après l’application du mappage de propriété par défaut.

## <a name="initialize-your-property-mappings"></a>Initialiser vos mappages de propriétés

1. Copiez le code suivant dans la définition de la classe `Form1`.

     [!code-csharp[PropertyMappingWithElementHost#11](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertyMappingWithElementHost/CSharp/PropertyMappingWithElementHost/Form1.cs#11)]
     [!code-vb[PropertyMappingWithElementHost#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertyMappingWithElementHost/VisualBasic/PropertyMappingWithElementHost/Form1.vb#11)]

     La méthode `Form1_Load` gère l’événement <xref:System.Windows.Forms.Form.Load> et effectue l’initialisation suivante.

    - Crée un élément [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Button>.

    - Appelle les méthodes que vous avez définies précédemment dans la procédure pas à pas pour configurer les mappages de propriétés.

    - Assigne les valeurs initiales aux propriétés mappées.

2. Appuyez sur F5 pour générer et exécuter l'application.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Mappage de propriétés Windows Forms et WPF](windows-forms-and-wpf-property-mapping.md)
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
