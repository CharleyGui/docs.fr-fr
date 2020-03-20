---
title: Scénarios synchrones utilisant HTTP, TCP ou Canal nommé
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 6ae96c0aac5010adf37eb78ed57d1549885ece58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185783"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scénarios synchrones utilisant HTTP, TCP ou Canal nommé
Cette rubrique décrit les activités et transferts pour différents scénarios de demande/réponse asynchrones, avec des demandes multithread utilisant une connexion HTTP, TCP ou de canal nommé.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Demande/réponse asynchrone sans erreurs  
 Cette section décrit les activités et transferts pour un scénario de demande/réponse asynchrone, avec des clients multithread.  
  
 L'activité de l'appelant se termine lorsque `beginCall` est retourné et `endCall` est retourné. Si un rappel est appelé, celui-ci est retourné.  
  
 L'activité appelée se termine lorsque `beginCall` est retourné, `endCall` est retourné, ou lorsque le rappel est retourné s'il a été appelé à partir de cette activité.  
  
### <a name="asynchronous-client-without-callback"></a>Client asynchrone sans rappel  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>La propagation est activée de chaque côté, avec HTTP  
 ![Client asynchrone sans rappel où la propagationActivité est configuré pour vrai des deux côtés.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 Si `propagateActivity=true`, ProcessMessage indique à quelle activité ProcessAction transférer.  
  
 Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>La propagation est désactivée d'un côté ou de l'autre, avec HTTP  
 Si `propagateActivity=false` de part et d’autre, ProcessMessage n’indique pas à quelle activité ProcessAction transférer. Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée. Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local. Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.  
  
 ![Client asynchrone sans rappel où la propagationActivité est mis à faux de chaque côté.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.  
  
 Une activité d’action de processus est créée `propagateActivity=false` sur un client asynchrone lorsqu’il est à l’appelant ou à l’appelant, et lorsque le message de réponse n’inclut pas un en-tête d’action.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>La propagation est activée de chaque côté, avec TCP ou Canal nommé  
 ![Client asynchrone sans rappel où la propagationActivité est définie pour vrai des deux côtés et nommé pipe / TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.  
  
 Semblable à la première `propagateActivity=true`image, si , ProcessMessage indique à quelle activité ProcessAction transférer.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>La propagation est désactivée d'un côté ou de l'autre, avec TCP ou Canal nommé  
 Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.  
  
 Semblable à la deuxième `propagateActivity=false` image, si de chaque côté, ProcessMessage n’indique pas à quelle activité ProcessAction transférer. Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée. Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local. Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.  
  
 ![Client asynchrone sans rappel où la propagationActivité est mis à faux de chaque côté et nommé pipe / TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a>Client asynchrone avec rappel  
 Ce scénario ajoute les activités G et A', pour le rappel et `endCall`, et leurs transferts entrants/sortants.  
  
 Cette section ne démontre `propagateActivity` = `true`que l’utilisation de HTTP avec . Toutefois, les activités et les transferts supplémentaires s’appliquent également aux autres cas (c’est-à-dire `propagateActivity` = `false`à l’aide de TCP ou de Named-Pipe).  
  
 Le rappel crée une activité (G) lorsque le client appelle le code utilisateur pour notifier que les résultats sont prêts. Le code utilisateur appelle ensuite `endCall` dans le rappel (comme indiqué à la figure 5) ou hors de celui-ci (figure 6). Parce qu’on ne `endCall` sait pas de quelle activité `A’`utilisateur est appelée, cette activité est étiquetée . L'activité A' peut être identique ou différente de l'activité A.  
  
 ![Affiche un client asynchrone avec rappel, endcall en rappel.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Affiche un client asynchrone avec rappel, endcall rappel extérieur.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a>Serveur asynchrone avec rappel  
 ![Affiche un serveur asynchrone avec rappel.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 La pile de canaux rappelle le client à la réception des messages : les traces de ce processus sont émises dans l'activité ProcessRequest elle-même.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Demande/Réponse asynchrone avec erreurs  
 Des messages d'erreur sont reçus au cours de `endCall`. Sinon, les activités et transferts sont identiques aux scénarios précédents.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Communication unidirectionnelle asynchrone avec ou sans erreurs  
 Aucune réponse ou erreur n'est renvoyée au client.
