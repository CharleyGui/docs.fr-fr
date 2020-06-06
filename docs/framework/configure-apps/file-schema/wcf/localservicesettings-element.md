---
title: <localServiceSettings> (élément)
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 4883fd563ecf989d67c369085df4fc43d0c5f078
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400305"
---
# <a name="localservicesettings-element"></a>\<localServiceSettings>, élément
Spécifie les paramètres de sécurité d’un service local pour cette liaison.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localServiceSettings>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>
  <localServiceSettings detectReplays="Boolean"
                        inactivityTimeout="TimeSpan"
                        issuedCookieLifeTime="TimeSpan"
                        maxCachedCookies="Integer"
                        maxClockSkew="TimeSpan"
                        maxPendingSessions="Integer"
                        maxStatefulNegotiations="Integer"
                        negotiationTimeout="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`detectReplays`|Valeur booléenne qui spécifie si les attaques par relecture contre le canal sont détectées et traitées automatiquement. Par défaut, il s’agit de `false`.|  
|`inactivityTimeout`|Positif <xref:System.TimeSpan> qui spécifie la durée d’inactivité pendant laquelle le canal attend avant d’expirer. La valeur par défaut est « 01:00:00 ».|  
|`issuedCookieLifeTime`|<xref:System.TimeSpan> qui spécifie la durée de vie de tous les nouveaux cookies de sécurité. Les cookies qui dépassent leur durée de vie sont recyclés et doivent être renégociés. La valeur par défaut est « 10:00:00 ».|  
|`maxCachedCookies`|Entier positif qui spécifie le nombre maximal de cookies pouvant être mis en cache. La valeur par défaut est 1000.|  
|`maxClockSkew`|<xref:System.TimeSpan> qui spécifie la différence de temps maximale entre les horloges système des deux parties communicantes. La valeur par défaut est « 00:05:00 ».<br /><br /> Lorsque la valeur par défaut est définie, le récepteur accepte des messages dont l'horodatage d'envoi diffère au maximum de 5 minutes de son horodatage de réception. Les messages qui échouent au test de l'heure d'envoi sont rejetés. Ce paramètre est utilisé conjointement à l'attribut `replayWindow`.|  
|`maxPendingSessions`|Entier positif qui spécifie le nombre maximal de sessions de sécurité en attente que le service prend en charge. Lorsque cette limite est atteinte, tous les nouveaux clients reçoivent des erreurs SOAP. La valeur par défaut est 1000.|  
|`maxStatefulNegotiations`|Entier positif qui spécifie le nombre de négociations de sécurité qui peuvent être actives en même temps. Au-delà de ce nombre limite, les sessions de négociation sont mises en file d'attente et peuvent être effectuées uniquement lorsqu'un espace sous la limite devient disponible. La valeur par défaut est 1024.|  
|`negotiationTimeout`|<xref:System.TimeSpan> qui spécifie la durée de vie de la stratégie de sécurité utilisée par canal. Lorsque ce temps arrive à expiration, le canal renégocie avec le client une nouvelle stratégie de sécurité. La valeur par défaut est « 00:02:00 ».|  
|`reconnectTransportOnFailure`|Valeur booléenne qui spécifie si des connexions utilisant la messagerie WS-Reliable tentent une reconnexion après des incidents de transport. La valeur par défaut est `true`, ce qui signifie que le nombre de tentatives de reconnexion est infini. Le cycle s'arrête si le délai d'attente expire suite à une inactivité prolongée, après laquelle le canal lève une exception lorsqu'il ne peut pas être reconnecté.|  
|`replayCacheSize`|Entier positif qui spécifie le nombre de pointeurs en cache utilisés pour la détection de relecture. Si cette limite est dépassée, le pointeur le plus ancien est supprimé et un pointeur est créé pour le nouveau message. La valeur par défaut est 500000.|  
|`replayWindow`|<xref:System.TimeSpan> qui spécifie la durée de validité des pointeurs de messages individuels.<br /><br /> Une fois cette durée écoulée, un message envoyé avec le même pointeur que celui envoyé précédemment ne sera pas accepté. Cet attribut est utilisé conjointement à l'attribut `maxClockSkew` pour empêcher des attaques par relecture. Un intrus pourrait relire un message une fois que sa fenêtre de relecture a expiré. Toutefois, ce message échouerait au test `maxClockSkew` qui rejette les messages portant un horodatage d'envoi qui diffère au maximum d'une heure par rapport à l'horodatage de réception du message.|  
|`sessionKeyRenewalInterval`|<xref:System.TimeSpan> qui spécifie le délai d'attente au terme duquel l'initiateur renouvellera la clé de la session de sécurité. La valeur par défaut est « 10:00:00 ».|  
|`sessionKeyRolloverInterval`|<xref:System.TimeSpan> qui spécifie la période de validité d'une clé de session précédente sur les messages entrants pendant un renouvellement de clé. La valeur par défaut est « 00:05:00 ».<br /><br /> Pendant un renouvellement de clé, le client et le serveur doivent toujours envoyer des messages à l'aide de la clé disponible la plus récente. Les deux correspondants doivent accepter des messages entrants sécurisés avec la clé de session précédente jusqu'à l'expiration de l'heure de substitution.|  
|`timestampValidityDuration`|<xref:System.TimeSpan> positif qui spécifie la durée de validité d'un horodatage. La valeur par défaut est « 00:15:00 ».|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|Spécifie les options de sécurité d’une liaison personnalisée.|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.|  
  
## <a name="remarks"></a>Remarques  
 Les paramètres sont locaux car ils ne sont pas publiés dans le cadre de la stratégie de sécurité du service et n'affectent pas la liaison du client.  
  
 Les attributs suivants de l'élément `localServiceSecuritySettings` peuvent aider à atténuer une attaque de sécurité par déni de service (DOS) :  
  
- `maxCachedCookies` : contrôle le nombre maximal de SecurityContextTokens limités par le temps mis en cache par le serveur après une négociation SSL ou SPNEGO.  
  
- `issuedCookieLifetime` : contrôle la durée de vie des SecurityContextTokens émis par le serveur après une négociation SSL ou SPNEGO. Le serveur met en cache les SecurityContextTokens pendant cette période.  
  
- `maxPendingSessions` : contrôle le nombre maximal de conversations sécurisées établies au niveau du serveur mais pour lesquelles aucun message d'application n'a été traité. Ce quota empêche les clients d'établir des conversations sécurisées au niveau du service, forçant ainsi le service à conserver l'état de chaque client, sans jamais les utiliser toutefois.  
  
- `inactivityTimeout` : contrôle le temps maximum pendant lequel le service garde une conversation sécurisée active sans jamais recevoir dessus un message d'application. Ce quota empêche les clients d'établir des conversations sécurisées au niveau du service, forçant ainsi le service à conserver l'état de chaque client, sans jamais les utiliser toutefois.  
  
 Dans une session de conversation sécurisée, notez que les attributs `inactivityTimeout` et `receiveTimeout` sur la liaison affectent le délai d'attente de la session. Le plus court des deux détermine le dépassement du délai d'attente.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Custom Binding Security](../../../wcf/samples/custom-binding-security.md)
