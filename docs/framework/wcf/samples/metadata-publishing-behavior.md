---
title: Metadata Publishing Behavior
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144394"
---
# <a name="metadata-publishing-behavior"></a>Metadata Publishing Behavior
Cet exemple montre comment contrôler les fonctionnalités de publication des métadonnées d’un service. Afin d’éviter la divulgation involontaire de métadonnées de service potentiellement sensibles, la configuration par défaut des services de la Windows Communication Foundation (WCF) désactive la publication de métadonnées. Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration.  
  
> [!IMPORTANT]
> Pour plus de clarté, cet exemple montre comment créer un point de terminaison de publication de métadonnées non sécurisé. De tels points de terminaison sont potentiellement disponibles aux consommateurs non authentifiés anonymes et il est nécessaire de se montrer vigilant et de s'assurer que la divulgation publique des métadonnées d'un service est appropriée avant de déployer de tels points de terminaison. Consultez l’échantillon [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) pour un échantillon qui sécurise un point de terminaison de métadonnées.  
  
 L’échantillon est basé sur le Getting `ICalculator` [Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui met en œuvre le contrat de service. Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Pour qu'un service expose des métadonnées, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> doit être configuré sur le service. Lorsque ce comportement est présent, vous pouvez publier des métadonnées en configurant un point de terminaison afin qu'il exposer le contrat <xref:System.ServiceModel.Description.IMetadataExchange> en tant qu'implémentation d'un protocole MEX (WS-MetadataExchange). Par commodité, le nom de configuration abrégé « IMetadataExchange » a été donné à ce contrat. Cet exemple utilise `mexHttpBinding`, qui est une liaison standard équivalente à `wsHttpBinding` dont le mode de sécurité a la valeur `None`. Une adresse relative de "mex" est utilisée dans le critère d’évaluation, qui, `http://localhost/servicemodelsamples/service.svc/mex`lorsqu’il est résolu contre l’adresse de base des services, aboutit à une adresse de point final de . La configuration de comportement se présente comme suit :  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Le point de terminaison MEX se présente comme suit :  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 Cet exemple affecte <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> à la propriété `true` qui expose également les métadonnées du service à l'aide de HTTP GET. Pour activer un point de terminaison de métadonnées HTTP GET, le service doit avoir une adresse de base HTTP. La chaîne de requête `?wsdl` est utilisée sur l'adresse de base du service pour accéder aux métadonnées. Par exemple, pour voir le WSDL pour le service `http://localhost/servicemodelsamples/service.svc?wsdl`dans un navigateur Web, vous utiliseriez l’adresse . Vous pouvez également utiliser ce comportement pour exposer des métadonnées sur HTTPS en affectant <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> à `true`. Cela requiert une adresse de base HTTPS.  
  
 Pour accéder au point de terminaison MEX du service, utilisez [l’outil utilitaire De métadonnées De ServiceModel (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Cette opération génère un client basé sur les métadonnées du service.  
  
 Pour accéder aux métadonnées du service à `http://localhost/servicemodelsamples/service.svc?wsdl`l’aide de HTTP GET, pointez votre navigateur vers .  
  
 Si vous supprimez ce comportement et tentez d'ouvrir le service, vous obtenez une exception. Cette erreur se produit car sans le comportement, le point de terminaison configuré avec le contrat `IMetadataExchange` n'a aucune implémentation.  
  
 Si vous affectez `HttpGetEnabled` à `false`, la page d'aide CalculatorService s'affiche à la place des métadonnées du service.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
