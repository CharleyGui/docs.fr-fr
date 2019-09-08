---
title: Opérations de traitement par lots (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 2a642bdfd6a8891c54c01a07609760bede2f5d5d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780500"
---
# <a name="batching-operations-wcf-data-services"></a>Opérations de traitement par lots (services de données WCF)
Le [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] prend en charge le traitement par lots [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]des demandes à un service basé sur. Pour plus d’informations, [consultez OData : Traitement](https://go.microsoft.com/fwlink/?LinkId=186075)par lots. Dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], chaque opération qui <xref:System.Data.Services.Client.DataServiceContext>utilise, telle que l’exécution d’une requête ou l’enregistrement de modifications, entraîne l’envoi d’une demande séparée au service de données. Pour maintenir une étendue logique pour les jeux d'opérations, vous pouvez définir explicitement des lots opérationnels. Cela garantit que toutes les opérations du lot sont envoyées au service de données dans une requête HTTP unique, permet au serveur de traiter les opérations de manière atomique et réduit le nombre d’allers-retours au service de données.  
  
## <a name="batching-query-operations"></a>Opérations de traitement par lot des requêtes  
 Pour exécuter plusieurs requêtes dans un lot unique, vous devez créer chaque requête dans le lot comme une instance distincte de la classe <xref:System.Data.Services.Client.DataServiceRequest%601>. Lorsque vous créez une requête d'interrogation de cette manière, la requête elle-même est définie comme un URI, et elle suit les règles pour l'adressage de ressources. Pour plus d’informations, consultez [accès aux ressources du service de données](accessing-data-service-resources-wcf-data-services.md). Les requêtes d'interrogation par lot sont envoyées au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> est appelée qui contient les objets de requête d'interrogation. Cette méthode retourne un objet <xref:System.Data.Services.Client.DataServiceResponse> qui est une collection d’objets <xref:System.Data.Services.Client.QueryOperationResponse%601> qui représentent des réponses aux requêtes individuelles dans le lot, chacune contenant une collection d’objets retournés par la requête ou des informations d’erreur. Lorsqu'une opération de requête unique dans le lot échoue, les informations d'erreur sont retournées dans l'objet <xref:System.Data.Services.Client.QueryOperationResponse%601> pour l'opération qui a échoué et les opérations restantes sont exécutées. Pour plus d’informations, consultez [Guide pratique pour Exécuter des requêtes dans un](how-to-execute-queries-in-a-batch-wcf-data-services.md)lot.  
  
 Les requêtes par lot peuvent également être exécutées de façon asynchrone. Pour plus d’informations, consultez [opérations asynchrones](asynchronous-operations-wcf-data-services.md).  
  
## <a name="batching-the-savechanges-operation"></a>Traitement par lot de l'opération SaveChanges  
 Lorsque vous appelez la <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> méthode, toutes les modifications apportées par les pistes de contexte sont traduites en opérations Rest envoyées en tant [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] que demandes au service. Par défaut, ces modifications ne sont pas envoyées dans un message de demande unique. Pour exiger que toutes les modifications soient envoyées dans une requête unique, vous devez appeler <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> la méthode et inclure une valeur <xref:System.Data.Services.Client.SaveChangesOptions.Batch> de dans <xref:System.Data.Services.Client.SaveChangesOptions> l’énumération que vous fournissez à la méthode.  
  
 Vous pouvez également enregistrer de façon asynchrone les modifications par lot. Pour plus d’informations, consultez [opérations asynchrones](asynchronous-operations-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)
