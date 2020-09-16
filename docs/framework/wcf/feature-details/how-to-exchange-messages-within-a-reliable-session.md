---
title: 'Procédure : échanger des messages au sein d’une session fiable'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 97371f8572d5d0db633ab8dd1ca82067d9d55c3f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550187"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a><span data-ttu-id="34088-102">Procédure : échanger des messages au sein d’une session fiable</span><span class="sxs-lookup"><span data-stu-id="34088-102">How to: Exchange Messages Within a Reliable Session</span></span>

<span data-ttu-id="34088-103">Cette rubrique décrit les étapes requises pour activer une session fiable utilisant l’une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut.</span><span class="sxs-lookup"><span data-stu-id="34088-103">This topic outlines the steps required to enable a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="34088-104">Vous activez une session fiable de façon impérative à l’aide du code ou de façon déclarative dans votre fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="34088-104">You enable a reliable session imperatively using code or declaratively in your configuration file.</span></span> <span data-ttu-id="34088-105">Cette procédure utilise les fichiers de configuration du client et du service pour activer la session fiable et stipuler que les messages arrivent dans l’ordre dans lequel ils ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="34088-105">This procedure uses the client and service configuration files to enable the reliable session and to stipulate that the messages arrive in the same order in which they were sent.</span></span>

<span data-ttu-id="34088-106">La partie clé de cette procédure est que l’élément de configuration de point de terminaison contient un `bindingConfiguration` attribut qui fait référence à une configuration de liaison nommée `Binding1` .</span><span class="sxs-lookup"><span data-stu-id="34088-106">The key part of this procedure is that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="34088-107">L' [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) élément de configuration fait référence à ce nom pour activer des sessions fiables en affectant `enabled` à l’attribut de l’élément la valeur [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` .</span><span class="sxs-lookup"><span data-stu-id="34088-107">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) element to `true`.</span></span> <span data-ttu-id="34088-108">Vous spécifiez les assurances de remise ordonnée pour la session fiable en affectant à l'attribut `ordered` la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="34088-108">You specify the ordered delivery assurances for the reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="34088-109">Pour obtenir la copie source de cet exemple, consultez [WS Reliable session](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="34088-109">For the source copy of this example, see [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="34088-110">Configurer le service avec une liaison WSHttpBinding pour utiliser une session fiable</span><span class="sxs-lookup"><span data-stu-id="34088-110">Configure the service with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="34088-111">Définissez un contrat de service pour le type de service.</span><span class="sxs-lookup"><span data-stu-id="34088-111">Define a service contract for the type of service.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. <span data-ttu-id="34088-112">Implémentez le contrat de service dans une classe de service.</span><span class="sxs-lookup"><span data-stu-id="34088-112">Implement the service contract in a service class.</span></span> <span data-ttu-id="34088-113">Notez que l’adresse ou les informations de liaison ne sont pas spécifiées dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="34088-113">Note that the address or binding information isn't specified inside the implementation of the service.</span></span> <span data-ttu-id="34088-114">Vous n’êtes pas obligé d’écrire du code pour récupérer l’adresse ou les informations de liaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="34088-114">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. <span data-ttu-id="34088-115">Créez un fichier de *Web.config* pour configurer un point de terminaison pour le `CalculatorService` qui utilise <xref:System.ServiceModel.WSHttpBinding> avec la session fiable activée et la livraison chronologique des messages requise.</span><span class="sxs-lookup"><span data-stu-id="34088-115">Create a *Web.config* file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding> with reliable session enabled and ordered delivery of messages required.</span></span>

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. <span data-ttu-id="34088-116">Créez un fichier *service. svc* qui contient la ligne :</span><span class="sxs-lookup"><span data-stu-id="34088-116">Create a *Service.svc* file that contains the line:</span></span>

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. <span data-ttu-id="34088-117">Placez le fichier *service. svc* dans votre répertoire virtuel Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="34088-117">Place the *Service.svc* file in your Internet Information Services (IIS) virtual directory.</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="34088-118">Configurer le client avec une liaison WSHttpBinding pour utiliser une session fiable</span><span class="sxs-lookup"><span data-stu-id="34088-118">Configure the client with a WSHttpBinding to use a reliable session</span></span>

1. <span data-ttu-id="34088-119">Utilisez l' [outil ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) à partir de la ligne de commande pour générer le code à partir des métadonnées de service :</span><span class="sxs-lookup"><span data-stu-id="34088-119">Use the [ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata:</span></span>

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. <span data-ttu-id="34088-120">Le client généré contient l' `ICalculator` interface qui définit le contrat de service que l’implémentation du client doit satisfaire.</span><span class="sxs-lookup"><span data-stu-id="34088-120">The generated client contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. <span data-ttu-id="34088-121">L'application cliente générée contient également l'implémentation de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="34088-121">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="34088-122">Notez que les informations d’adresse et de liaison ne sont pas spécifiées n’importe où dans l’implémentation du service.</span><span class="sxs-lookup"><span data-stu-id="34088-122">Note that the address and binding information isn't specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="34088-123">Vous n’êtes pas obligé d’écrire du code pour récupérer l’adresse ou les informations de liaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="34088-123">You aren't required to write code to retrieve the address or binding information from the configuration file.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. <span data-ttu-id="34088-124">*Svcutil.exe* génère également la configuration du client qui utilise la <xref:System.ServiceModel.WSHttpBinding> classe.</span><span class="sxs-lookup"><span data-stu-id="34088-124">*Svcutil.exe* also generates the configuration for the client that uses the <xref:System.ServiceModel.WSHttpBinding> class.</span></span> <span data-ttu-id="34088-125">Nommez le fichier de configuration *App.config* lors de l’utilisation de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="34088-125">Name the configuration file *App.config* when using Visual Studio.</span></span>

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. <span data-ttu-id="34088-126">Créez une instance de `ClientCalculator` dans une application et appelez les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="34088-126">Create an instance of the `ClientCalculator` in an application and call the service operations.</span></span>

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. <span data-ttu-id="34088-127">Compilez, puis exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="34088-127">Compile and run the client.</span></span>

## <a name="example"></a><span data-ttu-id="34088-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="34088-128">Example</span></span>

<span data-ttu-id="34088-129">Plusieurs liaisons fournies par le système prennent en charge des sessions fiables par défaut.</span><span class="sxs-lookup"><span data-stu-id="34088-129">Several of the system-provided bindings support reliable sessions by default.</span></span> <span data-ttu-id="34088-130">Elles incluent notamment :</span><span class="sxs-lookup"><span data-stu-id="34088-130">These include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

<span data-ttu-id="34088-131">Pour obtenir un exemple de création d’une liaison personnalisée qui prend en charge les sessions fiables, consultez Guide pratique [pour créer une liaison de session fiable personnalisée avec HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span><span class="sxs-lookup"><span data-stu-id="34088-131">For an example of how to create a custom binding that supports reliable sessions, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34088-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34088-132">See also</span></span>

- [<span data-ttu-id="34088-133">Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="34088-133">Reliable Sessions</span></span>](reliable-sessions.md)
