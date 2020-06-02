---
title: 'Comment : exécuter directement des requêtes SQL'
description: Découvrez comment utiliser ExecuteQuery pour exécuter une requête, puis convertir les résultats directement en objets dans les cas où une requête LINQ to SQL est insuffisante.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 59bd404e41f6be1181d6a625c31ee23358db0df3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286363"
---
# <a name="how-to-directly-execute-sql-queries"></a>Comment : exécuter directement des requêtes SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez dans les requêtes SQL paramétrées (sous forme textuelle) et les envoie au serveur SQL pour traitement.  
  
 SQL ne peut pas exécuter les diverses méthodes qui peuvent être localement disponibles pour votre application. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] essaie de convertir ces méthodes locales en opérations et fonctions équivalentes qui sont disponibles à l'intérieur de l'environnement SQL. La plupart des méthodes et opérateurs sur .NET Framework types intégrés ont des traductions directes vers les commandes SQL. Certains peuvent être produits à partir des fonctions disponibles. Ceux qui ne peuvent pas être produits génèrent des exceptions runtime. Pour plus d’informations, consultez [mappage de type SQL-CLR](sql-clr-type-mapping.md).  
  
 Dans les cas où une requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est insuffisante pour une tâche spécialisée, vous pouvez utiliser la méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> pour exécuter une requête SQL, puis convertir directement le résultat de votre requête en objets.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, supposons que les données de la classe `Customer` sont réparties sur deux tables (customer1 et customer2). La requête retourne une séquence d'objets `Customer`.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Tant que les noms des colonnes dans les résultats tabulaires correspondent aux propriétés des colonnes de votre classe d’entité, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée vos objets à partir d’une requête SQL.  
  
## <a name="example"></a>Exemple  
 La méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> autorise également les paramètres. Utilisez un code similaire à l'exemple de code suivant pour exécuter une requête paramétrée.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Les paramètres sont exprimés dans le texte de requête en utilisant la même notation avec accolades utilisée par `Console.WriteLine()` et `String.Format()`. En fait, `String.Format()` est appelé dans la chaîne de requête que vous fournissez, en remplaçant les paramètres par des accolades par des noms de paramètre générés tels que @p0 , @p1 ..., @p (n).  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](background-information.md)
- [Interrogation de la base de données](querying-the-database.md)
