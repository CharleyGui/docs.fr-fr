---
title: PII Security Lockdown
ms.date: 03/30/2017
ms.assetid: c44fb338-9527-4dd0-8607-b8787d15acb4
ms.openlocfilehash: ad4f4a024b04a028b815faedded58713e001cab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144264"
---
# <a name="pii-security-lockdown"></a>PII Security Lockdown
Cet exemple montre comment contrôler plusieurs fonctionnalités liées à la sécurité d’un service de la Windows Communication Foundation (WCF) en :  
  
- Chiffrement des informations sensibles dans le fichier de configuration du service.  
  
- Verrouillage de certains éléments du fichier de configuration afin que les sous-répertoires de service imbriqués ne puissent pas se substituer aux paramètres.  
  
- Contrôle de l'enregistrement des informations d'identification personnelle (PII, Personally Identifiable Information) dans les journaux de suivi et de message.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\SecurityLockdown`  
  
## <a name="discussion"></a>Discussions  
 Chacune de ces fonctionnalités peut être utilisée séparément ou simultanément afin de contrôler les divers aspects relatifs à la sécurité des services. Ce n’est pas un guide définitif pour obtenir un service WCF.  
  
 Les fichiers de configuration .NET Framework peuvent contenir des informations sensibles telles que les chaînes de connexion permettant de se connecter aux bases de données. Dans le cadre de services partagés et hébergés par le Web, le chiffrement de ces informations dans le fichier de configuration des services concernés peut s'avérer souhaitable pour assurer leur protection en cas de consultation informelle. .NET Framework 2.0 et ses versions ultérieures permettent de chiffrer certains passages des fichiers de configuration à l'aide de l'interface de programmation d'applications de protection des données Windows (Data Protection Application Programming Interface, DPAPI) ou du fournisseur de services de chiffrement RSA. Le programme aspnet_regiis.exe peut chiffrer les sections choisies d'un fichier de configuration donné à l'aide de l'interface ou du fournisseur ci-dessus.  
  
 Dans le cadre de scénarios hébergés par le Web, il est possible de placer ces services dans les sous-répertoires d'autres services. La valeur par défaut sémantique définissant les valeurs de configuration permet aux fichiers de configuration figurant dans les répertoires imbriqués de se substituer aux valeurs de configuration figurant dans le répertoire parent. Dans certaines situations et pour diverses raisons, il peut s'avérer préférable qu'une telle substitution ne soit pas possible. La configuration du service WCF prend en charge le verrouillage des valeurs de configuration de sorte que la configuration imbriquée génère des exceptions lorsqu’un service imbriqué est exécuté à l’aide de valeurs de configurations dépassées.  
  
 Cet exemple illustre comment contrôler la fonctionnalité d'enregistrement des informations d'identification personnelle connues, telles que le nom d'utilisateur et le mot de passe, dans les journaux de suivi et de message. Par défaut, l'enregistrement des PII connues est désactivé. Toutefois, dans certaines situations, leur enregistrement peut s'avérer essentiel lors du débogage des applications. Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). En outre, cet exemple utilise l'enregistrement des suivis et des messages. Pour plus d’informations, consultez l’échantillon [de traçage et de logging de messages.](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)  
  
## <a name="encrypting-configuration-file-elements"></a>Chiffrement des éléments de fichier de configuration  
 Pour des raisons de sécurité, dans le cadre d'un environnement partagé avec hébergement Web, le chiffrement de certains éléments de configuration tels que les chaînes de connexion aux bases de données, susceptibles de contenir des informations sensibles, peut s'avérer souhaitable. Un élément de configuration peut être crypté à l’aide de l’outil aspnet_regiis.exe trouvé dans le dossier .NET Framework Par exemple, %WINDIR%-Microsoft.NET-Framework-v4.0.20728.  
  
#### <a name="to-encrypt-the-values-in-the-appsettings-section-in-webconfig-for-the-sample"></a>Pour chiffrer les valeurs dans la section appSettings du fichier Web.config de l'exemple  
  
1. Ouvrez une invite de commande en utilisant Start->Run.... Tapez `cmd` et cliquez **sur OK**.  
  
2. Naviguez jusqu'au répertoire .NET Framework actuel en publiant la commande suivante : `cd %WINDIR%\Microsoft.NET\Framework\v4.0.20728`.  
  
3. Chiffrez les paramètres de configuration appSettings du dossier Web.config en publiant la commande suivante : `aspnet_regiis -pe "appSettings" -app "/servicemodelsamples" -prov "DataProtectionConfigurationProvider"`.  
  
 Plus d’informations sur le cryptage des sections de fichiers de configuration peuvent être trouvées en lisant un comment faire sur DPAPI en configuration ASP.NET[(Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))) et un comment faire sur RSA en configuration ASP.NET ([Comment : Chiffrer les sections de configuration dans ASP.NET 2.0 En utilisant RSA](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))).  
  
## <a name="locking-configuration-file-elements"></a>Verrouillage des éléments de fichier de configuration  
 Dans le cadre de services hébergés par le Web, il est possible de placer ces services dans les sous-répertoires d'autres services. Dans ce genre de situation, les valeurs de configuration des services placés dans ces sous-répertoires sont calculées en examinant les valeurs du fichier Machine.config. Ces valeurs sont ensuite fusionnées avec les valeurs des éventuels fichiers Web.config figurant dans les répertoires parents en descendant la hiérarchie de l’arborescence de répertoires jusqu’au fichier Web.config du répertoire contenant les services concernés. Le comportement par défaut de la plupart des éléments de configuration permet aux fichiers de configuration des sous-répertoires de se substituer aux valeurs définies dans leurs répertoires parents. Dans certains cas, il peut s'avérer préférable d'empêcher une telle substitution.  
  
 Le .NET Framework propose une fonctionnalité permettant de verrouiller les éléments de configuration, provoquant ainsi la levée d'exception pendant l'exécution lorsque les fichiers de configuration des sous-répertoires tentent de se substituer aux éléments verrouillés.  
  
 Les éléments de configuration peuvent être verrouillés en spécifiant l'attribut `lockItem` pour un nœud du fichier de configuration. Par exemple, pour verrouiller le nœud CalculatorServiceBehavior afin que les services de calculatrice des fichiers de configuration imbriqués ne puissent pas modifier ce comportement, la configuration suivante peut être utilisée.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>
          <serviceBehaviors>
             <behavior name="CalculatorServiceBehavior" lockItem="true">
               <serviceMetadata httpGetEnabled="True"/>
               <serviceDebug includeExceptionDetailInFaults="False" />
             </behavior>
          </serviceBehaviors>
       </behaviors>
    </system.serviceModel>  
</configuration>  
```  
  
 Le verrouillage des éléments de configuration peut être plus spécifique. La valeur à laquelle `lockElements` est appliqué peut être spécifiée sous la forme d'une liste d'éléments afin de verrouiller un ensemble d'éléments au sein d'une collection de sous-éléments. La valeur à laquelle `lockAttributes` est appliqué peut être définie sous la forme d'une liste d'attributs pour verrouiller un ensemble d'attributs au sein d'un élément. Une collection entière d’éléments ou d’attributs peut être verrouillée à l’exception d’une liste spécifiée au niveau des attributs `lockAllElementsExcept` ou `lockAllAttributesExcept` sur un nœud.  
  
## <a name="pii-logging-configuration"></a>Configuration de l'enregistrement des informations d'identification personnelle  
 L'enregistrement des PII est contrôlé par deux commutateurs : paramètre à l'échelle de l'ordinateur situé dans le fichier Machine.config permettant à l'administrateur de cet ordinateur d'autoriser ou non leur enregistrement et paramètre d'application permettant aux administrateurs d'application d'activer ou non leur enregistrement pour chaque source dans les fichiers Web.config ou App.config.  
  
 Le réglage à l’échelle `enableLoggingKnownPii` de `true` `false`l’ordinateur `machineSettings` est contrôlé par réglage ou , dans l’élément dans Machine.config. Par exemple, ce qui suit permet aux applications d’activer l’enregistrement des IPI.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <machineSettings enableLoggingKnownPii="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
> Le fichier Machine.config se trouve dans un emplacement par défaut : %WINDIR%\Microsoft.NET\Framework\v2.0.50727\CONFIG.  
  
 Si l'attribut `enableLoggingKnownPii` n'est pas présent dans le fichier Machine.config, l'enregistrement des PII n'est pas autorisé.  
  
 L'enregistrement des PII pour une application est activé en affectant à l'attribut `logKnownPii` de l'élément source la valeur `true` ou `false` dans les fichiers Web.config ou App.config. Par exemple, le code suivant active l'enregistrement des PII à la fois pour l'enregistrement des messages et des suivis.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel.MessageLogging" logKnownPii="true">  
                <listeners>
                ...
                </listeners>  
            </source>  
            <source name="System.ServiceModel" switchValue="Verbose, ActivityTracing">  
            <listeners>  
        ...
            </listeners>  
            </source>  
        </sources>  
    </system.diagnostics>  
</configuration>  
```  
  
 Si l'attribut `logKnownPii` n'est pas spécifié, les PII ne sont pas enregistrées.  
  
 Les PII sont uniquement enregistrées si les deux attributs `enableLoggingKnownPii` et `true` ont la valeur `logKnownPii`.  
  
> [!NOTE]
> System.Diagnostics ignore tous les attributs de toutes les sources, sauf le premier attribut répertorié dans le fichier de configuration. L'ajout de l'attribut `logKnownPii` à la seconde source du fichier de configuration est sans effet.  
  
> [!IMPORTANT]
> Pour exécuter cet échantillon implique la modification manuelle de Machine.config. Il faut faire attention lors de la modification de Machine.config que les valeurs incorrectes ou la syntaxe peut empêcher toutes les applications .NET Framework de s’exécuter.  
  
 Les éléments de fichier de configuration peuvent également être chiffrés à l'aide de DPAPI et RSA. Pour plus d'informations, consultez les liens suivants :  
  
- [Construire des applications sécurisées ASP.NET : authentification, à l’autorisation et à la communication sécurisée](https://docs.microsoft.com/previous-versions/msp-n-p/ff649248(v=pandp.10))  
  
- [Comment : chiffrer des sections de configuration dans ASP.NET 2.0 à l'aide de RSA (page pouvant être en anglais)](https://docs.microsoft.com/previous-versions/msp-n-p/ff650304(v=pandp.10))  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Modifiez le fichier Machine.config pour affecter à l'attribut `enableLoggingKnownPii` la valeur `true` en ajoutant les nœuds parents, si nécessaire.  
  
3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Pour exécuter l’échantillon dans une configuration mono-ou cross-computer, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
#### <a name="to-clean-up-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
1. Modifiez le fichier Machine.config pour affecter à l'attribut `enableLoggingKnownPii` la valeur `false`.  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
