---
title: WMI Provider
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: dd1cb5f580ba182516f94f10c809cfa649365045
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589413"
---
# <a name="wmi-provider"></a>WMI Provider
Cet exemple montre comment collecter des données à partir des services Windows Communication Foundation (WCF) lors de l’exécution en utilisant le fournisseur Windows Management Instrumentation (WMI) qui est intégré à WCF. Cet exemple montre également comment ajouter un objet WMI défini par l'utilisateur à un service. L’exemple active le fournisseur WMI pour les [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) et montre comment collecter des données depuis le `ICalculator` service lors de l’exécution.  
  
 WMI est l'implémentation de Microsoft de la norme WBEM (Web-Based Enterprise Management). Pour plus d’informations sur le SDK WMI, consultez [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page). WBEM est une norme d'industrie qui détermine comment les applications exposent l'instrumentation de gestion aux outils de gestion externes.  
  
 WCF implémente un fournisseur WMI, un composant qui expose l’instrumentation lors de l’exécution via une interface WBEM compatible. Les outils de gestion peuvent se connecter aux services au moment de l'exécution par l'intermédiaire de l'interface. WCF expose des attributs de services tels que les adresses, liaisons, comportements et écouteurs.  
  
 Le fournisseur WMI intégré est activé dans le fichier de configuration de l'application. Cette opération est effectuée via le `wmiProviderEnabled` attribut de la [ \<diagnostics >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) dans le [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, comme illustré dans l’exemple suivant configuration :  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 Cette entrée de configuration expose une interface WMI. Les applications de gestion peuvent maintenant se connecter par le biais de cette interface et accéder à l'instrumentation de gestion de l'application.  
  
## <a name="custom-wmi-object"></a>Objet  WMI personnalisé.  
 L'ajout d'objets WMI à un service permet de révéler des informations définies par l'utilisateur en même temps que les informations du fournisseur WMI intégré. Cela s'effectue en publiant le schéma du service dans WMI en utilisant l'application Installutil.exe. Des instructions plus détaillées sont disponibles dans les instructions d'installation à la fin de cette rubrique.  
  
## <a name="accessing-wmi-information"></a>Accès aux informations WMI  
 Les données WMI sont accessibles de plusieurs façons différentes. Microsoft fournit des API WMI pour les scripts, les applications Visual Basic, C++ applications et le .NET Framework (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).  
  
 Cet exemple utilise deux scripts Java : un pour énumérer des services qui s'exécutent sur l'ordinateur avec certaines de leurs propriétés et le second pour consulter les données WMI définies par l'utilisateur. Le script ouvre une connexion au fournisseur WMI, analyse les données et affiche les données rassemblées.  
  
 Démarrer l’exemple pour créer une instance en cours d’exécution d’un service WCF. Pendant que le service s'exécute, exécutez chaque script Java en utilisant la commande suivante dans l'invite de commandes :  
  
```  
cscript EnumerateServices.js  
```  
  
 Le script accède à l'instrumentation contenue dans le service et produit la sortie suivante :  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 Ensuite, exécutez le deuxième script Java pour afficher les données WMI définies par l'utilisateur :  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 Le script accède à l'instrumentation définie par l'utilisateur contenue dans les services et produit la sortie suivante :  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 La sortie montre qu'un service unique s'exécute sur l'ordinateur. Le service expose un point de terminaison qui implémente le contrat `ICalculator`. Les paramètres du comportement et de la liaison qui sont implémentés par le point de terminaison sont répertoriés comme la somme des éléments individuels de la pile de messagerie.  
  
 WMI n’est pas limité à exposer l’instrumentation de gestion de l’infrastructure WCF. L'application peut exposer ses propres éléments de données spécifiques au domaine à travers le même mécanisme. WMI est un mécanisme unifié pour l'inspection et le contrôle d'un service Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Publiez le schéma de services dans WMI en exécutant InstallUtil.exe (l'emplacement par défaut pour Installutil.exe est « %WINDIR%\Microsoft.NET\Framework\v4.0.30319 ») sur le fichier service.dll dans le répertoire d'hébergement. Cette étape doit seulement être exécutée lorsque des modifications ont été apportées au fichier service.dll.
  
4. Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    >  Si vous avez installé WCF après l’installation d’ASP.NET, vous devrez peut-être exécuter « %WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication foundation\servicemodelreg Foundation\servicemodelreg.exe » - r - x autoriser le compte ASPNET pour publier des objets WMI.  
  
5. Consultez les données de l'exemple révélées par WMI en utilisant la commande `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d’analyse AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
