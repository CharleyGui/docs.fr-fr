---
title: 'Procédure : Mapper des hiérarchies d’héritage'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 618abc8e681a6f43a1054d0ca2cec2fbdec853f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943564"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Procédure : Mapper des hiérarchies d’héritage
Pour implémenter un mappage d'héritage dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], vous devez spécifier les attributs et les propriétés d'attribut sur la classe racine de la hiérarchie d'héritage, comme décrit dans les étapes suivantes. Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour mapper des hiérarchies d’héritage. Voir [Guide pratique pour configurer l’héritage à l’aide du Concepteur O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
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
  
     Cette propriété sert à désigner un mappage de *secours* lorsque la valeur de discriminateur de la table de base de <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> données ne correspond à aucune valeur dans les mappages d’héritage.  
  
6. Ajoutez une propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour un attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
     Cette propriété signifie qu'il s'agit de la colonne qui contient la valeur <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
## <a name="example"></a>Exemples  
  
> [!NOTE]
> Si vous utilisez Visual Studio, vous pouvez utiliser la Concepteur Objet Relationnel pour configurer l’héritage. Voir [Guide pratique pour configurer l’héritage à l’aide du Concepteur O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 Dans l'exemple de code suivant, `Vehicle` est défini comme classe racine. Les étapes précédentes ont été implémentées pour décrire la hiérarchie de [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Prise en charge de l’héritage](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [Guide pratique pour Personnaliser des classes d’entité à l’aide de l’éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
