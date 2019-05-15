---
title: 'Procédure : Exécuter directement des requêtes SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 04353361f8356b1d2b2aa3b930bb9b5ab88b9c0b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583686"
---
# <a name="how-to-directly-execute-sql-queries"></a>Procédure : Exécuter directement des requêtes SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez dans les requêtes SQL paramétrées (sous forme textuelle) et les envoie au serveur SQL pour traitement.  
  
 SQL ne peut pas exécuter les diverses méthodes qui peuvent être localement disponibles pour votre application. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] essaie de convertir ces méthodes locales en opérations et fonctions équivalentes qui sont disponibles à l'intérieur de l'environnement SQL. La plupart des méthodes et opérateurs sur les types intégrés .NET Framework ont des traductions directes en commandes SQL. Certains peuvent être produits à partir des fonctions disponibles. Ceux qui ne peuvent pas être produits génèrent des exceptions runtime. Pour plus d’informations, consultez [le mappage de Type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Dans les cas où une requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] est insuffisante pour une tâche spécialisée, vous pouvez utiliser la méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> pour exécuter une requête SQL, puis convertir directement le résultat de votre requête en objets.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, supposons que les données de la classe `Customer` sont réparties sur deux tables (customer1 et customer2). La requête retourne une séquence d'objets `Customer`.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Tant que les noms de colonne dans les résultats sous forme de tableau correspondent aux propriétés des colonnes de votre classe d’entité, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée vos objets à partir de n’importe quelle requête SQL.  
  
## <a name="example"></a>Exemple  
 La méthode <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> autorise également les paramètres. Utilisez un code similaire à l'exemple de code suivant pour exécuter une requête paramétrée.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Les paramètres sont exprimés dans le texte de requête en utilisant la même notation avec accolades utilisée par `Console.WriteLine()` et `String.Format()`. En fait, `String.Format()` est réellement appelé sur la chaîne de requête que vous fournissez, en remplaçant les paramètres entre accolades avec générés tels que les noms de paramètres @p0, @p1 ..., @p(n).  
  
## <a name="see-also"></a>Voir aussi

- [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Interrogation de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
