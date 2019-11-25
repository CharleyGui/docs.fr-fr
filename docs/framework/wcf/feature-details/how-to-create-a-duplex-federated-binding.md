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
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="0cd3c-102">Comment : créer une liaison fédérée duplex</span><span class="sxs-lookup"><span data-stu-id="0cd3c-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="0cd3c-103"><xref:System.ServiceModel.WSFederationHttpBinding> ne prend en charge que le datagramme et les contrats d'échange de demande/message de réponse.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="0cd3c-104">Pour utiliser le contrat d'échange de messages duplex, vous devez créer une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="0cd3c-105">Les procédures suivantes indiquent comment faire ceci dans la configuration, à l'aide de la sécurité de mode de transmission de messages pour les transports HTTP et TCP, et à l'aide de la sécurité de mode mixte pour le transport TCP.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="0cd3c-106">L’exemple de code illustrant les 3 liaisons est présenté à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="0cd3c-107">Vous pouvez également créer la liaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-107">You can also create the binding in code.</span></span> <span data-ttu-id="0cd3c-108">Pour obtenir une description de la pile d’éléments de liaison à créer, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="0cd3c-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="0cd3c-109">Pour créer une liaison personnalisée fédérée duplex avec HTTP</span><span class="sxs-lookup"><span data-stu-id="0cd3c-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="0cd3c-110">Dans le [\<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un élément [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0cd3c-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="0cd3c-111">À l’intérieur de l’élément [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un élément de [liaison\<](../../configure-apps/file-schema/wcf/bindings.md) avec l’attribut `name` défini sur `FederationDuplexHttpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="0cd3c-112">À l’intérieur de l’élément de [> de liaison\<](../../configure-apps/file-schema/wcf/bindings.md) , créez un élément [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut `authenticationMode` défini sur `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="0cd3c-113">Dans l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut `authenticationMode` défini sur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="0cd3c-114">Après l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<CompositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vide.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="0cd3c-115">À la suite de l’élément [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) , créez un élément [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vide.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="0cd3c-116">À la suite de l’élément [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) , créez un élément [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vide.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="0cd3c-117">Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité de message TCP</span><span class="sxs-lookup"><span data-stu-id="0cd3c-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="0cd3c-118">Dans le [\<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un élément [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0cd3c-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="0cd3c-119">À l’intérieur de l’élément [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un élément de [liaison\<](../../configure-apps/file-schema/wcf/bindings.md) avec l’attribut `name` défini sur `FederationDuplexTcpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="0cd3c-120">À l’intérieur de l’élément de [> de liaison\<](../../configure-apps/file-schema/wcf/bindings.md) , créez un élément [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut `authenticationMode` défini sur `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="0cd3c-121">Dans l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut `authenticationMode` défini sur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="0cd3c-122">Après l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<TcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="0cd3c-123">Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité mixte TCP</span><span class="sxs-lookup"><span data-stu-id="0cd3c-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="0cd3c-124">Dans le [\<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un élément [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0cd3c-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="0cd3c-125">À l’intérieur de l’élément [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , créez un élément de [liaison\<](../../configure-apps/file-schema/wcf/bindings.md) avec l’attribut `name` défini sur `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="0cd3c-126">À l’intérieur de l’élément de [> de liaison\<](../../configure-apps/file-schema/wcf/bindings.md) , créez un élément [\<Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) avec l’attribut `authenticationMode` défini sur `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="0cd3c-127">Dans l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) avec l’attribut `authenticationMode` défini sur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="0cd3c-128">Après l’élément [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , créez un élément [\<section sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vide.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="0cd3c-129">À la suite de l’élément [\<section sslstreamsecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) , créez un élément [\<TcpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vide.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="0cd3c-130">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="0cd3c-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="0cd3c-131">Exemple avec 3 liaisons</span><span class="sxs-lookup"><span data-stu-id="0cd3c-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="0cd3c-132">Insérez le code suivant dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="0cd3c-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="0cd3c-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cd3c-133">Example</span></span>

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
