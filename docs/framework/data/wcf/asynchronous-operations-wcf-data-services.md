---
title: Opérations asynchrones (services de données WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 3e8d3ec46362751ea8bbfe5120e35a050d0e7a6c
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569359"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Opérations asynchrones (services de données WCF)
Les applications Web doivent gérer une latence plus élevée entre le client et le serveur, comparé aux applications qui s'exécutent sur des réseaux internes. Pour optimiser les performances et l’expérience utilisateur de votre application, nous vous recommandons d’utiliser les méthodes asynchrones des <xref:System.Data.Services.Client.DataServiceContext> et des classes <xref:System.Data.Services.Client.DataServiceQuery%601> lors de l’accès aux serveurs de WCF Data Services sur le Web.  
  
 Bien que les serveurs WCF Data Services traitent les requêtes HTTP de façon asynchrone, certaines méthodes des bibliothèques clientes WCF Data Services sont synchrones et attendent la fin de la totalité de l’échange requête-réponse avant de poursuivre l’exécution. Les méthodes asynchrones des bibliothèques clientes WCF Data Services n’attendent pas que cet échange se termine et peuvent permettre à votre application de gérer une interface utilisateur réactive en attendant.  
  
 Vous pouvez effectuer des opérations asynchrones à l’aide d’une paire de méthodes sur les <xref:System.Data.Services.Client.DataServiceContext> et <xref:System.Data.Services.Client.DataServiceQuery%601> les classes qui commencent respectivement par *Begin* et *end* . Les méthodes *Begin* inscrivent un délégué appelé par le service lorsque l’opération est terminée. Les méthodes *end* doivent être appelées dans le délégué inscrit pour gérer le rappel des opérations terminées. Quand vous appelez la méthode *end* pour terminer une opération asynchrone, vous devez le faire à partir du même <xref:System.Data.Services.Client.DataServiceQuery%601> ou <xref:System.Data.Services.Client.DataServiceContext> instance que vous avez utilisé pour commencer l’opération. Chaque méthode *Begin* prend un paramètre `state` qui peut passer un objet d’État au rappel. Cet objet d’État est récupéré à partir de l' <xref:System.IAsyncResult> fourni avec le rappel et permet d’appeler la méthode *end* correspondante pour terminer l’opération asynchrone. Par exemple, lorsque vous fournissez l'instance <xref:System.Data.Services.Client.DataServiceQuery%601> comme paramètre `state` lorsque vous appelez la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> sur l'instance, la même instance <xref:System.Data.Services.Client.DataServiceQuery%601> est retournée par <xref:System.IAsyncResult>. Puis cette instance de <xref:System.Data.Services.Client.DataServiceQuery%601> est utilisée pour appeler la méthode <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> pour terminer l'opération de requête. Pour plus d’informations, consultez [Comment : exécuter des requêtes de service de données asynchrones](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
> Seules les opérations asynchrones sont prises en charge par les bibliothèques clientes fournies dans le .NET Framework pour Silverlight. Pour plus d’informations, consultez [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Les bibliothèques clientes .NET Framework prennent en charge les opérations asynchrones suivantes :  
  
|Opération|Méthodes|  
|---------------|-------------|  
|Exécution d'un <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Exécution d'une requête du <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Exécution d'une requête par lot du <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Chargement d'une entité connexe dans <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Enregistrement des modifications apportées aux objets dans <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Considérations sur le threading relatives aux opérations asynchrones  
 Dans une application multithread, le délégué inscrit comme rappel pour l’opération asynchrone n’est pas nécessairement appelé sur le même thread que celui utilisé pour appeler la méthode *Begin* , ce qui crée la demande initiale. Dans une application où le rappel doit être appelé sur un thread spécifique, vous devez marshaler explicitement l’exécution de la méthode *end* , qui gère la réponse, vers le thread souhaité. Par exemple, dans les applications WPF (Windows Presentation Foundation) et Silverlight, la réponse doit être remarshalée au thread de l’interface utilisateur en utilisant la méthode <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> sur l’objet <xref:System.Windows.Threading.Dispatcher>. Pour plus d’informations, consultez [interrogation du service de données (WCF Data Services/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)
