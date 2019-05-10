---
title: Gestion des erreurs HTTP Web WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 491c39d97c48e2f92ff258ac42b9576d407b898e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648417"
---
# <a name="wcf-web-http-error-handling"></a>Gestion des erreurs HTTP Web WCF
Gestion d’erreurs HTTP Web Windows Communication Foundation (WCF) vous permet de retourner des erreurs à partir des services HTTP Web WCF qui spécifient un code d’état HTTP et de retournent les détails de l’erreur utilisent le même format que l’opération (par exemple, XML ou JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Gestion des erreurs HTTP Web WCF  
 La classe <xref:System.ServiceModel.Web.WebFaultException> définit un constructeur qui vous permet de spécifier un code d'état HTTP. Ce code d'état est alors retourné au client. Une version générique de la classe <xref:System.ServiceModel.Web.WebFaultException>, <xref:System.ServiceModel.Web.WebFaultException%601>, vous permet de retourner un type défini par l'utilisateur contenant des informations sur l'erreur qui s'est produite. Cet objet personnalisé est sérialisé à l'aide du format spécifié par l'opération et retourné au client. L'exemple suivant indique comment retourner un code d'état HTTP.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 L'exemple suivant montre comment retourner un code d'état HTTP et une information supplémentaire dans un type défini par l'utilisateur. `MyErrorDetail` est un type défini par l'utilisateur qui contient des informations supplémentaires à propos de l'erreur qui s'est produite.  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 Le code précédent retourne une réponse HTTP avec le code d'état interdit et un corps qui contient une instance de l'objet `MyErrorDetails`. Le format de l'objet `MyErrorDetails` est déterminé par :  
  
- la valeur du paramètre `ResponseFormat` de l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> spécifié sur l'opération de service ;  
  
- la valeur de la propriété <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> ;  
  
- la valeur de la propriété <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> en accédant à l'objet <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Pour plus d’informations sur la façon dont ces valeurs affectent la mise en forme de l’opération, consultez [mise en forme de WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> est un <xref:System.ServiceModel.FaultException> et par conséquent peut être utilisé comme le modèle de programmation d'exception d'erreur pour les services qui exposent des points de terminaison SOAP, ainsi que des points de terminaison HTTP Web.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle de programmation HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Mise en forme HTTP web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)
- [Définition et spécification des erreurs](../../../../docs/framework/wcf/defining-and-specifying-faults.md)
- [Gestion des exceptions et des erreurs](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)
- [Envoi et réception des erreurs](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
