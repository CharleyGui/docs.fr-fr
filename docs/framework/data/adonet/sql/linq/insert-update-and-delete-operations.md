---
title: Opérations d'insertion, de mise à jour et de suppression
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fa3690ae74869f5dc0fbaa8d824d4aebca8ce724
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743058"
---
# <a name="insert-update-and-delete-operations"></a>Opérations d'insertion, de mise à jour et de suppression
Pour effectuer des opérations d'`Insert`, de `Update` et de `Delete` dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ajoutez, modifiez et supprimez des objets dans votre modèle objet. Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit vos actions en SQL et soumet les modifications à la base de données.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] offre une flexibilité maximale dans la manipulation et la persistance des modifications que vous avez apportées à vos objets. Dès que des objets d'entité sont disponibles (objets récupérés via une requête ou reconstruits), vous pouvez les modifier comme des objets standard de votre application. Autrement dit, vous pouvez modifier leurs valeurs, vous pouvez les ajouter à vos collections, et vous pouvez les supprimer à partir de vos collections. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suit vos modifications et est prêt à les renvoyer à la base de données lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge ni ne reconnaît les opérations de suppression en cascade. Si vous souhaitez supprimer une ligne dans une table comportant des contraintes par rapport à elle, vous devez définir le `ON DELETE CASCADE` règle dans la contrainte de clé étrangère dans la base de données, ou utiliser votre propre code pour supprimer en premier les objets enfants qui empêchent la suppression de l’objet parent. Sinon, une exception est levée. Pour plus d’informations, consultez [Guide pratique pour Supprimer des lignes de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Les extraits suivants utilisent les classes `Customer` et `Order` de l'exemple de base de données Northwind. Les définitions de classe ne sont pas présentées pour des raisons de concision.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère automatiquement et exécute les commandes SQL requises pour renvoyer vos modifications à la base de données.  
  
> [!NOTE]
>  Vous pouvez substituer ce comportement en utilisant votre propre logique personnalisée, en général au moyen d'une procédure stockée. Pour plus d’informations, consultez [responsabilités du développeur de substitution par défaut comportement](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Les développeurs qui utilisent Visual Studio peuvent utiliser le concepteur objet/relationnel pour développer des procédures stockées à cet effet.  
  
## <a name="see-also"></a>Voir aussi

- [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Personnalisation des opérations d’insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
