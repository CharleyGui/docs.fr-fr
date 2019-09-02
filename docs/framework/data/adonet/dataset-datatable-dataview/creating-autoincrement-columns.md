---
title: Création de colonnes AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 2548ad9382b406978dac0a3d366207626278f501
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205129"
---
# <a name="creating-autoincrement-columns"></a>Création de colonnes AutoIncrement
Pour garantir que les valeurs de colonne sont uniques, vous pouvez les définir de sorte qu'elles s'incrémentent automatiquement lors de l'ajout de lignes à la table. Pour créer une auto-incrémentation <xref:System.Data.DataColumn>, affectez <xref:System.Data.DataColumn.AutoIncrement%2A> la valeur **true**à la propriété de la colonne. Le <xref:System.Data.DataColumn> commence par la valeur définie dans la <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriété, et chaque ligne ajoutée à la valeur de la colonne **AutoIncrement** augmente de la valeur définie dans la <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriété de la colonne.  
  
 Pour les colonnes **AutoIncrement** , nous vous recommandons <xref:System.Data.DataColumn.ReadOnly%2A> d’affecter la valeur **true**à la propriété du **DataColumn** .  
  
 L'exemple suivant montre comment créer une colonne commençant par la valeur 200, avec une incrémentation par pas de 3.  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Data.DataColumn>
- [Définition de schéma de DataTable](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
