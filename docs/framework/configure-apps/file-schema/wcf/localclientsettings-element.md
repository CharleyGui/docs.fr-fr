---
title: <localClientSettings> (élément)
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 19eaea71fdaad1b945524cca5cf15634e0b0fa14
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158732"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="876df-102">\<localClientSettings>, élément</span><span class="sxs-lookup"><span data-stu-id="876df-102">\<localClientSettings> element</span></span>

<span data-ttu-id="876df-103">Spécifie les paramètres de sécurité d’un client local pour cette liaison.</span><span class="sxs-lookup"><span data-stu-id="876df-103">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="876df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="876df-104">Syntax</span></span>  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="876df-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="876df-105">Attributes and Elements</span></span>  

 <span data-ttu-id="876df-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="876df-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="876df-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="876df-107">Attributes</span></span>  
  
|<span data-ttu-id="876df-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="876df-108">Attribute</span></span>|<span data-ttu-id="876df-109">Description</span><span class="sxs-lookup"><span data-stu-id="876df-109">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="876df-110">Valeur booléenne qui spécifie si la mise en cache de cookie est activée.</span><span class="sxs-lookup"><span data-stu-id="876df-110">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="876df-111">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="876df-111">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="876df-112">Entier qui spécifie le pourcentage maximal des cookies qui peuvent être renouvelés.</span><span class="sxs-lookup"><span data-stu-id="876df-112">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="876df-113">Cette valeur doit être comprise entre 0 et 100.</span><span class="sxs-lookup"><span data-stu-id="876df-113">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="876df-114">La valeur par défaut est 90.</span><span class="sxs-lookup"><span data-stu-id="876df-114">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="876df-115">Valeur booléenne qui spécifie si les attaques par relecture contre le canal sont détectées et traitées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="876df-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="876df-116">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="876df-116">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="876df-117"><xref:System.TimeSpan> qui spécifie la différence de temps maximale entre les horloges système des deux parties communicantes.</span><span class="sxs-lookup"><span data-stu-id="876df-117">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="876df-118">La valeur par défaut est « 00:05:00 ».</span><span class="sxs-lookup"><span data-stu-id="876df-118">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="876df-119">Lorsque la valeur par défaut est définie, le récepteur accepte des messages dont l'horodatage d'envoi diffère au maximum de 5 minutes de son horodatage de réception.</span><span class="sxs-lookup"><span data-stu-id="876df-119">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="876df-120">Les messages qui échouent au test de l'heure d'envoi sont rejetés.</span><span class="sxs-lookup"><span data-stu-id="876df-120">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="876df-121">Ce paramètre est utilisé conjointement à l'attribut `replayWindow`.</span><span class="sxs-lookup"><span data-stu-id="876df-121">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="876df-122"><xref:System.TimeSpan> qui spécifie la durée de vie maximale des cookies.</span><span class="sxs-lookup"><span data-stu-id="876df-122">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="876df-123">La valeur par défaut est « 10675199.02:48:05.4775807 ».</span><span class="sxs-lookup"><span data-stu-id="876df-123">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="876df-124">Valeur booléenne qui spécifie si des connexions utilisant la messagerie WS-Reliable tentent une reconnexion après des incidents de transport.</span><span class="sxs-lookup"><span data-stu-id="876df-124">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="876df-125">La valeur par défaut est `true`, ce qui signifie que le nombre de tentatives de reconnexion est infini.</span><span class="sxs-lookup"><span data-stu-id="876df-125">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="876df-126">Le cycle s'arrête si le délai d'attente expire suite à une inactivité prolongée, après laquelle le canal lève une exception lorsqu'il ne peut pas être reconnecté.</span><span class="sxs-lookup"><span data-stu-id="876df-126">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="876df-127">Entier positif qui spécifie le nombre de pointeurs en cache utilisés pour la détection de relecture.</span><span class="sxs-lookup"><span data-stu-id="876df-127">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="876df-128">Si cette limite est dépassée, le pointeur le plus ancien est supprimé et un pointeur est créé pour le nouveau message.</span><span class="sxs-lookup"><span data-stu-id="876df-128">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="876df-129">La valeur par défaut est 500000.</span><span class="sxs-lookup"><span data-stu-id="876df-129">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="876df-130"><xref:System.TimeSpan> qui spécifie la durée de validité des pointeurs de messages individuels.</span><span class="sxs-lookup"><span data-stu-id="876df-130">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="876df-131">Une fois cette durée écoulée, un message envoyé avec le même pointeur que celui envoyé précédemment ne sera pas accepté.</span><span class="sxs-lookup"><span data-stu-id="876df-131">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="876df-132">Cet attribut est utilisé conjointement à l'attribut `maxClockSkew` pour empêcher des attaques par relecture.</span><span class="sxs-lookup"><span data-stu-id="876df-132">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="876df-133">Un intrus pourrait relire un message une fois que sa fenêtre de relecture a expiré.</span><span class="sxs-lookup"><span data-stu-id="876df-133">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="876df-134">Toutefois, ce message échouerait au test `maxClockSkew` qui rejette les messages portant un horodatage d'envoi qui diffère au maximum d'une heure par rapport à l'horodatage de réception du message.</span><span class="sxs-lookup"><span data-stu-id="876df-134">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="876df-135"><xref:System.TimeSpan> qui spécifie le délai d'attente au terme duquel l'initiateur renouvellera la clé de la session de sécurité.</span><span class="sxs-lookup"><span data-stu-id="876df-135">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="876df-136">La valeur par défaut est « 10:00:00 ».</span><span class="sxs-lookup"><span data-stu-id="876df-136">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="876df-137"><xref:System.TimeSpan> qui spécifie la période de validité d'une clé de session précédente sur les messages entrants pendant un renouvellement de clé.</span><span class="sxs-lookup"><span data-stu-id="876df-137">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="876df-138">La valeur par défaut est « 00:05:00 ».</span><span class="sxs-lookup"><span data-stu-id="876df-138">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="876df-139">Pendant un renouvellement de clé, le client et le serveur doivent toujours envoyer des messages à l'aide de la clé disponible la plus récente.</span><span class="sxs-lookup"><span data-stu-id="876df-139">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="876df-140">Les deux correspondants doivent accepter des messages entrants sécurisés avec la clé de session précédente jusqu'à l'expiration de l'heure de substitution.</span><span class="sxs-lookup"><span data-stu-id="876df-140">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="876df-141"><xref:System.TimeSpan> positif qui spécifie la durée de validité d'un horodatage.</span><span class="sxs-lookup"><span data-stu-id="876df-141">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="876df-142">La valeur par défaut est « 00:15:00 ».</span><span class="sxs-lookup"><span data-stu-id="876df-142">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="876df-143">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="876df-143">Child Elements</span></span>  

 <span data-ttu-id="876df-144">None</span><span class="sxs-lookup"><span data-stu-id="876df-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="876df-145">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="876df-145">Parent Elements</span></span>  
  
|<span data-ttu-id="876df-146">Élément</span><span class="sxs-lookup"><span data-stu-id="876df-146">Element</span></span>|<span data-ttu-id="876df-147">Description</span><span class="sxs-lookup"><span data-stu-id="876df-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="876df-148">Spécifie les options de sécurité d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="876df-148">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="876df-149">Spécifie les valeurs par défaut utilisées pour initialiser un service de conversation sécurisé.</span><span class="sxs-lookup"><span data-stu-id="876df-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="876df-150">Notes</span><span class="sxs-lookup"><span data-stu-id="876df-150">Remarks</span></span>  

 <span data-ttu-id="876df-151">Les paramètres sont locaux dans le sens où ils ne dérivent pas de la stratégie de sécurité du service.</span><span class="sxs-lookup"><span data-stu-id="876df-151">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="876df-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="876df-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="876df-153">Liaisons</span><span class="sxs-lookup"><span data-stu-id="876df-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="876df-154">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="876df-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="876df-155">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="876df-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="876df-156">Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="876df-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="876df-157">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="876df-157">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
