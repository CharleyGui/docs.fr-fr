---
title: Fournisseur WMI
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: a170a20212791d789af589c1ff99dcd1abad1c9e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094772"
---
# <a name="wmi-provider"></a>Fournisseur WMI
Cet exemple montre comment collecter des données à partir de services Windows Communication Foundation (WCF) au moment de l’exécution à l’aide du fournisseur Windows Management Instrumentation (WMI) intégré à WCF. Cet exemple montre également comment ajouter un objet WMI défini par l'utilisateur à un service. L’exemple active le fournisseur WMI pour la [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md) et montre comment collecter des données à partir du service `ICalculator` au moment de l’exécution.  
  
 WMI est l'implémentation de Microsoft de la norme WBEM (Web-Based Enterprise Management). Pour plus d’informations sur le kit de développement logiciel (SDK) WMI, consultez [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page). WBEM est une norme d'industrie qui détermine comment les applications exposent l'instrumentation de gestion aux outils de gestion externes.  
  
 WCF implémente un fournisseur WMI, un composant qui expose l’instrumentation au moment de l’exécution par le biais d’une interface compatible WBEM. Les outils de gestion peuvent se connecter aux services au moment de l'exécution par l'intermédiaire de l'interface. WCF expose des attributs de services tels que les adresses, les liaisons, les comportements et les écouteurs.  
  
 Le fournisseur WMI intégré est activé dans le fichier de configuration de l'application. Cette opération s’effectue via l’attribut `wmiProviderEnabled` de l' [>\<Diagnostics](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) dans la section [\<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , comme illustré dans l’exemple de configuration suivant :  
  
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

Les données WMI sont accessibles de plusieurs façons différentes. Microsoft fournit des API WMI pour les scripts, les C++ applications Visual Basic, les applications et les .NET Framework. Pour plus d’informations, consultez [utilisation de WMI](/windows/desktop/wmisdk/using-wmi).
  
 Cet exemple utilise deux scripts Java : un pour énumérer des services qui s'exécutent sur l'ordinateur avec certaines de leurs propriétés et le second pour consulter les données WMI définies par l'utilisateur. Le script ouvre une connexion au fournisseur WMI, analyse les données et affiche les données rassemblées.  
  
 Démarrez l’exemple pour créer une instance en cours d’exécution d’un service WCF. Pendant que le service s'exécute, exécutez chaque script Java en utilisant la commande suivante dans l'invite de commandes :  
  
```console  
cscript EnumerateServices.js  
```  
  
 Le script accède à l'instrumentation contenue dans le service et produit la sortie suivante :  
  
```console  
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
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 Le script accède à l'instrumentation définie par l'utilisateur contenue dans les services et produit la sortie suivante :  
  
```console 
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 La sortie montre qu'un service unique s'exécute sur l'ordinateur. Le service expose un point de terminaison qui implémente le contrat `ICalculator`. Les paramètres du comportement et de la liaison qui sont implémentés par le point de terminaison sont répertoriés comme la somme des éléments individuels de la pile de messagerie.  
  
 WMI n’est pas limité à l’exposition de l’instrumentation de gestion de l’infrastructure WCF. L'application peut exposer ses propres éléments de données spécifiques au domaine à travers le même mécanisme. WMI est un mécanisme unifié pour l'inspection et le contrôle d'un service Web.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Publiez le schéma de services dans WMI en exécutant InstallUtil.exe (l'emplacement par défaut pour Installutil.exe est « %WINDIR%\Microsoft.NET\Framework\v4.0.30319 ») sur le fichier service.dll dans le répertoire d'hébergement. Cette étape doit seulement être exécutée lorsque des modifications ont été apportées au fichier service.dll.
  
4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Si vous avez installé WCF après l’installation de ASP.NET, vous devrez peut-être exécuter «% WINDIR% \ Microsoft. Net\Framework\v3.0\Windows communication Foundation\servicemodelreg.exe "-r-x pour accorder au compte ASPNET l’autorisation de publier des objets WMI.  
  
5. Consultez les données de l'exemple révélées par WMI en utilisant la commande `cscript EnumerateServices.js` ou `cscript EnumerateCustomObjects.js`.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de surveillance AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
