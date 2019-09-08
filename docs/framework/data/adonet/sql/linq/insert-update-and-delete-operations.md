---
title: Opérations d'insertion, de mise à jour et de suppression
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: fac89f905b85493bc0ec36a85635f369bb354266
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793056"
---
# <a name="insert-update-and-delete-operations"></a>Opérations d'insertion, de mise à jour et de suppression

Pour effectuer des opérations d'`Insert`, de `Update` et de `Delete` dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ajoutez, modifiez et supprimez des objets dans votre modèle objet. Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit vos actions en SQL et soumet les modifications à la base de données.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]offre une flexibilité maximale pour la manipulation et la persistance des modifications que vous avez apportées à vos objets. Dès que des objets d'entité sont disponibles (objets récupérés via une requête ou reconstruits), vous pouvez les modifier comme des objets standard de votre application. En d’autres termes, vous pouvez modifier leurs valeurs, vous pouvez les ajouter à vos collections et les supprimer de vos collections. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suit vos modifications et est prêt à les renvoyer à la base de données lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.

> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge ni ne reconnaît les opérations de suppression en cascade. Si vous souhaitez supprimer une ligne d’une table qui contient des contraintes, vous devez définir la `ON DELETE CASCADE` règle dans la contrainte FOREIGN-KEY dans la base de données ou utiliser votre propre code pour supprimer en premier les objets enfants qui empêchent la suppression de l’objet parent. Sinon, une exception est levée. Pour plus d'informations, voir [Procédure : Supprimer des lignes de la](how-to-delete-rows-from-the-database.md)base de données.

Les extraits suivants utilisent les classes `Customer` et `Order` de l'exemple de base de données Northwind. Les définitions de classe ne sont pas présentées pour des raisons de concision.

[!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
[!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]

Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère automatiquement et exécute les commandes SQL requises pour renvoyer vos modifications à la base de données.

> [!NOTE]
> Vous pouvez substituer ce comportement en utilisant votre propre logique personnalisée, en général au moyen d'une procédure stockée. Pour plus d’informations, consultez [responsabilités du développeur en matière de substitution du comportement par défaut](responsibilities-of-the-developer-in-overriding-default-behavior.md).
>
> Les développeurs qui utilisent Visual Studio peuvent utiliser le Concepteur Objet Relationnel pour développer des procédures stockées à cet effet.

## <a name="see-also"></a>Voir aussi

- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
- [Personnalisation des opérations d’insertion, de mise à jour et de suppression](customizing-insert-update-and-delete-operations.md)
