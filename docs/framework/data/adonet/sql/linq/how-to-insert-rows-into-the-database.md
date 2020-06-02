---
title: 'Comment : insérer des lignes dans la base de données'
description: Apprenez à insérer des lignes dans une base de données en ajoutant des objets LINQ to SQL à une collection liée à une table. LINQ to SQL traduit les ajouts en commandes SQL INSERT.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 39eee6edf59d2adb7de41efd88899050fbe69fd8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286350"
---
# <a name="how-to-insert-rows-into-the-database"></a>Comment : insérer des lignes dans la base de données

Vous insérez des lignes dans une base de données en ajoutant des objets à la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> collection associée, puis en soumettant les modifications à la base de données. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]traduit vos modifications en commandes SQL appropriées `INSERT` .

> [!NOTE]
> Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données. Pour plus d’informations, consultez [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md).
>
> Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées dans le même but.

Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind. Pour plus d’informations, consultez [Comment : se connecter à une base de données](how-to-connect-to-a-database.md).

### <a name="to-insert-a-row-into-the-database"></a>Pour insérer une ligne dans la base de données

1. Créez un objet qui inclut les données de colonne à soumettre.

2. Ajoutez le nouvel objet à la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` collection associée à la table cible dans la base de données.

3. Soumettez la modification à la base de données.

## <a name="example"></a>Exemple

L'exemple de code suivant crée un objet de type `Order` et le remplit avec les valeurs appropriées. Il ajoute ensuite le nouvel objet à la collection `Order`. Enfin, il soumet la modification à la base de données comme une nouvelle ligne de la table `Orders`.

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Comment : gérer les conflits de changement](how-to-manage-change-conflicts.md)
- [Méthode DataContext (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Guide pratique pour affecter des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions (Concepteur O/R)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [Apport et soumission de modifications de données](making-and-submitting-data-changes.md)
