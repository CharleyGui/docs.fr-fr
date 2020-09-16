---
title: 'Procédure : activer la détection de réexécution des messages'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: c99500a3d4dc0bd8abe7062f23e064d395cadf36
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557877"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="5692f-102">Procédure : activer la détection de réexécution des messages</span><span class="sxs-lookup"><span data-stu-id="5692f-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="5692f-103">Une attaque par relecture se produit lorsqu'un intrus copie un flux de messages entre deux correspondants et relit le flux à l'un ou plusieurs des correspondants.</span><span class="sxs-lookup"><span data-stu-id="5692f-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="5692f-104">Sauf atténuation, les ordinateurs sujets à l'attaque traiteront le flux comme messages légitimes, ce qui a des conséquences néfastes telles que des ordres redondants d'un élément.</span><span class="sxs-lookup"><span data-stu-id="5692f-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="5692f-105">Pour plus d’informations sur la détection de relecture des messages, consultez [détection de relecture des messages](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="5692f-105">For more information about message replay detection, see [Message Replay Detection](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="5692f-106">La procédure suivante montre différentes propriétés que vous pouvez utiliser pour contrôler la détection de relecture à l’aide de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5692f-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="5692f-107">Pour contrôler la détection de relecture sur le client à l'aide du code</span><span class="sxs-lookup"><span data-stu-id="5692f-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="5692f-108">Créez un <xref:System.ServiceModel.Channels.SecurityBindingElement> à utiliser dans un <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="5692f-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="5692f-109">Pour plus d’informations, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="5692f-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="5692f-110">L'exemple suivant utilise un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> créé avec le <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="5692f-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="5692f-111">Utilisez la propriété <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> pour retourner une référence à la classe <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> et définir les propriétés suivantes, selon le cas :</span><span class="sxs-lookup"><span data-stu-id="5692f-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="5692f-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="5692f-112">`DetectReplay`.</span></span> <span data-ttu-id="5692f-113">Valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="5692f-113">A Boolean value.</span></span> <span data-ttu-id="5692f-114">Elle détermine si le client doit détecter les relectures à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="5692f-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="5692f-115">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="5692f-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="5692f-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="5692f-116">`MaxClockSkew`.</span></span> <span data-ttu-id="5692f-117">Valeur <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="5692f-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="5692f-118">Détermine l'inclinaison d'horloge que peut tolérer le mécanisme de relecture entre le client et le serveur.</span><span class="sxs-lookup"><span data-stu-id="5692f-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="5692f-119">Le mécanisme de sécurité examine l'horodatage envoyé et détermine s'il a été envoyé il y a trop longtemps.</span><span class="sxs-lookup"><span data-stu-id="5692f-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="5692f-120">La valeur par défaut est 5 minutes.</span><span class="sxs-lookup"><span data-stu-id="5692f-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="5692f-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="5692f-121">`ReplayWindow`.</span></span> <span data-ttu-id="5692f-122">Valeur `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="5692f-122">A `TimeSpan` value.</span></span> <span data-ttu-id="5692f-123">Détermine pendant combien de temps un message peut vivre sur le réseau après que le serveur l'a envoyé (par le biais d'intermédiaires) avant d'atteindre le client.</span><span class="sxs-lookup"><span data-stu-id="5692f-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="5692f-124">Le client effectue le suivi des signatures des messages envoyés dans le `ReplayWindow` le plus récent pour les besoins de la détection de relecture.</span><span class="sxs-lookup"><span data-stu-id="5692f-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="5692f-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="5692f-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="5692f-126">Valeur entière.</span><span class="sxs-lookup"><span data-stu-id="5692f-126">An integer value.</span></span> <span data-ttu-id="5692f-127">Le client stocke les signatures du message dans un cache.</span><span class="sxs-lookup"><span data-stu-id="5692f-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="5692f-128">Ce paramètre spécifie combien de signatures le cache peut stocker.</span><span class="sxs-lookup"><span data-stu-id="5692f-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="5692f-129">Si le nombre de messages envoyés dans la dernière fenêtre de relecture atteint la limite de cache, les nouveaux messages sont rejetés jusqu'à ce que les signatures mises en cache les plus anciennes atteignent la limite de temps.</span><span class="sxs-lookup"><span data-stu-id="5692f-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="5692f-130">La valeur par défaut est 500000.</span><span class="sxs-lookup"><span data-stu-id="5692f-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="5692f-131">Pour contrôler la détection de relecture sur le service à l'aide du code</span><span class="sxs-lookup"><span data-stu-id="5692f-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="5692f-132">Créez un <xref:System.ServiceModel.Channels.SecurityBindingElement> à utiliser dans un <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="5692f-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="5692f-133">Utilisez la propriété <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> pour retourner une référence à la classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> et définissez les propriétés comme décrit précédemment.</span><span class="sxs-lookup"><span data-stu-id="5692f-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="5692f-134">Pour contrôler la détection de relecture dans la configuration pour le client ou le service</span><span class="sxs-lookup"><span data-stu-id="5692f-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="5692f-135">Créez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="5692f-135">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="5692f-136">Créez un élément `<security>`.</span><span class="sxs-lookup"><span data-stu-id="5692f-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="5692f-137">Créez un [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) ou un [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="5692f-137">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="5692f-138">Définissez les valeurs d'attributs suivantes, le cas échéant : `detectReplays`, `maxClockSkew`, `replayWindow` et `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="5692f-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="5692f-139">L'exemple suivant définit les attributs d'un élément `<localServiceSettings>` et d'un élément `<localClientSettings>` :</span><span class="sxs-lookup"><span data-stu-id="5692f-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="5692f-140"> Exemple</span><span class="sxs-lookup"><span data-stu-id="5692f-140">Example</span></span>  
 <span data-ttu-id="5692f-141">L’exemple suivant crée un <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à l’aide de la méthode <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> et définit les propriétés de relecture de la liaison.</span><span class="sxs-lookup"><span data-stu-id="5692f-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="5692f-142">Étendue de relecture : sécurité de message uniquement</span><span class="sxs-lookup"><span data-stu-id="5692f-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="5692f-143">Notez que les procédures suivantes s'appliquent uniquement au mode de sécurité Message.</span><span class="sxs-lookup"><span data-stu-id="5692f-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="5692f-144">Pour les modes Transport et Transport avec informations d'identification de message, les mécanismes de transport détectent les relectures.</span><span class="sxs-lookup"><span data-stu-id="5692f-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="5692f-145">Remarques relatives aux conversations sécurisées</span><span class="sxs-lookup"><span data-stu-id="5692f-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="5692f-146">Pour les liaisons qui activent les conversations sécurisées, vous pouvez ajuster ces paramètres à la fois pour le canal d’application et pour la liaison du démarrage de conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="5692f-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="5692f-147">Par exemple, vous pouvez désactiver les relectures pour le canal d'application mais les activer pour le canal de démarrage qui établit la conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="5692f-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="5692f-148">Si vous n'utilisez pas de sessions de conversation sécurisée, la détection des relectures n'est pas garantie dans les scénarios de batterie de serveurs et lorsque le processus est recyclé.</span><span class="sxs-lookup"><span data-stu-id="5692f-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="5692f-149">Cela s’applique aux liaisons fournies par le système suivantes :</span><span class="sxs-lookup"><span data-stu-id="5692f-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="5692f-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5692f-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="5692f-151">Objet <xref:System.ServiceModel.WSHttpBinding> avec la propriété <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> définie à la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="5692f-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5692f-152">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5692f-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="5692f-153">Les espaces de noms suivants sont requis pour compiler le code :</span><span class="sxs-lookup"><span data-stu-id="5692f-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="5692f-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5692f-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="5692f-155">Conversations sécurisées et sessions sécurisées</span><span class="sxs-lookup"><span data-stu-id="5692f-155">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="5692f-156">Procédure : créer une liaison personnalisée à l’aide de SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5692f-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
