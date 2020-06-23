---
title: "Comment : sécuriser un service à l'aide d'informations d'identification Windows"
description: Découvrez comment activer la sécurité de transport sur un service WCF résidant dans un domaine Windows et appelé par des clients dans le même domaine.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 8ef164e1475bfd5f047a99426a2bed43a7aa7353
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244631"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="d84eb-103">Comment : sécuriser un service à l'aide d'informations d'identification Windows</span><span class="sxs-lookup"><span data-stu-id="d84eb-103">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="d84eb-104">Cette rubrique montre comment activer la sécurité de transport sur un service Windows Communication Foundation (WCF) qui réside dans un domaine Windows et qui est appelé par des clients dans le même domaine.</span><span class="sxs-lookup"><span data-stu-id="d84eb-104">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="d84eb-105">Pour plus d’informations sur ce scénario, consultez [sécurité du transport avec l’authentification Windows](./feature-details/transport-security-with-windows-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d84eb-105">For more information about this scenario, see [Transport Security with Windows Authentication](./feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="d84eb-106">Pour obtenir un exemple d’application, consultez l’exemple [WSHttpBinding](./samples/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d84eb-106">For a sample application, see the [WSHttpBinding](./samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="d84eb-107">Cette rubrique suppose que vous avez une interface de contrat existante et que l'implémentation est déjà définie et s'ajoute à cela.</span><span class="sxs-lookup"><span data-stu-id="d84eb-107">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="d84eb-108">Vous pouvez également modifier un service et un client existants.</span><span class="sxs-lookup"><span data-stu-id="d84eb-108">You can also modify an existing service and client.</span></span>

<span data-ttu-id="d84eb-109">Vous pouvez sécuriser complètement un service avec les informations d'identification Windows dans le code.</span><span class="sxs-lookup"><span data-stu-id="d84eb-109">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="d84eb-110">Vous pouvez également omettre un peu du code en utilisant un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d84eb-110">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="d84eb-111">Cette rubrique décrit les deux approches.</span><span class="sxs-lookup"><span data-stu-id="d84eb-111">This topic shows both ways.</span></span> <span data-ttu-id="d84eb-112">Veillez à n'en utiliser qu'une seule, pas les deux.</span><span class="sxs-lookup"><span data-stu-id="d84eb-112">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="d84eb-113">Les trois premières procédures indiquent comment sécuriser le service à l'aide du code.</span><span class="sxs-lookup"><span data-stu-id="d84eb-113">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="d84eb-114">Les quatrième et cinquième procédures indiquent comment le faire avec un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d84eb-114">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="d84eb-115">Utilisation du code</span><span class="sxs-lookup"><span data-stu-id="d84eb-115">Using Code</span></span>

<span data-ttu-id="d84eb-116">L'intégralité du code du service et du client est présentée dans la section Exemple à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d84eb-116">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="d84eb-117">La première procédure vous guide tout au long de la création et la configuration d'une classe <xref:System.ServiceModel.WSHttpBinding> dans le code.</span><span class="sxs-lookup"><span data-stu-id="d84eb-117">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="d84eb-118">La liaison utilise le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="d84eb-118">The binding uses the HTTP transport.</span></span> <span data-ttu-id="d84eb-119">La même liaison est utilisée sur le client.</span><span class="sxs-lookup"><span data-stu-id="d84eb-119">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="d84eb-120">Pour créer un WSHttpBinding qui utilise des informations d'identification Windows et la sécurité de message</span><span class="sxs-lookup"><span data-stu-id="d84eb-120">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="d84eb-121">Le code de cette procédure est inséré au début de la méthode `Run` de la classe `Test` dans le code de service indiqué à la section Exemple.</span><span class="sxs-lookup"><span data-stu-id="d84eb-121">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="d84eb-122">Créez une instance de la classe <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d84eb-122">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="d84eb-123">Affectez la valeur <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> à la propriété <xref:System.ServiceModel.WSHttpSecurity> de la classe <xref:System.ServiceModel.SecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="d84eb-123">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="d84eb-124">Affectez la valeur <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> à la propriété <xref:System.ServiceModel.MessageSecurityOverHttp> de la classe <xref:System.ServiceModel.MessageCredentialType.Windows>.</span><span class="sxs-lookup"><span data-stu-id="d84eb-124">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="d84eb-125">Le code de cette procédure se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="d84eb-125">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="d84eb-126">Utilisation de la liaison dans un service</span><span class="sxs-lookup"><span data-stu-id="d84eb-126">Using the Binding in a Service</span></span>

<span data-ttu-id="d84eb-127">Il s’agit de la deuxième procédure, qui indique comment utiliser la liaison dans un service auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="d84eb-127">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="d84eb-128">Pour plus d’informations sur les services d’hébergement, consultez [Hébergement de services](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="d84eb-128">For more information about hosting services see [Hosting Services](hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="d84eb-129">Pour utiliser une liaison dans un service</span><span class="sxs-lookup"><span data-stu-id="d84eb-129">To use a binding in a service</span></span>

1. <span data-ttu-id="d84eb-130">Insérez le code de cette procédure après celui de la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="d84eb-130">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="d84eb-131">Créez une variable <xref:System.Type> nommée `contractType` et assignez-lui le type de l'interface (`ICalculator`).</span><span class="sxs-lookup"><span data-stu-id="d84eb-131">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="d84eb-132">Quand vous utilisez Visual Basic, utilisez l' `GetType` opérateur. quand vous utilisez C#, utilisez le `typeof` mot clé.</span><span class="sxs-lookup"><span data-stu-id="d84eb-132">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="d84eb-133">Créez une deuxième variable <xref:System.Type> nommée `serviceType` et assignez-lui le type du contrat implémenté (`Calculator`).</span><span class="sxs-lookup"><span data-stu-id="d84eb-133">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="d84eb-134">Créez une instance de la classe <xref:System.Uri> nommée `baseAddress` avec l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="d84eb-134">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="d84eb-135">L'adresse de base doit avoir un schéma qui correspond au transport.</span><span class="sxs-lookup"><span data-stu-id="d84eb-135">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="d84eb-136">Dans ce cas, le schéma de transport est HTTP, et l’adresse comprend l’Uniform Resource Identifier spéciale (URI) « localhost » et un numéro de port (8036), ainsi qu’une adresse de point de terminaison de base («serviceModelSamples/) : `http://localhost:8036/serviceModelSamples/` .</span><span class="sxs-lookup"><span data-stu-id="d84eb-136">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="d84eb-137">Créez une instance de la classe <xref:System.ServiceModel.ServiceHost> avec les variables `serviceType` et `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="d84eb-137">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="d84eb-138">Ajoutez un point de terminaison au service à l'aide du `contractType`, de la liaison et d'un nom de point de terminaison (secureCalculator).</span><span class="sxs-lookup"><span data-stu-id="d84eb-138">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="d84eb-139">Un client doit concaténer l'adresse de base et le nom de point de terminaison lors du lancement d'un appel au service.</span><span class="sxs-lookup"><span data-stu-id="d84eb-139">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="d84eb-140">Appelez la méthode <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="d84eb-140">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="d84eb-141">Le code de cette procédure est indiqué ici :</span><span class="sxs-lookup"><span data-stu-id="d84eb-141">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="d84eb-142">Utilisation de la liaison sur un client</span><span class="sxs-lookup"><span data-stu-id="d84eb-142">Using the Binding in a Client</span></span>

<span data-ttu-id="d84eb-143">Cette procédure indique comment générer un proxy qui communique avec le service.</span><span class="sxs-lookup"><span data-stu-id="d84eb-143">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="d84eb-144">Le proxy est généré avec l' [outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) qui utilise les métadonnées de service pour créer le proxy.</span><span class="sxs-lookup"><span data-stu-id="d84eb-144">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="d84eb-145">Cette procédure crée également une instance de la classe <xref:System.ServiceModel.WSHttpBinding> pour communiquer avec le service, puis appelle ce dernier.</span><span class="sxs-lookup"><span data-stu-id="d84eb-145">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="d84eb-146">Cet exemple utilise uniquement du code pour créer le client.</span><span class="sxs-lookup"><span data-stu-id="d84eb-146">This example uses only code to create the client.</span></span> <span data-ttu-id="d84eb-147">Vous pouvez aussi, si vous le souhaitez, utiliser un fichier de configuration, indiqué dans la section qui suit cette procédure.</span><span class="sxs-lookup"><span data-stu-id="d84eb-147">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="d84eb-148">Pour utiliser une liaison sur un client avec le code</span><span class="sxs-lookup"><span data-stu-id="d84eb-148">To use a binding in a client with code</span></span>

1. <span data-ttu-id="d84eb-149">Utilisez l'outil SvcUtil.exe pour générer le code du proxy à partir des métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="d84eb-149">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="d84eb-150">Pour plus d’informations, consultez [Comment : créer un client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="d84eb-150">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="d84eb-151">Le code proxy généré hérite de la <xref:System.ServiceModel.ClientBase%601> classe, ce qui garantit que chaque client dispose des constructeurs, méthodes et propriétés nécessaires pour communiquer avec un service WCF.</span><span class="sxs-lookup"><span data-stu-id="d84eb-151">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="d84eb-152">Dans cet exemple, le code généré inclut la classe `CalculatorClient`, qui implémente l'interface `ICalculator`, activant ainsi la compatibilité avec le code de service.</span><span class="sxs-lookup"><span data-stu-id="d84eb-152">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="d84eb-153">Le code de cette procédure est inséré au début de la méthode `Main` du programme client.</span><span class="sxs-lookup"><span data-stu-id="d84eb-153">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="d84eb-154">Créez une instance de la classe <xref:System.ServiceModel.WSHttpBinding> et affectez à son mode de sécurité la valeur `Message` et à son type d'informations d'identification client la valeur `Windows`.</span><span class="sxs-lookup"><span data-stu-id="d84eb-154">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="d84eb-155">L'exemple nomme la variable `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="d84eb-155">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="d84eb-156">Créez une instance de la classe <xref:System.ServiceModel.EndpointAddress> nommée `serviceAddress`.</span><span class="sxs-lookup"><span data-stu-id="d84eb-156">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="d84eb-157">Initialisez l'instance avec l'adresse de base concaténée avec le nom de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d84eb-157">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="d84eb-158">Créez une instance de la classe de client générée avec les variables `serviceAddress` et `clientBinding`.</span><span class="sxs-lookup"><span data-stu-id="d84eb-158">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="d84eb-159">Appelez la méthode <xref:System.ServiceModel.ClientBase%601.Open%2A>, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d84eb-159">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="d84eb-160">Appelez le service et affichez les résultats.</span><span class="sxs-lookup"><span data-stu-id="d84eb-160">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="d84eb-161">Utilisation du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="d84eb-161">Using the Configuration File</span></span>

<span data-ttu-id="d84eb-162">Au lieu de créer la liaison avec le code de procédure, vous pouvez utiliser le code suivant indiqué pour la section Liaisons du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d84eb-162">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="d84eb-163">Si vous n’avez pas encore défini de service, consultez [conception et implémentation de services](designing-and-implementing-services.md)et [Configuration des services](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="d84eb-163">If you do not already have a service defined, see [Designing and Implementing Services](designing-and-implementing-services.md), and [Configuring Services](configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d84eb-164">Ce code de configuration est utilisé dans les fichiers de configuration du service et du client.</span><span class="sxs-lookup"><span data-stu-id="d84eb-164">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="d84eb-165">Pour activer la sécurité de transfert sur un service dans un domaine Windows à l'aide de la configuration</span><span class="sxs-lookup"><span data-stu-id="d84eb-165">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="d84eb-166">Ajoutez un [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) élément à la [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section de l’élément du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d84eb-166">Add a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="d84eb-167">Ajoutez un `binding` élément <> à l' `WSHttpBinding` élément> <et affectez `configurationName` à l’attribut une valeur appropriée à votre application.</span><span class="sxs-lookup"><span data-stu-id="d84eb-167">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="d84eb-168">Ajoutez un `security` élément <> et affectez `mode` à l’attribut la valeur message.</span><span class="sxs-lookup"><span data-stu-id="d84eb-168">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="d84eb-169">Ajoutez un `message` élément <> et affectez `clientCredentialType` à l’attribut la valeur Windows.</span><span class="sxs-lookup"><span data-stu-id="d84eb-169">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="d84eb-170">Dans le fichier de configuration du service, remplacez la section `<bindings>` par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d84eb-170">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="d84eb-171">Si vous n’avez pas encore de fichier de configuration de service, consultez [utilisation de liaisons pour configurer des services et des clients](using-bindings-to-configure-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d84eb-171">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](using-bindings-to-configure-services-and-clients.md).</span></span>

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="d84eb-172">Utilisation de la liaison sur un client</span><span class="sxs-lookup"><span data-stu-id="d84eb-172">Using the Binding in a Client</span></span>

<span data-ttu-id="d84eb-173">Cette procédure indique comment générer deux fichiers : un proxy qui communique avec le service et un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d84eb-173">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="d84eb-174">Elle décrit également les modifications du programme client, qui est le troisième fichier utilisé sur le client.</span><span class="sxs-lookup"><span data-stu-id="d84eb-174">It also describes changes to the client program, which is the third file used on the client.</span></span>

#### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="d84eb-175">Pour utiliser une liaison sur un client avec la configuration</span><span class="sxs-lookup"><span data-stu-id="d84eb-175">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="d84eb-176">Utilisez l'outil SvcUtil.exe pour générer le code proxy et le fichier de configuration à partir des métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="d84eb-176">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="d84eb-177">Pour plus d’informations, consultez [Comment : créer un client](how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="d84eb-177">For more information, see [How to: Create a Client](how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="d84eb-178">Remplacez la [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section du fichier de configuration généré par le code de configuration de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="d84eb-178">Replace the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="d84eb-179">Le code de la procédure est inséré au début de la méthode `Main` du programme client.</span><span class="sxs-lookup"><span data-stu-id="d84eb-179">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="d84eb-180">Créez une instance de la classe de client générée qui passe le nom de la liaison dans le fichier de configuration comme un paramètre d'entrée.</span><span class="sxs-lookup"><span data-stu-id="d84eb-180">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="d84eb-181">Appelez la méthode <xref:System.ServiceModel.ClientBase%601.Open%2A>, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d84eb-181">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="d84eb-182">Appelez le service et affichez les résultats.</span><span class="sxs-lookup"><span data-stu-id="d84eb-182">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="d84eb-183">Exemple</span><span class="sxs-lookup"><span data-stu-id="d84eb-183">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="d84eb-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d84eb-184">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="d84eb-185">Outil Service Model Metadata Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d84eb-185">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="d84eb-186">Guide pratique pour créer un client</span><span class="sxs-lookup"><span data-stu-id="d84eb-186">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="d84eb-187">Sécurisation de services</span><span class="sxs-lookup"><span data-stu-id="d84eb-187">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="d84eb-188">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="d84eb-188">Security Overview</span></span>](./feature-details/security-overview.md)
