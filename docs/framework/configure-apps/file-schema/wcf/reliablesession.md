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

Définit le paramètre pour la messagerie WS-Reliable. Lorsque cet élément est ajouté à une liaison personnalisée, le canal résultant peut prendre en charge des assurances de remise EOD (Exactly-Once-Delivery).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<reliableSession>**  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="attributes-and-elements"></a>Attributs et éléments  

 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|acknowledgementInterval|<xref:System.TimeSpan> qui contient l'intervalle de temps maximum pendant lequel le canal doit attendre avant d'envoyer un accusé de réception pour les messages reçus jusqu'alors. La valeur par défaut est 00:00:0.2.|  
|flowControlEnabled|Valeur booléenne qui indique si le contrôle de flux avancé (une implémentation du contrôle de flux de la messagerie WS-Reliable spécifique à Microsoft) est activé. Par défaut, il s’agit de `true`.|  
|inactivityTimeout|<xref:System.TimeSpan> qui spécifie la durée maximale pendant laquelle le canal autorisera l'autre partie communicante à ne pas envoyer de messages avant qu'une erreur soit provoquée sur le canal. La valeur par défaut est 00:10:00.<br /><br /> L'activité sur un canal est définie comme étant la réception de messages d'application ou d'infrastructure. Cette propriété contrôle la durée maximale d'activation d'une session inactive. En cas de durée supérieure sans activité, la session est abandonnée par l'infrastructure et une erreur est provoquée sur le canal. **Remarque :**  Il n’est pas nécessaire que l’application envoie régulièrement des messages pour maintenir la connexion active.|  
|maxPendingChannels|Entier qui spécifie le nombre maximal de canaux en attente d'être acceptés sur l'écouteur. Cette valeur doit être comprise entre 1 et 16 384 inclus. Valeur par défaut : 4.<br /><br /> Les canaux sont en attente lorsqu'ils attendent d'être acceptés. Une fois que cette limite est atteinte, aucun canal n'est créé. Au contraire, ils sont mis en mode d'attente jusqu'à ce que ce nombre se réduise (en acceptant des canaux en attente). Cette limite dépend des fabriques.<br /><br /> Lorsque le seuil est atteint et qu'une application distante essaie d'établir une nouvelle session fiable, la demande est refusée et l'opération d'ouverture initiale notifie l'erreur. Cette limite ne s'applique pas au nombre de canaux sortants en attente.|  
|maxRetryCount|Entier qui spécifie le nombre maximal de tentatives effectuées par un canal fiable pour retransmettre un message pour lequel il n'a pas reçu d'accusé de réception en appelant Send sur son canal sous-jacent.<br /><br /> Cette valeur doit être supérieure à zéro. La valeur par défaut est 8.<br /><br /> Cette valeur doit être un entier supérieur à zéro. Si aucun accusé de réception n'est reçu après la dernière retransmission, le canal notifie l'erreur.<br /><br /> Un message est considéré comme devant être transféré si sa remise au destinataire a été acceptée par le destinataire.<br /><br /> Si, pour un message ayant été transmis, aucun accusé de réception n'a été reçu après un certain temps, l'infrastructure retransmet automatiquement le message. L'infrastructure essaie de renvoyer le message à autant de reprises que celles spécifiées par cette propriété. Si aucun accusé de réception n'est reçu après la dernière retransmission, le canal notifie l'erreur.<br /><br /> L'infrastructure utilise un algorithme de réduction de puissance exponentiel pour déterminer quand retransmettre, selon un délai aller-retour moyen calculé. Ce délai démarre initialement 1 seconde avant la retransmission et, le délai doublant à chaque tentative, le délai écoulé entre la première et la dernière tentative de retransmission est d'environ 8,5 minutes. Le délai de la première tentative de retransmission est ajusté au délai aller-retour calculé et le décalage créé par ces tentatives varie en conséquence. Cela permet au délai de retransmission de s'adapter dynamiquement aux conditions de réseau variables.|  
|maxTransferWindowSize|Entier qui spécifie la taille maximale de la mémoire tampon. Les valeurs autorisées sont comprises entre 1 et 4 096 (inclus).<br /><br /> Pour le client, cet attribut définit la taille maximale de la mémoire tampon utilisée par un canal fiable pour contenir les messages n'ayant pas encore été acceptés par le récepteur. L'unité du quota est un message. Si la mémoire tampon est pleine, les opérations SEND suivantes sont bloquées.<br /><br /> Pour le récepteur, cet attribut définit la taille maximale de la mémoire tampon utilisée par le canal pour stocker les messages entrants n'ayant pas encore été distribués dans l'application. Si la mémoire tampon est pleine, les messages suivants sont supprimés de manière silencieuse par le récepteur et doivent être retransmis par le client.|  
|ordered|Valeur booléenne qui spécifie s'il est garanti que les messages arrivent dans l'ordre dans lequel ils ont été envoyés. Si ce paramètre est `false`, les messages peuvent arriver dans le désordre. Par défaut, il s’agit de `true`.|  
|reliableMessagingVersion|Valeur autorisée de <xref:System.ServiceModel.ReliableMessagingVersion> qui spécifie la version de messagerie WS-Reliable à utiliser.|  
  
### <a name="child-elements"></a>Éléments enfants  

 None  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  

 Les sessions fiables fournissent des fonctionnalités pour une messagerie et des sessions fiables. La messagerie fiable réessaie d'établir la communication en cas d'échec et permet de spécifier des assurances de remise telles que l'ordre d'arrivée des messages. Les sessions conservent l'état pour les clients entre les appels. Cet élément assure également en option la remise de messages ordonnés. Cette session implémentée peut croiser des intermédiaires SOAP et de transport.  
  
 Chaque élément de liaison représente une étape de traitement lors de l’envoi ou de la réception des messages. Au moment de l’exécution, les éléments de liaison créent les fabrications de canal et les écouteurs nécessaires pour générer les piles de canaux sortants et entrants requis pour envoyer et recevoir des messages. Le `reliableSession` fournit une couche facultative dans la pile capable d'établir une session fiable entre des points de terminaison et de configurer le comportement de cette session.  
  
 Pour plus d’informations, consultez [sessions fiables](../../../wcf/feature-details/reliable-sessions.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre comment configurer une liaison personnalisée avec plusieurs éléments de transport et d’encodage de message, en activant surtout des sessions fiables qui maintiennent l’état du client et spécifient des assurances de remise dans l’ordre. Cette fonctionnalité est configurée dans les fichiers de configuration de l'application pour le client et le service. L'exemple présente la configuration du service.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [Sessions fiables](../../../wcf/feature-details/reliable-sessions.md)
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
