---
title: 'Comment : appeler des fonctions de base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: a4cf77000af56ed2a6445beaef2d7856486b85db
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173664"
---
# <a name="how-to-call-database-functions"></a>Comment : appeler des fonctions de base de données

La classe <xref:System.Data.Objects.SqlClient.SqlFunctions> contient des méthodes qui exposent les fonctions SQL Server à utiliser dans les requêtes LINQ to Entities. Lorsque vous utilisez des méthodes <xref:System.Data.Objects.SqlClient.SqlFunctions> dans les requêtes LINQ to Entities, les fonctions de base de données correspondantes sont exécutées dans la base de données.  
  
> [!NOTE]
> Les fonctions de base de données qui effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique (également appelées fonctions de base de données d'agrégation) peuvent être appelées directement. Les autres fonctions canoniques peuvent être appelées uniquement dans le cadre d'une requête LINQ to Entities. Pour appeler directement une fonction d'agrégation, vous devez passer un objet <xref:System.Data.Objects.ObjectQuery%601> à la fonction. Pour plus d'informations, consultez le second exemple ci-dessous.  
  
> [!NOTE]
> Les méthodes dans la classe <xref:System.Data.Objects.SqlClient.SqlFunctions> sont spécifiques aux fonctions SQL Server. Des classes semblables qui exposent des fonctions de base de données peuvent être disponibles via d'autres fournisseurs.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). L'exemple exécute une requête LINQ to Entities qui utilise la méthode <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> pour retourner tous les contacts dont le nom commence par « Si » :  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). L'exemple appelle directement la méthode d'agrégation <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A>. Notez qu'un <xref:System.Data.Objects.ObjectQuery%601> est passé à la fonction, ce qui lui permet d'être appelée même si elle ne figure pas dans une requête LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- [Appel de fonctions dans les requêtes LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
