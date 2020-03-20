---
title: WS Reliable Session
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143497"
---
# <a name="ws-reliable-session"></a>WS Reliable Session
Cet exemple montre l'utilisation des sessions fiables. Les sessions fiables fournissent la prise en charge de la messagerie et des sessions fiables. La messagerie fiable réessaie d'établir la communication en cas d'échec et permet de spécifier des assurances de remise telles que l'ordre d'arrivée des messages. Les sessions conservent l'état pour les clients entre les appels. Cet exemple implémente des sessions permettant de conserver l'état du client et spécifie des assurances de remise par ordre d'arrivée.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui met en œuvre un service de calculatrice. Les fonctionnalités de sessions fiables sont activées et configurées dans les fichiers de configuration d'application respectifs du client et du service.  
  
 Dans cet exemple, le service est hébergé dans les services IIS (Internet Information Services) et le client est une application console (.exe).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple utilise le fichier `wsHttpBinding`. La liaison est spécifiée dans les fichiers de configuration pour le client et le service. Le type de liaison est spécifié dans l’attribut `binding` de l’élément de point de terminaison, tel qu’indiqué dans l’exemple de configuration suivant.  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 Le point de terminaison contient un attribut `bindingConfiguration` qui référence une configuration de liaison appelée « Binding1 ». La configuration de liaison permet `enabled` des sessions fiables en définissant `true`l’attribut de la [ \<>fiables](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) . Les assurances de remise pour les sessions ordonnées sont contrôlées en affectant `true` ou `false` à l'attribut ordonné. Par défaut, il s’agit de `true`.  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 La classe d'implémentation de service implémente l'instanciation <xref:System.ServiceModel.InstanceContextMode.PerSession> afin de conserver une instance de classe distincte pour chaque client, tel qu'indiqué dans l'exemple de code suivant.  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
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
  
1. Installez ASP.NET 4.0 à l’aide de la commande suivante.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
