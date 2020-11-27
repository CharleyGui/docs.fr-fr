---
title: Configuration du suivi de flux de messages
ms.date: 03/30/2017
ms.assetid: 15571ca2-bee2-47fb-ba10-fcbc09152ad0
ms.openlocfilehash: 6c271c26eb4e57014b3aaebf306b283bd06c7119
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254881"
---
# <a name="configuring-message-flow-tracing"></a>Configuration du suivi de flux de messages

Lorsque le suivi d’activité Windows Communication Foundation (WCF) est activé, les ID d’activité de bout en bout sont affectés aux activités logiques dans la pile WCF. Il existe désormais dans [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)], une version plus performante de cette fonctionnalité qui fonctionne avec ETW (Suivi d'événements Windows), appelée le suivi de flux de messages. Lorsqu'il est activé, les ID d'activité de bout en bout sont extraits des messages entrants (ou leur sont affectés, s'ils sont vides) et sont propagés à tous les événements de suivi émis une fois que le message a été décodé par le canal. Les clients peuvent utiliser cette fonctionnalité pour reconstruire des flux de messages avec les journaux de suivi de différents services après décodage.  
  
 Le suivi peut être activé lorsqu'un problème a été détecté avec l'application, puis désactivé une fois le problème résolu.  
  
## <a name="enabling-tracing"></a>Activation du traçage  

 Vous pouvez activer le suivi de flux de messages en définissant l'élément de configuration `messageFlowTracing` du .NET Framework 4 sur `true`, comme indiqué dans l'exemple suivant.  
  
```xml  
<system.servicemodel>  
  <diagnostics>  
    <endToEndTracing propagateActivity="true" messageFlowTracing="true" />  
  </diagnostics>  
</system.servicemodel>  
```  
  
> [!NOTE]
> Étant donné que l'élément de configuration `endToEndTracing` réside dans un fichier Web.config, il ne peut pas être configuré dynamiquement de la même manière qu'ETW. Pour que l'élément de configuration `endToEndTracing` entre en vigueur, l'application doit être recyclée.  
  
 Les activités sont corrélées par l'échange d'un identificateur qu'on appelle l'ID d'activité. Cet identificateur est un GUID généré par la classe System.Diagnostics.CorrelationManager. Si vous modifiez System.Diagnostics.Trace.CorrelationManager.ActivityID, assurez-vous que la valeur d'origine est définie lorsque le contrôle d'exécution retourne le code WCF.  Par ailleurs, si vous utilisez un modèle de programmation WCF asynchrone, assurez-vous que System.Diagnostics.Trace.CorrelationManager.ActivityID est transféré entre les threads.  
  
## <a name="message-flow-tracing-and-rest-services"></a>Traçage de flux de messages et services REST  

 Le traçage de flux de messages vous permet de tracer une requête de bout en bout.  Avec les services SOAP, un ID d'activité est envoyé dans un en-tête de message SOAP. Les demandes REST ne contiennent pas d'en-tête , par conséquent, un en-tête d'événement HTTP spécial est utilisé à la place. L'extrait de code suivant affiche illustre comment récupérer par programme la valeur d'ID d'activité :  
  
```csharp
Object output = null;
if (OperationContext.Current.IncomingMessageProperties.TryGetValue(HttpRequestMessageProperty.Name, out output))
{
   HttpRequestMessageProperty httpHeaders = output as HttpRequestMessageProperty;
   // Retrieve the Activity Id from the HTTP header    string e2eId = httpHeaders.Headers["E2EActivity"];
   // ...
}
```

 Ajoutez l'en-tête par programme à l'aide du code suivant :  
  
```csharp  
HttpContent content = new StreamContent(contentStream);  
Guid correlation = Guid.NewGuid();  
content.Headers.Add("E2EActivity", Convert.ToBase64String(correlation.ToByteArray()));  
```
