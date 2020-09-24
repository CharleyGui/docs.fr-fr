---
title: Opérations de traitement par lots (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 95524c1397172e645d682a6ef3f03b17bb3a639d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166064"
---
# <a name="batching-operations-wcf-data-services"></a>Opérations de traitement par lots (services de données WCF)

Le Open Data Protocol (OData) prend en charge le traitement par lots des demandes à un service OData. Pour plus d’informations, consultez [OData : traitement par lots](https://www.odata.org/documentation/odata-version-2-0/batch-processing/). Dans WCF Data Services, chaque opération qui utilise <xref:System.Data.Services.Client.DataServiceContext> , telle que l’exécution d’une requête ou l’enregistrement de modifications, entraîne l’envoi d’une demande séparée au service de données. Pour maintenir une étendue logique pour les jeux d'opérations, vous pouvez définir explicitement des lots opérationnels. Cela garantit que toutes les opérations dans le lot sont envoyées au service de données dans une requête HTTP unique, et cela permet au serveur de traiter les opérations de manière atomique et de réduire le nombre de boucles vers le service de données.  
  
## <a name="batching-query-operations"></a>Opérations de traitement par lot des requêtes  

 Pour exécuter plusieurs requêtes dans un lot unique, vous devez créer chaque requête dans le lot comme une instance distincte de la classe <xref:System.Data.Services.Client.DataServiceRequest%601>. Lorsque vous créez une requête d'interrogation de cette manière, la requête elle-même est définie comme un URI, et elle suit les règles pour l'adressage de ressources. Pour plus d’informations, consultez [accès aux ressources du service de données](accessing-data-service-resources-wcf-data-services.md). Les requêtes d'interrogation par lot sont envoyées au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> est appelée qui contient les objets de requête d'interrogation. Cette méthode retourne un objet <xref:System.Data.Services.Client.DataServiceResponse> qui est une collection d’objets <xref:System.Data.Services.Client.QueryOperationResponse%601> qui représentent des réponses aux requêtes individuelles dans le lot, chacune contenant une collection d’objets retournés par la requête ou des informations d’erreur. Lorsqu'une opération de requête unique dans le lot échoue, les informations d'erreur sont retournées dans l'objet <xref:System.Data.Services.Client.QueryOperationResponse%601> pour l'opération qui a échoué et les opérations restantes sont exécutées. Pour plus d’informations, consultez [Comment : exécuter des requêtes dans un lot](how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Les requêtes par lot peuvent également être exécutées de façon asynchrone. Pour plus d’informations, consultez [opérations asynchrones](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Traitement par lot de l'opération SaveChanges  

 Lorsque vous appelez la <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> méthode, toutes les modifications apportées par les pistes de contexte sont traduites en opérations Rest envoyées en tant que demandes au service OData. Par défaut, ces modifications ne sont pas envoyées dans un message de demande unique. Pour exiger que toutes les modifications soient envoyées dans une requête unique, vous devez appeler la <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> méthode et inclure une valeur de <xref:System.Data.Services.Client.SaveChangesOptions.Batch> dans l' <xref:System.Data.Services.Client.SaveChangesOptions> énumération que vous fournissez à la méthode.  
  
 Vous pouvez également enregistrer de façon asynchrone les modifications par lot. Pour plus d’informations, consultez [opérations asynchrones](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
