---
title: 'Comment : créer une liaison fédérée duplex'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141720"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Comment : créer une liaison fédérée duplex

<xref:System.ServiceModel.WSFederationHttpBinding> ne prend en charge que le datagramme et les contrats d'échange de demande/message de réponse. Pour utiliser le contrat d'échange de messages duplex, vous devez créer une liaison personnalisée. Les procédures suivantes indiquent comment faire ceci dans la configuration, à l'aide de la sécurité de mode de transmission de messages pour les transports HTTP et TCP, et à l'aide de la sécurité de mode mixte pour le transport TCP. L’exemple de code illustrant les 3 liaisons est présenté à la fin de cette rubrique.

Vous pouvez également créer la liaison dans le code. Pour obtenir une description de la pile d’éléments de liaison à créer, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Pour créer une liaison personnalisée fédérée duplex avec HTTP

1. Dans le [\<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un élément [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. À l’intérieur de l’élément [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un élément de [liaison\<](../../configure-apps/file-schema/wcf/bindings.md) avec l’attribut `name` défini sur `FederationDuplexHttpMessageSecurityBinding`.

3. À l’intérieur de l’élément de [> de liaison\<](../../configure-apps/file-schema/wcf/bindings.md) , créez un élément [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut `authenticationMode` défini sur `SecureConversation`.

4. Dans l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut `authenticationMode` défini sur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.

5. Après l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vide.

6. À la suite de l’élément [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) , créez un élément [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vide.

7. À la suite de l’élément [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) , créez un élément [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vide.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité de message TCP

1. Dans le [\<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un élément [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. À l’intérieur de l’élément [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un élément de [liaison\<](../../configure-apps/file-schema/wcf/bindings.md) avec l’attribut `name` défini sur `FederationDuplexTcpMessageSecurityBinding`.

3. À l’intérieur de l’élément de [> de liaison\<](../../configure-apps/file-schema/wcf/bindings.md) , créez un élément [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut `authenticationMode` défini sur `SecureConversation`.

4. Dans l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut `authenticationMode` défini sur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.

5. Après l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité mixte TCP

1. Dans le [\<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un élément [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. À l’intérieur de l’élément [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un élément de [liaison\<](../../configure-apps/file-schema/wcf/bindings.md) avec l’attribut `name` défini sur `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.

3. À l’intérieur de l’élément de [> de liaison\<](../../configure-apps/file-schema/wcf/bindings.md) , créez un élément [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut `authenticationMode` défini sur `SecureConversation`.

4. Dans l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut `authenticationMode` défini sur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.

5. Après l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<section sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vide.

6. À la suite de l’élément [\<section sslstreamsecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) , créez un élément [\<TcpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.

## <a name="code-sample"></a>Exemple de code

### <a name="sample-with-3-bindings"></a>Exemple avec 3 liaisons

1. Insérez le code suivant dans votre fichier de configuration.

## <a name="example"></a>Exemple

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
