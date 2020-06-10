---
title: 'Comment : configurer les services WCF pour interagir avec les clients WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 600b9c28d92f9e2b6e4d586b052cc5762d591521
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599059"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Comment : configurer les services WCF pour interagir avec les clients WSE 3.0

Les services Windows Communication Foundation (WCF) sont compatibles au niveau du câble avec les clients Web Services Enhancements 3,0 for Microsoft .NET (WSE) lorsque les services WCF sont configurés pour utiliser la version du 2004 d’août de la spécification WS-Addressing.

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Pour permettre à un service WCF d'interagir avec les clients WSE 3.0

1. Définissez une liaison personnalisée pour le service WCF.

    Pour indiquer que la version d'août 2004 de la spécification WS-Addressing est utilisée pour l'encodage des messages, il est nécessaire de créer une liaison personnalisée.

    1. Ajoutez un enfant [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) au [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) du fichier de configuration du service.

    2. Spécifiez un nom pour la liaison en ajoutant un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) au [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) et en définissant l' `name` attribut.

    3. Spécifiez un mode d’authentification et la version des spécifications WS-Security utilisées pour sécuriser les messages compatibles avec WSE 3,0, en ajoutant un enfant [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) au [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .

        Pour définir le mode d’authentification, définissez l' `authenticationMode` attribut de [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) . Un mode d'authentification équivaut approximativement à une assertion de sécurité clés en main dans WSE 3.0. Le tableau suivant mappe les modes d’authentification dans WCF à des assertions de sécurité clé en main dans WSE 3,0.

        |Mode d'authentification WCF|Assertion de sécurité clé en main de WSE 3.0|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \*L’une des principales différences entre les `mutualCertificate10Security` `mutualCertificate11Security` assertions de sécurité clé en main et est la version de la spécification WS-Security utilisée par WSE pour sécuriser les messages SOAP. Pour `mutualCertificate10Security`, la version 1.0 de WS-Security est utilisée tandis que c'est la version 1.1 de WS-Security qui est utilisée pour `mutualCertificate11Security`. Pour WCF, la version de la spécification WS-Security est spécifiée dans l' `messageSecurityVersion` attribut de [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) .

        Pour définir la version de la spécification WS-Security utilisée pour sécuriser les messages SOAP, définissez l' `messageSecurityVersion` attribut de [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) . Pour permettre l'interaction avec WSE 3.0, affectez `messageSecurityVersion` à la valeur de l'attribut <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.

    4. Spécifiez que la version d’août 2004 de la spécification WS-Addressing est utilisée par WCF en ajoutant un [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) et en attribuant `messageVersion` à sa valeur la valeur <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> .

        > [!NOTE]
        > Lorsque vous utilisez SOAP 1.2, affectez à l'attribut `messageVersion` la valeur <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.

2. Spécifiez que le service utilise la liaison personnalisée.

    1. Affectez `binding` à l’attribut de l’élément la valeur [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) `customBinding` .

    2. Affectez `bindingConfiguration` à l’attribut de l' [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) élément la valeur spécifiée dans l' `name` attribut du [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) pour la liaison personnalisée.

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

- [Guide pratique pour personnaliser une liaison fournie par le système](../extending/how-to-customize-a-system-provided-binding.md)
