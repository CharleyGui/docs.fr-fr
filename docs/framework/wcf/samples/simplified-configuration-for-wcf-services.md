---
title: Configuration simplifiée pour WCF Services
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 61720fff957bfe7a13da1d7498487342b2ee234c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584101"
---
# <a name="simplified-configuration-for-wcf-services"></a>Configuration simplifiée pour WCF Services
Cet exemple montre comment implémenter et configurer un service et un client standard à l’aide de Windows Communication Foundation (WCF). Cet exemple constitue la base de tous les autres exemples de technologie de base.  
  
 Ce service, qui expose un point de terminaison pour communiquer avec le service, utilise la configuration simplifiée dans .NET Framework 4. Avant le .NET Framework 4, le point de terminaison est généralement défini dans un fichier de configuration (Web. config), comme le montre l’exemple de code de configuration suivant.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Dans .NET Framework 4, l' `<service>` élément est facultatif. Lorsqu'un service ne définit pas de points de terminaison, un point de terminaison est ajouté au service pour chaque adresse de base et contrat implémentés. L’adresse de base est ajoutée au nom du contrat pour déterminer le point de terminaison et la liaison est déterminée par le schéma d’adresse. L'exemple de code suivant montre un fichier de configuration simplifié. Comme configuré, le service est accessible à `http://localhost/servicemodelsamples/service.svc` un client sur le même ordinateur. Pour que les clients installés sur des ordinateurs distants puissent accéder au service, un nom de domaine complet doit être spécifié au lieu de localhost. Par défaut, le service n'expose pas de métadonnées. Comme tel, le service active le comportement <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Exécutez l'exemple en procédant comme suit :  
  
    1. Cliquez avec le bouton droit sur le projet de **service** et sélectionnez **définir comme projet de démarrage**, puis appuyez sur **CTRL + F5**.  
  
    2. Attendez le message de la console confirmant le bon fonctionnement du service.  
  
    3. Cliquez avec le bouton droit sur le projet **client** et sélectionnez **définir comme projet de démarrage**, puis appuyez sur **CTRL + F5**.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de gestion AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Configuration simplifiée](../simplified-configuration.md)
