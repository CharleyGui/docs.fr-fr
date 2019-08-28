---
title: Configuration Channel Factory
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1b74c15599ebc932a2a0ed46d646b54bec986794
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045653"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="7aca6-102">Configuration Channel Factory</span><span class="sxs-lookup"><span data-stu-id="7aca6-102">Configuration Channel Factory</span></span>
<span data-ttu-id="7aca6-103">Cet exemple couvre l'utilisation du <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="7aca6-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="7aca6-104">Le <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permet la gestion centralisée de la configuration du client WCF.</span><span class="sxs-lookup"><span data-stu-id="7aca6-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="7aca6-105">Celle-ci peut également être utile dans les scénarios où la configuration est sélectionnée ou modifiée après le chargement du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="7aca6-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="7aca6-106">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="7aca6-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="7aca6-107">Discussion</span><span class="sxs-lookup"><span data-stu-id="7aca6-107">Discussion</span></span>
 <span data-ttu-id="7aca6-108">Cet exemple montre comment utiliser <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> pour ajouter un fichier de configuration particulier à une application cliente, sans avoir à utiliser le fichier de configuration de l'application par défaut.</span><span class="sxs-lookup"><span data-stu-id="7aca6-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="7aca6-109">Cet exemple est composé de deux projets.</span><span class="sxs-lookup"><span data-stu-id="7aca6-109">The sample consists of two projects.</span></span> <span data-ttu-id="7aca6-110">Le premier projet est un service simple qui s'exécute pour répondre aux messages provenant des clients.</span><span class="sxs-lookup"><span data-stu-id="7aca6-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="7aca6-111">Le deuxième projet est une application cliente qui génère deux objets <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> à l'aide d'un <xref:System.Configuration.ExeConfigurationFileMap> pour le fichier de configuration Test.config et les utilise pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="7aca6-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="7aca6-112">Les deux clients communiquent avec le service à l'aide de la configuration spécifiée dans Test.config.</span><span class="sxs-lookup"><span data-stu-id="7aca6-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="7aca6-113">Le code suivant ajoute un fichier de configuration personnalisé à une application cliente.</span><span class="sxs-lookup"><span data-stu-id="7aca6-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7aca6-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="7aca6-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7aca6-115">Ouvrez Visual Studio 2012 avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="7aca6-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="7aca6-116">Cliquez avec le bouton droit sur la solution ConfigurationChannelFactory (2 projets), puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7aca6-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="7aca6-117">Dans **Propriétés communes**, sélectionnez **projet de démarrage**, puis cliquez sur **plusieurs projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="7aca6-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="7aca6-118">Déplacez le projet de **service** au début de la liste, avec l' **action «Start»** , puis déplacez le projet **client** après le projet de **service** , également avec l' **action «Start»** , afin que le projet **client** soit exécuté après le projet de **service** .</span><span class="sxs-lookup"><span data-stu-id="7aca6-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="7aca6-119">Cliquez sur **OK**, puis appuyez sur F5 (ou CTRL + F5) pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="7aca6-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7aca6-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7aca6-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7aca6-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="7aca6-121">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7aca6-122">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="7aca6-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7aca6-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="7aca6-123">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
