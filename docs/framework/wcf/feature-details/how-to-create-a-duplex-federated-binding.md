---
title: 'Comment : créer une liaison fédérée duplex'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598968"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Comment : créer une liaison fédérée duplex

<xref:System.ServiceModel.WSFederationHttpBinding> ne prend en charge que le datagramme et les contrats d'échange de demande/message de réponse. Pour utiliser le contrat d'échange de messages duplex, vous devez créer une liaison personnalisée. Les procédures suivantes indiquent comment faire ceci dans la configuration, à l'aide de la sécurité de mode de transmission de messages pour les transports HTTP et TCP, et à l'aide de la sécurité de mode mixte pour le transport TCP. L’exemple de code illustrant les 3 liaisons est présenté à la fin de cette rubrique.

Vous pouvez également créer la liaison dans le code. Pour obtenir une description de la pile d’éléments de liaison à créer, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Pour créer une liaison personnalisée fédérée duplex avec HTTP

1. Dans le [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément.

2. À l’intérieur de l' [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément, créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément dont l' `name` attribut a la valeur `FederationDuplexHttpMessageSecurityBinding` .

3. À l’intérieur de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément, créez un [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément dont l' `authenticationMode` attribut a la valeur `SecureConversation` .

4. À l’intérieur de l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément dont l' `authenticationMode` attribut a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .

5. Après l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) élément vide.

6. Après l' [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) élément, créez un [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) élément vide.

7. Après l' [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) élément, créez un [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) élément vide.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité de message TCP

1. Dans le [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément.

2. À l’intérieur de l' [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément, créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément dont l' `name` attribut a la valeur `FederationDuplexTcpMessageSecurityBinding` .

3. À l’intérieur de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément, créez un [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément dont l' `authenticationMode` attribut a la valeur `SecureConversation` .

4. À l’intérieur de l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément dont l' `authenticationMode` attribut a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .

5. Après l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) élément vide.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité mixte TCP

1. Dans le [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément.

2. À l’intérieur de l' [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément, créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément dont l' `name` attribut a la valeur `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .

3. À l’intérieur de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément, créez un [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément dont l' `authenticationMode` attribut a la valeur `SecureConversation` .

4. À l’intérieur de l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément dont l' `authenticationMode` attribut a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .

5. Après l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) élément vide.

6. Après l' [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) élément, créez un [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) élément vide.

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
