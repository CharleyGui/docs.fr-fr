---
title: 'Procédure : créer une liaison de session fiable personnalisée avec HTTPS'
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: f39325829cf4b548482a6a570a5aa1fd65e61a1d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039531"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="5601b-102">Procédure : créer une liaison de session fiable personnalisée avec HTTPS</span><span class="sxs-lookup"><span data-stu-id="5601b-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="5601b-103">Cette rubrique décrit l'utilisation de la sécurité de transport SSL (Secure Socket Layer) avec les sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="5601b-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="5601b-104">Pour utiliser une session fiable sur HTTPS, vous devez créer une liaison personnalisée qui utilise une session fiable et le transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5601b-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="5601b-105">Vous activez la session fiable soit impérativement en utilisant du code ou de façon déclarative dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5601b-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="5601b-106">Cette procédure utilise les fichiers de configuration client et le service pour activer la session fiable et le [  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) élément.</span><span class="sxs-lookup"><span data-stu-id="5601b-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="5601b-107">La partie clé de cette procédure est que le  **\<point de terminaison >** élément de configuration contiennent un `bindingConfiguration` attribut qui fait référence à une configuration de liaison personnalisée nommée `reliableSessionOverHttps`.</span><span class="sxs-lookup"><span data-stu-id="5601b-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="5601b-108">Le [  **\<liaison >** ](../../../../docs/framework/misc/binding.md) élément de configuration fait référence à ce nom pour spécifier qu’une session fiable et le transport HTTPS sont utilisés en incluant  **\< reliableSession >** et  **\<httpsTransport >** éléments.</span><span class="sxs-lookup"><span data-stu-id="5601b-108">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="5601b-109">Pour la copie de la source de cet exemple, consultez [personnalisé de liaison de Session fiable sur HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="5601b-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="5601b-110">Configurer le service avec une liaison personnalisée afin d’utiliser une session fiable avec HTTPS</span><span class="sxs-lookup"><span data-stu-id="5601b-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="5601b-111">Définissez un contrat de service pour le type de service.</span><span class="sxs-lookup"><span data-stu-id="5601b-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="5601b-112">Implémentez le contrat de service dans une classe de service.</span><span class="sxs-lookup"><span data-stu-id="5601b-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="5601b-113">Notez que les informations de liaison ou d’adresse n’est pas spécifiées dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="5601b-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="5601b-114">Vous n’êtes pas obligé d’écrire du code pour extraire les informations de liaison ou d’adresse à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5601b-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="5601b-115">Créer un *Web.config* fichier pour configurer un point de terminaison pour le `CalculatorService` avec une liaison personnalisée nommée `reliableSessionOverHttps` qui utilise une session fiable et le transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5601b-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="5601b-116">Créer un *Service.svc* fichier qui contient la ligne :</span><span class="sxs-lookup"><span data-stu-id="5601b-116">Create a *Service.svc* file that contains the line:</span></span>

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="5601b-117">Place le *Service.svc* fichier dans votre répertoire virtuel Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="5601b-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="5601b-118">Configurer le client avec une liaison personnalisée afin d’utiliser une session fiable avec HTTPS</span><span class="sxs-lookup"><span data-stu-id="5601b-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="5601b-119">Utilisez le [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) à partir de la ligne de commande pour générer le code à partir des métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="5601b-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="5601b-120">Le client généré contient la `ICalculator` interface qui définit le contrat de service que l’implémentation du client doit satisfaire.</span><span class="sxs-lookup"><span data-stu-id="5601b-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="5601b-121">L'application cliente générée contient également l'implémentation de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="5601b-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="5601b-122">Notez que les informations d’adresse et la liaison n’est pas spécifiées dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="5601b-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="5601b-123">Vous n’êtes pas obligé d’écrire du code pour extraire les informations de liaison et l’adresse à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="5601b-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="5601b-124">Configurer une liaison personnalisée nommée `reliableSessionOverHttps` à utiliser le transport HTTPS et les sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="5601b-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="5601b-125">Créez une instance `ClientCalculator` dans une application, puis appelez les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="5601b-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="5601b-126">Compilez, puis exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="5601b-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="5601b-127">sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5601b-127">.NET Framework security</span></span>

<span data-ttu-id="5601b-128">Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec *Makecert.exe*, une alerte de sécurité s’affiche lorsque vous essayez d’accéder à une adresse HTTPS, comme `https://localhost/servicemodelsamples/service.svc`, à partir de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="5601b-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="5601b-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5601b-129">See also</span></span>

- [<span data-ttu-id="5601b-130">Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="5601b-130">Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
