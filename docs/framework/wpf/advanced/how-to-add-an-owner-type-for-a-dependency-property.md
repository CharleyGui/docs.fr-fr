---
title: 'Procédure : Ajouter un type propriétaire d’une propriété de dépendance'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401136"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Procédure : Ajouter un type propriétaire d’une propriété de dépendance
Cet exemple montre comment ajouter une classe en tant que propriétaire d’une propriété de dépendance inscrite pour un type différent. En procédant ainsi, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] le lecteur et le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] système de propriétés sont tous deux capables de reconnaître la classe en tant que propriétaire supplémentaire de la propriété. L’ajout de en tant que propriétaire permet éventuellement à la classe d’ajout de fournir des métadonnées spécifiques au type.  
  
 Dans l’exemple suivant, `StateProperty` est une propriété inscrite par `MyStateControl` la classe. La classe `UnrelatedStateControl` s’ajoute à lui-même en `StateProperty` tant que <xref:System.Windows.DependencyProperty.AddOwner%2A> propriétaire de à l’aide de la méthode, en utilisant spécifiquement la signature qui autorise les nouvelles métadonnées pour la propriété de dépendance telle qu’elle existe sur le type d’ajout. Notez que vous devez fournir des accesseurs common language runtime (CLR) pour la propriété similaire à l’exemple indiqué dans l’exemple [implémenter une propriété de dépendance](how-to-implement-a-dependency-property.md) , ainsi que pour réexposer l’identificateur de propriété de dépendance sur la classe qui est ajoutée en tant que propriétaire.  
  
 Sans wrappers, la propriété de dépendance continue de fonctionner du point de vue de l' <xref:System.Windows.DependencyObject.GetValue%2A> accès <xref:System.Windows.DependencyObject.SetValue%2A>par programme à l’aide de ou de. Toutefois, vous souhaitez généralement parallèler ce comportement de système de propriétés avec les wrappers de propriété CLR. Les wrappers facilitent la définition de la propriété de dépendance par programmation et permettent de définir les propriétés en tant qu' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributs.  
  
 Pour savoir comment substituer les métadonnées par défaut, consultez [substituer les métadonnées d’une propriété de dépendance](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Voir aussi

- [Propriétés de dépendance personnalisées](custom-dependency-properties.md)
- [Vue d’ensemble des propriétés de dépendance](dependency-properties-overview.md)
