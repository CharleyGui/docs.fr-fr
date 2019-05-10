---
title: Service Debug Behavior
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 2f2eefb01e66efddea05116f640a60defe78de1b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664720"
---
# <a name="service-debug-behavior"></a>Service Debug Behavior
Cet exemple montre comment configurer les paramètres de comportement de débogage de service. L’exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente le `ICalculator` contrat de service. Cet exemple définit explicitement le comportement de débogage de service dans le fichier de configuration. Cela peut également être fait de façon impérative dans le code.  
  
 Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le fichier Web.config du serveur définit le comportement de débogage de service permettant d'activer la page d'aide et la gestion des exceptions, tel qu'indiqué dans l'exemple suivant.  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) est l’élément de configuration qui permet de modifier les propriétés de comportement de débogage de service. L'utilisateur peut modifier ce comportement aux fins suivantes :  
  
- Cela permet au service de retourner une exceptions levée par le code d'application même si celle-ci n'est pas déclarée à l'aide de <xref:System.ServiceModel.FaultContractAttribute>. Pour ce faire, affectez `includeExceptionDetailInFaults` à `true`. Ce paramètre est utile lors du débogage de cas où le serveur lève une exception inattendue.  
  
    > [!IMPORTANT]
    >  Pour des raisons de sécurité, il est déconseillé d'activer ce paramètre dans un environnement de production. Une exception de serveur inattendue peut contenir des informations qui ne sont pas destinées au client et l'affectation de `includeExceptionDetailsInFaults` à `true` peut entraîner une fuite des informations.  
  
- Le [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) permet également à un utilisateur Activer ou désactiver la page d’aide. Chaque service peut éventuellement exposer une page d'aide qui contient des informations sur le service, et notamment le point de terminaison permettant d'obtenir le WSDL pour le service. Pour ce faire, affectez `httpHelpPageEnabled` à `true`. Cela permet de retourner la page d'aide dans une demande GET à l'adresse de base du service. Pour modifier cette adresse, définissez un autre attribut `httpHelpPageUrl`. Pour sécuriser cette procédure, utilisez HTTPS au lieu de HTTP. Pour ce faire, définissez `httpsHelpPageEnabled` et `httpsHelpPageUrl`  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Les trois premières opérations (ajout, soustraction et multiplication) doivent réussir. La dernière (division) échoue avec une exception de division par zéro.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
