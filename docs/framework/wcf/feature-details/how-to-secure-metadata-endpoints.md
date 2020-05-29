---
title: 'Comment : sécuriser des points de terminaison de métadonnées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: 2746c608fb47b94446c5d7e10748ba185d555e7f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202326"
---
# <a name="how-to-secure-metadata-endpoints"></a><span data-ttu-id="317e9-102">Comment : sécuriser des points de terminaison de métadonnées</span><span class="sxs-lookup"><span data-stu-id="317e9-102">How to: Secure Metadata Endpoints</span></span>

<span data-ttu-id="317e9-103">Les métadonnées d'un service peuvent contenir des informations sensibles sur votre application dont un utilisateur malveillant peut tirer parti.</span><span class="sxs-lookup"><span data-stu-id="317e9-103">Metadata for a service can contain sensitive information about your application that a malicious user can leverage.</span></span> <span data-ttu-id="317e9-104">Les consommateurs de votre service peuvent également avoir besoin d'un mécanisme sécurisé pour obtenir des métadonnées sur votre service.</span><span class="sxs-lookup"><span data-stu-id="317e9-104">Consumers of your service may also require a secure mechanism for obtaining metadata about your service.</span></span> <span data-ttu-id="317e9-105">Par conséquent, il est parfois nécessaire de publier vos métadonnées à l'aide d'un point de terminaison sécurisé.</span><span class="sxs-lookup"><span data-stu-id="317e9-105">Therefore, it is sometimes necessary to publish your metadata using a secure endpoint.</span></span>

<span data-ttu-id="317e9-106">Les points de terminaison de métadonnées sont généralement sécurisés à l’aide des mécanismes de sécurité standard définis dans Windows Communication Foundation (WCF) pour la sécurisation des points de terminaison d’application.</span><span class="sxs-lookup"><span data-stu-id="317e9-106">Metadata endpoints are generally secured using the standard security mechanisms defined in Windows Communication Foundation (WCF) for securing application endpoints.</span></span> <span data-ttu-id="317e9-107">Pour plus d’informations, consultez [Vue d’ensemble de la sécurité](security-overview.md).</span><span class="sxs-lookup"><span data-stu-id="317e9-107">For more information, see [Security Overview](security-overview.md).</span></span>

<span data-ttu-id="317e9-108">Cette rubrique présente en détail les étapes permettant de créer un point de terminaison sécurisé par un certificat SSL (Secure Sockets Layer) ou, en d'autres termes, un point de terminaison HTTPS.</span><span class="sxs-lookup"><span data-stu-id="317e9-108">This topic walks through the steps to create an endpoint secured by a Secure Sockets Layer (SSL) certificate or, in other words, an HTTPS endpoint.</span></span>

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a><span data-ttu-id="317e9-109">Pour créer un point de terminaison sécurisé de métadonnées HTTPS GET dans le code</span><span class="sxs-lookup"><span data-stu-id="317e9-109">To create a secure HTTPS GET metadata endpoint in code</span></span>

1. <span data-ttu-id="317e9-110">Configurez un port avec un certificat X.509 approprié.</span><span class="sxs-lookup"><span data-stu-id="317e9-110">Configure a port with an appropriate X.509 certificate.</span></span> <span data-ttu-id="317e9-111">Le certificat doit provenir d'une autorité approuvée et il doit avoir une utilisation prévue de l'autorisation de service.</span><span class="sxs-lookup"><span data-stu-id="317e9-111">The certificate must come from a trusted authority, and it must have an intended use of "Service Authorization."</span></span> <span data-ttu-id="317e9-112">Vous devez utiliser l'outil HttpCfg.exe pour joindre le certificat au port.</span><span class="sxs-lookup"><span data-stu-id="317e9-112">You must use the HttpCfg.exe tool to attach the certificate to the port.</span></span> <span data-ttu-id="317e9-113">Consultez [procédure : configurer un port avec un certificat SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="317e9-113">See [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="317e9-114">Le sujet du certificat ou son nom DNS (Domain Name System) doit correspondre au nom de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="317e9-114">The subject of the certificate or its Domain Name System (DNS) must match the name of the computer.</span></span> <span data-ttu-id="317e9-115">Ceci est essentiel car l'une des premières étapes effectuées par le mécanisme HTTPS est de vérifier que le certificat est émis vers le même URI (Uniform Resource Identifier) que l'adresse avec laquelle il est appelé.</span><span class="sxs-lookup"><span data-stu-id="317e9-115">This is essential because one of the first steps the HTTPS mechanism performs is to check that the certificate is issued to the same Uniform Resource Identifier (URI) as the address upon which it is invoked.</span></span>

2. <span data-ttu-id="317e9-116">Créez une nouvelle instance de la classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="317e9-116">Create a new instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class.</span></span>

3. <span data-ttu-id="317e9-117">Affectez la valeur <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior> de la classe `true`.</span><span class="sxs-lookup"><span data-stu-id="317e9-117">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> property of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class to `true`.</span></span>

4. <span data-ttu-id="317e9-118">Affectez une URL appropriée à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>.</span><span class="sxs-lookup"><span data-stu-id="317e9-118">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> property to an appropriate URL.</span></span> <span data-ttu-id="317e9-119">Notez que si vous spécifiez une adresse absolue, l’URL doit commencer par le schéma `https://` .</span><span class="sxs-lookup"><span data-stu-id="317e9-119">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="317e9-120">Si vous spécifiez une adresse relative, vous devez fournir une adresse de base HTTPS pour votre hôte de service.</span><span class="sxs-lookup"><span data-stu-id="317e9-120">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="317e9-121">Si cette propriété n'est pas définie, l'adresse par défaut est "" ou directement l'adresse de base HTTPS pour le service.</span><span class="sxs-lookup"><span data-stu-id="317e9-121">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

5. <span data-ttu-id="317e9-122">Ajoutez l’instance à la collection de comportements que la propriété <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> de la classe <xref:System.ServiceModel.Description.ServiceDescription> retourne, comme l’illustre le code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="317e9-122">Add the instance to the behaviors collection that the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property of the <xref:System.ServiceModel.Description.ServiceDescription> class returns, as shown in the following code.</span></span>

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a><span data-ttu-id="317e9-123">Pour créer un point de terminaison sécurisé de métadonnées HTTPS GET dans la configuration</span><span class="sxs-lookup"><span data-stu-id="317e9-123">To create a secure HTTPS GET metadata endpoint in configuration</span></span>

1. <span data-ttu-id="317e9-124">Ajoutez un [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément à l' [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément du fichier de configuration pour votre service.</span><span class="sxs-lookup"><span data-stu-id="317e9-124">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element of the configuration file for your service.</span></span>

2. <span data-ttu-id="317e9-125">Ajoutez un [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) élément à l' [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément.</span><span class="sxs-lookup"><span data-stu-id="317e9-125">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

3. <span data-ttu-id="317e9-126">Ajoutez un [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) élément à l' `<serviceBehaviors>` élément.</span><span class="sxs-lookup"><span data-stu-id="317e9-126">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element to the `<serviceBehaviors>` element.</span></span>

4. <span data-ttu-id="317e9-127">Affectez une valeur appropriée à l'attribut `name` de l'élément `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="317e9-127">Set the `name` attribute of the `<behavior>` element to an appropriate value.</span></span> <span data-ttu-id="317e9-128">L'attribut `name` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="317e9-128">The `name` attribute is required.</span></span> <span data-ttu-id="317e9-129">L'exemple ci-dessous utilise la valeur `mySvcBehavior`.</span><span class="sxs-lookup"><span data-stu-id="317e9-129">The example below uses the value `mySvcBehavior`.</span></span>

5. <span data-ttu-id="317e9-130">Ajoutez un [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) à l' `<behavior>` élément.</span><span class="sxs-lookup"><span data-stu-id="317e9-130">Add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) to the `<behavior>` element.</span></span>

6. <span data-ttu-id="317e9-131">Affectez à l'attribut `httpsGetEnabled` de l'élément `<serviceMetadata>` la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="317e9-131">Set the `httpsGetEnabled` attribute of the `<serviceMetadata>` element to `true`.</span></span>

7. <span data-ttu-id="317e9-132">Affectez une valeur appropriée à l'attribut `httpsGetUrl` de l'élément `<serviceMetadata>`.</span><span class="sxs-lookup"><span data-stu-id="317e9-132">Set the `httpsGetUrl` attribute of the `<serviceMetadata>` element to an appropriate value.</span></span> <span data-ttu-id="317e9-133">Notez que si vous spécifiez une adresse absolue, l’URL doit commencer par le schéma `https://` .</span><span class="sxs-lookup"><span data-stu-id="317e9-133">Note that if you specify an absolute address, the URL must begin with the scheme `https://`.</span></span> <span data-ttu-id="317e9-134">Si vous spécifiez une adresse relative, vous devez fournir une adresse de base HTTPS pour votre hôte de service.</span><span class="sxs-lookup"><span data-stu-id="317e9-134">If you specify a relative address, you must supply an HTTPS base address for your service host.</span></span> <span data-ttu-id="317e9-135">Si cette propriété n'est pas définie, l'adresse par défaut est "" ou directement l'adresse de base HTTPS pour le service.</span><span class="sxs-lookup"><span data-stu-id="317e9-135">If this property is not set, the default address is "", or directly at the HTTPS base address for the service.</span></span>

8. <span data-ttu-id="317e9-136">Pour utiliser le comportement avec un service, affectez `behaviorConfiguration` à l’attribut de l' [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) élément la valeur de l’attribut Name de l’élément Behavior.</span><span class="sxs-lookup"><span data-stu-id="317e9-136">To use the behavior with a service, set the `behaviorConfiguration` attribute of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element to the value of the name attribute of the behavior element.</span></span> <span data-ttu-id="317e9-137">Le code de configuration ci-dessous illustre un exemple complet.</span><span class="sxs-lookup"><span data-stu-id="317e9-137">The following configuration code shows a complete example.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a><span data-ttu-id="317e9-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="317e9-138">Example</span></span>

<span data-ttu-id="317e9-139">L'exemple ci-dessous crée une instance d'une classe <xref:System.ServiceModel.ServiceHost> et ajoute un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="317e9-139">The following example creates an instance of a <xref:System.ServiceModel.ServiceHost> class and adds an endpoint.</span></span> <span data-ttu-id="317e9-140">Le code crée ensuite une instance de la classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> et définit les propriétés pour créer un point d'échange de métadonnées sécurisé.</span><span class="sxs-lookup"><span data-stu-id="317e9-140">The code then creates an instance of the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class and sets the properties to create a secure metadata exchange point.</span></span>

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="317e9-141">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="317e9-141">Compiling the Code</span></span>

<span data-ttu-id="317e9-142">L'exemple de code utilise les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="317e9-142">The code example uses the following namespaces:</span></span>

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a><span data-ttu-id="317e9-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="317e9-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [<span data-ttu-id="317e9-144">Comment : configurer un port avec un certificat SSL</span><span class="sxs-lookup"><span data-stu-id="317e9-144">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="317e9-145">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="317e9-145">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="317e9-146">Considérations sur la sécurité des métadonnées</span><span class="sxs-lookup"><span data-stu-id="317e9-146">Security Considerations with Metadata</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [<span data-ttu-id="317e9-147">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="317e9-147">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
