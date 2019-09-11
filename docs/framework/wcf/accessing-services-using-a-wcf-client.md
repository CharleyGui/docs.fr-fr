---
title: Accès aux services à l'aide d'un client WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: ae589e1c418b1cf13fe9f5b34648bdf7a2210eed
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855672"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="3d124-102">Accès aux services à l'aide d'un client WCF</span><span class="sxs-lookup"><span data-stu-id="3d124-102">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="3d124-103">Une fois que vous avez créé un service, l’étape suivante consiste à créer un proxy client WCF.</span><span class="sxs-lookup"><span data-stu-id="3d124-103">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="3d124-104">Une application cliente utilise le proxy client WCF pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="3d124-104">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="3d124-105">En règle générale, les applications clientes importent les métadonnées d’un service pour générer le code client WCF qui peut être utilisé pour appeler le service.</span><span class="sxs-lookup"><span data-stu-id="3d124-105">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="3d124-106">Les étapes de base pour la création d’un client WCF sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3d124-106">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="3d124-107">Compiler le code de service.</span><span class="sxs-lookup"><span data-stu-id="3d124-107">Compile the service code.</span></span>

2. <span data-ttu-id="3d124-108">Générez le proxy client WCF.</span><span class="sxs-lookup"><span data-stu-id="3d124-108">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="3d124-109">Instanciez le proxy client WCF.</span><span class="sxs-lookup"><span data-stu-id="3d124-109">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="3d124-110">Le proxy client WCF peut être généré manuellement à l’aide de l’outil Service Model Metadata Utility (SvcUtil. exe) pour plus d’informations, consultez [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3d124-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="3d124-111">Le proxy client WCF peut également être généré dans Visual Studio à l’aide de la fonctionnalité **Ajouter une référence de service** .</span><span class="sxs-lookup"><span data-stu-id="3d124-111">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="3d124-112">Pour générer le proxy client WCF à l'aide de l'une de ces méthodes, le service doit s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="3d124-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="3d124-113">Si le service est auto-hébergé, vous devez exécuter l'hôte.</span><span class="sxs-lookup"><span data-stu-id="3d124-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="3d124-114">Si le service est hébergé dans IIS/WAS, aucune action n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3d124-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="3d124-115">Outil Service Model Metadata Tool</span><span class="sxs-lookup"><span data-stu-id="3d124-115">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="3d124-116">L' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) est un outil de ligne de commande permettant de générer du code à partir de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3d124-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="3d124-117">Voici un exemple d'utilisation d'une commande Svcutil.exe de base.</span><span class="sxs-lookup"><span data-stu-id="3d124-117">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="3d124-118">Vous pouvez également utiliser Svcutil.exe avec des fichiers WSDL (Web Services Description Language) et XSD (XML Schema Definition) sur le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="3d124-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="3d124-119">Le résultat est un fichier de code qui contient le code client WCF que l’application cliente peut utiliser pour appeler le service.</span><span class="sxs-lookup"><span data-stu-id="3d124-119">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="3d124-120">L'outil permet également de générer des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="3d124-120">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="3d124-121">Si un seul nom de fichier est fourni, il s'agit du nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="3d124-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="3d124-122">Si deux noms de fichiers sont fournis, le premier est un fichier de configuration d’entrée dont le contenu est fusionné avec la configuration générée et écrit dans le deuxième fichier.</span><span class="sxs-lookup"><span data-stu-id="3d124-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="3d124-123">Pour plus d’informations sur la configuration, consultez [Configuration des liaisons pour les services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3d124-123">For more information about configuration, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d124-124">Les demandes de métadonnées non sécurisées présentent certains risques de la même façon que n’importe quelle demande réseau non sécurisée : Si vous n’êtes pas certain que le point de terminaison avec lequel vous communiquez est celui qu’il prétend, les informations que vous récupérez peuvent être des métadonnées d’un service malveillant.</span><span class="sxs-lookup"><span data-stu-id="3d124-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="3d124-125">Ajouter une référence de service dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3d124-125">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="3d124-126">Lorsque le service est en cours d’exécution, cliquez avec le bouton droit sur le projet qui contiendra le proxy client WCF et sélectionnez **Ajouter** > une**référence de service**.</span><span class="sxs-lookup"><span data-stu-id="3d124-126">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="3d124-127">Dans la **boîte de dialogue Ajouter une référence de service**, tapez l’URL du service que vous souhaitez appeler, puis cliquez sur le bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="3d124-127">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="3d124-128">La boîte de dialogue affiche une liste de services disponibles à l'adresse que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="3d124-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="3d124-129">Double-cliquez sur le service pour afficher les contrats et les opérations disponibles, spécifiez un espace de noms pour le code généré, puis cliquez sur le bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="3d124-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="3d124-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="3d124-130">Example</span></span>
 <span data-ttu-id="3d124-131">L'exemple de code suivant montre un contrat de service créé pour un service.</span><span class="sxs-lookup"><span data-stu-id="3d124-131">The following code example shows a service contract created for a service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 <span data-ttu-id="3d124-132">L’outil utilitaire de métadonnées ServiceModel et **Ajouter une référence de service** dans Visual Studio génère la classe de client WCF suivante.</span><span class="sxs-lookup"><span data-stu-id="3d124-132">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="3d124-133">La classe hérite de la classe générique <xref:System.ServiceModel.ClientBase%601> et implémente l'interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="3d124-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="3d124-134">L'outil génère également l'interface `ICalculator` (qui n'est pas présentée ici).</span><span class="sxs-lookup"><span data-stu-id="3d124-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a><span data-ttu-id="3d124-135">Utilisation du client WCF</span><span class="sxs-lookup"><span data-stu-id="3d124-135">Using the WCF Client</span></span>
 <span data-ttu-id="3d124-136">Pour utiliser le client WCF, créez une instance du client WCF, puis appelez ses méthodes, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="3d124-136">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="3d124-137">Débogage d'exceptions levées par un Client</span><span class="sxs-lookup"><span data-stu-id="3d124-137">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="3d124-138">De nombreuses exceptions levées par un client WCF sont provoquées par une exception sur le service.</span><span class="sxs-lookup"><span data-stu-id="3d124-138">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="3d124-139">Quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="3d124-139">Some examples of this are:</span></span>

- <span data-ttu-id="3d124-140"><xref:System.Net.Sockets.SocketException>: Une connexion existante a été fermée de force par l'hôte distant.</span><span class="sxs-lookup"><span data-stu-id="3d124-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="3d124-141"><xref:System.ServiceModel.CommunicationException>: La connexion sous-jacente a été fermée de manière inattendue.</span><span class="sxs-lookup"><span data-stu-id="3d124-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="3d124-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: La connexion de socket a été abandonnée.</span><span class="sxs-lookup"><span data-stu-id="3d124-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="3d124-143">Cela peut être dû à une erreur lors du traitement de votre message, l'expiration du délai de réception par l'hôte distant ou un problème de ressource sur le réseau sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="3d124-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="3d124-144">Lorsque ces types d'exceptions se produisent, le meilleur moyen de les résoudre consiste à activer le suivi du côté service et de déterminer l'exception qui s'y est produite.</span><span class="sxs-lookup"><span data-stu-id="3d124-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="3d124-145">Pour plus d’informations sur le suivi, consultez [traçage](../../../docs/framework/wcf/diagnostics/tracing/index.md) et [utilisation du suivi pour résoudre les problèmes de votre application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="3d124-145">For more information about tracing, see [Tracing](../../../docs/framework/wcf/diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d124-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d124-146">See also</span></span>

- [<span data-ttu-id="3d124-147">Guide pratique pour Créer un client</span><span class="sxs-lookup"><span data-stu-id="3d124-147">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="3d124-148">Guide pratique pour Accéder aux services à l’aide d’un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="3d124-148">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="3d124-149">Guide pratique : Appeler des opérations de service de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="3d124-149">How to: Call Service Operations Asynchronously</span></span>](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="3d124-150">Guide pratique pour Accéder aux services avec des contrats à sens unique et demande-réponse</span><span class="sxs-lookup"><span data-stu-id="3d124-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="3d124-151">Guide pratique : Accéder à un service WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="3d124-151">How to: Access a WSE 3.0 Service</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="3d124-152">Fonctionnement du code client généré</span><span class="sxs-lookup"><span data-stu-id="3d124-152">Understanding Generated Client Code</span></span>](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="3d124-153">Guide pratique pour Améliorer le temps de démarrage des applications clientes WCF à l’aide de XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="3d124-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="3d124-154">Spécification du comportement du client au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="3d124-154">Specifying Client Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="3d124-155">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="3d124-155">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
