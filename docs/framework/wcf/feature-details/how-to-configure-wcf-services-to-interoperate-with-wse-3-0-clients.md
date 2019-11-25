---
title: 'Comment : configurer les services WCF pour interagir avec les clients WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: bd9f2bec94ca45f76590f64366428a00edd5d6ea
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141746"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Comment : configurer les services WCF pour interagir avec les clients WSE 3.0

Les services Windows Communication Foundation (WCF) sont compatibles au niveau du câble avec les clients Web Services Enhancements 3,0 for Microsoft .NET (WSE) lorsque les services WCF sont configurés pour utiliser la version du 2004 d’août de la spécification WS-Addressing.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Pour permettre à un service WCF d'interagir avec les clients WSE 3.0

1. Définissez une liaison personnalisée pour le service WCF.

    Pour indiquer que la version d'août 2004 de la spécification WS-Addressing est utilisée pour l'encodage des messages, il est nécessaire de créer une liaison personnalisée.

    1. Ajoutez un enfant [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) aux [liaisons de\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration du service.

    2. Spécifiez un nom pour la liaison en ajoutant une [liaison\<](../../configure-apps/file-schema/wcf/bindings.md) au [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) et en définissant l’attribut `name`.

    3. Spécifiez un mode d’authentification et la version des spécifications WS-Security utilisées pour sécuriser les messages compatibles avec WSE 3,0, en ajoutant un > enfant [\<de sécurité](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) aux [> de liaison de\<](../../configure-apps/file-schema/wcf/bindings.md).

        Pour définir le mode d’authentification, définissez l’attribut `authenticationMode` du [> de sécurité\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Un mode d'authentification équivaut approximativement à une assertion de sécurité clés en main dans WSE 3.0. Le tableau suivant mappe les modes d’authentification dans WCF à des assertions de sécurité clé en main dans WSE 3,0.

        |Mode d'authentification WCF|Assertion de sécurité clé en main de WSE 3.0|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \* l’une des principales différences entre les `mutualCertificate10Security` et les assertions de sécurité clé en main `mutualCertificate11Security` est la version de la spécification WS-Security utilisée par WSE pour sécuriser les messages SOAP. Pour `mutualCertificate10Security`, la version 1.0 de WS-Security est utilisée tandis que c'est la version 1.1 de WS-Security qui est utilisée pour `mutualCertificate11Security`. Pour WCF, la version de la spécification WS-Security est spécifiée dans l’attribut `messageSecurityVersion` de la [> de sécurité\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).

        Pour définir la version de la spécification WS-Security utilisée pour sécuriser les messages SOAP, définissez l’attribut `messageSecurityVersion` de la [> de sécurité\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Pour permettre l'interaction avec WSE 3.0, affectez `messageSecurityVersion` à la valeur de l'attribut <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.

    4. Spécifiez que la version d’août 2004 de la spécification WS-Addressing est utilisée par WCF en ajoutant un [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) et affectez à la `messageVersion` sa valeur pour <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.

        > [!NOTE]
        > Lorsque vous utilisez SOAP 1.2, affectez à l'attribut `messageVersion` la valeur <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.

2. Spécifiez que le service utilise la liaison personnalisée.

    1. Affectez la valeur `customBinding`à l’attribut `binding` de l’élément [> point de terminaison\<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) .

    2. Affectez à l’attribut `bindingConfiguration` de l’élément [> point de terminaison\<](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) la valeur spécifiée dans l’attribut `name` de la\<de [liaison >](../../configure-apps/file-schema/wcf/bindings.md) pour la liaison personnalisée.

## <a name="example"></a>Exemple

Dans l’exemple de code suivant, `Service.HelloWorldService` utilise une liaison personnalisée pour interagir avec les clients WSE 3.0. La liaison personnalisée spécifie que la version d'août 2004 de la spécification WS-Addressing et que la version 1.1 de WS-Security sont utilisées pour encoder les messages échangés. Les messages sont sécurisés à l'aide du mode d'authentification <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>.

```xml
<configuration>
  <system.serviceModel>
    <services>
      <service
        behaviorConfiguration="ServiceBehavior"
        name="Service.HelloWorldService">
        <endpoint binding="customBinding" address=""
          bindingConfiguration="ServiceBinding"
          contract="Service.IHelloWorld"></endpoint>
      </service>
    </services>

    <bindings>
      <customBinding>
        <binding name="ServiceBinding">
          <security authenticationMode="AnonymousForCertificate"
                  messageProtectionOrder="SignBeforeEncrypt"
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"
                  requireDerivedKeys="false">
          </security>
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>
          <httpTransport/>
        </binding>
      </customBinding>
    </bindings>
    <behaviors>
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">
        <serviceCredentials>
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>
        </serviceCredentials>
      </behavior>
    </behaviors>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour personnaliser une liaison fournie par le système](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
