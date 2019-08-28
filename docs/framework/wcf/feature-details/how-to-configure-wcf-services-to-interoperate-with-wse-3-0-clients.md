---
title: 'Procédure : configurer les services WCF pour interagir avec des clients WSE 3.0'
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: 0349c9ba76b3f240bf98daa0e095b415bc98a87c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045937"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="4237d-102">Procédure : configurer les services WCF pour interagir avec des clients WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="4237d-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>

<span data-ttu-id="4237d-103">Les services Windows Communication Foundation (WCF) sont compatibles au niveau du câble avec les clients Web Services Enhancements 3,0 for Microsoft .NET (WSE) lorsque les services WCF sont configurés pour utiliser la version du 2004 d’août de la spécification WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="4237d-103">Windows Communication Foundation (WCF) services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when WCF services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="4237d-104">Pour permettre à un service WCF d'interagir avec les clients WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="4237d-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>

1. <span data-ttu-id="4237d-105">Définissez une liaison personnalisée pour le service WCF.</span><span class="sxs-lookup"><span data-stu-id="4237d-105">Define a custom binding for the WCF service.</span></span>

    <span data-ttu-id="4237d-106">Pour indiquer que la version d'août 2004 de la spécification WS-Addressing est utilisée pour l'encodage des messages, il est nécessaire de créer une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4237d-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>

    1. <span data-ttu-id="4237d-107">Ajoutez une [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [ >CustomBindingenfantauxliaisons>dufichierdeconfigurationduservice.\<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4237d-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>

    2. <span data-ttu-id="4237d-108">Spécifiez un nom pour la liaison en ajoutant `name` une [ \<](../../../../docs/framework/misc/binding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) > de liaison au > CustomBinding et en définissant l’attribut.</span><span class="sxs-lookup"><span data-stu-id="4237d-108">Specify a name for the binding, by adding a [\<binding>](../../../../docs/framework/misc/binding.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>

    3. <span data-ttu-id="4237d-109">Spécifiez un mode d’authentification et la version des spécifications WS-Security utilisées pour sécuriser les messages compatibles avec WSE 3,0, en ajoutant un [ \<](../../../../docs/framework/misc/binding.md)> de [ \<sécurité](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) enfant au > de liaison.</span><span class="sxs-lookup"><span data-stu-id="4237d-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>

        <span data-ttu-id="4237d-110">Pour définir le mode d’authentification, définissez `authenticationMode` l’attribut de la [ \<> de sécurité](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="4237d-110">To set the authentication mode, set the `authenticationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="4237d-111">Un mode d'authentification équivaut approximativement à une assertion de sécurité clés en main dans WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="4237d-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="4237d-112">Le tableau suivant mappe les modes d’authentification dans WCF à des assertions de sécurité clé en main dans WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="4237d-112">The following table maps authentication modes in WCF to turnkey security assertions in WSE 3.0.</span></span>

        |<span data-ttu-id="4237d-113">Mode d'authentification WCF</span><span class="sxs-lookup"><span data-stu-id="4237d-113">WCF Authentication Mode</span></span>|<span data-ttu-id="4237d-114">Assertion de sécurité clé en main de WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="4237d-114">WSE 3.0 turnkey security assertion</span></span>|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        <span data-ttu-id="4237d-115">\*L’une des principales différences entre les `mutualCertificate10Security` assertions de sécurité clé en main et `mutualCertificate11Security` est la version de la spécification WS-Security utilisée par WSE pour sécuriser les messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="4237d-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="4237d-116">Pour `mutualCertificate10Security`, la version 1.0 de WS-Security est utilisée tandis que c'est la version 1.1 de WS-Security qui est utilisée pour `mutualCertificate11Security`.</span><span class="sxs-lookup"><span data-stu-id="4237d-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="4237d-117">Pour WCF, la version de la spécification WS-Security est spécifiée dans l' `messageSecurityVersion` attribut de la [ \<> de sécurité](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="4237d-117">For WCF, the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>

        <span data-ttu-id="4237d-118">Pour définir la version de la spécification WS-Security utilisée pour sécuriser les messages SOAP, définissez l' `messageSecurityVersion` attribut de la [ \<> de sécurité](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="4237d-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="4237d-119">Pour permettre l'interaction avec WSE 3.0, affectez `messageSecurityVersion` à la valeur de l'attribut <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span><span class="sxs-lookup"><span data-stu-id="4237d-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>

    4. <span data-ttu-id="4237d-120">Spécifiez que la version d’août 2004 de la spécification WS-Addressing est utilisée par WCF en ajoutant un [ \<> textMessageEncoding](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) et en attribuant à sa valeur la `messageVersion` valeur <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="4237d-120">Specify that the August 2004 version of the WS-Addressing specification is used by WCF by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>

        > [!NOTE]
        > <span data-ttu-id="4237d-121">Lorsque vous utilisez SOAP 1.2, affectez à l'attribut `messageVersion` la valeur <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span><span class="sxs-lookup"><span data-stu-id="4237d-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>

2. <span data-ttu-id="4237d-122">Spécifiez que le service utilise la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4237d-122">Specify that the service uses the custom binding.</span></span>

    1. <span data-ttu-id="4237d-123">Affectez `binding` à`customBinding`l’attribut [ \<du point de terminaison >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) élément la valeur.</span><span class="sxs-lookup"><span data-stu-id="4237d-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>

    2. <span data-ttu-id="4237d-124">Affectez à l' `name` [ \<attributde](../../../../docs/framework/misc/binding.md) l' [ \<élément de point de terminaison >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) la valeur spécifiée dans l’attribut de la > de liaison pour la liaison personnalisée. `bindingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="4237d-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) for the custom binding.</span></span>

## <a name="example"></a><span data-ttu-id="4237d-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="4237d-125">Example</span></span>

<span data-ttu-id="4237d-126">Dans l’exemple de code suivant, `Service.HelloWorldService` utilise une liaison personnalisée pour interagir avec les clients WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="4237d-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="4237d-127">La liaison personnalisée spécifie que la version d'août 2004 de la spécification WS-Addressing et que la version 1.1 de WS-Security sont utilisées pour encoder les messages échangés.</span><span class="sxs-lookup"><span data-stu-id="4237d-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="4237d-128">Les messages sont sécurisés à l'aide du mode d'authentification <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>.</span><span class="sxs-lookup"><span data-stu-id="4237d-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4237d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4237d-129">See also</span></span>

- [<span data-ttu-id="4237d-130">Guide pratique pour Personnaliser une liaison fournie par le système</span><span class="sxs-lookup"><span data-stu-id="4237d-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
