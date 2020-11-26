---
title: Scénarios synchrones utilisant HTTP, TCP ou Canal nommé
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 00213c8d117f4319d7e29312dd0b9805d916231a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244143"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="f75be-102">Scénarios synchrones utilisant HTTP, TCP ou Canal nommé</span><span class="sxs-lookup"><span data-stu-id="f75be-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>

<span data-ttu-id="f75be-103">Cette rubrique décrit les activités et transferts pour différents scénarios de demande/réponse asynchrones, avec des demandes multithread utilisant une connexion HTTP, TCP ou de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="f75be-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="f75be-104">Demande/réponse asynchrone sans erreurs</span><span class="sxs-lookup"><span data-stu-id="f75be-104">Asynchronous Request/Reply without Errors</span></span>  

 <span data-ttu-id="f75be-105">Cette section décrit les activités et transferts pour un scénario de demande/réponse asynchrone, avec des clients multithread.</span><span class="sxs-lookup"><span data-stu-id="f75be-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="f75be-106">L'activité de l'appelant se termine lorsque `beginCall` est retourné et `endCall` est retourné.</span><span class="sxs-lookup"><span data-stu-id="f75be-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="f75be-107">Si un rappel est appelé, celui-ci est retourné.</span><span class="sxs-lookup"><span data-stu-id="f75be-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="f75be-108">L'activité appelée se termine lorsque `beginCall` est retourné, `endCall` est retourné, ou lorsque le rappel est retourné s'il a été appelé à partir de cette activité.</span><span class="sxs-lookup"><span data-stu-id="f75be-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="f75be-109">Client asynchrone sans rappel</span><span class="sxs-lookup"><span data-stu-id="f75be-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="f75be-110">La propagation est activée de chaque côté, avec HTTP</span><span class="sxs-lookup"><span data-stu-id="f75be-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  

 ![Client asynchrone sans rappel où propagateActivity a la valeur true sur les deux côtés.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 <span data-ttu-id="f75be-112">Si `propagateActivity=true` la valeur est, ProcessMessage indique l’activité ProcessAction vers laquelle effectuer le transfert.</span><span class="sxs-lookup"><span data-stu-id="f75be-112">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="f75be-113">Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.</span><span class="sxs-lookup"><span data-stu-id="f75be-113">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="f75be-114">La propagation est désactivée d'un côté ou de l'autre, avec HTTP</span><span class="sxs-lookup"><span data-stu-id="f75be-114">Propagation is Disabled on Either Sides, using HTTP</span></span>  

 <span data-ttu-id="f75be-115">Si `propagateActivity=false` de chaque côté, ProcessMessage n’indique pas l’activité ProcessAction vers laquelle effectuer le transfert.</span><span class="sxs-lookup"><span data-stu-id="f75be-115">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="f75be-116">Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée.</span><span class="sxs-lookup"><span data-stu-id="f75be-116">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="f75be-117">Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local.</span><span class="sxs-lookup"><span data-stu-id="f75be-117">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="f75be-118">Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.</span><span class="sxs-lookup"><span data-stu-id="f75be-118">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Client asynchrone sans rappel où propagateActivity a la valeur false de chaque côté.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 <span data-ttu-id="f75be-120">Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.</span><span class="sxs-lookup"><span data-stu-id="f75be-120">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="f75be-121">Une activité traiter l’action est créée sur un client asynchrone lorsqu' `propagateActivity=false` il est au niveau de l’appelant ou de l’appelé, et lorsque le message de réponse n’inclut pas d’en-tête action.</span><span class="sxs-lookup"><span data-stu-id="f75be-121">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="f75be-122">La propagation est activée de chaque côté, avec TCP ou Canal nommé</span><span class="sxs-lookup"><span data-stu-id="f75be-122">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  

 ![Client asynchrone sans rappel où propagateActivity a la valeur true sur les deux côtés et le canal nommé/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="f75be-124">Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.</span><span class="sxs-lookup"><span data-stu-id="f75be-124">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="f75be-125">Semblable à la première image, si `propagateActivity=true` , ProcessMessage indique l’activité ProcessAction vers laquelle effectuer le transfert.</span><span class="sxs-lookup"><span data-stu-id="f75be-125">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="f75be-126">La propagation est désactivée d'un côté ou de l'autre, avec TCP ou Canal nommé</span><span class="sxs-lookup"><span data-stu-id="f75be-126">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  

 <span data-ttu-id="f75be-127">Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.</span><span class="sxs-lookup"><span data-stu-id="f75be-127">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="f75be-128">Semblable à la deuxième image, si `propagateActivity=false` de chaque côté, ProcessMessage n’indique pas l’activité ProcessAction vers laquelle effectuer le transfert.</span><span class="sxs-lookup"><span data-stu-id="f75be-128">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="f75be-129">Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée.</span><span class="sxs-lookup"><span data-stu-id="f75be-129">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="f75be-130">Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local.</span><span class="sxs-lookup"><span data-stu-id="f75be-130">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="f75be-131">Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.</span><span class="sxs-lookup"><span data-stu-id="f75be-131">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Client asynchrone sans rappel où propagateActivity a la valeur false sur l’un et l’autre côté et le canal nommé/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="f75be-133">Client asynchrone avec rappel</span><span class="sxs-lookup"><span data-stu-id="f75be-133">Asynchronous client with Callback</span></span>  

 <span data-ttu-id="f75be-134">Ce scénario ajoute les activités G et A', pour le rappel et `endCall`, et leurs transferts entrants/sortants.</span><span class="sxs-lookup"><span data-stu-id="f75be-134">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="f75be-135">Cette section illustre uniquement l’utilisation de HTTP avec `propagateActivity` = `true` .</span><span class="sxs-lookup"><span data-stu-id="f75be-135">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="f75be-136">Toutefois, les activités et les transferts supplémentaires s’appliquent également aux autres cas (c’est-à-dire `propagateActivity` = `false` à l’aide de TCP ou d’un canal nommé).</span><span class="sxs-lookup"><span data-stu-id="f75be-136">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="f75be-137">Le rappel crée une activité (G) lorsque le client appelle le code utilisateur pour notifier que les résultats sont prêts.</span><span class="sxs-lookup"><span data-stu-id="f75be-137">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="f75be-138">Le code utilisateur appelle ensuite `endCall` dans le rappel (comme indiqué à la figure 5) ou hors de celui-ci (figure 6).</span><span class="sxs-lookup"><span data-stu-id="f75be-138">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="f75be-139">Étant donné qu’il n’est pas connu de quelle activité utilisateur `endCall` est appelée, cette activité est étiquetée `A’` .</span><span class="sxs-lookup"><span data-stu-id="f75be-139">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="f75be-140">L'activité A' peut être identique ou différente de l'activité A.</span><span class="sxs-lookup"><span data-stu-id="f75be-140">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![Affiche un client asynchrone avec rappel, endCall dans le rappel.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Montre un client asynchrone avec rappel, endCall en dehors du rappel.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="f75be-143">Serveur asynchrone avec rappel</span><span class="sxs-lookup"><span data-stu-id="f75be-143">Asynchronous Server with Callback</span></span>  

 ![Affiche un serveur asynchrone avec un rappel.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 <span data-ttu-id="f75be-145">La pile de canaux rappelle le client à la réception des messages : les traces de ce processus sont émises dans l'activité ProcessRequest elle-même.</span><span class="sxs-lookup"><span data-stu-id="f75be-145">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="f75be-146">Demande/Réponse asynchrone avec erreurs</span><span class="sxs-lookup"><span data-stu-id="f75be-146">Asynchronous Request/Reply with Errors</span></span>  

 <span data-ttu-id="f75be-147">Des messages d'erreur sont reçus au cours de `endCall`.</span><span class="sxs-lookup"><span data-stu-id="f75be-147">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="f75be-148">Sinon, les activités et transferts sont identiques aux scénarios précédents.</span><span class="sxs-lookup"><span data-stu-id="f75be-148">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="f75be-149">Communication unidirectionnelle asynchrone avec ou sans erreurs</span><span class="sxs-lookup"><span data-stu-id="f75be-149">Asynchronous One-Way with or without Errors</span></span>  

 <span data-ttu-id="f75be-150">Aucune réponse ou erreur n'est renvoyée au client.</span><span class="sxs-lookup"><span data-stu-id="f75be-150">No response or fault is returned to the client.</span></span>
