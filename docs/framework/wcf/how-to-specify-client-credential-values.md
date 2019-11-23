---
title: "Comment : spécifier des valeurs d'informations d'identification du client"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319863"
---
# <a name="how-to-specify-client-credential-values"></a><span data-ttu-id="2f0b4-102">Comment : spécifier des valeurs d'informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="2f0b4-102">How to: Specify Client Credential Values</span></span>

<span data-ttu-id="2f0b4-103">À l’aide de Windows Communication Foundation (WCF), le service peut spécifier comment un client est authentifié auprès du service.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-103">Using Windows Communication Foundation (WCF), the service can specify how a client is authenticated to the service.</span></span> <span data-ttu-id="2f0b4-104">Par exemple, un service peut stipuler que le client soit authentifié avec un certificat.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-104">For example, a service can stipulate that the client be authenticated with a certificate.</span></span>

## <a name="to-determine-the-client-credential-type"></a><span data-ttu-id="2f0b4-105">Pour déterminer le type d'informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="2f0b4-105">To determine the client credential type</span></span>

1. <span data-ttu-id="2f0b4-106">Récupérez les métadonnées à partir du point de terminaison des métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-106">Retrieve metadata from the service's metadata endpoint.</span></span> <span data-ttu-id="2f0b4-107">Les métadonnées se composent généralement de deux fichiers : le code client dans le langage de programmation de votre choix (la valeur par défaut est Visual C#) et un fichier de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-107">The metadata typically consists of two files: the client code in the programming language of your choice (the default is Visual C#), and an XML configuration file.</span></span> <span data-ttu-id="2f0b4-108">L'une des manières permettant de récupérer des métadonnées consiste à utiliser l'outil Svcutil.exe pour retourner le code client et la configuration cliente.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-108">One way to retrieve metadata is to use the Svcutil.exe tool to return the client code and client configuration.</span></span> <span data-ttu-id="2f0b4-109">Pour plus d’informations, consultez [récupération des métadonnées](./feature-details/retrieving-metadata.md) et [outil utilitaire de métadonnées ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2f0b4-109">For more information, see [Retrieving Metadata](./feature-details/retrieving-metadata.md) and [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

2. <span data-ttu-id="2f0b4-110">Ouvrez le fichier de configuration XML.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-110">Open the XML configuration file.</span></span> <span data-ttu-id="2f0b4-111">Si vous utilisez l'outil Svcutil.exe, le nom par défaut du fichier est Output.config.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-111">If you use the Svcutil.exe tool, the default name of the file is Output.config.</span></span>

3. <span data-ttu-id="2f0b4-112">Recherchez l’élément **\<security >** avec l’attribut **mode** ( **\<Security mode =** `MessageOrTransport` **>** , où `MessageOrTransport` est défini sur l’un des modes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-112">Find the **\<security>** element with the **mode** attribute (**\<security mode =**`MessageOrTransport`**>** where `MessageOrTransport` is set to one of the security modes.</span></span>

4. <span data-ttu-id="2f0b4-113">Recherchez l'élément enfant qui correspond à la valeur de mode.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-113">Find the child element that matches the mode value.</span></span> <span data-ttu-id="2f0b4-114">Par exemple, si le mode est défini sur **message**, recherchez le **\<message >** contenu dans l’élément **\<de > de sécurité** .</span><span class="sxs-lookup"><span data-stu-id="2f0b4-114">For example, if the mode is set to **Message**, find the **\<message>** element contained in the **\<security>** element.</span></span>

5. <span data-ttu-id="2f0b4-115">Notez la valeur assignée à l’attribut **ClientCredentialType** .</span><span class="sxs-lookup"><span data-stu-id="2f0b4-115">Note the value assigned to the **clientCredentialType** attribute.</span></span> <span data-ttu-id="2f0b4-116">La valeur réelle dépend du mode utilisé, du transport ou du message.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-116">The actual value depends on which mode is used, transport or message.</span></span>

<span data-ttu-id="2f0b4-117">Le code XML suivant montre la configuration pour un client utilisant la sécurité du message et nécessitant un certificat pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-117">The following XML code shows configuration for a client using message security and requiring a certificate to authenticate the client.</span></span>

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a><span data-ttu-id="2f0b4-118">Exemple : mode de transport TCP avec certificat comme informations d'identification du client</span><span class="sxs-lookup"><span data-stu-id="2f0b4-118">Example: TCP Transport Mode with Certificate as Client Credential</span></span>

<span data-ttu-id="2f0b4-119">Cet exemple définit le mode de sécurité sur le mode Transport et définit la valeur d'informations d'identification du client sur un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-119">This example sets the security mode to Transport mode and sets the client credential value to an X.509 certificate.</span></span> <span data-ttu-id="2f0b4-120">Les procédures suivantes montrent comment définir la valeur d'information d'identification du client sur le client dans le code et dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-120">The following procedures demonstrate how to set the client credential value on the client in code and configuration.</span></span> <span data-ttu-id="2f0b4-121">Cela suppose que vous avez utilisé l' [outil ServiceModel Metadata Utility (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour retourner les métadonnées (code et configuration) du service.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-121">This assumes that you have used the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to return the metadata (code and configuration) from the service.</span></span> <span data-ttu-id="2f0b4-122">Pour plus d’informations, consultez [Comment : créer un client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="2f0b4-122">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a><span data-ttu-id="2f0b4-123">Pour spécifier la valeur d'information d'identification du client sur le client dans le code</span><span class="sxs-lookup"><span data-stu-id="2f0b4-123">To specify the client credential value on the client in code</span></span>

1. <span data-ttu-id="2f0b4-124">Utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le code et la configuration à partir du service.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-124">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate code and configuration from the service.</span></span>

2. <span data-ttu-id="2f0b4-125">Créez une instance du client WCF à l’aide du code généré.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-125">Create an instance of the WCF client using the generated code.</span></span>

3. <span data-ttu-id="2f0b4-126">Sur la classe de client, affectez à la propriété <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> de la classe <xref:System.ServiceModel.ClientBase%601> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-126">On the client class, set the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class to an appropriate value.</span></span> <span data-ttu-id="2f0b4-127">Cet exemple affecte à la propriété un certificat X.509 à l'aide de la méthode <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> de la classe <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-127">This example sets the property to an X.509 certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     <span data-ttu-id="2f0b4-128">Vous pouvez utiliser n'importe lesquelles des énumérations de la classe <xref:System.Security.Cryptography.X509Certificates.X509FindType>.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-128">You can use any of the enumerations of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> class.</span></span> <span data-ttu-id="2f0b4-129">Le nom du sujet est utilisé ici au cas où le certificat serait modifié (en raison d'une date d'expiration).</span><span class="sxs-lookup"><span data-stu-id="2f0b4-129">The subject name is used here in case the certificate is changed (due to an expiration date).</span></span> <span data-ttu-id="2f0b4-130">L'utilisation du nom du sujet permet à l'infrastructure de retrouver le certificat.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-130">Using the subject name enables the infrastructure to find the certificate again.</span></span>

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a><span data-ttu-id="2f0b4-131">Pour spécifier la valeur d'information d'identification du client sur le client dans la configuration</span><span class="sxs-lookup"><span data-stu-id="2f0b4-131">To specify the client credential value on the client in configuration</span></span>

1. <span data-ttu-id="2f0b4-132">Ajoutez un élément de [> de comportement\<](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) à l’élément de [> comportements\<](../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="2f0b4-132">Add a [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

2. <span data-ttu-id="2f0b4-133">Ajoutez un élément [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) à l’élément comportements de l' [\<>](../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="2f0b4-133">Add a [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element to the [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md) element.</span></span> <span data-ttu-id="2f0b4-134">Assurez-vous d'affecter à l'attribut `name` requis une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-134">Be sure to set the required `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="2f0b4-135">Ajoutez un élément [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) à l’élément [\<ClientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="2f0b4-135">Add a [\<clientCertificate>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) element to the [\<clientCredentials>](../configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>

4. <span data-ttu-id="2f0b4-136">Affectez aux attributs suivants des valeurs appropriées : `storeLocation`, `storeName`, `x509FindType` et `findValue`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-136">Set the following attributes to appropriate values: `storeLocation`, `storeName`, `x509FindType`, and `findValue`, as shown in the following code.</span></span> <span data-ttu-id="2f0b4-137">Pour plus d’informations sur les certificats, consultez [Utilisation de certificats](./feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2f0b4-137">For more information about certificates, see [Working with Certificates](./feature-details/working-with-certificates.md).</span></span>

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

5. <span data-ttu-id="2f0b4-138">Lorsque vous configurez le client, spécifiez le comportement en définissant l'attribut `behaviorConfiguration` de l'élément `<endpoint>`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-138">When configuring the client, specify the behavior by setting the `behaviorConfiguration` attribute of the `<endpoint>` element, as shown in the following code.</span></span> <span data-ttu-id="2f0b4-139">L’élément de point de terminaison est un enfant de l’élément de [> du client\<](../configure-apps/file-schema/wcf/client.md) .</span><span class="sxs-lookup"><span data-stu-id="2f0b4-139">The endpoint element is a child of the [\<client>](../configure-apps/file-schema/wcf/client.md) element.</span></span> <span data-ttu-id="2f0b4-140">Spécifiez également le nom de la configuration de liaison en affectant à l’attribut `bindingConfiguration` la liaison pour le client.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-140">Also, specify the name of the binding configuration by setting the `bindingConfiguration` attribute to the binding for the client.</span></span> <span data-ttu-id="2f0b4-141">Si vous utilisez un fichier de configuration généré, le nom de la liaison est généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-141">If you are using a generated configuration file, the binding's name is automatically generated.</span></span> <span data-ttu-id="2f0b4-142">Dans cet exemple, le nom est `"tcpBindingWithCredential"`.</span><span class="sxs-lookup"><span data-stu-id="2f0b4-142">In this example, the name is `"tcpBindingWithCredential"`.</span></span>

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a><span data-ttu-id="2f0b4-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f0b4-143">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [<span data-ttu-id="2f0b4-144">Programmation de la sécurité dans WCF</span><span class="sxs-lookup"><span data-stu-id="2f0b4-144">Programming WCF Security</span></span>](./feature-details/programming-wcf-security.md)
- [<span data-ttu-id="2f0b4-145">Sélection d’un type d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="2f0b4-145">Selecting a Credential Type</span></span>](./feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="2f0b4-146">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="2f0b4-146">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="2f0b4-147">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="2f0b4-147">Working with Certificates</span></span>](./feature-details/working-with-certificates.md)
- [<span data-ttu-id="2f0b4-148">Guide pratique pour créer un client</span><span class="sxs-lookup"><span data-stu-id="2f0b4-148">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="2f0b4-149">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="2f0b4-149">\<netTcpBinding></span></span>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [<span data-ttu-id="2f0b4-150">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="2f0b4-150">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [<span data-ttu-id="2f0b4-151">\<message></span><span class="sxs-lookup"><span data-stu-id="2f0b4-151">\<message></span></span>](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [<span data-ttu-id="2f0b4-152">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2f0b4-152">\<behavior></span></span>](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [<span data-ttu-id="2f0b4-153">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="2f0b4-153">\<behaviors></span></span>](../configure-apps/file-schema/wcf/behaviors.md)
- [<span data-ttu-id="2f0b4-154">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="2f0b4-154">\<clientCertificate></span></span>](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [<span data-ttu-id="2f0b4-155">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="2f0b4-155">\<clientCredentials></span></span>](../configure-apps/file-schema/wcf/clientcredentials.md)
