---
title: Consultation des journaux de messages
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: c8313b14a45051b7828a1ab223a3da63b2e7a153
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291152"
---
# <a name="viewing-message-logs"></a>Consultation des journaux de messages

Cette rubrique contient des instructions permettant d'afficher les journaux des messages.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>Consultation des journaux de messages dans Service Trace Viewer  

 Un message est transformé au fur et à mesure qu’il est traité par WCF. Par conséquent, un message consigné reflète uniquement le contenu du message au moment où il a été consigné, et non pas le contenu sur le câble.  
  
 Comme la sortie de l'enregistrement des messages n'est pas liée au format de transfert du message, l'enregistrement des messages génère le message décodé. Si vous avez configuré l'enregistrement des messages correctement, tout message enregistré doit être au format de texte brut. Par exemple, le format (texte brut) des messages enregistrés n'est pas affecté par l'utilisation d'un encodeur de message binaire.  
  
 La sortie de XmlWriterTraceListener est un fichier qui contient une séquence de fragments XML. Sachez qu'il ne s'agit pas d'un fichier XML valide. Il est recommandé d’utiliser l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) pour afficher les fichiers journaux des messages. Pour plus d’informations sur l’utilisation de cet outil, consultez [utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Dans Service Trace Viewer, les messages sont répertoriés sous l’onglet **message** . Les messages qui ont provoqué, ou sont liés à, une erreur de traitement sont mis en surbrillance en jaune (niveau d’avertissement) ou rouge (niveau d’erreur), en fonction de la gravité de l’erreur. Si vous double-cliquez sur le message, le suivi du message s'affiche dans le contexte de la demande.  
  
> [!NOTE]
> Si un message n'a pas d'en-tête, aucune balise `<header/>` n'est enregistrée.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Consultation des messages consignés par un client, un relais et un service  

 Votre environnement peut contenir un client, qui envoie un message à un relais, qui par la suite envoie le message au service. Lorsque la journalisation des messages est activée sur les trois emplacements, et que les trois journaux des messages sont affichés simultanément dans l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) , les échanges de journaux de messages ne sont pas restitués correctement. Cela est dû au fait que `CorrelationId` et `ActivityId` dans l'en-tête de message ne sont pas uniques pour chaque paire émetteur-récepteur.  
  
 Pour résoudre ce problème, utilisez l'une des méthodes suivantes :  
  
- Affichez uniquement deux des trois journaux de messages dans l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) à tout moment.  
  
- Si vous devez afficher les trois journaux dans l' [outil Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) en même temps, vous pouvez modifier le service de relais en créant une nouvelle <xref:System.ServiceModel.Channels.Message> instance. Cette instance doit être une copie du corps du message entrant et de tous les en-têtes à l'exception de `ActivityId` et `Action`. L'exemple de code suivant montre comment procéder.  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Cas exceptionnels de contenu de journalisation de message inexact  

 Dans les conditions suivantes, les messages consignés peuvent ne pas être la représentation exacte du flux d'octets présent sur le câble.  
  
- Concernant BasicHttpBinding, les en-têtes d'enveloppe sont enregistrés pour les messages entrants de l'espace de noms /addressing/none.  
  
- Les espaces blancs peuvent être incompatibles.  
  
- Concernant les messages entrants, les éléments vides peuvent être représentés différemment. Par exemple, \<tag> \</tag> au lieu de\<tag/>  
  
- Lorsque la journalisation PII connue est désactivée soit par défaut, soit par le paramètre explicite enableLoggingKnownPii= "true".  
  
- L'encodage est activé pour la conversion au format UTF-8.  
  
## <a name="see-also"></a>Voir aussi

- [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](./tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Journalisation des messages](message-logging.md)
