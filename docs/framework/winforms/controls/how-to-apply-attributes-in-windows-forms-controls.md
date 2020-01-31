---
title: Appliquer des attributs dans les contrôles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: b8ecd516cf6bb189c6ad1b208dd8e3a5444f001c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741490"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Comment : appliquer des attributs dans les contrôles Windows Forms
Pour développer des composants et des contrôles qui interagissent correctement avec l’environnement de conception et s’exécutent correctement au moment de l’exécution, vous devez appliquer correctement les attributs aux classes et aux membres.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser plusieurs attributs sur un contrôle personnalisé. Le contrôle illustre une fonctionnalité de journalisation simple. Lorsque le contrôle est lié à une source de données, il affiche les valeurs envoyées par la source de données dans un contrôle de <xref:System.Windows.Forms.DataGridView>. Si une valeur dépasse la valeur spécifiée par la propriété `Threshold`, un événement `ThresholdExceeded` est déclenché.  
  
 Le `AttributesDemoControl` journalise les valeurs avec une classe `LogEntry`. La classe `LogEntry` est une classe de modèle, ce qui signifie qu’elle est paramétrée sur le type qu’elle enregistre. Par exemple, si le `AttributesDemoControl` enregistre des valeurs de type `float`, chaque instance `LogEntry` est déclarée et utilisée comme suit.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> Étant donné que `LogEntry` est paramétré par un type arbitraire, il doit utiliser la réflexion pour fonctionner sur le type de paramètre. Pour que la fonctionnalité de seuil fonctionne, le type de paramètre `T` doit implémenter l’interface <xref:System.IComparable>.  
  
 Le formulaire qui héberge le `AttributesDemoControl` interroge périodiquement un compteur de performance. Chaque valeur est empaquetée dans un `LogEntry` du type approprié et ajoutée au <xref:System.Windows.Forms.BindingSource>du formulaire. L' `AttributesDemoControl` reçoit la valeur par le biais de sa liaison de données et affiche la valeur dans un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 Le premier exemple de code est l’implémentation de `AttributesDemoControl`. Le deuxième exemple de code illustre un formulaire qui utilise l' `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Attributs au niveau de la classe  
 Certains attributs sont appliqués au niveau de la classe. L’exemple de code suivant affiche les attributs qui sont généralement appliqués à un contrôle Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter (attribut)  
 <xref:System.ComponentModel.TypeConverterAttribute> est un autre attribut couramment utilisé au niveau de la classe. L’exemple de code suivant illustre son utilisation pour la classe `LogEntry`. Cet exemple montre également une implémentation d’une <xref:System.ComponentModel.TypeConverter> pour le type de `LogEntry`, appelée `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Attributs au niveau du membre  
 Certains attributs sont appliqués au niveau du membre. Les exemples de code suivants montrent des attributs qui sont généralement appliqués aux propriétés des contrôles Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Attribut AmbientValue  
 L’exemple suivant illustre le <xref:System.ComponentModel.AmbientValueAttribute> et affiche le code qui prend en charge son interaction avec l’environnement de conception. Cette interaction est appelée *ambiance*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Attributs DataBinding  
 Les exemples suivants illustrent une implémentation d’une liaison de données complexe. La <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>au niveau de la classe, indiquée précédemment, spécifie les propriétés de `DataSource` et de `DataMember` à utiliser pour la liaison de données. Le <xref:System.ComponentModel.AttributeProviderAttribute> spécifie le type auquel la propriété `DataSource` sera liée.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Le formulaire qui héberge le `AttributesDemoControl` requiert une référence à l’assembly `AttributesDemoControl` afin de générer.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
- [Attributs dans les contrôles Windows Forms](attributes-in-windows-forms-controls.md)
- [Comment : sérialiser des collections de types standard avec DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
