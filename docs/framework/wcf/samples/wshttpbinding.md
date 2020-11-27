---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 6e5946dd7d107c34eafe55a62c51d089931b5b77
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252282"
---
# <a name="wshttpbinding"></a>WSHttpBinding

Cet exemple montre comment implémenter un service classique et un client standard à l’aide de Windows Communication Foundation (WCF). Cet exemple se compose d'un programme de console cliente (client.exe) et d'une bibliothèque de service hébergés par les services IIS (Internet Information Services). Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `ICalculator`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division. Le client adresse des demandes synchrones à une opération mathématique donnée et le service répond avec le résultat. L'activité du client est affichée dans la fenêtre de console.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple expose le `ICalculator` contrat à l’aide du [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . La configuration de cette liaison a été développée dans le fichier Web.config.  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"
              transactionFlow="false"
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"
              textEncoding="utf-8"
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 Sur l'élément de `binding` de base, la valeur `maxReceivedMessageSize` vous permet de configurer la taille maximale d'un message entrant (en octets). La valeur `hostNameComparisonMode` vous permet de configurer la prise en compte du nom d'hôte lors du démultiplexage des messages vers le service. La valeur `messageEncoding` vous permet de configurer l'utilisation de l'encodage texte ou MTOM pour les messages. La valeur `textEncoding` vous permet de configurer l'encodage de caractères pour les messages. La valeur `bypassProxyOnLocal` vous permet de configurer l'utilisation d'un proxy HTTP pour les communications locales. La valeur `transactionFlow` configure la transmission de la transaction en cours (si une opération est configurée en ce sens).  
  
 Sur l' [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) élément, la valeur booléenne activée configure si les sessions fiables sont activées. La valeur `ordered` configure l'activation du classement des messages. La valeur `inactivityTimeout` configure la durée d'inactivité maximale avant son expiration.  
  
 Sur le [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) , la `mode` valeur configure le mode de sécurité à utiliser. Dans cet exemple, la sécurité des messages est utilisée, ce qui explique pourquoi [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) est spécifié à l’intérieur du [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) .  
  
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
  
3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
