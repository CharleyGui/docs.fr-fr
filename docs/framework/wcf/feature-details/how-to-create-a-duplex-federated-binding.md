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
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="78dd5-102">Comment : créer une liaison fédérée duplex</span><span class="sxs-lookup"><span data-stu-id="78dd5-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="78dd5-103"><xref:System.ServiceModel.WSFederationHttpBinding> ne prend en charge que le datagramme et les contrats d'échange de demande/message de réponse.</span><span class="sxs-lookup"><span data-stu-id="78dd5-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="78dd5-104">Pour utiliser le contrat d'échange de messages duplex, vous devez créer une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="78dd5-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="78dd5-105">Les procédures suivantes indiquent comment faire ceci dans la configuration, à l'aide de la sécurité de mode de transmission de messages pour les transports HTTP et TCP, et à l'aide de la sécurité de mode mixte pour le transport TCP.</span><span class="sxs-lookup"><span data-stu-id="78dd5-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="78dd5-106">L’exemple de code illustrant les 3 liaisons est présenté à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="78dd5-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="78dd5-107">Vous pouvez également créer la liaison dans le code.</span><span class="sxs-lookup"><span data-stu-id="78dd5-107">You can also create the binding in code.</span></span> <span data-ttu-id="78dd5-108">Pour obtenir une description de la pile d’éléments de liaison à créer, consultez [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="78dd5-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="78dd5-109">Pour créer une liaison personnalisée fédérée duplex avec HTTP</span><span class="sxs-lookup"><span data-stu-id="78dd5-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="78dd5-110">Dans le [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="78dd5-110">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="78dd5-111">À l’intérieur de l' [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément, créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément dont l' `name` attribut a la valeur `FederationDuplexHttpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-111">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="78dd5-112">À l’intérieur de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément, créez un [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément dont l' `authenticationMode` attribut a la valeur `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="78dd5-113">À l’intérieur de l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément dont l' `authenticationMode` attribut a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-113">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="78dd5-114">Après l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) élément vide.</span><span class="sxs-lookup"><span data-stu-id="78dd5-114">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="78dd5-115">Après l' [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) élément, créez un [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) élément vide.</span><span class="sxs-lookup"><span data-stu-id="78dd5-115">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="78dd5-116">Après l' [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) élément, créez un [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) élément vide.</span><span class="sxs-lookup"><span data-stu-id="78dd5-116">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="78dd5-117">Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité de message TCP</span><span class="sxs-lookup"><span data-stu-id="78dd5-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="78dd5-118">Dans le [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="78dd5-118">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="78dd5-119">À l’intérieur de l' [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément, créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément dont l' `name` attribut a la valeur `FederationDuplexTcpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-119">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="78dd5-120">À l’intérieur de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément, créez un [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément dont l' `authenticationMode` attribut a la valeur `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="78dd5-121">À l’intérieur de l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément dont l' `authenticationMode` attribut a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-121">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="78dd5-122">Après l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) élément vide.</span><span class="sxs-lookup"><span data-stu-id="78dd5-122">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="78dd5-123">Pour créer une liaison personnalisée fédérée duplex avec le mode de sécurité mixte TCP</span><span class="sxs-lookup"><span data-stu-id="78dd5-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="78dd5-124">Dans le [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) nœud du fichier de configuration, créez un [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="78dd5-124">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="78dd5-125">À l’intérieur de l' [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) élément, créez un [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément dont l' `name` attribut a la valeur `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-125">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="78dd5-126">À l’intérieur de l' [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) élément, créez un [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément dont l' `authenticationMode` attribut a la valeur `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="78dd5-127">À l’intérieur de l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) élément dont l' `authenticationMode` attribut a la valeur `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="78dd5-127">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="78dd5-128">Après l' [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) élément, créez un [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) élément vide.</span><span class="sxs-lookup"><span data-stu-id="78dd5-128">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="78dd5-129">Après l' [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) élément, créez un [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) élément vide.</span><span class="sxs-lookup"><span data-stu-id="78dd5-129">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="78dd5-130">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="78dd5-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="78dd5-131">Exemple avec 3 liaisons</span><span class="sxs-lookup"><span data-stu-id="78dd5-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="78dd5-132">Insérez le code suivant dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="78dd5-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="78dd5-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="78dd5-133">Example</span></span>

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
