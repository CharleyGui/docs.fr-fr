---
title: "Comment : créer une liaison de session fiable personnalisée à l'aide de HTTPS"
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 70f8f4f33626ab0d1705e03750bfd9baa324e60a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598994"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a><span data-ttu-id="f9aea-102">Comment : créer une liaison de session fiable personnalisée à l'aide de HTTPS</span><span class="sxs-lookup"><span data-stu-id="f9aea-102">How to: Create a Custom Reliable Session Binding with HTTPS</span></span>

<span data-ttu-id="f9aea-103">Cette rubrique décrit l'utilisation de la sécurité de transport SSL (Secure Socket Layer) avec les sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="f9aea-103">This topic demonstrates the use of Secure Sockets Layer (SSL) transport security with reliable sessions.</span></span> <span data-ttu-id="f9aea-104">Pour utiliser une session fiable sur HTTPS, vous devez créer une liaison personnalisée qui utilise une session fiable et le transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f9aea-104">To use a reliable session over HTTPS, you must create a custom binding that uses a reliable session and the HTTPS transport.</span></span> <span data-ttu-id="f9aea-105">Vous activez la session fiable de manière impérative en utilisant le code ou de façon déclarative dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f9aea-105">You enable the reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="f9aea-106">Cette procédure utilise les fichiers de configuration du client et du service pour activer la session fiable et l' [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) élément.</span><span class="sxs-lookup"><span data-stu-id="f9aea-106">This procedure uses the client and service configuration files to enable the reliable session and the [**\<httpsTransport>**](../../configure-apps/file-schema/wcf/httpstransport.md) element.</span></span>

<span data-ttu-id="f9aea-107">La partie clé de cette procédure est que l' **\<endpoint>** élément de configuration contient un `bindingConfiguration` attribut qui fait référence à une configuration de liaison personnalisée nommée `reliableSessionOverHttps` .</span><span class="sxs-lookup"><span data-stu-id="f9aea-107">The key part of this procedure is that the **\<endpoint>** configuration element contain a `bindingConfiguration` attribute that references a custom binding configuration named `reliableSessionOverHttps`.</span></span> <span data-ttu-id="f9aea-108">L' [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) élément de configuration fait référence à ce nom pour spécifier qu’une session fiable et le transport HTTPS sont utilisés en incluant **\<reliableSession>** des **\<httpsTransport>** éléments et.</span><span class="sxs-lookup"><span data-stu-id="f9aea-108">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to specify that a reliable session and the HTTPS transport are used by including **\<reliableSession>** and **\<httpsTransport>** elements.</span></span>

<span data-ttu-id="f9aea-109">Pour obtenir la copie source de cet exemple, consultez [liaison personnalisée session fiable sur https](../samples/custom-binding-reliable-session-over-https.md).</span><span class="sxs-lookup"><span data-stu-id="f9aea-109">For the source copy of this example, see [Custom Binding Reliable Session over HTTPS](../samples/custom-binding-reliable-session-over-https.md).</span></span>

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="f9aea-110">Configurer le service avec une connexion CustomBinding pour utiliser une session fiable avec HTTPs</span><span class="sxs-lookup"><span data-stu-id="f9aea-110">Configure the service with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="f9aea-111">Définissez un contrat de service pour le type de service.</span><span class="sxs-lookup"><span data-stu-id="f9aea-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. <span data-ttu-id="f9aea-112">Implémentez le contrat de service dans une classe de service.</span><span class="sxs-lookup"><span data-stu-id="f9aea-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="f9aea-113">Notez que l’adresse ou les informations de liaison ne sont pas spécifiées dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="f9aea-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="f9aea-114">Vous n’êtes pas obligé d’écrire du code pour récupérer l’adresse ou les informations de liaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f9aea-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. <span data-ttu-id="f9aea-115">Créez un fichier *Web. config* pour configurer un point de terminaison pour le `CalculatorService` avec une liaison personnalisée nommée `reliableSessionOverHttps` qui utilise une session fiable et le transport HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f9aea-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` with a custom binding named `reliableSessionOverHttps` that uses a reliable session and the HTTPS transport.</span></span>

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. <span data-ttu-id="f9aea-116">Créez un fichier *service. svc* qui contient la ligne :</span><span class="sxs-lookup"><span data-stu-id="f9aea-116">Create a *Service.svc* file that contains the line:</span></span>

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. <span data-ttu-id="f9aea-117">Placez le fichier *service. svc* dans votre répertoire virtuel Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="f9aea-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a><span data-ttu-id="f9aea-118">Configurer le client avec une connexion CustomBinding pour utiliser une session fiable avec HTTPs</span><span class="sxs-lookup"><span data-stu-id="f9aea-118">Configure the client with a CustomBinding to use a reliable session with HTTPS</span></span>

1. <span data-ttu-id="f9aea-119">Utilisez l' [outil ServiceModel Metadata Utility Tool (*Svcutil. exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) à partir de la ligne de commande pour générer le code à partir des métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="f9aea-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="f9aea-120">Le client généré contient l' `ICalculator` interface qui définit le contrat de service que l’implémentation du client doit satisfaire.</span><span class="sxs-lookup"><span data-stu-id="f9aea-120">The client that's generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. <span data-ttu-id="f9aea-121">L'application cliente générée contient également l'implémentation de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="f9aea-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="f9aea-122">Notez que les informations d’adresse et de liaison ne sont pas spécifiées dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="f9aea-122">Note that the address and binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="f9aea-123">Vous n’êtes pas obligé d’écrire du code pour récupérer les informations d’adresse et de liaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f9aea-123">You aren't required to write code to retrieve the address and binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. <span data-ttu-id="f9aea-124">Configurez une liaison personnalisée nommée `reliableSessionOverHttps` pour utiliser le transport HTTPS et des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="f9aea-124">Configure a custom binding named `reliableSessionOverHttps` to use the HTTPS transport and reliable sessions.</span></span>

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. <span data-ttu-id="f9aea-125">Créez une instance `ClientCalculator` dans une application, puis appelez les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="f9aea-125">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. <span data-ttu-id="f9aea-126">Compilez, puis exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="f9aea-126">Compile and run the client.</span></span>  

## <a name="net-framework-security"></a><span data-ttu-id="f9aea-127">sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f9aea-127">.NET Framework security</span></span>

<span data-ttu-id="f9aea-128">Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec *Makecert. exe*, une alerte de sécurité s’affiche lorsque vous essayez d’accéder à une adresse https, telle que `https://localhost/servicemodelsamples/service.svc` , à partir de votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="f9aea-128">Because the certificate used in this sample is a test certificate created with *Makecert.exe*, a security alert appears when you try to access an HTTPS address, such as `https://localhost/servicemodelsamples/service.svc`, from your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9aea-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9aea-129">See also</span></span>

- [<span data-ttu-id="f9aea-130">Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="f9aea-130">Reliable Sessions</span></span>](reliable-sessions.md)
