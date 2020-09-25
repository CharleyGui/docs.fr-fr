---
title: Chargement de contenu différé (services de données WCF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: 6eff454bf4f79f7fe215828956ffe79d0c1f6757
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194321"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Chargement de contenu différé (services de données WCF)

Par défaut, WCF Data Services limite la quantité de données retournées par une requête. Toutefois, vous pouvez charger explicitement des données supplémentaires, notamment les entités connexes, les données de réponse paginées et les flux de données binaires, à partir du service de données si nécessaire. Cette rubrique décrit comment charger un contenu différé dans votre application.  
  
## <a name="related-entities"></a>Entités connexes  

 Lorsque vous exécutez une requête, seules les entités dans le jeu d'entités traitées sont retournées. Par exemple, lorsqu'une requête exécutée sur le service de données Northwind retourne les entités `Customers`, par défaut, les entités `Orders` connexes ne sont pas retournées, même s'il existe une relation entre `Customers` et `Orders`. De plus, lorsque la pagination est autorisée dans le service de données, vous devez charger explicitement les pages de données suivantes à partir du service. Il y a deux façons de charger des entités connexes :  
  
- **Chargement hâtif**: vous pouvez utiliser l' `$expand` option de requête pour demander à ce que la requête retourne les entités qui sont liées par une association au jeu d’entités que la requête a demandée. Utilisez la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> sur le <xref:System.Data.Services.Client.DataServiceQuery%601> pour ajouter l'option `$expand` à la requête envoyée au service de données. Vous pouvez demander plusieurs jeux d'entités connexes en les séparant par une virgule, comme dans l'exemple suivant. Toutes les entités demandées par la requête sont retournées dans une réponse unique. L'exemple de code suivant retourne `Order_Details` et `Customers` ainsi que le jeu d'entités `Orders` :  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     WCF Data Services limite à 12 le nombre de jeux d’entités qui peuvent être inclus dans une requête unique à l’aide de l' `$expand` option de requête.  
  
- **Chargement explicite**: vous pouvez appeler la <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> méthode sur l' <xref:System.Data.Services.Client.DataServiceContext> instance pour charger explicitement des entités connexes. Chaque appel à la méthode <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> crée une demande séparée au service de données. L'exemple suivant charge explicitement `Order_Details` pour une entité `Orders` :  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Au moment de choisir l'option à utiliser, sachez qu'il y a une corrélation entre le nombre de demandes adressées au service de données et la quantité de données retournées dans une réponse individuelle. Utilisez le chargement hâtif lorsque votre application requiert des objets associés et que vous souhaitez éviter la latence liée aux demandes supplémentaires nécessaires à leur récupération explicite. Toutefois, s'il y a des cas où l'application ne nécessite que les données pour les instances d'entité connexes spécifiques, vous devez envisager de charger explicitement ces entités en appelant la méthode <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A>. Pour plus d’informations, consultez [Comment : charger des entités connexes](how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Contenu paginé  

 Lorsque la pagination est autorisée dans le service de données, le nombre d'entrées dans le flux qui sont retournées par le service de données est limité par la configuration du service de données. Des limites de pPage peuvent être définies séparément pour chaque jeu d'entités. Pour plus d’informations, consultez [configuration du service de données](configuring-the-data-service-wcf-data-services.md). Lorsque la pagination est activée, la dernière entrée dans le flux contient un lien vers la page suivante de données. Ce lien est contenu dans un objet <xref:System.Data.Services.Client.DataServiceQueryContinuation%601>. Vous obtenez l'URI vers la page suivante de données en appelant la méthode <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> sur le <xref:System.Data.Services.Client.QueryOperationResponse%601> retourné lorsque <xref:System.Data.Services.Client.DataServiceQuery%601> est exécuté. L'objet <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> retourné est ensuite utilisé pour charger la page suivante de résultats. Vous devez énumérer le résultat de la requête avant d'appeler la méthode <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A>. Envisagez d'utiliser une boucle `do…while` pour énumérer en premier le résultat de la requête, puis rechercher une valeur `non-null` de lien suivante. Lorsque la méthode <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> retourne `null` (`Nothing` en Visual Basic), il n'y a aucune page de résultat supplémentaire pour la requête d'origine. L'exemple suivant affiche une boucle `do…while` qui charges des données clientes paginées depuis l'exemple de service de données Northwind.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Lorsqu'une requête demande que les entités connexes soient retournées dans une réponse unique avec le jeu d'entités demandé, des limites de pagination peuvent affecter les flux imbriqués inclus inline avec la réponse. Par exemple, lorsqu'une limite de pagination est définie dans l'exemple de service de données Northwind pour le jeu d'entités `Customers`, une limite de pagination indépendante peut également être définie pour le jeu d'entités `Orders` connexe, comme dans l'exemple suivant du fichier Northwind.svc.cs qui définit l'exemple de service de données Northwind.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 Dans ce cas, vous devez implémenter la pagination pour le `Customers` de niveau supérieur et les flux d'entité `Orders` imbriqués. L'exemple suivant montre la boucle `while` utilisée pour charger des pages d'entités `Orders` associées à une entité `Customers` sélectionnée.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Pour plus d’informations, consultez [Comment : charger des résultats paginés](how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Flux de données binaires  

 WCF Data Services vous permet d’accéder à des données BLOB (Binary Large Object) en tant que flux de données. La diffusion en continu diffère le chargement des données binaires tant qu'elles ne sont pas nécessaires, et le client peut traiter ces données plus efficacement. Pour tirer parti de ces fonctionnalités, le service de données doit implémenter le fournisseur <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Pour plus d’informations, consultez la page [fournisseur de streaming](streaming-provider-wcf-data-services.md). Lorsque la diffusion en continu est activée, les types d'entité sont retournés sans les données binaires associées. Dans ce cas, vous devez utiliser la <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> méthode de la <xref:System.Data.Services.Client.DataServiceContext> classe pour accéder au flux de données pour les données binaires du service. De la même façon, utilisez la méthode <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> pour ajouter ou modifier les données binaires pour une entité comme un flux de données. Pour plus d’informations, consultez [utilisation de données binaires](working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
- [Interrogation du service de données](querying-the-data-service-wcf-data-services.md)
