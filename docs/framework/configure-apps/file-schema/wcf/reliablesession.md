---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: ec69d9194d98302a4744e290f23fbb150b2e87cc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181311"
---
# \<reliableSession>

<span data-ttu-id="8d21e-101">Définit le paramètre pour la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="8d21e-101">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="8d21e-102">Lorsque cet élément est ajouté à une liaison personnalisée, le canal résultant peut prendre en charge des assurances de remise EOD (Exactly-Once-Delivery).</span><span class="sxs-lookup"><span data-stu-id="8d21e-102">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<reliableSession>**  
  
## <a name="syntax"></a><span data-ttu-id="8d21e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d21e-103">Syntax</span></span>  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"
                 flowControlEnabled="Boolean"
                 inactivityTimeout="TimeSpan"
                 maxPendingChannels="Integer"
                 maxRetryCount="Integer"
                 maxTransferWindowSize="Integer"
                 reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"
                 ordered="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d21e-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8d21e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="8d21e-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8d21e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d21e-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="8d21e-106">Attributes</span></span>  
  
|<span data-ttu-id="8d21e-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="8d21e-107">Attribute</span></span>|<span data-ttu-id="8d21e-108">Description</span><span class="sxs-lookup"><span data-stu-id="8d21e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d21e-109">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="8d21e-109">acknowledgementInterval</span></span>|<span data-ttu-id="8d21e-110"><xref:System.TimeSpan> qui contient l'intervalle de temps maximum pendant lequel le canal doit attendre avant d'envoyer un accusé de réception pour les messages reçus jusqu'alors.</span><span class="sxs-lookup"><span data-stu-id="8d21e-110">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="8d21e-111">La valeur par défaut est 00:00:0.2.</span><span class="sxs-lookup"><span data-stu-id="8d21e-111">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="8d21e-112">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="8d21e-112">flowControlEnabled</span></span>|<span data-ttu-id="8d21e-113">Valeur booléenne qui indique si le contrôle de flux avancé (une implémentation du contrôle de flux de la messagerie WS-Reliable spécifique à Microsoft) est activé.</span><span class="sxs-lookup"><span data-stu-id="8d21e-113">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="8d21e-114">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="8d21e-114">The default is `true`.</span></span>|  
|<span data-ttu-id="8d21e-115">inactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="8d21e-115">inactivityTimeout</span></span>|<span data-ttu-id="8d21e-116"><xref:System.TimeSpan> qui spécifie la durée maximale pendant laquelle le canal autorisera l'autre partie communicante à ne pas envoyer de messages avant qu'une erreur soit provoquée sur le canal.</span><span class="sxs-lookup"><span data-stu-id="8d21e-116">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="8d21e-117">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="8d21e-117">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="8d21e-118">L'activité sur un canal est définie comme étant la réception de messages d'application ou d'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="8d21e-118">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="8d21e-119">Cette propriété contrôle la durée maximale d'activation d'une session inactive.</span><span class="sxs-lookup"><span data-stu-id="8d21e-119">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="8d21e-120">En cas de durée supérieure sans activité, la session est abandonnée par l'infrastructure et une erreur est provoquée sur le canal.</span><span class="sxs-lookup"><span data-stu-id="8d21e-120">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="8d21e-121">**Remarque :**  Il n’est pas nécessaire que l’application envoie régulièrement des messages pour maintenir la connexion active.</span><span class="sxs-lookup"><span data-stu-id="8d21e-121">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="8d21e-122">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="8d21e-122">maxPendingChannels</span></span>|<span data-ttu-id="8d21e-123">Entier qui spécifie le nombre maximal de canaux en attente d'être acceptés sur l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="8d21e-123">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="8d21e-124">Cette valeur doit être comprise entre 1 et 16 384 inclus.</span><span class="sxs-lookup"><span data-stu-id="8d21e-124">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="8d21e-125">Valeur par défaut : 4.</span><span class="sxs-lookup"><span data-stu-id="8d21e-125">The default is 4.</span></span><br /><br /> <span data-ttu-id="8d21e-126">Les canaux sont en attente lorsqu'ils attendent d'être acceptés.</span><span class="sxs-lookup"><span data-stu-id="8d21e-126">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="8d21e-127">Une fois que cette limite est atteinte, aucun canal n'est créé.</span><span class="sxs-lookup"><span data-stu-id="8d21e-127">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="8d21e-128">Au contraire, ils sont mis en mode d'attente jusqu'à ce que ce nombre se réduise (en acceptant des canaux en attente).</span><span class="sxs-lookup"><span data-stu-id="8d21e-128">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="8d21e-129">Cette limite dépend des fabriques.</span><span class="sxs-lookup"><span data-stu-id="8d21e-129">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="8d21e-130">Lorsque le seuil est atteint et qu'une application distante essaie d'établir une nouvelle session fiable, la demande est refusée et l'opération d'ouverture initiale notifie l'erreur.</span><span class="sxs-lookup"><span data-stu-id="8d21e-130">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="8d21e-131">Cette limite ne s'applique pas au nombre de canaux sortants en attente.</span><span class="sxs-lookup"><span data-stu-id="8d21e-131">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="8d21e-132">maxRetryCount</span><span class="sxs-lookup"><span data-stu-id="8d21e-132">maxRetryCount</span></span>|<span data-ttu-id="8d21e-133">Entier qui spécifie le nombre maximal de tentatives effectuées par un canal fiable pour retransmettre un message pour lequel il n'a pas reçu d'accusé de réception en appelant Send sur son canal sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="8d21e-133">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="8d21e-134">Cette valeur doit être supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="8d21e-134">This value should be greater than zero.</span></span> <span data-ttu-id="8d21e-135">La valeur par défaut est 8.</span><span class="sxs-lookup"><span data-stu-id="8d21e-135">The default is 8.</span></span><br /><br /> <span data-ttu-id="8d21e-136">Cette valeur doit être un entier supérieur à zéro.</span><span class="sxs-lookup"><span data-stu-id="8d21e-136">This value should be an integer greater than zero.</span></span> <span data-ttu-id="8d21e-137">Si aucun accusé de réception n'est reçu après la dernière retransmission, le canal notifie l'erreur.</span><span class="sxs-lookup"><span data-stu-id="8d21e-137">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="8d21e-138">Un message est considéré comme devant être transféré si sa remise au destinataire a été acceptée par le destinataire.</span><span class="sxs-lookup"><span data-stu-id="8d21e-138">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="8d21e-139">Si, pour un message ayant été transmis, aucun accusé de réception n'a été reçu après un certain temps, l'infrastructure retransmet automatiquement le message.</span><span class="sxs-lookup"><span data-stu-id="8d21e-139">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="8d21e-140">L'infrastructure essaie de renvoyer le message à autant de reprises que celles spécifiées par cette propriété.</span><span class="sxs-lookup"><span data-stu-id="8d21e-140">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="8d21e-141">Si aucun accusé de réception n'est reçu après la dernière retransmission, le canal notifie l'erreur.</span><span class="sxs-lookup"><span data-stu-id="8d21e-141">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="8d21e-142">L'infrastructure utilise un algorithme de réduction de puissance exponentiel pour déterminer quand retransmettre, selon un délai aller-retour moyen calculé.</span><span class="sxs-lookup"><span data-stu-id="8d21e-142">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="8d21e-143">Ce délai démarre initialement 1 seconde avant la retransmission et, le délai doublant à chaque tentative, le délai écoulé entre la première et la dernière tentative de retransmission est d'environ 8,5 minutes.</span><span class="sxs-lookup"><span data-stu-id="8d21e-143">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="8d21e-144">Le délai de la première tentative de retransmission est ajusté au délai aller-retour calculé et le décalage créé par ces tentatives varie en conséquence.</span><span class="sxs-lookup"><span data-stu-id="8d21e-144">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="8d21e-145">Cela permet au délai de retransmission de s'adapter dynamiquement aux conditions de réseau variables.</span><span class="sxs-lookup"><span data-stu-id="8d21e-145">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="8d21e-146">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="8d21e-146">maxTransferWindowSize</span></span>|<span data-ttu-id="8d21e-147">Entier qui spécifie la taille maximale de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="8d21e-147">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="8d21e-148">Les valeurs autorisées sont comprises entre 1 et 4 096 (inclus).</span><span class="sxs-lookup"><span data-stu-id="8d21e-148">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="8d21e-149">Pour le client, cet attribut définit la taille maximale de la mémoire tampon utilisée par un canal fiable pour contenir les messages n'ayant pas encore été acceptés par le récepteur.</span><span class="sxs-lookup"><span data-stu-id="8d21e-149">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="8d21e-150">L'unité du quota est un message.</span><span class="sxs-lookup"><span data-stu-id="8d21e-150">The unit of the quota is a message.</span></span> <span data-ttu-id="8d21e-151">Si la mémoire tampon est pleine, les opérations SEND suivantes sont bloquées.</span><span class="sxs-lookup"><span data-stu-id="8d21e-151">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="8d21e-152">Pour le récepteur, cet attribut définit la taille maximale de la mémoire tampon utilisée par le canal pour stocker les messages entrants n'ayant pas encore été distribués dans l'application.</span><span class="sxs-lookup"><span data-stu-id="8d21e-152">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="8d21e-153">Si la mémoire tampon est pleine, les messages suivants sont supprimés de manière silencieuse par le récepteur et doivent être retransmis par le client.</span><span class="sxs-lookup"><span data-stu-id="8d21e-153">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="8d21e-154">ordered</span><span class="sxs-lookup"><span data-stu-id="8d21e-154">ordered</span></span>|<span data-ttu-id="8d21e-155">Valeur booléenne qui spécifie s'il est garanti que les messages arrivent dans l'ordre dans lequel ils ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="8d21e-155">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="8d21e-156">Si ce paramètre est `false`, les messages peuvent arriver dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="8d21e-156">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="8d21e-157">Par défaut, il s’agit de `true`.</span><span class="sxs-lookup"><span data-stu-id="8d21e-157">The default is `true`.</span></span>|  
|<span data-ttu-id="8d21e-158">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="8d21e-158">reliableMessagingVersion</span></span>|<span data-ttu-id="8d21e-159">Valeur autorisée de <xref:System.ServiceModel.ReliableMessagingVersion> qui spécifie la version de messagerie WS-Reliable à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8d21e-159">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d21e-160">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8d21e-160">Child Elements</span></span>  

 <span data-ttu-id="8d21e-161">None</span><span class="sxs-lookup"><span data-stu-id="8d21e-161">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d21e-162">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8d21e-162">Parent Elements</span></span>  
  
|<span data-ttu-id="8d21e-163">Élément</span><span class="sxs-lookup"><span data-stu-id="8d21e-163">Element</span></span>|<span data-ttu-id="8d21e-164">Description</span><span class="sxs-lookup"><span data-stu-id="8d21e-164">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="8d21e-165">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8d21e-165">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d21e-166">Notes</span><span class="sxs-lookup"><span data-stu-id="8d21e-166">Remarks</span></span>  

 <span data-ttu-id="8d21e-167">Les sessions fiables fournissent des fonctionnalités pour une messagerie et des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="8d21e-167">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="8d21e-168">La messagerie fiable réessaie d'établir la communication en cas d'échec et permet de spécifier des assurances de remise telles que l'ordre d'arrivée des messages.</span><span class="sxs-lookup"><span data-stu-id="8d21e-168">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="8d21e-169">Les sessions conservent l'état pour les clients entre les appels.</span><span class="sxs-lookup"><span data-stu-id="8d21e-169">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="8d21e-170">Cet élément assure également en option la remise de messages ordonnés.</span><span class="sxs-lookup"><span data-stu-id="8d21e-170">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="8d21e-171">Cette session implémentée peut croiser des intermédiaires SOAP et de transport.</span><span class="sxs-lookup"><span data-stu-id="8d21e-171">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="8d21e-172">Chaque élément de liaison représente une étape de traitement lors de l’envoi ou de la réception des messages.</span><span class="sxs-lookup"><span data-stu-id="8d21e-172">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="8d21e-173">Au moment de l’exécution, les éléments de liaison créent les fabrications de canal et les écouteurs nécessaires pour générer les piles de canaux sortants et entrants requis pour envoyer et recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="8d21e-173">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="8d21e-174">Le `reliableSession` fournit une couche facultative dans la pile capable d'établir une session fiable entre des points de terminaison et de configurer le comportement de cette session.</span><span class="sxs-lookup"><span data-stu-id="8d21e-174">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="8d21e-175">Pour plus d’informations, consultez [sessions fiables](../../../wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="8d21e-175">For more information, see [Reliable Sessions](../../../wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d21e-176">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d21e-176">Example</span></span>  

 <span data-ttu-id="8d21e-177">L’exemple suivant montre comment configurer une liaison personnalisée avec plusieurs éléments de transport et d’encodage de message, en activant surtout des sessions fiables qui maintiennent l’état du client et spécifient des assurances de remise dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="8d21e-177">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="8d21e-178">Cette fonctionnalité est configurée dans les fichiers de configuration de l'application pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="8d21e-178">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="8d21e-179">L'exemple présente la configuration du service.</span><span class="sxs-lookup"><span data-stu-id="8d21e-179">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="8d21e-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d21e-180">See also</span></span>

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [<span data-ttu-id="8d21e-181">Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="8d21e-181">Reliable Sessions</span></span>](../../../wcf/feature-details/reliable-sessions.md)
- [<span data-ttu-id="8d21e-182">Liaisons</span><span class="sxs-lookup"><span data-stu-id="8d21e-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8d21e-183">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="8d21e-183">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8d21e-184">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="8d21e-184">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
