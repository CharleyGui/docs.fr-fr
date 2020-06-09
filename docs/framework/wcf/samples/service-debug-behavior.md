---
title: Service Debug Behavior
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 53f21129860c644d09d1a2eb9cb956aecf8ab0ad
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596637"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="8111f-102">Service Debug Behavior</span><span class="sxs-lookup"><span data-stu-id="8111f-102">Service Debug Behavior</span></span>

<span data-ttu-id="8111f-103">Cet exemple montre comment configurer les paramètres de comportement de débogage de service.</span><span class="sxs-lookup"><span data-stu-id="8111f-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="8111f-104">L’exemple est basé sur le [prise en main](getting-started-sample.md), qui implémente le `ICalculator` contrat de service.</span><span class="sxs-lookup"><span data-stu-id="8111f-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="8111f-105">Cet exemple définit explicitement le comportement de débogage de service dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="8111f-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="8111f-106">Cela peut également être fait de façon impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="8111f-106">It can also be done imperatively in code.</span></span>

<span data-ttu-id="8111f-107">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="8111f-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="8111f-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="8111f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="8111f-109">Le fichier Web.config du serveur définit le comportement de débogage de service permettant d'activer la page d'aide et la gestion des exceptions, tel qu'indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="8111f-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>

```xml
<behaviors>
     <serviceBehaviors>
         <behavior name="CalculatorServiceBehavior">
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->
         <!-- Please set this to false when deploying -->
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>
         </behavior>
     </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="8111f-110">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)est l’élément de configuration qui permet de modifier les propriétés de comportement de débogage de service.</span><span class="sxs-lookup"><span data-stu-id="8111f-110">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="8111f-111">L'utilisateur peut modifier ce comportement aux fins suivantes :</span><span class="sxs-lookup"><span data-stu-id="8111f-111">The user can modify this behavior to achieve the following:</span></span>

- <span data-ttu-id="8111f-112">Cela permet au service de retourner une exceptions levée par le code d'application même si celle-ci n'est pas déclarée à l'aide de <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8111f-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="8111f-113">Pour ce faire, affectez `includeExceptionDetailInFaults` à `true`.</span><span class="sxs-lookup"><span data-stu-id="8111f-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="8111f-114">Ce paramètre est utile lors du débogage de cas où le serveur lève une exception inattendue.</span><span class="sxs-lookup"><span data-stu-id="8111f-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="8111f-115">Pour des raisons de sécurité, il est déconseillé d'activer ce paramètre dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="8111f-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="8111f-116">Une exception de serveur inattendue peut contenir des informations qui ne sont pas destinées au client et l'affectation de `includeExceptionDetailsInFaults` à `true` peut entraîner une fuite des informations.</span><span class="sxs-lookup"><span data-stu-id="8111f-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>

- <span data-ttu-id="8111f-117">[\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md)Permet également à un utilisateur d’activer ou de désactiver la page d’aide.</span><span class="sxs-lookup"><span data-stu-id="8111f-117">The [\<serviceDebug>](../../configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="8111f-118">Chaque service peut éventuellement exposer une page d'aide qui contient des informations sur le service, et notamment le point de terminaison permettant d'obtenir le WSDL pour le service.</span><span class="sxs-lookup"><span data-stu-id="8111f-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="8111f-119">Pour ce faire, affectez `httpHelpPageEnabled` à `true`.</span><span class="sxs-lookup"><span data-stu-id="8111f-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="8111f-120">Cela permet de retourner la page d'aide dans une demande GET à l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="8111f-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="8111f-121">Pour modifier cette adresse, définissez un autre attribut `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="8111f-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="8111f-122">Pour sécuriser cette procédure, utilisez HTTPS au lieu de HTTP.</span><span class="sxs-lookup"><span data-stu-id="8111f-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="8111f-123">Pour ce faire, définissez `httpsHelpPageEnabled` et `httpsHelpPageUrl`</span><span class="sxs-lookup"><span data-stu-id="8111f-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>

<span data-ttu-id="8111f-124">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="8111f-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8111f-125">Les trois premières opérations (ajout, soustraction et multiplication) doivent réussir.</span><span class="sxs-lookup"><span data-stu-id="8111f-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="8111f-126">La dernière (division) échoue avec une exception de division par zéro.</span><span class="sxs-lookup"><span data-stu-id="8111f-126">The last operation ("divide") fails with a division by zero exception.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8111f-127">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="8111f-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8111f-128">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8111f-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="8111f-129">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8111f-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="8111f-130">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8111f-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8111f-131">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8111f-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8111f-132">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="8111f-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8111f-133">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8111f-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8111f-134">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="8111f-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`
