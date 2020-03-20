---
title: STREAM
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: f22339ca298f053fa636cc37281276051c70f6d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183331"
---
# <a name="stream"></a><span data-ttu-id="4d0f6-102">STREAM</span><span class="sxs-lookup"><span data-stu-id="4d0f6-102">Stream</span></span>
<span data-ttu-id="4d0f6-103">Cet exemple de flux montre l'utilisation de la communication en mode de transfert par diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="4d0f6-104">Le service expose plusieurs opérations qui envoient et reçoivent des flux.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="4d0f6-105">Cet exemple est auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-105">This sample is self-hosted.</span></span> <span data-ttu-id="4d0f6-106">Le client et le service sont tous deux des programmes de console.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d0f6-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4d0f6-108">Windows Communication Foundation (WCF) peut communiquer en deux modes de transfert : tamponné ou en streaming.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="4d0f6-109">En mode de transfert par mise en mémoire tampon, un message doit être complètement remis avant qu'un récepteur puisse le lire.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="4d0f6-110">En mode de transfert par diffusion en continu, le récepteur peut commencer à traiter le message avant qu'il ne soit complètement remis.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="4d0f6-111">Le mode de diffusion en continu est utile lorsque les informations passées sont volumineuses et peuvent être traitées en série.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="4d0f6-112">Le mode de diffusion en continu est également utile lorsque le message est trop volumineux pour être mis entièrement en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="4d0f6-113">Diffusion en continu et contrats de service</span><span class="sxs-lookup"><span data-stu-id="4d0f6-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="4d0f6-114">La diffusion en continu est un élément à prendre en compte lors de la conception d'un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="4d0f6-115">Si une opération reçoit ou retourne des données volumineuses, diffusez-les en continu afin d'éviter d'utiliser une grande quantité de mémoire en raison de la mise en mémoire tampon des messages d'entrée ou de sortie.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="4d0f6-116">Pour diffuser des données en continu, le paramètre qui gère ces données doit être le seul de ce type dans le message.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="4d0f6-117">Par exemple, si le message d'entrée est celui à diffuser en continu, l'opération ne doit avoir qu'un seul paramètre d'entrée.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="4d0f6-118">De la même façon, si le message de sortie doit être diffusé en continu, l'opération ne doit avoir qu'un seul paramètre de sortie ou qu'une seule valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="4d0f6-119">Dans les deux cas, le type de paramètre ou de valeur de retour doit être `Stream`, `Message` ou `IXmlSerializable`.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="4d0f6-120">Le contrat de service utilisé dans cet exemple de diffusion en continu est le suivant :</span><span class="sxs-lookup"><span data-stu-id="4d0f6-120">The following is the service contract used in this streaming sample.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="4d0f6-121">L'opération `GetStream` reçoit des données d'entrée sous forme d'une chaîne, qui est mise en mémoire tampon, et retourne `Stream` qui est diffusé en continu.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="4d0f6-122">Inversement, `UploadStream` utilise `Stream` (transmis en continu) et retourne `bool` (mis en mémoire tampon).</span><span class="sxs-lookup"><span data-stu-id="4d0f6-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="4d0f6-123">`EchoStream` prend et retourne `Stream` et constitue un exemple d'opération dont les messages d'entrée et de sortie sont tous deux diffusés en continu.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="4d0f6-124">Enfin, `GetReversedStream` ne prend pas d'entrée et retourne `Stream` (diffusion en continu).</span><span class="sxs-lookup"><span data-stu-id="4d0f6-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="4d0f6-125">Activation des transferts avec diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="4d0f6-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="4d0f6-126">La définition de contrats d'opération telle qu'elle est décrite précédemment fournit la diffusion en continu au niveau du modèle de programmation.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="4d0f6-127">Si vous vous arrêtez là, le transport met toujours en mémoire tampon l'ensemble du contenu du message.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="4d0f6-128">Pour activer la diffusion en continu du transport, sélectionnez un mode de transfert sur l'élément de liaison du transport.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="4d0f6-129">La propriété `TransferMode` de l'élément de liaison peut avoir la valeur `Buffered`, `Streamed`, `StreamedRequest` ou `StreamedResponse`.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="4d0f6-130">L'affectation de `Streamed` au mode de transfert permet d'assurer la communication en mode de diffusion en continu dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="4d0f6-131">Si vous affectez `StreamedRequest` ou `StreamedResponse` au mode de transfert, la communication en mode de diffusion en continu s'active uniquement dans la demande ou la réponse, respectivement.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="4d0f6-132">À l’instar de `basicHttpBinding` et `TransferMode`, `NetTcpBinding` expose la propriété `NetNamedPipeBinding` sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="4d0f6-133">Pour les autres transports, vous devez créer une liaison personnalisée pour pouvoir définir le mode de transfert.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="4d0f6-134">Le code de configuration suivant de l'exemple présente l'affectation du mode de diffusion en continu à la propriété `TransferMode` sur `basicHttpBinding` et une liaison HTTP personnalisée :</span><span class="sxs-lookup"><span data-stu-id="4d0f6-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="4d0f6-135">En plus d'affecter au `transferMode` la valeur `Streamed`, le code de configuration précédent définit `maxReceivedMessageSize` à 64 Mo.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="4d0f6-136">En tant que mécanisme de défense, `maxReceivedMessageSize` place une limite concernant la taille maximale autorisée des messages en réception.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="4d0f6-137">La valeur par défaut de `maxReceivedMessageSize` est 64 Ko, ce qui est habituellement trop bas pour les scénarios de diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="4d0f6-138">Traitement des données lorsqu'elles sont diffusées en continu</span><span class="sxs-lookup"><span data-stu-id="4d0f6-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="4d0f6-139">Les opérations `GetStream`, `UploadStream` et `EchoStream` concernent toutes l'envoi de données directement à partir d'un fichier ou l'enregistrement des données reçues directement dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="4d0f6-140">Dans certains cas cependant, il peut s'avérer nécessaire d'envoyer ou de recevoir de grandes quantités de données et d'effectuer des traitements sur des segments de celles-ci lors de leur envoi ou de leur réception.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="4d0f6-141">L'une des méthodes utilisées résoudre les scénarios de ce type consiste à écrire un flux personnalisé (une classe dérivant de <xref:System.IO.Stream>) qui traite les données lors de leur lecture ou de leur écriture.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="4d0f6-142">L'opération `GetReversedStream` et la classe `ReverseStream` en sont un exemple.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="4d0f6-143">`GetReversedStream` crée et retourne une nouvelle instance de `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="4d0f6-144">Le traitement se produit lorsque le système lit l'objet `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="4d0f6-145">L'implémentation `ReverseStream.Read` lit un segment d'octets du fichier sous-jacent, les inverse, puis retourne les octets inversés.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="4d0f6-146">Cette opération n'inverse pas l'ensemble du contenu du fichier, mais uniquement un segment d'octets à la fois.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="4d0f6-147">Cet exemple vous montre comment procéder au traitement du flux lors sa lecture ou de son écriture.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="4d0f6-148">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="4d0f6-148">Running the Sample</span></span>  
 <span data-ttu-id="4d0f6-149">Pour exécuter l'exemple, générez d'abord le service et le client en suivant les instructions indiquées à la fin de ce document.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="4d0f6-150">Puis démarrez le service et le client dans deux fenêtres de console différentes.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="4d0f6-151">Lorsque le client démarre, il attend que vous appuyiez sur ENTER lorsque le service est prêt.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="4d0f6-152">Le client appelle ensuite les méthodes `GetStream()`, `UploadStream()` et `GetReversedStream()` sur HTTP dans un premier temps, puis sur TCP.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="4d0f6-153">Voici un exemple de sortie du service suivi d'un exemple de sortie du client:</span><span class="sxs-lookup"><span data-stu-id="4d0f6-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="4d0f6-154">Sortie du service :</span><span class="sxs-lookup"><span data-stu-id="4d0f6-154">Service Output:</span></span>  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="4d0f6-155">Sortie du client :</span><span class="sxs-lookup"><span data-stu-id="4d0f6-155">Client Output:</span></span>  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4d0f6-156">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="4d0f6-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4d0f6-157">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="4d0f6-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4d0f6-158">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d0f6-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4d0f6-159">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d0f6-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d0f6-160">Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4d0f6-161">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4d0f6-162">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-162">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4d0f6-163">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d0f6-164">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="4d0f6-164">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
