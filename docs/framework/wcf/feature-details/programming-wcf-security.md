---
title: Programmation de la sécurité dans WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: d36bd5002d15e98d0cf3273bf18a78684bd3e067
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638436"
---
# <a name="programming-wcf-security"></a>Programmation de la sécurité dans WCF
Cette rubrique décrit les tâches de programmation fondamentales utilisées pour créer une application Windows Communication Foundation (WCF) sécurisé. Cette rubrique couvre uniquement l’authentification, la confidentialité et l’intégrité, collectivement appelées *sécurité de transfert*. Cette rubrique ne couvre pas l’autorisation (le contrôle d’accès aux ressources ou services) ; Pour plus d’informations sur l’autorisation, consultez [autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
>  Pour une présentation correcte des concepts de sécurité, en particulier en ce qui concerne les WCF, consultez l’ensemble de didacticiels de modèles et pratiques sur MSDN à l’adresse [scénarios, les modèles et les conseils d’implémentation pour Web Services Enhancements (WSE) 3.0](https://go.microsoft.com/fwlink/?LinkID=88250).  
  
 Programmation de la sécurité WCF repose sur trois étapes définissant les éléments suivants : le mode de sécurité, un type d’informations d’identification du client et les valeurs d’informations d’identification. Ces étapes peuvent être effectuées au choix dans le code ou la configuration.  
  
## <a name="setting-the-security-mode"></a>Définition du mode de sécurité  
 La section suivante présente les étapes générales pour la programmation avec le mode de sécurité dans WCF :  
  
1. Sélectionnez une liaison prédéfinie adaptée aux exigences de votre application. Pour obtenir la liste des liaisons, consultez [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md). Par défaut, la sécurité de pratiquement toutes les liaisons est activée. La seule exception concerne le <xref:System.ServiceModel.BasicHttpBinding> classe (à l’aide de la configuration, le [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Le transport dépend de la liaison sélectionnée. Par exemple, <xref:System.ServiceModel.WSHttpBinding> utilise le transport HTTP tandis que <xref:System.ServiceModel.NetTcpBinding> utilise le transport TCP.  
  
2. Sélectionnez l'un des modes de sécurité disponibles pour la liaison. Remarque : les modes de sécurité disponibles dépendent de la liaison sélectionnée. Par exemple, la liaison <xref:System.ServiceModel.WSDualHttpBinding> ne permet pas de définir le niveau transport comme mode de sécurité (ce mode n'est pas disponible pour cette liaison). De la même façon, les liaisons <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> et <xref:System.ServiceModel.NetNamedPipeBinding> ne permettent pas de définir le niveau message comme mode de sécurité.  
  
     Trois choix sont possibles :  
  
    1. `Transport`  
  
         La sécurité de transport dépend du mécanisme utilisé par la liaison sélectionnée. Par exemple, si vous utilisez la liaison `WSHttpBinding`, la sécurité utilisée correspondra à Secure Sockets Layer (SSL) (il s'agit également de la sécurité utilisée pour le protocole HTTPS). De manière générale, le principal avantage de la sécurité de niveau transport réside dans le fait qu'elle offre un débit relativement élevé quel que soit le transport utilisé. Toutefois, il a deux limites : Le premier est que le mécanisme de transport détermine le type d’informations d’identification utilisé pour authentifier un utilisateur. Cela pose problème uniquement lorsque le service concerné doit interagir avec d'autres services exigeant un autre type d'informations d'identification. Le second réside dans le fait que la sécurité est implémentée saut par saut plutôt que de bout en bout. Cela peut poser un problème lorsque les messages circulant entre le client et le service concernés rencontrent des intermédiaires. Pour plus d’informations sur le transport à utiliser, consultez [choix d’un Transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Pour plus d’informations sur l’utilisation de la sécurité du transport, consultez [vue d’ensemble de sécurité de Transport](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2. `Message`  
  
         La sécurité de niveau message signifie que chaque message comporte les en-têtes et les données nécessaires à sa sécurisation. La composition des en-têtes variant, vous pouvez ajouter aux messages un nombre illimité d'informations d'identification. Cette possibilité est essentielle lorsque votre service doit interagir avec des services exigeant un type d'informations d'identification spécifique qu'un mécanisme de transport ne peut fournir ou lorsqu'un message doit être utilisé par plusieurs services, chacun d'eux exigeant un type d'informations d'identification différent.  
  
         Pour plus d’informations, consultez [sécurité de Message](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3. `TransportWithMessageCredential`  
  
         Ce mode utilise la couche de transport pour sécuriser le transfert des messages, tandis que chaque message inclut l'ensemble des informations d'identification requises par les autres services. Ce mode allie les avantages de la sécurité de niveau transport aux avantages présentés par la sécurité de niveau message, notamment celui d'utiliser un nombre illimité d'informations d'identification. Ce mode est disponible avec les liaisons suivantes : <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding> et <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Si vous choisissez d’utiliser la sécurité de transport pour HTTP, c’est-à-dire HTTPS, vous devez également configurer l’hôte avec un certificat SSL et activer ce certificat sur l’un des ports de votre ordinateur. Pour plus d’informations, consultez [sécurité du Transport HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4. Si vous utilisez la liaison <xref:System.ServiceModel.WSHttpBinding> et que vous n'avez pas besoin d'établir une session sécurisée, affectez à la propriété <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> la valeur `false`.  
  
     Une session sécurisée intervient lorsqu'un client et un service créent un canal à l'aide d'une clé symétrique (le client et le serveur utilisent la même clé pendant toute la durée de la conversation, jusqu'au terme de celle-ci).  
  
## <a name="setting-the-client-credential-type"></a>Définition du type d'informations d'identification client  
 Sélectionnez un type d'informations d'identification client comme requis. Pour plus d’informations, consultez [sélection d’un Type d’informations d’identification](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). Les types suivants d'informations d'identification client sont disponibles :  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 Vous devez définir le type d'informations d'identification en fonction du mode de sécurité que vous avez sélectionné. Par exemple, si vous avez sélectionné la liaison `wsHttpBinding` et que vous avez affecté au mode de sécurité la valeur Message, vous pouvez alors affecter à l'attribut `clientCredentialType` de l'élément de message l'une des valeurs suivantes : `None`, `Windows`, `UserName`, `Certificate` et `IssuedToken`, comme illustré dans l'exemple de configuration suivant.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 Ou dans le code :  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Définition des valeurs d'informations d'identification service  
 Après avoir sélectionné un type d'informations d'identification client, vous devez définir les informations d'identification que le client et le service devront effectivement utiliser. Du côté service, les informations d'identification sont définies à l'aide de la classe <xref:System.ServiceModel.Description.ServiceCredentials> et sont retournées par la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> de la classe <xref:System.ServiceModel.ServiceHostBase>. Les types d'informations d'identification service et client ainsi que le mode de sécurité dépendent de la liaison utilisée. L'exemple de code suivant définit un certificat pour les informations d'identification service.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Définition des valeurs d'informations d'identification client  
 Du côté client, les informations d'identification sont définies à l'aide de la classe <xref:System.ServiceModel.Description.ClientCredentials> et sont retournées par la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la classe <xref:System.ServiceModel.ClientBase%601>. L'exemple de code suivant définit un certificat pour les informations d'identification client, le protocole TCP étant utilisé.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Programmation WCF de base](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Scénarios de sécurité courants](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
