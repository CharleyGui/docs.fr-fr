---
title: 'Procédure : appliquer des attributs dans des contrôles Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 720172e9fcb13837b527d72176a35d366d83c948
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612824"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>Procédure : appliquer des attributs dans des contrôles Windows Forms
Pour développer des composants et des contrôles qui interagissent correctement avec l’environnement de conception et s’exécutent correctement au moment de l’exécution, vous devez appliquer correctement des attributs aux classes et membres.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser plusieurs attributs sur un contrôle personnalisé. Le contrôle montre une fonctionnalité de journalisation simple. Lorsque le contrôle est lié à une source de données, il affiche les valeurs envoyées par la source de données dans un <xref:System.Windows.Forms.DataGridView> contrôle. Si une valeur dépasse la valeur spécifiée par le `Threshold` propriété, un `ThresholdExceeded` événement est déclenché.  
  
 Le `AttributesDemoControl` enregistre des valeurs avec une `LogEntry` classe. Le `LogEntry` classe est une classe de modèle, ce qui signifie qu’elle est paramétrée sur le type qu’il journalise. Par exemple, si le `AttributesDemoControl` enregistre des valeurs de type `float`, chaque `LogEntry` instance est déclarée et utilisée comme suit.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  Étant donné que `LogEntry` est paramétré par un type arbitraire, il doit utiliser la réflexion pour fonctionner sur le type de paramètre. Pour la fonctionnalité de seuil fonctionne, le type de paramètre `T` doit implémenter le <xref:System.IComparable> interface.  
  
 Le formulaire qui héberge le `AttributesDemoControl` interroge périodiquement un compteur de performances. Chaque valeur est empaquetée dans un `LogEntry` du type approprié et ajouté à la forme <xref:System.Windows.Forms.BindingSource>. Le `AttributesDemoControl` reçoit la valeur via sa liaison de données et affiche la valeur dans un <xref:System.Windows.Forms.DataGridView> contrôle.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 Le premier exemple de code est le `AttributesDemoControl` implémentation. Le deuxième exemple de code montre un formulaire qui utilise le `AttributesDemoControl`.  
  
## <a name="class-level-attributes"></a>Attributs de niveau classe  
 Certains attributs sont appliqués au niveau de la classe. L’exemple de code suivant montre les attributs qui sont couramment appliqués à un contrôle Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>Attribut TypeConverter  
 <xref:System.ComponentModel.TypeConverterAttribute> est un autre attribut de niveau classe couramment utilisé. L’exemple de code suivant illustre son utilisation pour la `LogEntry` classe. Cet exemple illustre également une implémentation d’un <xref:System.ComponentModel.TypeConverter> pour le `LogEntry` type, appelé `LogEntryTypeConverter`.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>Attributs au niveau de membre  
 Certains attributs sont appliqués au niveau du membre. Les exemples de code suivants montrent certains attributs qui sont couramment appliqués aux propriétés des contrôles Windows Forms.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>Attribut de AmbientValue  
 L’exemple suivant montre le <xref:System.ComponentModel.AmbientValueAttribute> et affiche un code qui prend en charge son interaction avec l’environnement de conception. Cette interaction est appelée *ambiance*.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Attributs de liaison de données  
 Les exemples suivants montrent une implémentation de la liaison de données complexe. Niveau de la classe <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>, comme indiqué précédemment, spécifie le `DataSource` et `DataMember` propriétés à utiliser pour la liaison de données. Le <xref:System.ComponentModel.AttributeProviderAttribute> Spécifie le type auquel le `DataSource` propriété liera.  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
- Le formulaire qui héberge le `AttributesDemoControl` requiert une référence à la `AttributesDemoControl` assembly afin de créer.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
- [Attributs dans les contrôles Windows Forms](attributes-in-windows-forms-controls.md)
- [Guide pratique pour Sérialiser des Collections de Types Standard avec DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
