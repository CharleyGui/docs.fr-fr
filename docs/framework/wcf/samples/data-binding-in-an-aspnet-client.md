---
title: Data Binding in an ASP.NET Client
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: c068c1cab5a5b9dad75e781e58076f4066a3b2a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145005"
---
# <a name="data-binding-in-an-aspnet-client"></a>Data Binding in an ASP.NET Client
Cet exemple montre comment lier les données retournées par un service typique de la Windows Communication Foundation (WCF) dans une application Web Forms.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple contient un service qui implémente un contrat définissant un modèle de communication demande-réponse. L’échantillon se compose d’une application Web Forms client accessible à partir d’un navigateur et d’un service WCF hébergé par Internet Information Services (IIS).  
  
 Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `IWeatherService`, laquelle expose une opération nommée `GetWeatherData`. Cette opération accepte un tableau de villes et retourne un tableau d'objets `WeatherData` qui représente les prévisions de températures maximales et minimales d'une ville.  
  
 Sur la page ASP.NET client .aspx, un contrôle Web DataGrid est défini, qui contient la représentation graphique des données retournées par le service. Code sur la page .aspx appelle le service WCF pour `WeatherData` les données météorologiques et renvoie les données à un tableau d’objets. DataGrid indique où obtenir ses données en affectant ce tableau à sa propriété `DataSource`. La liaison de données se produit avec un appel à la méthode `DataBind` de DataGrid. Tout ce code est contenu à l’intérieur de la .`aspx` méthode de `Page_Load` la page, donc chaque fois que l’utilisateur actualise la page du navigateur, les données sont mises à jour dans le DataGrid.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Le client de cet exemple est un site web qui s’exécute sous un serveur Web de développement. Pour lancer le serveur Web de développement, `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`tapez ce qui suit à la commande invite: . Ensuite, naviguez vers `http://localhost:8000/client`. Pour exécuter cet exemple sur plusieurs ordinateurs, remplacez toutes les références à `localhost` dans le fichier Web.config du client par le nom d'ordinateur du serveur.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
