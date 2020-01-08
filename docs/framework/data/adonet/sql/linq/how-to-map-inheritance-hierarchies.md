---
title: "Comment : mapper des hiérarchies d'héritage"
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 737cb8743d8fd9c93cd46ebf50fba3fe554a35f2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634662"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Comment : mapper des hiérarchies d'héritage
Pour implémenter le mappage d’héritage dans LINQ, vous devez spécifier les attributs et les propriétés d’attribut sur la classe racine de la hiérarchie d’héritage, comme décrit dans les étapes suivantes. Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour mapper des hiérarchies d’héritage. Consultez [Comment : configurer l’héritage à l’aide du Concepteur O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
> Les sous-classes ne requièrent pas de propriétés ni d'attributs spéciaux. Notez surtout que les sous-classes n'ont pas l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Pour mapper une hiérarchie d'héritage  
  
1. Ajoutez l'attribut <xref:System.Data.Linq.Mapping.TableAttribute> à la classe racine.  
  
2. Ajoutez-lui également un attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> pour chaque classe dans la structure hiérarchique.  
  
3. Pour chaque attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, définissez une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
     Cette propriété contient une valeur qui apparaît dans la table de base de données dans la colonne <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour indiquer à quelle classe ou sous-classe appartient cette ligne de données.  
  
4. Pour chaque attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, ajoutez également une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.  
  
     Cette propriété contient une valeur qui spécifie la classe ou la sous-classe que la valeur de clé désigne.  
  
5. Ajoutez une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> à un seul des attributs <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.  
  
     Cette propriété sert à désigner un mappage de *secours* lorsque la valeur de discriminateur de la table de base de données ne correspond à aucune valeur de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> dans les mappages d’héritage.  
  
6. Ajoutez une propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour un attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
     Cette propriété signifie qu'il s'agit de la colonne qui contient la valeur <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
## <a name="example"></a>Exemple  
  
> [!NOTE]
> Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour configurer l’héritage. Consultez [Comment : configurer l’héritage à l’aide du Concepteur O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 Dans l’exemple de code suivant, `Vehicle` est défini en tant que classe racine, et les étapes précédentes ont été implémentées pour décrire la hiérarchie pour LINQ.  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Prise en charge de l’héritage](inheritance-support.md)
- [Guide pratique pour personnaliser des classes d’entité à l’aide de l’éditeur de code](how-to-customize-entity-classes-by-using-the-code-editor.md)
