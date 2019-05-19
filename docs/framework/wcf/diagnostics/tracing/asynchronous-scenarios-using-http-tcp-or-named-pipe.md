---
title: Scénarios synchrones utilisant HTTP, TCP ou Canal nommé
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 48957ec0abd1b4b0623f9b613fcd94912a38845b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881705"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Scénarios synchrones utilisant HTTP, TCP ou Canal nommé
Cette rubrique décrit les activités et transferts pour différents scénarios de demande/réponse asynchrones, avec des demandes multithread utilisant une connexion HTTP, TCP ou de canal nommé.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Demande/réponse asynchrone sans erreurs  
 Cette section décrit les activités et transferts pour un scénario de demande/réponse asynchrone, avec des clients multithread.  
  
 L'activité de l'appelant se termine lorsque `beginCall` est retourné et `endCall` est retourné. Si un rappel est appelé, celui-ci est retourné.  
  
 L'activité appelée se termine lorsque `beginCall` est retourné, `endCall` est retourné, ou lorsque le rappel est retourné s'il a été appelé à partir de cette activité.  
  
### <a name="asynchronous-client-without-callback"></a>Client asynchrone sans rappel  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>La propagation est activée de chaque côté, avec HTTP  
 ![Client asynchrone sans rappel où propagateActivity est définie sur true des deux côtés.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)   
  
 Si `propagateActivity` = `true`, ProcessMessage indique l’activité ProcessAction pour transférer vers laquelle.  
  
 Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>La propagation est désactivée d'un côté ou de l'autre, avec HTTP  
 Si `propagateActivity` = `false` de chaque côté, ProcessMessage n’indique pas quelle activité ProcessAction pour transférer vers. Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée. Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local. Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.  
  
 ![Client asynchrone sans rappel où propagateActivity est définie sur false, chaque côté.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  
    
 Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.  
  
 Une activité traiter l’Action est créée sur un client asynchrone lorsque `propagateActivity` = `false` à l’appelant ou appelé et lorsque le message de réponse n’inclut pas un en-tête d’Action.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>La propagation est activée de chaque côté, avec TCP ou Canal nommé  
 ![Client asynchrone sans rappel où propagateActivity est définie à true des deux côtés et nommé/TCP du canal.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.  
  
 Similaire à la première image, si `propagateActivity` = `true`, ProcessMessage indique l’activité ProcessAction pour transférer vers laquelle.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>La propagation est désactivée d'un côté ou de l'autre, avec TCP ou Canal nommé  
 Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.  
  
 Similaire à la deuxième image si `propagateActivity` = `false` de chaque côté, ProcessMessage n’indique pas quelle activité ProcessAction pour transférer vers. Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée. Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local. Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.  
  
 ![Client asynchrone sans rappel, propagateActivity est de false à côté et nommé/TCP du canal.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  
    
### <a name="asynchronous-client-with-callback"></a>Client asynchrone avec rappel  
 Ce scénario ajoute les activités G et A', pour le rappel et `endCall`, et leurs transferts entrants/sortants.  
  
 Cette section montre seulement l’utilisation de HTTP `propragateActivity` = `true`. Toutefois, les activités et transferts supplémentaires s’appliquent également aux autres cas (autrement dit, `propagateActivity` = `false`, à l’aide de TCP ou canal nommé).  
  
 Le rappel crée une activité (G) lorsque le client appelle le code utilisateur pour notifier que les résultats sont prêts. Le code utilisateur appelle ensuite `endCall` dans le rappel (comme indiqué à la figure 5) ou hors de celui-ci (figure 6). Car on ne sait pas quelle activité utilisateur `endCall` est appelée à partir, cette activité est étiquetée `A’`. L'activité A' peut être identique ou différente de l'activité A.  
  
 ![Montre un client asynchrone avec rappel, endcall à dans le rappel.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  
    
 ![Montre un client asynchrone avec rappel, endcall à l’extérieur de rappel.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  
    
### <a name="asynchronous-server-with-callback"></a>Serveur asynchrone avec rappel  
 ![Montre un serveur asynchrone avec rappel.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  
    
 La pile de canaux rappelle le client à la réception des messages : les traces de ce processus sont émises dans l'activité ProcessRequest elle-même.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Demande/Réponse asynchrone avec erreurs  
 Des messages d'erreur sont reçus au cours de `endCall`. Sinon, les activités et transferts sont identiques aux scénarios précédents.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Communication unidirectionnelle asynchrone avec ou sans erreurs  
 Aucune réponse ou erreur n'est renvoyée au client.
