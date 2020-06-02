---
title: 'Comment : supprimer des lignes de la base de données'
description: Apprenez à supprimer des lignes dans une base de données en supprimant LINQ to SQL objets d’une collection liée à une table. LINQ to SQL traduit les suppressions en commandes SQL DELETE.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: d08621e834961e1db9312cac36bd2e69133142b5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286389"
---
# <a name="how-to-delete-rows-from-the-database"></a>Comment : supprimer des lignes de la base de données

Vous pouvez supprimer des lignes dans une base de données en supprimant les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objets correspondants de leur collection liée à la table. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traduit vos modifications en commandes SQL appropriées `DELETE` .

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge ni ne reconnaît les opérations de suppression en cascade. Si vous souhaitez supprimer une ligne dans une table comportant des contraintes sur cette suppression, vous devez terminer l'une des tâches suivantes :

- Définissez la règle `ON DELETE CASCADE` dans la contrainte de clé étrangère dans la base de données.

- Utilisez votre propre code pour supprimer en premier les objets enfants qui empêchent la suppression de l'objet parent.

 Sinon, une exception est levée. Consultez le second exemple de code décrit plus loin dans cette rubrique.

> [!NOTE]
> Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données. Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).
>
> Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.

Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind. Pour plus d’informations, consultez [Comment : se connecter à une base de données](how-to-connect-to-a-database.md).

### <a name="to-delete-a-row-in-the-database"></a>Pour supprimer une ligne de la base de données

1. Interrogez la base de données concernant la ligne à supprimer.

2. Appelez la méthode <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> .

3. Soumettez la modification à la base de données.

## <a name="example"></a>Exemple

Le premier exemple de code interroge la base de données à propos de détails de commande concernant la commande 11000, marque ces détails de commande pour suppression, et soumet ces modifications à la base de données.

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a>Exemple

Dans ce second exemple, l'objectif est de supprimer une commande (10250). Le code commence par examiner la table `OrderDetails` pour voir si la commande à supprimer y a des enfants. Si la commande a des enfants, ces enfants sont marqués en vue de leur suppression, puis c'est au tour de la commande. Le <xref:System.Data.Linq.DataContext> place les véritables suppressions dans l'ordre approprié afin que les commandes de suppression envoyées à la base de données se conforment aux contraintes de la base de données.

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Comment : gérer les conflits de changement](how-to-manage-change-conflicts.md)
- [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Apport et soumission de modifications de données](making-and-submitting-data-changes.md)
