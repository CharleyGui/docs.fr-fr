---
title: Configuration Channel Factory
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183950"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="716bd-102">Configuration Channel Factory</span><span class="sxs-lookup"><span data-stu-id="716bd-102">Configuration Channel Factory</span></span>
<span data-ttu-id="716bd-103">Cet exemple couvre l'utilisation du <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="716bd-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="716bd-104">Cela <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permet la gestion centrale de la configuration des clients WCF.</span><span class="sxs-lookup"><span data-stu-id="716bd-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="716bd-105">Celle-ci peut également être utile dans les scénarios où la configuration est sélectionnée ou modifiée après le chargement du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="716bd-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="716bd-106">Illustre le</span><span class="sxs-lookup"><span data-stu-id="716bd-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="716bd-107">Discussions</span><span class="sxs-lookup"><span data-stu-id="716bd-107">Discussion</span></span>
 <span data-ttu-id="716bd-108">Cet exemple montre comment utiliser <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> pour ajouter un fichier de configuration particulier à une application cliente, sans avoir à utiliser le fichier de configuration de l'application par défaut.</span><span class="sxs-lookup"><span data-stu-id="716bd-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="716bd-109">Cet exemple est composé de deux projets.</span><span class="sxs-lookup"><span data-stu-id="716bd-109">The sample consists of two projects.</span></span> <span data-ttu-id="716bd-110">Le premier projet est un service simple qui s'exécute pour répondre aux messages provenant des clients.</span><span class="sxs-lookup"><span data-stu-id="716bd-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="716bd-111">Le deuxième projet est une application cliente qui génère deux objets <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> à l'aide d'un <xref:System.Configuration.ExeConfigurationFileMap> pour le fichier de configuration Test.config et les utilise pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="716bd-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="716bd-112">Les deux clients communiquent avec le service à l'aide de la configuration spécifiée dans Test.config.</span><span class="sxs-lookup"><span data-stu-id="716bd-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="716bd-113">Le code suivant ajoute un fichier de configuration personnalisé à une application cliente.</span><span class="sxs-lookup"><span data-stu-id="716bd-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="716bd-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="716bd-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="716bd-115">Open Visual Studio 2012 avec privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="716bd-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="716bd-116">Cliquez à droite sur la solution ConfigurationChannelFactory (2 projets) puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="716bd-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="716bd-117">Dans **Common Properties**, sélectionnez Startup **Project**, puis cliquez sur **plusieurs projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="716bd-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="716bd-118">Déplacez le projet **de service** au début de la liste, avec **l’Action 'Start'**, puis déplacez le projet **Client** après le projet **de service,** également avec **l’Action 'Démarrer'**, de sorte que le projet **Client** est exécuté après le projet **de service.**</span><span class="sxs-lookup"><span data-stu-id="716bd-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="716bd-119">Cliquez **sur OK**, puis appuyez sur F5 (ou CTRL-F5) pour exécuter l’échantillon.</span><span class="sxs-lookup"><span data-stu-id="716bd-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="716bd-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="716bd-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="716bd-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="716bd-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="716bd-122">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="716bd-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="716bd-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="716bd-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
