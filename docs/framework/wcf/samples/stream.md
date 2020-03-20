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
# <a name="stream"></a>STREAM
Cet exemple de flux montre l'utilisation de la communication en mode de transfert par diffusion en continu. Le service expose plusieurs opérations qui envoient et reçoivent des flux. Cet exemple est auto-hébergé. Le client et le service sont tous deux des programmes de console.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Windows Communication Foundation (WCF) peut communiquer en deux modes de transfert : tamponné ou en streaming. En mode de transfert par mise en mémoire tampon, un message doit être complètement remis avant qu'un récepteur puisse le lire. En mode de transfert par diffusion en continu, le récepteur peut commencer à traiter le message avant qu'il ne soit complètement remis. Le mode de diffusion en continu est utile lorsque les informations passées sont volumineuses et peuvent être traitées en série. Le mode de diffusion en continu est également utile lorsque le message est trop volumineux pour être mis entièrement en mémoire tampon.  
  
## <a name="streaming-and-service-contracts"></a>Diffusion en continu et contrats de service  
 La diffusion en continu est un élément à prendre en compte lors de la conception d'un contrat de service. Si une opération reçoit ou retourne des données volumineuses, diffusez-les en continu afin d'éviter d'utiliser une grande quantité de mémoire en raison de la mise en mémoire tampon des messages d'entrée ou de sortie. Pour diffuser des données en continu, le paramètre qui gère ces données doit être le seul de ce type dans le message. Par exemple, si le message d'entrée est celui à diffuser en continu, l'opération ne doit avoir qu'un seul paramètre d'entrée. De la même façon, si le message de sortie doit être diffusé en continu, l'opération ne doit avoir qu'un seul paramètre de sortie ou qu'une seule valeur de retour. Dans les deux cas, le type de paramètre ou de valeur de retour doit être `Stream`, `Message` ou `IXmlSerializable`. Le contrat de service utilisé dans cet exemple de diffusion en continu est le suivant :  
  
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
  
 L'opération `GetStream` reçoit des données d'entrée sous forme d'une chaîne, qui est mise en mémoire tampon, et retourne `Stream` qui est diffusé en continu. Inversement, `UploadStream` utilise `Stream` (transmis en continu) et retourne `bool` (mis en mémoire tampon). `EchoStream` prend et retourne `Stream` et constitue un exemple d'opération dont les messages d'entrée et de sortie sont tous deux diffusés en continu. Enfin, `GetReversedStream` ne prend pas d'entrée et retourne `Stream` (diffusion en continu).  
  
## <a name="enabling-streamed-transfers"></a>Activation des transferts avec diffusion en continu  
 La définition de contrats d'opération telle qu'elle est décrite précédemment fournit la diffusion en continu au niveau du modèle de programmation. Si vous vous arrêtez là, le transport met toujours en mémoire tampon l'ensemble du contenu du message. Pour activer la diffusion en continu du transport, sélectionnez un mode de transfert sur l'élément de liaison du transport. La propriété `TransferMode` de l'élément de liaison peut avoir la valeur `Buffered`, `Streamed`, `StreamedRequest` ou `StreamedResponse`. L'affectation de `Streamed` au mode de transfert permet d'assurer la communication en mode de diffusion en continu dans les deux sens. Si vous affectez `StreamedRequest` ou `StreamedResponse` au mode de transfert, la communication en mode de diffusion en continu s'active uniquement dans la demande ou la réponse, respectivement.  
  
 À l’instar de `basicHttpBinding` et `TransferMode`, `NetTcpBinding` expose la propriété `NetNamedPipeBinding` sur la liaison. Pour les autres transports, vous devez créer une liaison personnalisée pour pouvoir définir le mode de transfert.  
  
 Le code de configuration suivant de l'exemple présente l'affectation du mode de diffusion en continu à la propriété `TransferMode` sur `basicHttpBinding` et une liaison HTTP personnalisée :  
  
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
  
 En plus d'affecter au `transferMode` la valeur `Streamed`, le code de configuration précédent définit `maxReceivedMessageSize` à 64 Mo. En tant que mécanisme de défense, `maxReceivedMessageSize` place une limite concernant la taille maximale autorisée des messages en réception. La valeur par défaut de `maxReceivedMessageSize` est 64 Ko, ce qui est habituellement trop bas pour les scénarios de diffusion en continu.  
  
## <a name="processing-data-as-it-is-streamed"></a>Traitement des données lorsqu'elles sont diffusées en continu  
 Les opérations `GetStream`, `UploadStream` et `EchoStream` concernent toutes l'envoi de données directement à partir d'un fichier ou l'enregistrement des données reçues directement dans un fichier. Dans certains cas cependant, il peut s'avérer nécessaire d'envoyer ou de recevoir de grandes quantités de données et d'effectuer des traitements sur des segments de celles-ci lors de leur envoi ou de leur réception. L'une des méthodes utilisées résoudre les scénarios de ce type consiste à écrire un flux personnalisé (une classe dérivant de <xref:System.IO.Stream>) qui traite les données lors de leur lecture ou de leur écriture. L'opération `GetReversedStream` et la classe `ReverseStream` en sont un exemple.  
  
 `GetReversedStream` crée et retourne une nouvelle instance de `ReverseStream`. Le traitement se produit lorsque le système lit l'objet `ReverseStream`. L'implémentation `ReverseStream.Read` lit un segment d'octets du fichier sous-jacent, les inverse, puis retourne les octets inversés. Cette opération n'inverse pas l'ensemble du contenu du fichier, mais uniquement un segment d'octets à la fois. Cet exemple vous montre comment procéder au traitement du flux lors sa lecture ou de son écriture.  
  
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
  
## <a name="running-the-sample"></a>Exécution de l'exemple  
 Pour exécuter l'exemple, générez d'abord le service et le client en suivant les instructions indiquées à la fin de ce document. Puis démarrez le service et le client dans deux fenêtres de console différentes. Lorsque le client démarre, il attend que vous appuyiez sur ENTER lorsque le service est prêt. Le client appelle ensuite les méthodes `GetStream()`, `UploadStream()` et `GetReversedStream()` sur HTTP dans un premier temps, puis sur TCP. Voici un exemple de sortie du service suivi d'un exemple de sortie du client:  
  
 Sortie du service :  
  
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
  
 Sortie du client :  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
