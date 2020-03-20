---
title: Point de terminaison de métadonnées sécurisé personnalisée
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 89f12b4490d556884aaa15dcb102b5ad876707ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183844"
---
# <a name="custom-secure-metadata-endpoint"></a>Point de terminaison de métadonnées sécurisé personnalisée
Cet exemple montre comment implémenter un service avec un point de terminaison sécurisé de métadonnées qui utilise l’une des liaisons d’échange de non-métadonnées, et comment configurer [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ou les clients pour aller chercher les métadonnées à partir d’un tel point de terminaison de métadonnées. Il existe deux liaisons fournies par le système pour exposer des points de terminaison de métadonnées : mexHttpBinding et mexHttpsBinding. mexHttpBinding est utilisé pour exposer un point de terminaison de métadonnées sur HTTP de façon non sécurisée. mexHttpsBinding est utilisé pour exposer un point de terminaison de métadonnées sur HTTPS de façon sécurisée. Cet exemple montre comment exposer un point de terminaison de métadonnées sécurisé à l'aide du <xref:System.ServiceModel.WSHttpBinding>. Cette opération peut être utile lorsque vous souhaitez modifier les paramètres de sécurité de la liaison sans devoir utiliser HTTPS. Si vous utilisez mexHttpsBinding, votre point de terminaison de métadonnées sera sécurisé, mais il n'existe aucun moyen de modifier les paramètres de la liaison.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="service"></a>Service  
 Dans cet exemple, le service dispose de deux points de terminaison. Le point de terminaison d'application sert le contrat `ICalculator` d'une liaison `WSHttpBinding`, `ReliableSession` étant activée et la sécurité `Message` utilisant des certificats. Le point de terminaison de métadonnées utilise également une liaison `WSHttpBinding`, avec les mêmes paramètres de sécurité mais sans `ReliableSession`. Le code suivant contient la configuration requise :  
  
```xml  
<services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 Dans de nombreux autres exemples, le point de terminaison de métadonnées utilise la liaison par défaut `mexHttpBinding`, laquelle n'est pas sécurisée. Dans cet exemple, les métadonnées sont sécurisées grâce à l'utilisation conjointe de la liaison `WSHttpBinding` et de la sécurité `Message`. Pour que des clients de métadonnées puissent récupérer ces métadonnées, ils doivent être configurés à l'aide d'une liaison similaire. Cet exemple contient deux clients configurés à l'aide d'une telle liaison.  
  
 Le premier client utilise Svcutil.exe pour extraire les métadonnées et générer le code client ainsi que la configuration pendant la conception. Le service utilisant une liaison non définie par défaut pour les métadonnées, l'outil Svcutil.exe doit être configuré de manière spécifique, c'est-à-dire de sorte à pouvoir obtenir les métadonnées de ce service en utilisant une telle liaison.  
  
 Le deuxième client utilise le `MetadataResolver` pour extraire dynamiquement les métadonnées d'un contrat connu, puis pour appeler des opérations sur le client généré dynamiquement.  
  
## <a name="svcutil-client"></a>Client Svcutil  
 Lorsque la liaison par défaut héberge votre point de terminaison `IMetadataExchange`, vous pouvez exécuter Svcutil.exe en utilisant l’adresse de ce point de terminaison :  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 ce qui fonctionnera parfaitement. Cependant, dans cet exemple, le serveur n'utilise pas de point de terminaison défini par défaut pour héberger les métadonnées. Vous devez donc indiquer à l’outil Svcutil.exe quelle liaison il doit utiliser. Pour ce faire, vous pouvez notamment utiliser un fichier Svcutil.exe.config.  
  
 Ce fichier ressemble à un fichier de configuration client standard. Le nom et le contrat de point de terminaison client qui y figurent sont les deux seuls points qui diffèrent :  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 Le nom de point de terminaison doit correspondre au nom du schéma de l'adresse où sont hébergées les métadonnées et le contrat de point de terminaison doit correspondre à `IMetadataExchange`. Par conséquent, lorsque Svcutil.exe est exécuté à l'aide d'une ligne de commande telle que celle présentée ci-dessous :  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 il recherche le point de terminaison nommé « http » et le contrat `IMetadataExchange` pour configurer la liaison et le comportement de l’échange de communication à l’aide du point de terminaison de métadonnées. Le reste du fichier Svcutil.exe.config (dans cet exemple) spécifie la configuration de la liaison et les informations d’identification du comportement de sorte à ce qu’elles correspondent à la configuration du point de terminaison de métadonnées côté serveur.  
  
 Pour que l'outil Svcutil.exe puisse récupérer la configuration spécifiée dans le fichier Svcutil.exe.config, ils doivent tous deux se trouver dans le même répertoire. Vous devez copier l'outil Svcutil.exe depuis son emplacement d'installation vers le répertoire qui contient le fichier Svcutil.exe.config. À partir de ce répertoire, exécutez ensuite la commande suivante :  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Le leader ". \\" assure que la copie de Svcutil.exe dans ce répertoire (celui qui a un Svcutil.exe.config correspondant) est exécuté.  
  
## <a name="metadataresolver-client"></a>Client MetadataResolver  
 Si le client connaît le contrat et sait comment s’adresser aux métadonnées pendant la conception, il peut trouver dynamiquement la liaison et l’adresse des points de terminaison d’application à l’aide du `MetadataResolver`. Cet exemple de client démontre comme cela est possible en indiquant comment configurer la liaison et les informations d’identification utilisées par `MetadataResolver` en créant et configurant un `MetadataExchangeClient`.  
  
 La liaison ainsi que les informations de certificat apparues dans Svcutil.exe.config peuvent également être spécifiées à l'identique et de manière impérative sur le `MetadataExchangeClient` :  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 Grâce au `mexClient` configuré, nous pouvons énumérer les contrats auxquels nous nous intéressons et utiliser un `MetadataResolver` pour récupérer une liste des points de terminaison correspondant à ces contrats :  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 Enfin, nous pouvons utiliser les informations de ces points de terminaison pour initialiser la liaison et l’adresse de la fabrication `ChannelFactory` utilisée pour créer les canaux assurant la communication avec les points de terminaison d’application.  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 L’objectif premier de cet exemple de client est de démontrer que si vous utilisez un `MetadataResolver` et que vous devez spécifier des liaisons ou comportements personnalisés pour la communication d’échange de métadonnées, vous pouvez utiliser un `MetadataExchangeClient` pour ce faire.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1. Exécutez Setup.bat à partir du dossier d'installation de l'exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés. Notez que Setup.bat utilise l’outil FindPrivateKey.exe, qui est installé en exécutant setupCertTool.bat de [one-Time Setup Procedure pour les échantillons de la Fondation de communication Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Exécutez l'application cliente à partir du dossier \MetadataResolverClient\bin ou du dossier \SvcutilClient\bin. L'activité du client s'affiche sur son application de console.  
  
3. Si le client et le service ne sont pas en mesure de communiquer, voir [Conseils de dépannage pour les échantillons WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
4. Supprimez les certificats en exécutant Cleanup.bat une fois l'exemple terminé. D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
#### <a name="to-run-the-sample-across-machines"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Sur le serveur, exécutez `setup.bat service`. Exécution `setup.bat` avec `service` l’argument crée un certificat de service avec le nom de domaine entièrement qualifié de la machine et exporte le certificat de service à un fichier nommé Service.cer.  
  
2. Sur le serveur, modifiez Web.config en fonction du nouveau nom de ce certificat. C’est-à-dire, changer l’attribut `findValue` dans le [ \<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) élément au nom de domaine entièrement qualifié de la machine.  
  
3. Copiez le fichier Service.cer du répertoire de service dans le répertoire client sur l'ordinateur client.  
  
4. Sur le client, exécutez `setup.bat client`. Exécution `setup.bat` avec `client` l’argument crée un certificat de client nommé Client.com et exporte le certificat du client à un fichier nommé Client.cer.  
  
5. Dans le fichier App.config du `MetadataResolverClient` de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison mex en fonction de la nouvelle adresse de votre service. Pour ce faire, remplacez localhost par le nom de domaine complet du serveur. Remplacez également l'occurrence de « localhost » dans le fichier metadataResolverClient.cs par le nouveau nom du certificat de service (c'est-à-dire par le nom de domaine complet du serveur). Effectuez la même opération pour l'App.config du projet SvcutilClient.  
  
6. Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
7. Sur le client, exécutez `ImportServiceCert.bat`. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
8. Sur le serveur, exécutez `ImportClientCert.bat`. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.  
  
9. Sur l'ordinateur de service, générez le projet de service à l'aide de Visual Studio, puis sélectionnez la page d'aide d'un navigateur Web afin de vous assurer que ce projet s'exécute.  
  
10. Sur l'ordinateur client, exécutez le MetadataResolverClient ou le SvcutilClient depuis VS.  
  
    1. Si le client et le service ne sont pas en mesure de communiquer, voir [Conseils de dépannage pour les échantillons WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
    > [!NOTE]
    > Ce script ne supprime pas les certificats de service figurant sur le client lorsque l'exemple est exécuté sur plusieurs ordinateurs. Si vous avez exécuté des échantillons de la Windows Communication Foundation (WCF) qui utilisent des certificats sur les machines, assurez-vous d’effacer les certificats de service qui ont été installés dans le magasin CurrentUser - TrustedPeople. Pour ce faire, utilisez la ligne de commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`. Par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
