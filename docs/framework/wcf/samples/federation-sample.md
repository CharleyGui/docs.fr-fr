---
title: Federation, exemple
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 9ec462f88c0e3a039b7f288554be3e28f13ece08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144667"
---
# <a name="federation-sample"></a>Federation, exemple
Cet exemple présente la sécurité fédérée :  
  
## <a name="sample-details"></a>Détails de l'exemple  
 Windows Communication Foundation (WCF) fournit un soutien pour le `wsFederationHttpBinding`déploiement d’architectures de sécurité fédérées à travers le . `wsFederationHttpBinding` fournit une liaison sécurisée, fiable et interopérable qui implique l'utilisation de HTTP comme mécanisme de transport sous-jacent pour la communication demande/réponse, le format de câble d'encodage étant Text/XML. Pour plus d’informations sur la Fédération dans WCF, voir [Fédération](../../../../docs/framework/wcf/feature-details/federation.md).  
  
 Le scénario comporte 4 parties :  
  
- Service BookStore  
  
- STS BookStore  
  
- STS HomeRealm  
  
- Client BookStore  
  
 Le service BookStore prend en charge deux opérations : `BrowseBooks` et `BuyBook`. Il autorise l'accès anonyme à l'opération `BrowseBooks`, mais requiert l'authentification pour accéder à l'opération `BuyBooks`. L'authentification prend la forme d'un jeton émis par le STS BookStore. Le fichier de configuration du service BookStore pointe des clients sur le STS BookStore à l'aide de `wsFederationHttpBinding`.  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 Le STS BookStore impose ensuite aux clients de s'authentifier à l'aide d'un jeton émis par le STS HomeRealm. Une fois encore, le fichier de configuration du STS BookStore pointe des clients sur le STS HomeRealm à l'aide de `wsFederationHttpBinding`.  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 La séquence des événements lors de l'accès à l'opération `BuyBook` est la suivante :  
  
1. Le client s'authentifie auprès du STS HomeRealm à l'aide d'informations d'identification Windows.  
  
2. Le STS HomeRealm émet un jeton qui peut être utilisé pour s'authentifier auprès du STS BookStore.  
  
3. Le client s'authentifie auprès du STS BookStore à l'aide du jeton émis par le STS HomeRealm.  
  
4. Le STS BookStore émet un jeton qui peut être utilisé pour s'authentifier auprès du service BookStore.  
  
5. Le client s'authentifie auprès du service BookStore à l'aide du jeton émis par le STS BookStore.  
  
6. Le client accède à l'opération `BuyBook`.  
  
 Suivez les instructions suivantes sur la configuration et l'exécution de cet exemple.  
  
> [!NOTE]
> Vous devez avoir e des autorisations à l’annuaire **wwwroot** pour exécuter cet échantillon.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Ouvrez la fenêtre de commande de Kit de développement SDK. Dans le chemin d’accès de l’exemple, exécutez Setup.bat. Cette opération crée les répertoires virtuels requis pour l'exemple et installe les certificats requis avec les autorisations appropriées.  
  
    > [!NOTE]
    > Le fichier de commandes Setup.bat est conçu pour s'exécuter à partir d'une invite de commandes du Kit de développement Windows SDK. La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK. Cette variable est définie automatiquement dans une invite de commandes du Kit de développement logiciel Windows. Sur Windows Vista, vous devez vous assurer que la compatibilité de gestion IIS 6.0 est installée parce que la configuration utilise des scripts d’administrateur IIS. L’exécution du script de configuration sur Windows Vista nécessite des privilèges d’administrateur.  
  
2. Ouvrez FederationSample.sln dans Visual Studio et sélectionnez **Build Solution** dans le menu **Build.** Cette opération génère les fichiers de projet communs, le service Bookstore, le STS Bookstore, le STS HomeRealm, et les déploie dans IIS. Elle génère également l’application cliente Bookstore et place le fichier exécutable BookStoreClient.exe dans le dossier FederationSample\BookStoreClient\bin\Debug.  
  
3. Double-cliquez sur BookStoreClient.exe. La fenêtre BookStoreClient s'affiche.  
  
4. Vous pouvez parcourir les livres disponibles dans la librairie en cliquant **sur Parcourir les livres**.  
  
5. Pour acheter un livre particulier, sélectionnez le livre dans la liste et cliquez sur **Buy Book**. L'application démarre et s'authentifie à l'aide de l'authentification Windows avec le STS HomeRealm.  
  
     L'exemple est configuré pour permettre aux utilisateurs d'acheter des livres pour un montant égal ou inférieur à 15 dollars. Si un client tente d'acheter des livres pour un montant supérieur à 15 dollars, il reçoit un message du service BookStore indiquant que l'accès est refusé.  
  
    > [!NOTE]
    > L'exemple ne met pas à jour la limite de crédit de l'utilisateur après un achat. Vous pouvez acheter des livres à plusieurs reprises dans la limite de crédit (fixée) de l'utilisateur.  
  
#### <a name="to-clean-up"></a>Pour nettoyer  
  
1. Exécutez Cleanup.bat. Cette opération supprime les répertoires virtuels créés pendant l'installation ainsi que les certificats installés pendant l'installation.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
