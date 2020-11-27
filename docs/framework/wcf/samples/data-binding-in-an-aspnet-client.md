---
title: Data Binding in an ASP.NET Client
ms.date: 03/30/2017
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
ms.openlocfilehash: 3e30bcb9852b34eeb919339d57d701e4dda8a644
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266868"
---
# <a name="data-binding-in-an-aspnet-client"></a>Data Binding in an ASP.NET Client

Cet exemple montre comment lier des données retournées par un service Windows Communication Foundation (WCF) classique dans une application Web Forms.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple contient un service qui implémente un contrat définissant un modèle de communication demande-réponse. L’exemple se compose d’une application cliente Web Forms accessible à partir d’un navigateur et d’un service WCF hébergé par Internet Information Services (IIS).  
  
 Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `IWeatherService`, laquelle expose une opération nommée `GetWeatherData`. Cette opération accepte un tableau de villes et retourne un tableau d'objets `WeatherData` qui représente les prévisions de températures maximales et minimales d'une ville.  
  
 Sur la page client. aspx ASP.NET, un contrôle Web DataGrid est défini, qui contient la représentation graphique des données retournées par le service. Le code sur la page. aspx appelle le service WCF pour les données météorologiques et retourne les données à un tableau d' `WeatherData` objets. DataGrid indique où obtenir ses données en affectant ce tableau à sa propriété `DataSource`. La liaison de données se produit avec un appel à la méthode `DataBind` de DataGrid. Tout ce code est contenu dans le.`aspx` méthode de la page `Page_Load` . ainsi, chaque fois que l’utilisateur actualise la page du navigateur, les données sont mises à jour dans la grille de données.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Le client de cet exemple est un site web qui s’exécute sous un serveur Web de développement. Pour lancer le serveur Web de développement, tapez la commande suivante à l’invite de commandes : `%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client` . Accédez ensuite à `http://localhost:8000/client` . Pour exécuter cet exemple sur plusieurs ordinateurs, remplacez toutes les références à `localhost` dans le fichier Web.config du client par le nom d'ordinateur du serveur.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`
