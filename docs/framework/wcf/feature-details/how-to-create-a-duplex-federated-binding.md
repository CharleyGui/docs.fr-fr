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
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="8d735-102">Procédure : créer une liaison fédérée duplex</span><span class="sxs-lookup"><span data-stu-id="8d735-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="8d735-103"><xref:System.ServiceModel.WSFederationHttpBinding> ne prend en charge que le datagramme et les contrats d'échange de demande/message de réponse.</span><span class="sxs-lookup"><span data-stu-id="8d735-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="8d735-104">Pour utiliser le contrat d'échange de messages duplex, vous devez créer une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="8d735-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="8d735-105">Les procédures suivantes indiquent comment faire ceci dans la configuration, à l'aide de la sécurité de mode de transmission de messages pour les transports HTTP et TCP, et à l'aide de la sécurité de mode mixte pour le transport TCP.</span><span class="sxs-lookup"><span data-stu-id="8d735-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="8d735-106">L’exemple de code illustrant les 3 liaisons est présenté à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8d735-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="8d735-107">Vous pouvez également créer la liaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="8d735-107">You can also create the binding in code.</span></span> <span data-ttu-id="8d735-108">Pour obtenir une description de la pile d’éléments de liaison à [créer, consultez Procédure: Créez une liaison personnalisée à l’aide](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)de SecurityBindingElement.</span><span class="sxs-lookup"><span data-stu-id="8d735-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="8d735-109">Pour créer une liaison personnalisée fédérée duplex avec HTTP</span><span class="sxs-lookup"><span data-stu-id="8d735-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="8d735-110">Dans le [ \<nœud liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration, créez un [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8d735-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="8d735-111">À l’intérieur `name` de l' `FederationDuplexHttpMessageSecurityBinding` [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un [ \<élément Binding >](../../../../docs/framework/misc/binding.md) avec l’attribut défini sur.</span><span class="sxs-lookup"><span data-stu-id="8d735-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="8d735-112">À l’intérieur `authenticationMode` de l' `SecureConversation` [ \<élément Binding >](../../../../docs/framework/misc/binding.md) , créez un [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut défini sur.</span><span class="sxs-lookup"><span data-stu-id="8d735-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="8d735-113">À l’intérieur de `authenticationMode` l' `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un [ \<élément secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut défini sur ou.</span><span class="sxs-lookup"><span data-stu-id="8d735-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="8d735-114">Après l' [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [ \<CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vide.</span><span class="sxs-lookup"><span data-stu-id="8d735-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="8d735-115">Après l' [ \<élément CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) , créez un élément [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vide.</span><span class="sxs-lookup"><span data-stu-id="8d735-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="8d735-116">À la suite de l' [ \<élément oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) , créez un élément [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vide.</span><span class="sxs-lookup"><span data-stu-id="8d735-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="8d735-117">Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité de message TCP</span><span class="sxs-lookup"><span data-stu-id="8d735-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="8d735-118">Dans le [ \<nœud liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration, créez un [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8d735-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="8d735-119">À l’intérieur `name` de l' `FederationDuplexTcpMessageSecurityBinding` [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un [ \<élément Binding >](../../../../docs/framework/misc/binding.md) avec l’attribut défini sur.</span><span class="sxs-lookup"><span data-stu-id="8d735-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="8d735-120">À l’intérieur `authenticationMode` de l' `SecureConversation` [ \<élément Binding >](../../../../docs/framework/misc/binding.md) , créez un [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut défini sur.</span><span class="sxs-lookup"><span data-stu-id="8d735-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="8d735-121">À l’intérieur de `authenticationMode` l' `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un [ \<élément secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut défini sur ou.</span><span class="sxs-lookup"><span data-stu-id="8d735-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="8d735-122">Après l' [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [ \<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.</span><span class="sxs-lookup"><span data-stu-id="8d735-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="8d735-123">Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité mixte TCP</span><span class="sxs-lookup"><span data-stu-id="8d735-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="8d735-124">Dans le [ \<nœud liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration, créez un [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8d735-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="8d735-125">À l’intérieur `name` de l' `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` [ \<élément CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un [ \<élément Binding >](../../../../docs/framework/misc/binding.md) avec l’attribut défini sur.</span><span class="sxs-lookup"><span data-stu-id="8d735-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="8d735-126">À l’intérieur `authenticationMode` de l' `SecureConversation` [ \<élément Binding >](../../../../docs/framework/misc/binding.md) , créez un [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut défini sur.</span><span class="sxs-lookup"><span data-stu-id="8d735-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="8d735-127">À l’intérieur de `authenticationMode` l' `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un [ \<élément secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut défini sur ou.</span><span class="sxs-lookup"><span data-stu-id="8d735-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="8d735-128">Après l' [ \<élément Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [ \<section sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vide.</span><span class="sxs-lookup"><span data-stu-id="8d735-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="8d735-129">À la suite de l' [ \<élément section sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) , créez un élément [ \<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.</span><span class="sxs-lookup"><span data-stu-id="8d735-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8d735-130">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="8d735-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="8d735-131">Exemple avec 3 liaisons</span><span class="sxs-lookup"><span data-stu-id="8d735-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="8d735-132">Insérez le code suivant dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8d735-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="8d735-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d735-133">Example</span></span>

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
