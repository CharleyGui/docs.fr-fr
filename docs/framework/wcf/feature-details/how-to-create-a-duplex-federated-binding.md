---
title: 'Procédure : créer une liaison fédérée duplex'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972059"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Procédure : créer une liaison fédérée duplex

<xref:System.ServiceModel.WSFederationHttpBinding> ne prend en charge que le datagramme et les contrats d'échange de demande/message de réponse. Pour utiliser le contrat d'échange de messages duplex, vous devez créer une liaison personnalisée. Les procédures suivantes indiquent comment faire ceci dans la configuration, à l'aide de la sécurité de mode de transmission de messages pour les transports HTTP et TCP, et à l'aide de la sécurité de mode mixte pour le transport TCP. L’exemple de code illustrant les 3 liaisons est présenté à la fin de cette rubrique.

Vous pouvez également créer la liaison dans le code. Pour obtenir une description de la pile d’éléments de liaison à [créer, consultez Procédure: Créez une liaison personnalisée à l’aide](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)de SecurityBindingElement.

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Pour créer une liaison personnalisée fédérée duplex avec HTTP

1. Dans le [ \<nœud liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration, créez un [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. À l’intérieur `name` de l' `FederationDuplexHttpMessageSecurityBinding` [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un [ \<élément Binding >](../../../../docs/framework/misc/binding.md) avec l’attribut défini sur.

3. À l’intérieur `authenticationMode` de l' `SecureConversation` [ \<élément Binding >](../../../../docs/framework/misc/binding.md) , créez un [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut défini sur.

4. À l’intérieur de `authenticationMode` l' `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un [ \<élément secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut défini sur ou.

5. Après l' [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [ \<CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vide.

6. Après l' [ \<élément CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) , créez un élément [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vide.

7. À la suite de l' [ \<élément oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) , créez un élément [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vide.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité de message TCP

1. Dans le [ \<nœud liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration, créez un [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. À l’intérieur `name` de l' `FederationDuplexTcpMessageSecurityBinding` [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un [ \<élément Binding >](../../../../docs/framework/misc/binding.md) avec l’attribut défini sur.

3. À l’intérieur `authenticationMode` de l' `SecureConversation` [ \<élément Binding >](../../../../docs/framework/misc/binding.md) , créez un [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut défini sur.

4. À l’intérieur de `authenticationMode` l' `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un [ \<élément secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut défini sur ou.

5. Après l' [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [ \<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité mixte TCP

1. Dans le [ \<nœud liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration, créez un [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. À l’intérieur `name` de l' `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un [ \<élément Binding >](../../../../docs/framework/misc/binding.md) avec l’attribut défini sur.

3. À l’intérieur `authenticationMode` de l' `SecureConversation` [ \<élément Binding >](../../../../docs/framework/misc/binding.md) , créez un [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut défini sur.

4. À l’intérieur de `authenticationMode` l' `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un [ \<élément secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut défini sur ou.

5. Après l' [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [ \<section sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vide.

6. À la suite de l' [ \<élément section sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) , créez un élément [ \<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.

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
