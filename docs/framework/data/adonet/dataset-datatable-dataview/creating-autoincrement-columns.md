---
title: Création de colonnes AutoIncrement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 9a979f39003e60c70c03206bd886bdd6827c82e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203720"
---
# <a name="creating-autoincrement-columns"></a>Création de colonnes AutoIncrement

Pour garantir que les valeurs de colonne sont uniques, vous pouvez les définir de sorte qu'elles s'incrémentent automatiquement lors de l'ajout de lignes à la table. Pour créer une auto-incrémentation <xref:System.Data.DataColumn> , affectez la valeur <xref:System.Data.DataColumn.AutoIncrement%2A> **true**à la propriété de la colonne. Le <xref:System.Data.DataColumn> commence par la valeur définie dans la <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriété, et chaque ligne ajoutée à la valeur de la colonne **AutoIncrement** augmente de la valeur définie dans la <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriété de la colonne.  
  
 Pour les colonnes **AutoIncrement** , nous vous recommandons d’affecter la valeur <xref:System.Data.DataColumn.ReadOnly%2A> **true**à la propriété du **DataColumn** .  
  
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
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
