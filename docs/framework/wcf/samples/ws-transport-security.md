---
title: WS Transport Security
ms.date: 03/30/2017
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
ms.openlocfilehash: 64059a5a09d49f83c9abda5b2f3d1601acf41a3e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252411"
---
# <a name="ws-transport-security"></a>WS Transport Security

Cet exemple illustre l’utilisation de la sécurité de transport SSL avec la liaison <xref:System.ServiceModel.WSHttpBinding>. Par défaut, la liaison `wsHttpBinding` assure la communication HTTP. En cas de configuration pour la sécurité du transport, la liaison prend en charge la communication HTTPS. Cet exemple est basé sur le [prise en main](getting-started-sample.md) qui implémente un service de calculatrice. La liaison `wsHttpBinding` est spécifiée et configurée dans les fichiers de configuration de l'application pour le client et le service.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 Le code du programme dans l’exemple est identique à celui du service [prise en main](getting-started-sample.md) . Vous devez créer un certificat et l'assigner en utilisant l'Assistant Certificat de serveur Web avant de générer et exécuter l'exemple. La définition du point de terminaison et la définition de la liaison dans les paramètres du fichier de configuration activent le mode de sécurité `Transport`, comme le montre l'exemple de configuration suivant pour le client.  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 L’adresse spécifiée utilise le `https://` schéma. La configuration de la liaison définit le mode de sécurité au mode `Transport`. Le même mode de sécurité doit être spécifié dans le fichier Web.config du service.  
  
 Étant donné que le certificat utilisé dans cet exemple est un certificat de test créé avec Makecert.exe, une alerte de sécurité s’affiche lorsque vous essayez d’accéder à une adresse https : par exemple `https://localhost/servicemodelsamples/service.svc` , à partir de votre navigateur. Pour permettre au client Windows Communication Foundation (WCF) d’utiliser un certificat de test sur place, du code supplémentaire a été ajouté au client pour supprimer l’alerte de sécurité. Ce code, et la classe qui l'accompagne, n'est pas requis lors de l'utilisation de certificats de production.  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Installez ASP.NET 4,0 à l’aide de la commande suivante.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Vérifiez que vous avez effectué les [instructions d’installation du certificat de serveur Internet Information Services (IIS)](iis-server-certificate-installation-instructions.md).  
  
4. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
5. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
