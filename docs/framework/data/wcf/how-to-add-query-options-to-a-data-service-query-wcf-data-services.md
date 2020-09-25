---
title: 'Comment : ajouter des options de requête à une requête de services de données (services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 76d2b1ff3cbb5440bfed62ba840e646cf68de025
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180723"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Comment : ajouter des options de requête à une requête de services de données (services de données WCF)

WCF Data Services vous permet d’interroger un service de données à partir d’une application cliente basée sur .NET Framework à l’aide des classes de service de données client générées. Le plus simple est de composer une expression de requête LINQ (Language Integrated Query) qui inclut les options de requête souhaitées. Vous pouvez également appeler une série de méthodes de requête LINQ pour composer une requête équivalente. Enfin, vous pouvez utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pour ajouter des options de requête à une requête. Dans tous ces cas, l'URI généré par le client inclut le jeu d'entités demandé et les options de requête sélectionnées appliquées. Pour plus d’informations, consultez [interrogation du service de données](querying-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment composer une expression de requête LINQ qui retourne uniquement les commandes dont le coût de fret est supérieur à $30 et qui classe les résultats selon la date d'expédition dans l'ordre décroissant.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment composer une requête LINQ à l'aide d'une des méthodes de requête LINQ équivalente à la requête précédente.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant indique comment utiliser la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pour créer un <xref:System.Data.Services.Client.DataServiceQuery%601> équivalent aux exemples précédents.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment utiliser l'option de requête `$orderby` pour filtrer et classer les objets Orders retournés par la propriété Freight.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Voir aussi

- [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)
- [Procédure : Projeter des résultats de requête](how-to-project-query-results-wcf-data-services.md)
