---
title: 'Procédure : Contrôle des versions du service'
ms.date: 03/30/2017
ms.assetid: 4287b6b3-b207-41cf-aebe-3b1d4363b098
ms.openlocfilehash: ec0f776f296e5ab24f4f628a204b04aa8d903d39
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268467"
---
# <a name="how-to-service-versioning"></a><span data-ttu-id="d8501-102">Procédure : Contrôle des versions du service</span><span class="sxs-lookup"><span data-stu-id="d8501-102">How To: Service Versioning</span></span>

<span data-ttu-id="d8501-103">Cette rubrique présente les étapes de base nécessaires pour créer une configuration de routage qui route les messages vers des versions différentes du même service.</span><span class="sxs-lookup"><span data-stu-id="d8501-103">This topic outlines the basic steps required to create a routing configuration that routes messages to different versions of the same service.</span></span> <span data-ttu-id="d8501-104">Dans cet exemple, les messages sont routés vers deux versions différentes d'un service de calculatrice, `roundingCalc` (v1) et `regularCalc` (v2).</span><span class="sxs-lookup"><span data-stu-id="d8501-104">In this example, messages are routed to two different versions of a calculator service, `roundingCalc` (v1) and `regularCalc` (v2).</span></span> <span data-ttu-id="d8501-105">Les deux implémentations prennent en charge les mêmes opérations ; toutefois, le service le plus ancien, `roundingCalc`, arrondit tous les calculs à la valeur entière la plus proche avant de les retourner.</span><span class="sxs-lookup"><span data-stu-id="d8501-105">Both implementations support the same operations; however the older service, `roundingCalc`, rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="d8501-106">Une application cliente doit être en mesure d'indiquer s'il faut utiliser le service `regularCalc` plus récent.</span><span class="sxs-lookup"><span data-stu-id="d8501-106">A client application must be able to indicate whether to use the newer `regularCalc` service.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d8501-107">Pour router un message vers une version spécifique du service, le service de routage doit être en mesure de déterminer la destination du message en fonction du contenu de message.</span><span class="sxs-lookup"><span data-stu-id="d8501-107">In order to route a message to a specific service version, the Routing Service must be able to determine the message destination based on the message content.</span></span> <span data-ttu-id="d8501-108">Dans la méthode présentée ci-dessous, le client spécifie la version en insérant des informations dans un en-tête de message.</span><span class="sxs-lookup"><span data-stu-id="d8501-108">In the method demonstrated below, the client will specify the version by inserting information into a message header.</span></span> <span data-ttu-id="d8501-109">Il existe des méthodes de contrôle des versions de service qui ne requièrent pas que les clients transmettent des données supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d8501-109">There are methods of service versioning that do not require clients to pass additional data.</span></span> <span data-ttu-id="d8501-110">Par exemple, un message peut être routé vers la version d'un service la plus récente ou la plus compatible ou le routeur peut utiliser une partie de l'enveloppe SOAP standard.</span><span class="sxs-lookup"><span data-stu-id="d8501-110">For example, a message could be routed to the most recent or most compatible version of a service or the router could use a part of the standard SOAP envelope.</span></span>  
  
 <span data-ttu-id="d8501-111">Les opérations exposées par les deux services sont :</span><span class="sxs-lookup"><span data-stu-id="d8501-111">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="d8501-112">Ajouter</span><span class="sxs-lookup"><span data-stu-id="d8501-112">Add</span></span>  
  
- <span data-ttu-id="d8501-113">Soustraire</span><span class="sxs-lookup"><span data-stu-id="d8501-113">Subtract</span></span>  
  
- <span data-ttu-id="d8501-114">Multiplier</span><span class="sxs-lookup"><span data-stu-id="d8501-114">Multiply</span></span>  
  
- <span data-ttu-id="d8501-115">Diviser</span><span class="sxs-lookup"><span data-stu-id="d8501-115">Divide</span></span>  
  
 <span data-ttu-id="d8501-116">Comme les deux implémentations de service gèrent les mêmes opérations et sont pour l'essentiel identiques en dehors des données qu'elles retournent, les données de base contenues dans les messages envoyés à partir d'applications clientes ne sont pas assez uniques pour vous permettre de déterminer comment router la demande.</span><span class="sxs-lookup"><span data-stu-id="d8501-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="d8501-117">Par exemple, les filtres Action ne peuvent pas être utilisés, parce que les actions par défaut des deux services sont identiques.</span><span class="sxs-lookup"><span data-stu-id="d8501-117">For example, Action filters cannot be used because the default actions for both services are the same.</span></span>  
  
 <span data-ttu-id="d8501-118">Il existe plusieurs solutions, par exemple exposer un point de terminaison spécifique sur le routeur pour chaque version du service ou ajouter au message un élément d'en-tête personnalisé pour indiquer la version du service.</span><span class="sxs-lookup"><span data-stu-id="d8501-118">This can be resolved in several ways, such as exposing a specific endpoint on the router for each version of the service or adding a custom header element to the message to indicate service version.</span></span>  <span data-ttu-id="d8501-119">Chacune de ces approches vous permet de router de manière unique des messages entrants vers une version spécifique du service, cependant la méthode recommandée pour différencier les demandes destinées à différentes versions de service est d'utiliser un contenu de message unique.</span><span class="sxs-lookup"><span data-stu-id="d8501-119">Each of these approaches allows you to uniquely route incoming messages to a specific version of the service, but utilizing unique message content is the preferred method of differentiating between requests for different service versions.</span></span>  
  
 <span data-ttu-id="d8501-120">Dans cet exemple, l'application cliente ajoute l'en-tête personnalisé « CalcVer » au message de demande.</span><span class="sxs-lookup"><span data-stu-id="d8501-120">In this example, the client application adds the ‘CalcVer’ custom header to the request message.</span></span> <span data-ttu-id="d8501-121">Cet en-tête contiendra une valeur qui indique la version du service vers lequel le message doit être routé.</span><span class="sxs-lookup"><span data-stu-id="d8501-121">This header will contain a value that indicates the version of the service that the message should be routed to.</span></span> <span data-ttu-id="d8501-122">La valeur « 1 » indique que le message doit être traité par le service roundingCalc, tandis que la valeur « 2 » indique le service regularCalc.</span><span class="sxs-lookup"><span data-stu-id="d8501-122">A value of ‘1’ indicates that the message must be processed by the roundingCalc service, while a value of ‘2’ indicates the regularCalc service.</span></span> <span data-ttu-id="d8501-123">Cela permet à l'application cliente de contrôler directement quelle version du service traitera le message.</span><span class="sxs-lookup"><span data-stu-id="d8501-123">This allows the client application to directly control which version of the service will process the message.</span></span>  <span data-ttu-id="d8501-124">Puisque l'en-tête personnalisé est une valeur contenue dans le message, vous pouvez utiliser un seul point de terminaison pour recevoir les messages destinés aux deux versions du service.</span><span class="sxs-lookup"><span data-stu-id="d8501-124">Since the custom header is a value contained within the message, you can use one endpoint to receive messages destined for both versions of the service.</span></span> <span data-ttu-id="d8501-125">Le code suivant peut être utilisé dans l'application cliente pour ajouter cet en-tête personnalisé au message :</span><span class="sxs-lookup"><span data-stu-id="d8501-125">The following code can be used in the client application to add this custom header to the message:</span></span>  
  
```csharp  
messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", "2"));  
```  
  
### <a name="implement-service-versioning"></a><span data-ttu-id="d8501-126">Implémenter le contrôle des versions du service</span><span class="sxs-lookup"><span data-stu-id="d8501-126">Implement Service Versioning</span></span>  
  
1. <span data-ttu-id="d8501-127">Créez la configuration du service de routage de base, en spécifiant le point de terminaison de service exposé par le service.</span><span class="sxs-lookup"><span data-stu-id="d8501-127">Create the basic Routing Service configuration by specifying the service endpoint exposed by the service.</span></span> <span data-ttu-id="d8501-128">L'exemple suivant définit un point de terminaison de service unique, qui sera utilisé pour recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="d8501-128">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="d8501-129">Il définit également les points de terminaison clients qui seront utilisés pour envoyer des messages aux services `roundingCalc` (v1) et `regularCalc` (v2).</span><span class="sxs-lookup"><span data-stu-id="d8501-129">It also defines the client endpoints which will be used to send messages to the `roundingCalc` (v1) and the `regularCalc` (v2) services.</span></span>  
  
    ```xml  
    <services>  
        <service behaviorConfiguration="routingConfiguration"  
                 name="System.ServiceModel.Routing.RoutingService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost/routingservice/router" />  
            </baseAddresses>  
          </host>  
          <!--Set up the inbound endpoint for the Routing Service-->  
          <endpoint address="calculator"  
                    binding="wsHttpBinding"  
                    name="routerEndpoint"  
                    contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        </service>  
    </services>  
    <client>  
    <!--set up the destination endpoints-->  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="http://localhost:8080/servicemodelsamples/service/"  
                    binding="wsHttpBinding"  
                    contract="*" />  
        </client>  
    ```  
  
2. <span data-ttu-id="d8501-130">Définissez les filtres utilisés pour router les messages vers les points de terminaison de destination.</span><span class="sxs-lookup"><span data-stu-id="d8501-130">Define the filters used to route messages to the destination endpoints.</span></span>  <span data-ttu-id="d8501-131">Pour cet exemple, le filtre XPath est utilisé pour détecter la valeur de l’en-tête personnalisé « CalcVer » afin de déterminer la version vers laquelle le message doit être routé.</span><span class="sxs-lookup"><span data-stu-id="d8501-131">For this example, the XPath filter is used to detect the value of the "CalcVer" custom header to determine which version the message should be routed to.</span></span> <span data-ttu-id="d8501-132">Un filtre XPath est également utilisé pour détecter les messages qui ne contiennent pas l’en-tête « CalcVer ».</span><span class="sxs-lookup"><span data-stu-id="d8501-132">An XPath filter is also used to detect messages that do not contain the "CalcVer" header.</span></span> <span data-ttu-id="d8501-133">L'exemple suivant définit les filtres et la table d'espace de noms nécessaires.</span><span class="sxs-lookup"><span data-stu-id="d8501-133">The following example defines the required filters and namespace table.</span></span>  
  
    ```xml  
    <!-- use the namespace table element to define a prefix for our custom namespace-->  
    <namespaceTable>  
      <add prefix="custom" namespace="http://my.custom.namespace/"/>  
    </namespaceTable>  
    <filters>  
      <!--define the different message filters-->  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 2-->  
      <filter name="XPathFilterRegular" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '2'"/>  
      <!--define an xpath message filter to look for the  
          custom header containing a value of 1-->  
      <filter name="XPathFilterRounding" filterType="XPath"  
              filterData="sm:header()/custom:CalcVer = '1'"/>  
       <!--define an xpath message filter to look for  
           messages that do not contain the custom header-->  
       <filter name="XPathFilterNoHeader" filterType="XPath"  
               filterData="count(sm:header()/custom:CalcVer)=0"/>  
    </filters>
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="d8501-134">Le préfixe d’espace de noms S12 est défini par défaut dans la table d’espace de noms et représente l’espace de noms `http://www.w3.org/2003/05/soap-envelope` .</span><span class="sxs-lookup"><span data-stu-id="d8501-134">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
3. <span data-ttu-id="d8501-135">Définissez la table de filtres, qui associe chaque filtre à un point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="d8501-135">Define the filter table, which associates each filter with a client endpoint.</span></span> <span data-ttu-id="d8501-136">Si le message contient l’en-tête « CalcVer » avec la valeur 1, il sera envoyé au service regularCalc.</span><span class="sxs-lookup"><span data-stu-id="d8501-136">If the message contains the "CalcVer" header with a value of 1, it will be sent to the regularCalc service.</span></span> <span data-ttu-id="d8501-137">Si l'en-tête contient la valeur 2, il sera envoyé au service roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="d8501-137">If the header contains a value of 2, it will be sent to the roundingCalc service.</span></span> <span data-ttu-id="d8501-138">Si aucun en-tête n'est présent, le message sera routé vers regularCalc.</span><span class="sxs-lookup"><span data-stu-id="d8501-138">If no header is present, the message will be routed to the regularCalc.</span></span>  
  
     <span data-ttu-id="d8501-139">Les éléments suivants définissent la table de filtres et ajoutent les filtres définis précédemment.</span><span class="sxs-lookup"><span data-stu-id="d8501-139">The following defines the filter table and adds the filters defined earlier.</span></span>  
  
    ```xml  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filters to the message filter table-->  
          <!--look for the custom header = 1, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
          <!--look for the custom header = 2, and if we find it,  
              send the message to the rounding calc endpoint-->  
          <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
          <!--look for the absence of the custom header, and if  
              it is not present, assume the v1 endpoint-->  
          <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
4. <span data-ttu-id="d8501-140">Pour évaluer les messages entrants en fonction des filtres contenus dans la table de filtres, vous devez associer la table de filtres aux points de terminaison de service à l'aide du comportement de routage.</span><span class="sxs-lookup"><span data-stu-id="d8501-140">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="d8501-141">L’exemple suivant illustre l’Association `filterTable1` avec les points de terminaison de service :</span><span class="sxs-lookup"><span data-stu-id="d8501-141">The following example demonstrates associating `filterTable1` with the service endpoints:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="d8501-142"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d8501-142">Example</span></span>  

 <span data-ttu-id="d8501-143">L'intégralité du fichier de configuration est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d8501-143">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="http://localhost:8080/servicemodelsamples/service/"  
                binding="wsHttpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 2-->  
        <filter name="XPathFilterRegular" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '2'"/>  
        <!--define an xpath message filter to look for the  
            custom header containing a value of 1-->  
        <filter name="XPathFilterRounding" filterType="XPath"  
                filterData="sm:header()/custom:CalcVer = '1'"/>  
        <!--define an xpath message filter to look for  
            messages that do not contain the custom header-->  
        <filter name="XPathFilterNoHeader" filterType="XPath"  
                filterData="count(sm:header()/custom:CalcVer)=0"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filters to the message filter table-->  
            <!--look for the custom header = 1, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRounding" endpointName="roundingCalcEndpoint"/>  
            <!--look for the custom header = 2, and if we find it,  
                send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilterRegular" endpointName="regularCalcEndpoint"/>  
            <!--look for the absence of the custom header, and if  
                it is not present, assume the v1 endpoint-->  
            <add filterName="XPathFilterNoHeader" endpointName="roundingCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="d8501-144"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d8501-144">Example</span></span>  

 <span data-ttu-id="d8501-145">L'intégralité de l'application cliente est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d8501-145">The following is a complete listing of the client application.</span></span>  
  
```csharp  
using System;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    //The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.  
  
    //Client implementation code.  
    class Client  
    {  
        static void Main()  
        {  
            //Print out the welcome text  
            Console.WriteLine("This sample routes the Calculator Sample through the new WCF RoutingService");  
            Console.WriteLine("Wait for all the services to indicate that they've started, then press");  
            Console.WriteLine("<ENTER> to start the client.");  
  
            while (Console.ReadLine() != "quit")  
            {  
                //Offer the Address configuration for the client  
                Console.WriteLine("");  
                Console.WriteLine("Welcome to the Calculator Client!");  
  
                EndpointAddress epa;  
                //set the default address as the general router endpoint  
                epa = new EndpointAddress("http://localhost/routingservice/router/calculator");  
  
                //set up the CalculatorClient with the EndpointAddress, the WSHttpBinding, and the ICalculator contract  
                //We use the WSHttpBinding so that the outgoing has a message envelope, which we'll manipulate in a minute  
                CalculatorClient client = new CalculatorClient(new WSHttpBinding(), epa);  
                //client.Endpoint.Contract = ContractDescription.GetContract(typeof(ICalculator));  
  
                //Ask the customer if they want to add a custom header to the outgoing message.  
                //The Router will look for this header, and if so ignore the endpoint the message was  
                //received on, and instead direct the message to the RoundingCalcService.  
                Console.WriteLine("");  
                Console.WriteLine("Which calculator service should be used?");  
                Console.WriteLine("Enter 1 for the rounding calculator, 2 for the regular calculator.");  
                Console.WriteLine("[1] or [2]?");  
  
                string header = Console.ReadLine();  
  
                //get the current operationContextScope from the client's inner channel  
                using (OperationContextScope ocs = new OperationContextScope((client.InnerChannel)))  
                {  
                    //get the outgoing message headers element (collection) from the context  
                    MessageHeaders messageHeadersElement = OperationContext.Current.OutgoingMessageHeaders;  
  
                    //if they wanted to create the header, go ahead and add it to the outgoing message  
                    if (header != null && (header=="1" || header=="2"))  
                    {  
                        //create a new header "RoundingCalculator", no specific namespace, and set the value to
                        //the value of header.  
                        //the Routing Service will look for this header in order to determine if the message  
                        //should be routed to the RoundingCalculator  
                        messageHeadersElement.Add(MessageHeader.CreateHeader("CalcVer", "http://my.custom.namespace/", header));  
                    }  
                    else //incorrect choice, no header added  
                    {  
                        Console.WriteLine("Incorrect value entered, not adding a header");  
                    }  
  
                        //call the client operations  
                        CallClient(client);  
                }  
  
                //close the client to clean it up  
                client.Close();  
                Console.WriteLine();  
                Console.WriteLine("Press <ENTER> to run the client again or type 'quit' to quit.");  
            }  
        }  
  
        private static void CallClient(CalculatorClient client)  
        {  
            Console.WriteLine("");  
            Console.WriteLine("Sending!");  
            // Call the Add service operation.  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            value1 = 145.00D;  
            value2 = 76.54D;  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            value1 = 9.00D;  
            value2 = 81.25D;  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            value1 = 22.00D;  
            value2 = 7.00D;  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8501-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8501-146">See also</span></span>

- [<span data-ttu-id="d8501-147">Services de routage</span><span class="sxs-lookup"><span data-stu-id="d8501-147">Routing Services</span></span>](../samples/routing-services.md)
