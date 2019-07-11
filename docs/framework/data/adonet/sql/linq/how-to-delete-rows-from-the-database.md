---
title: 'Procédure : Supprimer des lignes de la base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 89b552d919898f78c0733c2af4507728f59a3c8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743336"
---
# <a name="how-to-delete-rows-from-the-database"></a>Procédure : Supprimer des lignes de la base de données
Vous pouvez supprimer des lignes dans une base de données en supprimant le correspondantes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objets à partir de leur collection liée à des tables. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit vos modifications à la requête SQL appropriée `DELETE` commandes.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge ni ne reconnaît les opérations de suppression en cascade. Si vous souhaitez supprimer une ligne dans une table comportant des contraintes sur cette suppression, vous devez terminer l'une des tâches suivantes :  
  
- Définissez la règle `ON DELETE CASCADE` dans la contrainte de clé étrangère dans la base de données.  
  
- Utilisez votre propre code pour supprimer en premier les objets enfants qui empêchent la suppression de l'objet parent.  
  
 Sinon, une exception est levée. Consultez le second exemple de code décrit plus loin dans cette rubrique.  
  
> [!NOTE]
>  Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données. Pour plus d’informations, consultez [personnalisation des opérations d’insertion, mise à jour et supprimer](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Les développeurs qui utilisent Visual Studio peuvent utiliser le concepteur objet/relationnel pour développer des procédures stockées dans le même but.  
  
 Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind. Pour plus d’informations, consultez [Guide pratique pour Se connecter à une base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-delete-a-row-in-the-database"></a>Pour supprimer une ligne de la base de données  
  
1. Interrogez la base de données concernant la ligne à supprimer.  
  
2. Appelez la méthode <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A>.  
  
3. Soumettez la modification à la base de données.  
  
## <a name="example"></a>Exemples  
 Le premier exemple de code interroge la base de données à propos de détails de commande concernant la commande 11000, marque ces détails de commande pour suppression, et soumet ces modifications à la base de données.  
  
 [!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]  
  
## <a name="example"></a>Exemple  
 Dans ce second exemple, l'objectif est de supprimer une commande (10250). Le code commence par examiner la table `OrderDetails` pour voir si la commande à supprimer y a des enfants. Si la commande a des enfants, ces enfants sont marqués en vue de leur suppression, puis c'est au tour de la commande. Le <xref:System.Data.Linq.DataContext> place les véritables suppressions dans l'ordre approprié afin que les commandes de suppression envoyées à la base de données se conforment aux contraintes de la base de données.  
  
 [!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
 [!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Guide pratique : affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
