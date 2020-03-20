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
# <a name="configuration-channel-factory"></a>Configuration Channel Factory
Cet exemple couvre l'utilisation du <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>. Cela <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permet la gestion centrale de la configuration des clients WCF. Celle-ci peut également être utile dans les scénarios où la configuration est sélectionnée ou modifiée après le chargement du domaine d'application.

## <a name="demonstrates"></a>Illustre le
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a>Discussions
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

1. Open Visual Studio 2012 avec privilèges d’administrateur.

2. Cliquez à droite sur la solution ConfigurationChannelFactory (2 projets) puis sélectionnez **Propriétés**.

3. Dans **Common Properties**, sélectionnez Startup **Project**, puis cliquez sur **plusieurs projets de démarrage**.

4. Déplacez le projet **de service** au début de la liste, avec **l’Action 'Start'**, puis déplacez le projet **Client** après le projet **de service,** également avec **l’Action 'Démarrer'**, de sorte que le projet **Client** est exécuté après le projet **de service.**

5. Cliquez **sur OK**, puis appuyez sur F5 (ou CTRL-F5) pour exécuter l’échantillon.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
