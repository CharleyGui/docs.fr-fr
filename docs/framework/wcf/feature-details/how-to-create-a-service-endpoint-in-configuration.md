---
title: 'Comment : créer un point de terminaison de service dans la configuration.'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 56b29da0c147eb9e73a08e2875e33e384da729ed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598916"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="53494-102">Comment : créer un point de terminaison de service dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="53494-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="53494-103">Les points de terminaison fournissent aux clients un accès aux fonctionnalités offertes par un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="53494-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="53494-104">Vous pouvez définir un ou plusieurs points de terminaison pour un service en utilisant une combinaison d'adresses de point de terminaison relative et absolue. Si vous ne définissez aucun point de terminaison de service, le runtime vous en fournit automatiquement par défaut.</span><span class="sxs-lookup"><span data-stu-id="53494-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="53494-105">Cette rubrique montre comment ajouter des points de terminaison en utilisant un fichier de configuration qui contient à la fois des adresses absolues et relatives.</span><span class="sxs-lookup"><span data-stu-id="53494-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53494-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="53494-106">Example</span></span>  
 <span data-ttu-id="53494-107">La configuration de service suivante spécifie une adresse de base et cinq points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="53494-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="53494-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="53494-108">Example</span></span>  
 <span data-ttu-id="53494-109">L'adresse de base est spécifiée à l'aide de l'élément `add`, sous service/host/baseAddresses, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="53494-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="53494-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="53494-110">Example</span></span>  
 <span data-ttu-id="53494-111">La première définition de point de terminaison affichée dans l'exemple suivant spécifie une adresse relative, ce qui signifie que l'adresse de point de terminaison est une combinaison de l'adresse de base et de l'adresse relative selon les règles de composition de l'URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="53494-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="53494-112">L'adresse relative est vide (""), donc l'adresse de point de terminaison est la même que l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="53494-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="53494-113">L’adresse du point de terminaison réel est `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="53494-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="53494-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="53494-114">Example</span></span>  
 <span data-ttu-id="53494-115">La deuxième définition de point de terminaison spécifie également une adresse relative, comme affiché dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="53494-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="53494-116">L'adresse relative, "test", est ajoutée à l'adresse de base.</span><span class="sxs-lookup"><span data-stu-id="53494-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="53494-117">L’adresse du point de terminaison réel est `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="53494-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="53494-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="53494-118">Example</span></span>  
 <span data-ttu-id="53494-119">La troisième définition de point de terminaison spécifie une adresse absolue, comme affiché dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="53494-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="53494-120">L'adresse de base ne joue aucun rôle dans l'adresse.</span><span class="sxs-lookup"><span data-stu-id="53494-120">The base address plays no role in the address.</span></span> <span data-ttu-id="53494-121">L’adresse du point de terminaison réel est `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="53494-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="53494-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="53494-122">Example</span></span>  
 <span data-ttu-id="53494-123">La quatrième adresse de point de terminaison spécifie une adresse absolue et un transport différent - TCP.</span><span class="sxs-lookup"><span data-stu-id="53494-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="53494-124">L'adresse de base ne joue aucun rôle dans l'adresse.</span><span class="sxs-lookup"><span data-stu-id="53494-124">The base address plays no role in the address.</span></span> <span data-ttu-id="53494-125">La véritable adresse de point de terminaison est net.tcp://localhost:9000/servicemodelsamples/service.</span><span class="sxs-lookup"><span data-stu-id="53494-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="53494-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="53494-126">Example</span></span>  
 <span data-ttu-id="53494-127">Pour utiliser les points de terminaison par défaut fournis par le runtime, ne spécifiez aucun point de terminaison de service dans le code ou dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="53494-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="53494-128">Dans cet exemple, le runtime crée les points de terminaison par défaut lors de l'ouverture du service.</span><span class="sxs-lookup"><span data-stu-id="53494-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="53494-129">Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](../simplified-configuration.md) et [Configuration simplifiée pour les services WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="53494-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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
