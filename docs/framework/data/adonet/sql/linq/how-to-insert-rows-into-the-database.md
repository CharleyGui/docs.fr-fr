---
title: 'Procédure : Insérer des lignes dans la base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 2852b0593f8b213f8cad6f9a2ab8f08eeb2a4dec
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943637"
---
# <a name="how-to-insert-rows-into-the-database"></a>Procédure : Insérer des lignes dans la base de données
Vous insérez des lignes dans une base de données en ajoutant des [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objets à la collection associée <xref:System.Data.Linq.Table%601> , puis en soumettant les modifications à la base de données. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traduit vos modifications en commandes SQL `INSERT` appropriées.  
  
> [!NOTE]
> Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données. Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.  
  
 Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind. Pour plus d’informations, consultez [Guide pratique pour Connectez-vous à](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)une base de données.  
  
### <a name="to-insert-a-row-into-the-database"></a>Pour insérer une ligne dans la base de données  
  
1. Créez un objet qui inclut les données de colonne à soumettre.  
  
2. Ajoutez le nouvel objet à la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associée à la table cible dans la base de données.  
  
3. Soumettez la modification à la base de données.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant crée un objet de type `Order` et le remplit avec les valeurs appropriées. Il ajoute ensuite le nouvel objet à la collection `Order`. Enfin, il soumet la modification à la base de données comme une nouvelle ligne de la table `Orders`.  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Gérer les conflits de modification](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [DataContext, méthodes (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Guide pratique : affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
