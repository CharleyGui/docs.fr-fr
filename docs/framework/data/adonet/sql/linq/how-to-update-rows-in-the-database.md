---
title: 'Procédure : Mettre à jour des lignes dans la base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: bf4c50bba4b4bc2bf6b7b1c2b79426566c874dd4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043573"
---
# <a name="how-to-update-rows-in-the-database"></a>Procédure : Mettre à jour des lignes dans la base de données

Vous pouvez mettre à jour des lignes dans une base de données en modifiant les valeurs de membre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] des objets associés à la <xref:System.Data.Linq.Table%601> collection, puis en soumettant les modifications à la base de données. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traduit vos modifications en commandes SQL `UPDATE` appropriées.

> [!NOTE]
> Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données. Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).
>
> Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.

Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind. Pour plus d’informations, consultez [Guide pratique pour Connectez-vous à](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)une base de données.

### <a name="to-update-a-row-in-the-database"></a>Pour mettre à jour une ligne dans la base de données

1. Interrogez la base de données concernant la ligne à mettre à jour.

2. Apportez les modifications souhaitées aux valeurs de membre dans l'objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obtenu.

3. Soumettez les modifications à la base de données.

## <a name="example"></a>Exemple

L'exemple suivant interroge la base de données concernant la commande 11000, puis modifie les valeurs de `ShipName` et `ShipVia` dans l'objet `Order` obtenu. Enfin, les modifications apportées à ces valeurs de membre sont soumises à la base de données comme modifications dans les colonnes `ShipName` et `ShipVia`.

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Guide pratique : Gérer les conflits de modification](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Guide pratique : affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
