---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 663b7921e4e8a66d9b905404bad00f613e2f04cc
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144654"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="29f28-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="29f28-102">WSStreamedHttpBinding</span></span>

<span data-ttu-id="29f28-103">Cet exemple montre comment créer une liaison conçue pour prendre en charge des scénarios de diffusion en continu lorsque le transport HTTP est utilisé.</span><span class="sxs-lookup"><span data-stu-id="29f28-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>

> [!NOTE]
> <span data-ttu-id="29f28-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="29f28-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29f28-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="29f28-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="29f28-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="29f28-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="29f28-107">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="29f28-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29f28-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="29f28-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 <span data-ttu-id="29f28-109">Les étapes de la création et de la configuration d’une nouvelle liaison standard sont les suivantes.</span><span class="sxs-lookup"><span data-stu-id="29f28-109">The steps to create and configure a new standard binding are as follows.</span></span>

1. <span data-ttu-id="29f28-110">Créez une liaison standard</span><span class="sxs-lookup"><span data-stu-id="29f28-110">Create a new standard binding</span></span>

    <span data-ttu-id="29f28-111">Les liaisons standard dans Windows Communication Foundation (WCF) telles que basicHttpBinding et netTcpBinding configurent les transports sous-jacents et la pile de canaux pour des exigences spécifiques.</span><span class="sxs-lookup"><span data-stu-id="29f28-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="29f28-112">Dans cet exemple, `WSStreamedHttpBinding` configure la pile de canaux pour prendre en charge la diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="29f28-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="29f28-113">Par défaut, WS-Security et messagerie fiable ne sont pas ajoutés à la pile de canaux car ces deux fonctionnalités ne sont pas prises en charge par la diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="29f28-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="29f28-114">La nouvelle liaison est implémentée dans la classe `WSStreamedHttpBinding` qui dérive de <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="29f28-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="29f28-115">`WSStreamedHttpBinding` contient les éléments de liaison suivants : <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> et <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="29f28-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="29f28-116">La classe fournit une méthode `CreateBindingElements()` permettant de configurer la pile de liaison résultante, tel qu’indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="29f28-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>

    ```csharp
    public override BindingElementCollection CreateBindingElements()
    {
        // return collection of BindingElements
        BindingElementCollection bindingElements = new BindingElementCollection();

        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by
        // the message encoder, and finally the transport at the end
        if (flowTransactions)
        {
            bindingElements.Add(transactionFlow);
        }
        bindingElements.Add(textEncoding);

        // add transport (http or https)
        bindingElements.Add(transport);
        return bindingElements.Clone();
    }
    ```

2. <span data-ttu-id="29f28-117">Ajoutez la prise en charge de la configuration</span><span class="sxs-lookup"><span data-stu-id="29f28-117">Add configuration support</span></span>

    <span data-ttu-id="29f28-118">Pour exposer le transport via la configuration, l'exemple implémente deux classes : `WSStreamedHttpBindingConfigurationElement` et `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="29f28-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="29f28-119">La classe `WSStreamedHttpBindingSection` est un <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> qui expose `WSStreamedHttpBinding` au système de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="29f28-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="29f28-120">Le bloc de l'implémentation est délégué à `WSStreamedHttpBindingConfigurationElement`, qui dérive de <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="29f28-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="29f28-121">La classe `WSStreamedHttpBindingConfigurationElement` a des propriétés qui correspondent à celles de `WSStreamedHttpBinding`, et des fonctions pour mapper chaque élément de configuration à une liaison.</span><span class="sxs-lookup"><span data-stu-id="29f28-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>

    <span data-ttu-id="29f28-122">Pour enregistrer le gestionnaire avec le système de configuration, ajoutez la section suivante au fichier de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="29f28-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <extensions>
          <bindingExtensions>
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />
          </bindingExtensions>
        </extensions>
      </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="29f28-123">Il pourra ensuite être référencé à partir de la section de configuration serviceModel.</span><span class="sxs-lookup"><span data-stu-id="29f28-123">The handler can then be referenced from the serviceModel configuration section.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <client>
          <endpoint
                    address="https://localhost/servicemodelsamples/service.svc"
                    bindingConfiguration="Binding"
                    binding="wsStreamedHttpBinding"
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>
        </client>
      </system.serviceModel>
    </configuration>
    ```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="29f28-124">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="29f28-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="29f28-125">Installez ASP.NET 4,0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="29f28-125">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="29f28-126">Assurez-vous que vous avez effectué les étapes indiquées dans [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29f28-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="29f28-127">Vérifiez que vous avez effectué les [instructions d’installation du certificat de serveur Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="29f28-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="29f28-128">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29f28-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="29f28-129">Pour exécuter l’exemple dans une configuration inter-ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29f28-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

6. <span data-ttu-id="29f28-130">Lorsque la fenêtre du client s'affiche, tapez « Sample.txt ».</span><span class="sxs-lookup"><span data-stu-id="29f28-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="29f28-131">Vous devez rechercher « Copy of Sample.txt » dans votre répertoire.</span><span class="sxs-lookup"><span data-stu-id="29f28-131">You should find a "Copy of Sample.txt" in your directory.</span></span>

## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="29f28-132">Exemple de service WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="29f28-132">The WSStreamedHttpBinding Sample Service</span></span>

<span data-ttu-id="29f28-133">L'exemple de service qui utilise `WSStreamedHttpBinding` se trouve dans le sous-répertoire de service.</span><span class="sxs-lookup"><span data-stu-id="29f28-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="29f28-134">L'implémentation de `OperationContract` utilise un `MemoryStream` pour récupérer dans un premier temps toutes les données du flux entrant avant de retourner `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="29f28-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="29f28-135">L'exemple de service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="29f28-135">The sample service is hosted by Internet Information Services (IIS).</span></span>

```csharp
[ServiceContract]
public interface IStreamedEchoService
{
    [OperationContract]
    Stream Echo(Stream data);
}

public class StreamedEchoService : IStreamedEchoService
{
    public Stream Echo(Stream data)
    {
        MemoryStream dataStorage = new MemoryStream();
        byte[] byteArray = new byte[8192];
        int bytesRead = data.Read(byteArray, 0, 8192);
        while (bytesRead > 0)
        {
            dataStorage.Write(byteArray, 0, bytesRead);
            bytesRead = data.Read(byteArray, 0, 8192);
        }
        data.Close();
        dataStorage.Seek(0, SeekOrigin.Begin);

        return dataStorage;
    }
}
```

## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="29f28-136">Exemple de client WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="29f28-136">The WSStreamedHttpBinding Sample Client</span></span>

<span data-ttu-id="29f28-137">Le client utilisé pour interagir avec le service à l'aide de `WSStreamedHttpBinding` se trouve dans le sous-répertoire client.</span><span class="sxs-lookup"><span data-stu-id="29f28-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="29f28-138">Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec Makecert. exe, une alerte de sécurité s’affiche lorsque vous tentez d’accéder à une adresse HTTPs dans votre navigateur, telle que `https://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="29f28-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as `https://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="29f28-139">Pour permettre au client WCF de fonctionner avec un certificat de test sur place, du code supplémentaire a été ajouté au client pour supprimer l’alerte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="29f28-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="29f28-140">Le code, et la classe qui l'accompagne, ne sont pas requis lors de l'utilisation de certificats de production.</span><span class="sxs-lookup"><span data-stu-id="29f28-140">The code and the accompanying class are not required when using production certificates.</span></span>

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
