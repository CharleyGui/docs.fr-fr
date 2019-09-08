---
title: 'Procédure : Représenter des colonnes en tant que membres de classe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 515a8477b3a9c72934e0ad11d7b1bf599e8b16a2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793515"
---
# <a name="how-to-represent-columns-as-class-members"></a>Procédure : Représenter des colonnes en tant que membres de classe
Utilisez l' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour associer un champ ou une propriété à une colonne de base de données.  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a>Pour mapper un champ ou une propriété à une colonne de base de données  
  
- Ajoutez l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> à la déclaration de propriété ou de champ.  
  
## <a name="example"></a>Exemple  
 Le code suivant mappe le champ `CustomerID` de la classe `Customer` à la colonne `CustomerID` de la table de base de données `Customers`.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Il n'est pas nécessaire de spécifier la propriété <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> si le nom peut être déduit. Si vous ne spécifiez pas de nom, on considère qu'il s'agit du même nom que pour la propriété ou le champ.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle objet LINQ to SQL](the-linq-to-sql-object-model.md)
- [Guide pratique : Personnaliser des classes d’entité à l’aide de l’éditeur de code](how-to-customize-entity-classes-by-using-the-code-editor.md)
