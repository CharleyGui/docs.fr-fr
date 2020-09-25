---
title: 'Procédure : Spécifier des noms de bases de données'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 82cb3f8f31af433b0299b4fec742b548d61921e4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197155"
---
# <a name="how-to-specify-database-names"></a>Procédure : Spécifier des noms de bases de données

Utilisez la propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> sur un attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute> pour spécifier le nom d'une base de données lorsque la connexion ne fournit pas de nom.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Pour spécifier le nom de la base de données  
  
1. Ajoutez l'attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute> à la déclaration de classe de la base de données.  
  
2. Ajoutez la propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> à l'attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
3. Affectez le nom que vous souhaitez spécifier à la valeur de propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle objet LINQ to SQL](the-linq-to-sql-object-model.md)
- [Procédure : Personnaliser des classes d’entité à l’aide de l’éditeur de code](how-to-customize-entity-classes-by-using-the-code-editor.md)
