---
title: 'Comment : créer un point de terminaison de service dans la configuration.'
description: Découvrez comment ajouter des points de terminaison pour un service WCF à l’aide d’un fichier de configuration contenant à la fois des adresses absolues et relatives.
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 184bcb5f7f3e83f12608757b55bbb4d57be58f7d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247063"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Comment : créer un point de terminaison de service dans la configuration.
Les points de terminaison fournissent aux clients un accès aux fonctionnalités offertes par un service Windows Communication Foundation (WCF). Vous pouvez définir un ou plusieurs points de terminaison pour un service en utilisant une combinaison d'adresses de point de terminaison relative et absolue. Si vous ne définissez aucun point de terminaison de service, le runtime vous en fournit automatiquement par défaut. Cette rubrique montre comment ajouter des points de terminaison en utilisant un fichier de configuration qui contient à la fois des adresses absolues et relatives.  
  
## <a name="example"></a>Exemple  
 La configuration de service suivante spécifie une adresse de base et cinq points de terminaison.  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced in .NET Framework 4. -->  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a>Exemple  
 L'adresse de base est spécifiée à l'aide de l'élément `add`, sous service/host/baseAddresses, comme illustré dans l'exemple suivant.  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a>Exemple  
 La première définition de point de terminaison affichée dans l'exemple suivant spécifie une adresse relative, ce qui signifie que l'adresse de point de terminaison est une combinaison de l'adresse de base et de l'adresse relative selon les règles de composition de l'URI (Uniform Resource Identifier). L'adresse relative est vide (""), donc l'adresse de point de terminaison est la même que l'adresse de base. L’adresse du point de terminaison réel est `http://localhost:8000/servicemodelsamples/service` .  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemple  
 La deuxième définition de point de terminaison spécifie également une adresse relative, comme affiché dans l'exemple de configuration suivant. L'adresse relative, "test", est ajoutée à l'adresse de base. L’adresse du point de terminaison réel est `http://localhost:8000/servicemodelsamples/service/test` .  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemple  
 La troisième définition de point de terminaison spécifie une adresse absolue, comme affiché dans l'exemple de configuration suivant. L'adresse de base ne joue aucun rôle dans l'adresse. L’adresse du point de terminaison réel est `http://localhost:8001/hello/servicemodelsamples` .  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemple  
 La quatrième adresse de point de terminaison spécifie une adresse absolue et un transport différent - TCP. L'adresse de base ne joue aucun rôle dans l'adresse. La véritable adresse de point de terminaison est net.tcp://localhost:9000/servicemodelsamples/service.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Exemple  
 Pour utiliser les points de terminaison par défaut fournis par le runtime, ne spécifiez aucun point de terminaison de service dans le code ou dans le fichier de configuration. Dans cet exemple, le runtime crée les points de terminaison par défaut lors de l'ouverture du service. Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](../simplified-configuration.md) et [Configuration simplifiée pour les services WCF](../samples/simplified-configuration-for-wcf-services.md).  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```
