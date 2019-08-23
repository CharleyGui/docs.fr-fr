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
# <a name="how-to-create-a-secure-session"></a>Procédure : créer une session sécurisée
À l’exception de la [ \<liaison basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , les liaisons fournies par le système dans Windows Communication Foundation (WCF) utilisent automatiquement des sessions sécurisées lorsque la sécurité de message est activée.  
  
 Par défaut, les sessions sécurisées ne survivent pas à un serveur web recyclé. Lorsqu'une session sécurisée est établie, le client et le service mettent en cache la clé associée à la session sécurisée. Lorsque les messages sont échangés, seul un identificateur de la clé mise en cache est échangé. Si le serveur web est recyclé, le cache est également recyclé, de sorte que le serveur web ne peut pas récupérer la clé mise en cache pour l’identificateur. Si cela arrive, une exception est retournée au client. Les sessions sécurisées qui utilisent un jeton de contexte de sécurité avec état peuvent survivre au recyclage d'un serveur Web. Pour plus d’informations sur l’utilisation d’un SCT avec état dans une session [sécurisée, consultez Procédure: Créez un jeton de contexte de sécurité pour une](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)session sécurisée.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Pour spécifier qu’un service utilise des sessions sécurisées à l’aide de l’une des liaisons fournies par le système  
  
- Configurez un service pour utiliser une liaison fournie par le système qui prend en charge la sécurité de message.  
  
     À l’exception de la [ \<liaison basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) , lorsque les liaisons fournies par le système sont configurées pour utiliser la sécurité de message, WCF utilise automatiquement des sessions sécurisées. Le tableau suivant répertorie les liaisons fournies par le système qui prennent en charge la sécurité de message et indique si la sécurité de message est le mécanisme de sécurité par défaut.  
  
    |Liaison fournie par le système|Élément de configuration|Sécurité de message activée par défaut|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Non|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Oui|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Oui|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Oui|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Non|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Non|  
  
     L’exemple de code suivant utilise la configuration pour spécifier une `wsHttpBinding_Calculator` liaison nommée qui utilise la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), la sécurité de message et les sessions sécurisées.  
  
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
  
     L’exemple de code suivant spécifie que la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), la sécurité de message et les sessions sécurisées `secureCalculator` sont utilisées pour sécuriser le service.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > Les sessions sécurisées peuvent être désactivées pour la [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) en affectant à `false`l’attribut la `establishSecurityContext` valeur. Pour les autres liaisons fournies par le système, les sessions sécurisées peuvent être désactivées uniquement en créant une liaison personnalisée.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Pour spécifier qu'un service utilise des sessions sécurisées à l'aide d'une liaison personnalisée  
  
- Créez une liaison personnalisée qui spécifie que les messages SOAP sont protégés par une session sécurisée.  
  
     Pour plus d’informations sur la création d’une liaison [personnalisée, consultez Procédure: Personnaliser une liaison](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)fournie par le système.  
  
     L’exemple de code suivant utilise la configuration pour spécifier une liaison personnalisée à laquelle les messages font appel dans une session sécurisée.  
  
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
  
     L’exemple de code suivant crée une liaison personnalisée qui utilise le mode d’authentification <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> pour démarrer une session sécurisée.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des liaisons WCF](../../../../docs/framework/wcf/bindings-overview.md)
