---
title: Sérialisation dans JSON avec programmation de niveau message
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 7576594f8fa694ce2d34cf38c88d2e28a00f5295
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991131"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Sérialisation dans JSON avec programmation de niveau message
WCF prend en charge la sérialisation des données au format JSON. Cette rubrique explique comment indiquer à WCF de sérialiser vos types à l'aide de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Programmation de message typé  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est utilisé lorsque <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> est appliqué à une opération de service. Les deux attributs vous permettent de spécifier `RequestFormat` et `ResponseFormat`. Pour utiliser JSON pour les demandes et les réponses. Définissez les deux sur `WebMessageFormat.Json`.  Pour utiliser JSON, vous devez utiliser le <xref:System.ServiceModel.WebHttpBinding>, qui configure automatiquement le. <xref:System.ServiceModel.Description.WebHttpBehavior> Pour plus d’informations sur la sérialisation WCF, consultez [sérialisation et désérialisation](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Pour plus d’informations sur JSON et WCF, consultez [station de service-introduction aux services RESTful avec WCF](https://msdn.microsoft.com/magazine/dd315413.aspx).  
  
> [!IMPORTANT]
> L'utilisation de JSON requiert l'utilisation de <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior> qui ne prennent pas en charge la communication SOAP. Les services qui communiquent <xref:System.ServiceModel.WebHttpBinding> avec ne prennent pas en charge l’exposition des métadonnées de service. ainsi, vous ne pourrez pas utiliser les fonctionnalités de ajouter une référence de service de Visual Studio ou l’outil de ligne de commande Svcutil pour générer un proxy côté client. Pour plus d’informations sur la façon dont vous pouvez appeler par programmation <xref:System.ServiceModel.WebHttpBinding>des services qui utilisent, consultez [comment utiliser les services REST avec WCF](https://blogs.msdn.microsoft.com/pedram/2008/04/21/how-to-consume-rest-services-with-wcf/).  
  
## <a name="untyped-message-programming"></a>Programmation de message non typé  
 Lorsque utilisez directement des objets du message non typé, vous devez définir explicitement les propriétés sur le message non typé pour le sérialiser comme JSON. L'extrait de code suivant montre comment procéder.  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Voir aussi

- [Intégration d’AJAX et prise en charge de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Sérialisation JSON autonome](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Sérialisation JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
