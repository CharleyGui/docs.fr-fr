---
title: Propagation
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 732ae5cb1ce311b78728f8d5de0fd9102bf32499
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578953"
---
# <a name="propagation"></a>Propagation
Cette rubrique décrit la propagation d’activité dans le modèle de suivi Windows Communication Foundation (WCF).  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a>Utilisation de la propagation pour corréler des activités sur des points de terminaison  
 La propagation fournit à l'utilisateur la corrélation directe de suivi d'erreur pour la même unité de traitement sur des points de terminaison d'application, par exemple, une demande. Les erreurs émises à des points de terminaison différents pour la même unité de traitement sont groupées dans la même activité, y compris sur les domaines d'application. Cette opération s'effectue par la propagation de l'ID d'activité dans les en-têtes de message. Par conséquent, en cas d'expiration d'un client à cause d'une erreur interne dans le serveur, les deux erreurs apparaissent dans la même activité pour une corrélation directe.  
  
 Pour ce faire, utilisez le paramètre `ActivityTracing` comme indiqué dans l'exemple précédent. Définissez aussi l'attribut `propagateActivity` pour la source de suivi `System.ServiceModel` à tous les points de terminaison.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 La propagation d’activité est une fonctionnalité configurable qui amène WCF à ajouter un en-tête aux messages sortants, qui comprend l’ID d’activité sur le TLS. En incluant ces informations dans les suivis ultérieurs sur le côté serveur, il est possible de mettre en corrélation les activités de client et de serveur.  
  
## <a name="propagation-definition"></a>Définition de la propagation  
 Le gAId de l'activité M est propagé à l'activité N si toutes les conditions suivantes s'appliquent.  
  
- N est créé à cause de M  
  
- Le gAId de M est connu de N  
  
- Le gAId de N est égal au gAId de M.  
  
 Le gAId est propagé par l'en-tête de message ActivityId, comme illustré dans le schéma XML suivant.  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 Les éléments suivants sont un exemple de l'en-tête de message.  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a>Limites de propagation et d'activité  
 Lorsque l'ID d'activité est propagé sur des points de terminaison, le récepteur de message émet un suivi de démarrage et d'arrêt avec cet ID d'activité (propagé). Par conséquent, il y a un suivi de démarrage et d'arrêt avec ce gAId à partir de chaque source de suivi. Si les points de terminaison sont dans le même processus et utilisent le même nom de source de suivi, plusieurs suivis Démarrer et Arrêter ayant le même lAId (gAId identique, source de suivi et processus identiques) sont créés.  
  
## <a name="synchronization"></a>Synchronisation  
 Pour synchroniser des événements sur les points de terminaison qui s’exécutent sur des ordinateurs différents, CorrelationId est ajouté à l’en-tête ActivityId propagé dans les messages. Les outils peuvent utiliser cet ID pour synchroniser des événements sur des ordinateurs présentant des différences d'horloge. En particulier, l'outil Service Trace Viewer utilise cet ID pour afficher les flux de messages d'un point de terminaison à un autre.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration du traçage](configuring-tracing.md)
- [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénarios de suivi de bout en bout](end-to-end-tracing-scenarios.md)
- [Outil Service Trace Viewer (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
