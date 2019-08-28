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
# <a name="configuration-channel-factory"></a>Configuration Channel Factory
Cet exemple couvre l'utilisation du <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. Le <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permet la gestion centralisée de la configuration du client WCF. Celle-ci peut également être utile dans les scénarios où la configuration est sélectionnée ou modifiée après le chargement du domaine d'application.

## <a name="demonstrates"></a>Démonstrations
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Discussion
 Cet exemple montre comment utiliser <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> pour ajouter un fichier de configuration particulier à une application cliente, sans avoir à utiliser le fichier de configuration de l'application par défaut.

 Cet exemple est composé de deux projets. Le premier projet est un service simple qui s'exécute pour répondre aux messages provenant des clients. Le deuxième projet est une application cliente qui génère deux objets <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> à l'aide d'un <xref:System.Configuration.ExeConfigurationFileMap> pour le fichier de configuration Test.config et les utilise pour communiquer avec le service. Les deux clients communiquent avec le service à l'aide de la configuration spécifiée dans Test.config.

 Le code suivant ajoute un fichier de configuration personnalisé à une application cliente.

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Ouvrez Visual Studio 2012 avec des privilèges d’administrateur.

2. Cliquez avec le bouton droit sur la solution ConfigurationChannelFactory (2 projets), puis sélectionnez **Propriétés**.

3. Dans **Propriétés communes**, sélectionnez **projet de démarrage**, puis cliquez sur **plusieurs projets de démarrage**.

4. Déplacez le projet de **service** au début de la liste, avec l' **action «Start»** , puis déplacez le projet **client** après le projet de **service** , également avec l' **action «Start»** , afin que le projet **client** soit exécuté après le projet de **service** .

5. Cliquez sur **OK**, puis appuyez sur F5 (ou CTRL + F5) pour exécuter l’exemple.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
