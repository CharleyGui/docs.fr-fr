---
title: 'Procédure : Exécuter directement des requêtes SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: a4971bc05b22c38790c5fd1493e70cccf5eaae16
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793782"
---
# <a name="how-to-directly-execute-sql-queries"></a>Procédure : Exécuter directement des requêtes SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez dans les requêtes SQL paramétrées (sous forme textuelle) et les envoie au serveur SQL pour traitement.  
  
 SQL ne peut pas exécuter les diverses méthodes qui peuvent être localement disponibles pour votre application. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] essaie de convertir ces méthodes locales en opérations et fonctions équivalentes qui sont disponibles à l'intérieur de l'environnement SQL. La plupart des méthodes et opérateurs sur .NET Framework types intégrés ont des traductions directes vers les commandes SQL. Certains peuvent être produits à partir des fonctions disponibles. Ceux qui ne peuvent pas être produits génèrent des exceptions runtime. Pour plus d’informations, consultez [mappage de type SQL-CLR](sql-clr-type-mapping.md).  
  
 Dans les cas où une requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est insuffisante pour une tâche spécialisée, vous pouvez utiliser la méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> pour exécuter une requête SQL, puis convertir directement le résultat de votre requête en objets.  
  
## <a name="example"></a>Exemples  
 Dans l'exemple suivant, supposons que les données de la classe `Customer` sont réparties sur deux tables (customer1 et customer2). La requête retourne une séquence d'objets `Customer`.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Tant que les noms des colonnes dans les résultats tabulaires correspondent aux propriétés des colonnes de votre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] classe d’entité, crée vos objets à partir d’une requête SQL.  
  
## <a name="example"></a>Exemple  
 La méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> autorise également les paramètres. Utilisez un code similaire à l'exemple de code suivant pour exécuter une requête paramétrée.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Les paramètres sont exprimés dans le texte de requête en utilisant la même notation avec accolades utilisée par `Console.WriteLine()` et `String.Format()`. En fait, `String.Format()` est appelé dans la chaîne de requête que vous fournissez, en remplaçant les paramètres par des accolades par des noms de @p0paramètre @p1 générés tels que @p,..., (n).  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
- [Interrogation de la base de données](querying-the-database.md)
