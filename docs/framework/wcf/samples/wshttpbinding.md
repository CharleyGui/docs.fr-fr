---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: c54cbf1fe881ef2ce5dffb0bc0c6dac4049135b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143367"
---
# <a name="wshttpbinding"></a>WSHttpBinding
Cet exemple montre comment implémenter un service typique et un client typique utilisant Windows Communication Foundation (WCF). Cet exemple se compose d'un programme de console cliente (client.exe) et d'une bibliothèque de service hébergés par les services IIS (Internet Information Services). Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `ICalculator`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division. Le client adresse des demandes synchrones à une opération mathématique donnée et le service répond avec le résultat. L'activité du client est affichée dans la fenêtre de console.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet échantillon expose `ICalculator` le contrat à l’aide de la [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). La configuration de cette liaison a été développée dans le fichier Web.config.  
  
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
  
 Sur l’élément [ \<fiableSsSession>,](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) la valeur Boolean activée configure si des sessions fiables sont activées. La valeur `ordered` configure l'activation du classement des messages. La valeur `inactivityTimeout` configure la durée d'inactivité maximale avant son expiration.  
  
 Sur la [ \<sécurité>, ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` la valeur configure quel mode de sécurité doit être utilisé. Dans cet échantillon, la sécurité des messages [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) est utilisée, c’est pourquoi le message>est spécifié à l’intérieur de la [ \<sécurité>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Installez ASP.NET 4.0 à l’aide de la commande suivante.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
