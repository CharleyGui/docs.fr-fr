---
title: Custom Binding Transport and Encoding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c0b353d-79ee-4e61-b348-be49ad0e9a16
ms.openlocfilehash: 00af245f49994314ca29e1f5a2debe3af2364999
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241861"
---
# <a name="custom-binding-transport-and-encoding"></a>Custom Binding Transport and Encoding

Une liaison personnalisée est définie par une liste ordonnée d’éléments de liaison discrets. Cet exemple montre comment configurer une liaison personnalisée avec plusieurs éléments de transport et d'encodage de message.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple est basé sur l' [auto-hôte](self-host.md)et a été modifié pour configurer trois points de terminaison afin de prendre en charge les transports http, TCP et NamedPipe avec des liaisons personnalisées. La configuration client a été modifiée de la même façon, et le code client a été modifié pour communiquer avec chacun des trois points de terminaison.  
  
 L'exemple montre comment configurer une liaison personnalisée qui prend en charge un transport et un encodage de message spécifiques. Pour ce faire, configurez un transport et un encodage de message pour l'élément `binding`. L’ordre des éléments de liaison est important pour la définition d’une liaison personnalisée, car chacun représente une couche dans la pile de canaux (consultez [liaisons personnalisées](../extending/custom-bindings.md)). Cet exemple configure trois liaisons personnalisées : un transport HTTP avec encodage texte, un transport TCP avec encodage texte et un transport NamedPipe avec encodage binaire.  
  
 La configuration du service définit les liaisons personnalisées comme suit :  
  
```xml  
<bindings>  
    <customBinding>  
        <binding name="HttpBinding" >  
            <textMessageEncoding
                messageVersion="Soap12Addressing10"/>  
            <httpTransport />  
        </binding>  
        <binding name="TcpBinding" >  
            <textMessageEncoding />  
            <tcpTransport />  
        </binding>  
        <binding name="NamedPipeBinding" >  
            <binaryMessageEncoding />  
            <namedPipeTransport />  
        </binding>  
    </customBinding>  
</bindings>  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses de l'opération s'affichent dans les fenêtres de console du service et du client. Le client communique avec chacun des trois points de terminaison, en accédant d'abord à HTTP, puis à TCP et enfin à NamedPipe. Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.  
  
 La liaison `namedPipeTransport` ne prend pas en charge les opérations d’un ordinateur à un autre. Elle est uniquement utilisée pour la communication sur le même ordinateur. Par conséquent, lorsque vous exécutez l'exemple sur plusieurs ordinateurs, mettez en commentaire les lignes suivantes dans le fichier de code client :  
  
```csharp  
CalculatorClient client = new CalculatorClient("default");  
Console.WriteLine("Communicate with named pipe endpoint.");  
// Call operations.  
DoCalculations(client);  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
```  
  
```vb  
Dim client As New CalculatorClient("default")  
Console.WriteLine("Communicate with named pipe endpoint.")  
' call operations  
DoCalculations(client)  
'Closing the client gracefully closes the connection and cleans up resources  
client.Close()  
```  
  
> [!NOTE]
> Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C#, C++ ou Visual Basic .NET de la solution, suivez les instructions de la [création des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\Transport`  
