---
title: Transférer
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 52b0cf35a2f8bab17252d3711f3143738c2bc39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587766"
---
# <a name="transfer"></a>Transférer
Cette rubrique décrit le transfert dans le modèle de suivi d’activité Windows Communication Foundation (WCF).  
  
## <a name="transfer-definition"></a>Définition d'un transfert  
 Les transferts entre activités représentent des liens de causalité entre événements dans les activités connexes dans des points de terminaison. Deux activités sont liées à des transferts lorsqu'un contrôle circule entre ces activités, par exemple, un appel de méthode qui traverse des limites d'activité. Dans WCF, lorsque les octets sont entrants sur le service, l’activité Listen at est transférée à l’activité Receive octets où l’objet message est créé. Pour obtenir la liste des scénarios de suivi de bout en bout, et leur conception d’activité et de suivi respective, consultez [scénarios de suivi de bout](end-to-end-tracing-scenarios.md)en bout.  
  
 Pour émettre des suivis de transfert, appliquez le paramètre `ActivityTracing` sur la source de suivi, tel que le montre le code de configuration suivant.  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>Utilisation du suivi Transfert pour corréler des activités dans des points de terminaison  
 Les activités et transferts permettent à l'utilisateur de rechercher de manière probabiliste la cause première d'une erreur. Par exemple, si nous transférons des données entre les activités M et N, dans les composants M et N, et qu'un incident se produit en N juste après le transfert vers M, il est possible de conclure que le problème provient du passage de données de N vers M.  
  
 Un suivi de transfert est émis de l'activité M vers l'activité N, lorsqu'il existe un flux de contrôle entre M et N. Par exemple, N exécute une tâche pour M à cause d'un appel de méthode franchissant les limites des activités. N existe peut-être déjà ou a été créé. N est généré par M lorsque N est une nouvelle activité qui exécute une tâche pour M.  
  
 Un transfert de M à N peut pas être suivi d'un transfert réciproque de N à M. Cela est dû au fait que M peut générer une tâche dans N sans assurer le suivi de l'exécution de cette tâche par N. En fait, M peut se terminer avant que N n’ait achevé sa tâche. Cela se produit dans l’activité « Open ServiceHost » (M) qui génère des activités d’écouteur (N), puis se termine. Un transfert de N à M indique que N a achevé la tâche liée à M.  
  
 N peut continuer à effectuer d'autres traitements non liés à M, par exemple, une activité d'authentificateur existante (N) qui continue à recevoir des demandes de connexion (M) provenant de différentes activités de connexion.  
  
 Il n'existe pas nécessairement de relation d'imbrication entre les activités M et N, et ce pour deux raisons : d'une part si l'activité M ne surveille pas le traitement réel effectué dans N bien qu'il ait initié ce traitement, d'autre part si N existe déjà.  
  
## <a name="example-of-transfers"></a>Exemples de transferts  
 Deux exemples de transferts sont présentés ci-dessous.  
  
- Lorsque vous créez un hôte de service, le constructeur prend le contrôle à partir du code appelant, ou le code appelant est transféré au constructeur. Lorsque le constructeur a terminé de s'exécuter, il retourne le contrôle au code appelant, ou le constructeur est transféré au code appelant. C'est le cas d'une relation imbriquée.  
  
- Lorsqu'un écouteur commence à traiter des données de transport, il crée un nouveau thread et remet à l'activité Recevoir des octets le contexte de traitement approprié, c'est-à-dire en passant le contrôle et les données. Lorsque ce thread a fini de traiter la demande, l'activité Recevoir des octets ne repasse aucune donnée à l'écouteur. Dans ce cas, la nouvelle activité de thread fait l'objet d'un transfert entrant mais pas d'un transfert sortant. Les deux activités sont liées mais pas imbriquées.  
  
## <a name="activity-transfer-sequence"></a>Séquence de transfert d'activité  
 Une séquence de transfert d'activité bien formée comprend les étapes suivantes.  
  
1. Commencer une nouvelle activité, qui consiste à sélectionner un nouveau gAId  
  
2. Émettre un suivi de transfert vers ce nouveau gAId à partir de l'ID d'activité actuel  
  
3. Définir le nouvel ID dans le stockage local des threads (TLS)  
  
4. Émettre un suivi de démarrage pour indiquer le début de la nouvelle activité  
  
5. Retourner à l'activité d'origine implique les étapes suivantes :  
  
6. Émettre un suivi de transfert vers le gAId d'origine  
  
7. Émettre un suivi d'arrêt pour indiquer la fin de la nouvelle activité  
  
8. Affecter au TLS l'ancien gAId  
  
 L'exemple de code suivant montre comment procéder. Cet exemple suppose qu'un appel bloquant est effectué lors du transfert vers la nouvelle activité, et inclut des suivis de suspension/reprise.  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a>Voir aussi

- [Configuration du traçage](configuring-tracing.md)
- [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Scénarios de suivi de bout en bout](end-to-end-tracing-scenarios.md)
- [Outil Service Trace Viewer (SvcTraceViewer.exe)](../../service-trace-viewer-tool-svctraceviewer-exe.md)
