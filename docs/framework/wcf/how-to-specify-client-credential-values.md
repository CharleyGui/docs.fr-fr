---
title: "Comment : spécifier des valeurs d'informations d'identification du client"
description: Découvrez comment un service WCF peut spécifier comment un client est authentifié auprès de ce service. Cet exemple spécifie un certificat X. 509 et un mode de transport.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 75a21a7dc083282f6b2fe839167ff1b2eddfb373
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244450"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="303ee-104">Comment : spécifier des valeurs d'informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="303ee-104">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="303ee-105">À l’aide de Windows Communication Foundation (WCF), le service peut spécifier comment un client est authentifié auprès du service.</span><span class="sxs-lookup"><span data-stu-id="303ee-105">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="303ee-106">Par exemple, un service peut stipuler que le client soit authentifié avec un certificat.</span><span class="sxs-lookup"><span data-stu-id="303ee-106">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="303ee-107">Pour déterminer le type d'informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="303ee-107">To determine the client credential type</span></span>

1. <span data-ttu-id="303ee-108">Récupérez les métadonnées à partir du point de terminaison des métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="303ee-108">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="303ee-109">Les métadonnées se composent généralement de deux fichiers : le code client dans le langage de programmation de votre choix (la valeur par défaut est Visual C#) et un fichier de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="303ee-109">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="303ee-110">L'une des manières permettant de récupérer des métadonnées consiste à utiliser l'outil Svcutil.exe pour retourner le code client et la configuration cliente.</span><span class="sxs-lookup"><span data-stu-id="303ee-110">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="303ee-111">Pour plus d’informations, consultez [récupération des métadonnées](./feature-details/retrieving-metadata.md) et [outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="303ee-111">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="303ee-112">Ouvrez le fichier de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="303ee-112">Open the XML configuration file.</span></span> <span data-ttu-id="303ee-113">Si vous utilisez l'outil Svcutil.exe, le nom par défaut du fichier est Output.config.</span><span class="sxs-lookup"><span data-stu-id="303ee-113">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="303ee-114">Recherchez l' **\<security>** élément avec l’attribut **mode** ( **\<security mode =**`MessageOrTransport`**>** où `MessageOrTransport` est défini sur l’un des modes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="303ee-114">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="303ee-115">Recherchez l'élément enfant qui correspond à la valeur de mode.</span><span class="sxs-lookup"><span data-stu-id="303ee-115">Find the child element that matches the mode value.</span></span> <span data-ttu-id="303ee-116">Par exemple, si le mode est défini sur **message**, recherchez l' **\<message>** élément contenu dans l' **\<security>** élément.</span><span class="sxs-lookup"><span data-stu-id="303ee-116">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="303ee-117">Notez la valeur assignée à l’attribut **ClientCredentialType** .</span><span class="sxs-lookup"><span data-stu-id="303ee-117">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="303ee-118">La valeur réelle dépend du mode utilisé, du transport ou du message.</span><span class="sxs-lookup"><span data-stu-id="303ee-118">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="303ee-119">Le code XML suivant montre la configuration pour un client utilisant la sécurité du message et nécessitant un certificat pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="303ee-119">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="303ee-120">Exemple : mode de transport TCP avec certificat comme informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="303ee-120">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="303ee-121">Cet exemple définit le mode de sécurité sur le mode Transport et définit la valeur d'informations d'identification du client sur un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="303ee-121">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="303ee-122">Les procédures suivantes montrent comment définir la valeur d'information d'identification du client sur le client dans le code et dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="303ee-122">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="303ee-123">Cela suppose que vous avez utilisé l' [outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour retourner les métadonnées (code et configuration) du service.</span><span class="sxs-lookup"><span data-stu-id="303ee-123">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="303ee-124">Pour plus d’informations, consultez [Comment : créer un client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="303ee-124">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="303ee-125">Pour spécifier la valeur d'information d'identification du client sur le client dans le code</span><span class="sxs-lookup"><span data-stu-id="303ee-125">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="303ee-126">Utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le code et la configuration à partir du service.</span><span class="sxs-lookup"><span data-stu-id="303ee-126">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="303ee-127">Créez une instance du client WCF à l’aide du code généré.</span><span class="sxs-lookup"><span data-stu-id="303ee-127">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="303ee-128">Sur la classe de client, affectez à la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la classe <xref:System.ServiceModel.ClientBase%601> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="303ee-128">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="303ee-129">Cet exemple affecte à la propriété un certificat X.509 à l'aide de la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.</span><span class="sxs-lookup"><span data-stu-id="303ee-129">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="303ee-130">Vous pouvez utiliser n'importe lesquelles des énumérations de la classe <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span><span class="sxs-lookup"><span data-stu-id="303ee-130">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="303ee-131">Le nom du sujet est utilisé ici au cas où le certificat serait modifié (en raison d'une date d'expiration).</span><span class="sxs-lookup"><span data-stu-id="303ee-131">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="303ee-132">L'utilisation du nom du sujet permet à l'infrastructure de retrouver le certificat.</span><span class="sxs-lookup"><span data-stu-id="303ee-132">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="303ee-133">Pour spécifier la valeur d'information d'identification du client sur le client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="303ee-133">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="303ee-134">Ajoutez un [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) élément à l' [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="303ee-134">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="303ee-135">Ajoutez un [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) élément à l' [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="303ee-135">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="303ee-136">Assurez-vous d'affecter à l'attribut `name` requis une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="303ee-136">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="303ee-137">Ajoutez un [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) élément à l' [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) élément.</span><span class="sxs-lookup"><span data-stu-id="303ee-137">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="303ee-138">Affectez aux attributs suivants des valeurs appropriées : `storeLocation`, `storeName`, `x509FindType` et `findValue`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="303ee-138">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="303ee-139">Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](./feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="303ee-139">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. <span data-ttu-id="303ee-140">Lorsque vous configurez le client, spécifiez le comportement en définissant l'attribut `behaviorConfiguration` de l'élément `<endpoint>`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="303ee-140">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="303ee-141">L’élément de point de terminaison est un enfant de l' [\<client>](../configure-apps/file-schema/wcf/client.md) élément.</span><span class="sxs-lookup"><span data-stu-id="303ee-141">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="303ee-142">Spécifiez également le nom de la configuration de liaison en affectant à l’attribut `bindingConfiguration` la liaison pour le client.</span><span class="sxs-lookup"><span data-stu-id="303ee-142">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="303ee-143">Si vous utilisez un fichier de configuration généré, le nom de la liaison est généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="303ee-143">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="303ee-144">Dans cet exemple, il s'agit du nom `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="303ee-144">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="303ee-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="303ee-145">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="303ee-146">Programmation de la sécurité dans WCF</span><span class="sxs-lookup"><span data-stu-id="303ee-146">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="303ee-147">Sélection d'un type d'informations d'identification</span><span class="sxs-lookup"><span data-stu-id="303ee-147">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="303ee-148">Outil Service Model Metadata Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="303ee-148">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="303ee-149">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="303ee-149">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="303ee-150">Guide pratique pour créer un client</span><span class="sxs-lookup"><span data-stu-id="303ee-150">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md)
