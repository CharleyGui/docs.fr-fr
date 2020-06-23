---
title: "Comment : utiliser des informations d'identification de sécurité de transport et de message"
description: Apprenez à implémenter la sécurité de transport avec les informations d’identification de message, qui offre le meilleur des modes de transport et de sécurité des messages dans WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246647"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="a54ea-103">Comment : utiliser des informations d'identification de sécurité de transport et de message</span><span class="sxs-lookup"><span data-stu-id="a54ea-103">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="a54ea-104">La sécurisation d’un service avec les informations d’identification de transport et de message utilise le meilleur des modes de sécurité de transport et de message dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a54ea-104">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="a54ea-105">En résumé, la sécurité de la couche de transport assure l'intégrité et la confidentialité des informations tandis que la sécurité de la couche de message offre diverses informations d'identification, lesquelles ne sont pas disponibles lorsque seule la sécurité de niveau transport est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-105">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="a54ea-106">Cette rubrique contient la procédure par étape permettant d’implémenter la sécurité de transport avec les informations d’identification de message à l’aide des liaisons <xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-106">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="a54ea-107">Pour plus d’informations sur la définition du mode de sécurité, consultez [Comment : définir le mode de sécurité](../how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="a54ea-107">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="a54ea-108">Lorsque vous affectez au mode de sécurité la valeur `TransportWithMessageCredential`, le mécanisme chargé d'offrir la sécurité de niveau transport dépend du transport utilisé.</span><span class="sxs-lookup"><span data-stu-id="a54ea-108">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="a54ea-109">Pour le transport HTTP, le mécanisme utilisé est Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire HTTPS, pour le transport TCP, il s'agit de SSL sur TCP ou de Windows.</span><span class="sxs-lookup"><span data-stu-id="a54ea-109">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="a54ea-110">Si le transport correspond à HTTP (à l'aide de la liaison <xref:System.ServiceModel.WSHttpBinding>), la sécurité de niveau transport est assurée par SSL sur HTTP.</span><span class="sxs-lookup"><span data-stu-id="a54ea-110">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="a54ea-111">Dans ce cas, vous devez configurer l’ordinateur hébergeant le service en attribuant un certificat SSL à l’un de ses ports, comme indiqué ci-après dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a54ea-111">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="a54ea-112">Si le transport correspond à TCP (à l'aide de la liaison <xref:System.ServiceModel.NetTcpBinding>), la sécurité de niveau transport est assurée par la sécurité Windows ou par SSL sur TCP.</span><span class="sxs-lookup"><span data-stu-id="a54ea-112">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="a54ea-113">Lorsque vous utilisez la sécurité SSL sur TCP, vous devez spécifier le certificat à l'aide de la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>, comme indiqué ci-après dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a54ea-113">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="a54ea-114">Pour utiliser la liaison WSHttpBinding avec un certificat pour la sécurité de niveau transport (dans le code)</span><span class="sxs-lookup"><span data-stu-id="a54ea-114">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="a54ea-115">Utilisez l’outil HttpCfg.exe pour attribuer un certificat SSL à l’un des ports de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a54ea-115">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="a54ea-116">Pour plus d’informations, consultez [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="a54ea-116">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="a54ea-117">Créez une instance de la classe <xref:System.ServiceModel.WSHttpBinding>, puis affectez à la propriété <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> la valeur <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-117">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="a54ea-118">Affectez à la propriété <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-118">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="a54ea-119">(Pour plus d’informations, consultez [sélection d’un type d’informations d’identification](selecting-a-credential-type.md).) Le code suivant utilise la <xref:System.ServiceModel.MessageCredentialType.Certificate> valeur.</span><span class="sxs-lookup"><span data-stu-id="a54ea-119">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="a54ea-120">Créez une instance de la classe <xref:System.Uri> en utilisant une adresse de base appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-120">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="a54ea-121">Remarque : cette adresse doit utiliser le schéma HTTPS et contenir le véritable nom de l’ordinateur ainsi que le numéro de port auquel le certificat SSL a été attribué.</span><span class="sxs-lookup"><span data-stu-id="a54ea-121">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="a54ea-122">Vous pouvez également définir l'adresse de base dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a54ea-122">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="a54ea-123">Ajoutez un point de terminaison de service à l'aide de la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-123">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="a54ea-124">Créez une instance de <xref:System.ServiceModel.ServiceHost>, puis appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A>, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="a54ea-124">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="a54ea-125">Pour utiliser la liaison NetTcpBinding avec un certificat pour la sécurité de niveau transport (dans le code)</span><span class="sxs-lookup"><span data-stu-id="a54ea-125">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="a54ea-126">Créez une instance de la classe <xref:System.ServiceModel.NetTcpBinding>, puis affectez à la propriété <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> la valeur <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-126">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="a54ea-127">Affectez à la propriété <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-127">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="a54ea-128">Dans l'exemple de code suivant, la valeur <xref:System.ServiceModel.MessageCredentialType.Certificate> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-128">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="a54ea-129">Créez une instance de la classe <xref:System.Uri> en utilisant une adresse de base appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-129">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="a54ea-130">Remarque : cette adresse doit utiliser le schéma « net.tcp ».</span><span class="sxs-lookup"><span data-stu-id="a54ea-130">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="a54ea-131">Vous pouvez également définir l'adresse de base dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a54ea-131">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="a54ea-132">Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-132">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="a54ea-133">Utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> pour définir de manière explicite le certificat X.509 de ce service.</span><span class="sxs-lookup"><span data-stu-id="a54ea-133">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="a54ea-134">Ajoutez un point de terminaison de service à l'aide de la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-134">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="a54ea-135">Appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A>, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a54ea-135">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="a54ea-136">Pour utiliser la liaison NetTcpBinding avec Windows comme sécurité de transport (dans le code)</span><span class="sxs-lookup"><span data-stu-id="a54ea-136">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="a54ea-137">Créez une instance de la classe <xref:System.ServiceModel.NetTcpBinding>, puis affectez à la propriété <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> la valeur <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-137">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="a54ea-138">Configurez la sécurité de transport sur Windows en affectant à la propriété <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> la valeur <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-138">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="a54ea-139">Remarque : il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a54ea-139">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="a54ea-140">Affectez à la propriété <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-140">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="a54ea-141">Dans l'exemple de code suivant, la valeur <xref:System.ServiceModel.MessageCredentialType.Certificate> est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-141">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="a54ea-142">Créez une instance de la classe <xref:System.Uri> en utilisant une adresse de base appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-142">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="a54ea-143">Remarque : cette adresse doit utiliser le schéma « net.tcp ».</span><span class="sxs-lookup"><span data-stu-id="a54ea-143">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="a54ea-144">Vous pouvez également définir l'adresse de base dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="a54ea-144">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="a54ea-145">Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-145">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="a54ea-146">Utilisez la méthode <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> pour définir de manière explicite le certificat X.509 de ce service.</span><span class="sxs-lookup"><span data-stu-id="a54ea-146">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="a54ea-147">Ajoutez un point de terminaison de service à l'aide de la méthode <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>.</span><span class="sxs-lookup"><span data-stu-id="a54ea-147">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="a54ea-148">Appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A>, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a54ea-148">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="a54ea-149">Utilisation de la configuration</span><span class="sxs-lookup"><span data-stu-id="a54ea-149">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="a54ea-150">Pour utiliser la liaison WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a54ea-150">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="a54ea-151">Configurez l’ordinateur en attribuant un certificat SSL à l’un de ses ports.</span><span class="sxs-lookup"><span data-stu-id="a54ea-151">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="a54ea-152">(Pour plus d’informations, consultez [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md)).</span><span class="sxs-lookup"><span data-stu-id="a54ea-152">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="a54ea-153">Vous n’avez pas besoin de définir une `transport` valeur d’élément <> avec cette configuration.</span><span class="sxs-lookup"><span data-stu-id="a54ea-153">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="a54ea-154">Spécifiez le type d'informations d'identification pour la sécurité de niveau message.</span><span class="sxs-lookup"><span data-stu-id="a54ea-154">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="a54ea-155">L’exemple suivant affecte la `clientCredentialType` valeur à l’attribut de l' `message` élément <> `UserName` .</span><span class="sxs-lookup"><span data-stu-id="a54ea-155">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="a54ea-156">Pour utiliser la liaison NetTcpBinding avec un certificat pour la sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="a54ea-156">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="a54ea-157">Pour la sécurité SSL sur TCP, vous devez spécifier de manière explicite le certificat dans l'élément `<behaviors>`.</span><span class="sxs-lookup"><span data-stu-id="a54ea-157">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="a54ea-158">Dans l'exemple suivant, le certificat spécifié est publié par un émetteur figurant dans l'emplacement de magasin par défaut (ordinateur local et magasins personnels).</span><span class="sxs-lookup"><span data-stu-id="a54ea-158">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="a54ea-159">Ajoutez un [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) à la section Bindings.</span><span class="sxs-lookup"><span data-stu-id="a54ea-159">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="a54ea-160">Ajoutez un élément de liaison, puis affectez à l’attribut `name` une valeur adéquate.</span><span class="sxs-lookup"><span data-stu-id="a54ea-160">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="a54ea-161">Ajoutez un `security` élément <> et affectez à l’attribut la valeur `mode` `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="a54ea-161">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="a54ea-162">Ajoutez un `message>` élément <et affectez `clientCredentialType` à l’attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-162">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="a54ea-163">Pour utiliser la liaison NetTcpBinding avec Windows comme sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="a54ea-163">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="a54ea-164">Ajoutez un [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) à la section Bindings,</span><span class="sxs-lookup"><span data-stu-id="a54ea-164">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="a54ea-165">Ajoutez un `binding` élément <> et affectez `name` à l’attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-165">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="a54ea-166">Ajoutez un `security` élément <> et affectez à l’attribut la valeur `mode` `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="a54ea-166">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="a54ea-167">Ajoutez un `transport` élément <> et affectez `clientCredentialType` à l’attribut la valeur `Windows` .</span><span class="sxs-lookup"><span data-stu-id="a54ea-167">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="a54ea-168">Ajoutez un `message` élément <> et affectez `clientCredentialType` à l’attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="a54ea-168">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="a54ea-169">Dans l'exemple de code suivant, un certificat est affecté à la valeur.</span><span class="sxs-lookup"><span data-stu-id="a54ea-169">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a54ea-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a54ea-170">See also</span></span>

- [<span data-ttu-id="a54ea-171">Comment : définir le mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="a54ea-171">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="a54ea-172">Sécurisation de services</span><span class="sxs-lookup"><span data-stu-id="a54ea-172">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="a54ea-173">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="a54ea-173">Securing Services and Clients</span></span>](securing-services-and-clients.md)
