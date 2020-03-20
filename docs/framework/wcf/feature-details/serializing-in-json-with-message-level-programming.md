---
title: Sérialisation dans JSON avec programmation de niveau message
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 36459dbc0ddee883678a98a27f9abb74fde78e86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184497"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Sérialisation dans JSON avec programmation de niveau message
WCF prend en charge la sérialisation des données au format JSON. Cette rubrique explique comment indiquer à WCF de sérialiser vos types à l'aide de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Programmation de message typé  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est utilisé lorsque <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> est appliqué à une opération de service. Les deux attributs vous permettent de spécifier `RequestFormat` et `ResponseFormat`. Utiliser JSON pour les demandes et réponses. définir ces deux `WebMessageFormat.Json`à .  Afin d’utiliser JSON, vous <xref:System.ServiceModel.WebHttpBinding>devez utiliser le <xref:System.ServiceModel.Description.WebHttpBehavior>, qui configure automatiquement le . Pour plus d’informations sur la sérialisation WCF, voir [La sérialisation et la désétérialisation](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Pour plus d’informations sur JSON et WCF, voir [Station-service - Une introduction aux services RESTful avec WCF](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).  
  
> [!IMPORTANT]
> L'utilisation de JSON requiert l'utilisation de <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior> qui ne prennent pas en charge la communication SOAP. Les services qui <xref:System.ServiceModel.WebHttpBinding> communiquent avec les métadonnées de service ne prennent pas en charge l’exposition des métadonnées de service de sorte que vous ne serez pas en mesure d’utiliser la fonctionnalité Add Service Reference de Visual Studio ou l’outil de ligne de commande svcutil pour générer un proxy côté client. Pour plus d’informations sur la façon <xref:System.ServiceModel.WebHttpBinding>dont vous pouvez appeler les services programmatiques qui utilisent , voir [Comment consommer des services REST avec WCF](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).  
  
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

- [Intégration d'AJAX et prise en charge de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Sérialisation JSON autonome](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Sérialisation JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
