---
title: 'Procédure : créer une session sécurisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: bdb0f89b950d086e04cbb9d6da161bd315fc64b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934378"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="1b148-102">Procédure : créer une session sécurisée</span><span class="sxs-lookup"><span data-stu-id="1b148-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="1b148-103">À l’exception de la [ \<liaison basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , les liaisons fournies par le système dans Windows Communication Foundation (WCF) utilisent automatiquement des sessions sécurisées lorsque la sécurité de message est activée.</span><span class="sxs-lookup"><span data-stu-id="1b148-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="1b148-104">Par défaut, les sessions sécurisées ne survivent pas à un serveur web recyclé.</span><span class="sxs-lookup"><span data-stu-id="1b148-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="1b148-105">Lorsqu'une session sécurisée est établie, le client et le service mettent en cache la clé associée à la session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1b148-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="1b148-106">Lorsque les messages sont échangés, seul un identificateur de la clé mise en cache est échangé.</span><span class="sxs-lookup"><span data-stu-id="1b148-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="1b148-107">Si le serveur web est recyclé, le cache est également recyclé, de sorte que le serveur web ne peut pas récupérer la clé mise en cache pour l’identificateur.</span><span class="sxs-lookup"><span data-stu-id="1b148-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="1b148-108">Si cela arrive, une exception est retournée au client.</span><span class="sxs-lookup"><span data-stu-id="1b148-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="1b148-109">Les sessions sécurisées qui utilisent un jeton de contexte de sécurité avec état peuvent survivre au recyclage d'un serveur Web.</span><span class="sxs-lookup"><span data-stu-id="1b148-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="1b148-110">Pour plus d’informations sur l’utilisation d’un SCT avec état dans une session [sécurisée, consultez Procédure: Créez un jeton de contexte de sécurité pour une](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1b148-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="1b148-111">Pour spécifier qu’un service utilise des sessions sécurisées à l’aide de l’une des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="1b148-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="1b148-112">Configurez un service pour utiliser une liaison fournie par le système qui prend en charge la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="1b148-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="1b148-113">À l’exception de la [ \<liaison basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , lorsque les liaisons fournies par le système sont configurées pour utiliser la sécurité de message, WCF utilise automatiquement des sessions sécurisées.</span><span class="sxs-lookup"><span data-stu-id="1b148-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="1b148-114">Le tableau suivant répertorie les liaisons fournies par le système qui prennent en charge la sécurité de message et indique si la sécurité de message est le mécanisme de sécurité par défaut.</span><span class="sxs-lookup"><span data-stu-id="1b148-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="1b148-115">Liaison fournie par le système</span><span class="sxs-lookup"><span data-stu-id="1b148-115">System-provided binding</span></span>|<span data-ttu-id="1b148-116">Élément de configuration</span><span class="sxs-lookup"><span data-stu-id="1b148-116">Configuration element</span></span>|<span data-ttu-id="1b148-117">Sécurité de message activée par défaut</span><span class="sxs-lookup"><span data-stu-id="1b148-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="1b148-118">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1b148-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="1b148-119">Non</span><span class="sxs-lookup"><span data-stu-id="1b148-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="1b148-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1b148-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="1b148-121">Oui</span><span class="sxs-lookup"><span data-stu-id="1b148-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="1b148-122">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1b148-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="1b148-123">Oui</span><span class="sxs-lookup"><span data-stu-id="1b148-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="1b148-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1b148-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="1b148-125">Oui</span><span class="sxs-lookup"><span data-stu-id="1b148-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="1b148-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1b148-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="1b148-127">Non</span><span class="sxs-lookup"><span data-stu-id="1b148-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="1b148-128">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="1b148-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="1b148-129">Non</span><span class="sxs-lookup"><span data-stu-id="1b148-129">No</span></span>|  
  
     <span data-ttu-id="1b148-130">L’exemple de code suivant utilise la configuration pour spécifier une `wsHttpBinding_Calculator` liaison nommée qui utilise la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), la sécurité de message et les sessions sécurisées.</span><span class="sxs-lookup"><span data-stu-id="1b148-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="1b148-131">L’exemple de code suivant spécifie que la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), la sécurité de message et les sessions sécurisées `secureCalculator` sont utilisées pour sécuriser le service.</span><span class="sxs-lookup"><span data-stu-id="1b148-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="1b148-132">Les sessions sécurisées peuvent être désactivées pour la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) en affectant à `false`l’attribut la `establishSecurityContext` valeur.</span><span class="sxs-lookup"><span data-stu-id="1b148-132">Secure sessions can be turned off for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="1b148-133">Pour les autres liaisons fournies par le système, les sessions sécurisées peuvent être désactivées uniquement en créant une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="1b148-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="1b148-134">Pour spécifier qu'un service utilise des sessions sécurisées à l'aide d'une liaison personnalisée</span><span class="sxs-lookup"><span data-stu-id="1b148-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="1b148-135">Créez une liaison personnalisée qui spécifie que les messages SOAP sont protégés par une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1b148-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="1b148-136">Pour plus d’informations sur la création d’une liaison [personnalisée, consultez Procédure: Personnaliser une liaison](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)fournie par le système.</span><span class="sxs-lookup"><span data-stu-id="1b148-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="1b148-137">L’exemple de code suivant utilise la configuration pour spécifier une liaison personnalisée à laquelle les messages font appel dans une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1b148-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="1b148-138">L’exemple de code suivant crée une liaison personnalisée qui utilise le mode d’authentification <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> pour démarrer une session sécurisée.</span><span class="sxs-lookup"><span data-stu-id="1b148-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1b148-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b148-139">See also</span></span>

- [<span data-ttu-id="1b148-140">Vue d’ensemble des liaisons WCF</span><span class="sxs-lookup"><span data-stu-id="1b148-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
