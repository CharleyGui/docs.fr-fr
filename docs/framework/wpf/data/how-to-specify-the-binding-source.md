---
title: 'Comment : spécifier la source de liaison'
description: Découvrez comment spécifier la source de liaison à l’aide de cet exemple dans le Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 02f27da007ebe8c5985f91b83adfba7d3d00219a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621663"
---
# <a name="how-to-specify-the-binding-source"></a>Comment : spécifier la source de liaison
Dans la liaison de données, l’objet de source de liaison fait référence à l’objet à partir duquel vous obtenez vos données. Cette rubrique décrit les différentes façons de spécifier la source de liaison.  
  
## <a name="example"></a>Exemple  
 Si vous liez plusieurs propriétés à une source commune, vous allez devoir utiliser la propriété `DataContext`, qui offre un moyen pratique d’établir une portée dans laquelle toutes les propriétés liées aux données héritent d’une source commune.  
  
 Dans l’exemple suivant, le contexte de données est établi sur l’élément racine de l’application. Ainsi, tous les éléments enfants vont hériter de ce contexte de données. Les données de la liaison proviennent d’une classe de données personnalisée, `NetIncome`, qui est référencée directement via un mappage et qui est affectée à la clé de ressource de `incomeDataSource`.  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 L’exemple suivant montre la définition de la classe `NetIncome`.  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
> L’exemple ci-dessus instancie l’objet dans le balisage et l’utilise en tant que ressource. Si vous souhaitez effectuer une liaison à un objet qui a déjà été instancié dans le code, vous devez définir la propriété `DataContext` par programmation. Pour obtenir un exemple, consultez la page [Rendre des données disponibles pour la liaison en XAML](how-to-make-data-available-for-binding-in-xaml.md).  
  
 Sinon, si vous souhaitez spécifier explicitement la source sur vos liaisons individuelles, vous disposez des options suivantes. Celles-ci ont priorité sur le contexte de données hérité.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|Cette propriété vous permet de définir la source à une instance d’un objet. Si vous n’avez pas besoin de la fonctionnalité d’établissement d’une étendue dans laquelle plusieurs propriétés héritent du même contexte de données, vous pouvez utiliser la propriété à la <xref:System.Windows.Data.Binding.Source%2A> place de la `DataContext` propriété. Pour plus d’informations, consultez <xref:System.Windows.Data.Binding.Source%2A>.|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|Cela est utile lorsque vous souhaitez spécifier la source par rapport à l’emplacement de votre cible de liaison. Vous pouvez utiliser cette propriété lorsque vous souhaitez lier une propriété de votre élément à une autre propriété du même élément ou si vous définissez une liaison dans un style ou un modèle. Pour plus d’informations, consultez <xref:System.Windows.Data.Binding.RelativeSource%2A>.|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|Vous spécifiez une chaîne qui représente l’élément que vous voulez lier. Cela est utile lorsque vous souhaitez effectuer une liaison à la propriété d’un autre élément sur votre application. Par exemple, si vous souhaitez utiliser un <xref:System.Windows.Controls.Slider> pour contrôler la hauteur d’un autre contrôle dans votre application, ou si vous souhaitez lier le <xref:System.Windows.Controls.ContentControl.Content%2A> de votre contrôle à la <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> propriété de votre <xref:System.Windows.Controls.ListBox> contrôle. Pour plus d’informations, consultez <xref:System.Windows.Data.Binding.ElementName%2A>.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [Héritage de la valeur de propriété](../advanced/property-value-inheritance.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des déclarations de liaison](binding-declarations-overview.md)
- [Rubriques de procédures](data-binding-how-to-topics.md)
