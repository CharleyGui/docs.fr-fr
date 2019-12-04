---
title: ASP.NET Caching Integration
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 23c10e56dba7daec2d1027de92e8252c8fe69055
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716178"
---
# <a name="aspnet-caching-integration"></a>ASP.NET Caching Integration

Cet exemple montre comment utiliser le cache de sortie ASP.NET avec le modèle de programmation HTTP Web WCF. Cette rubrique met l’accent sur la fonctionnalité d’intégration du cache de sortie ASP.NET.

## <a name="demonstrates"></a>Montre

Intégration au cache de sortie ASP.NET

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a>Discussion

L’exemple utilise la <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> pour utiliser la mise en cache de sortie ASP.NET avec le service Windows Communication Foundation (WCF). L'<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> est appliqué aux opérations de service et fournit le nom d'un profil de cache dans un fichier de configuration qui doit être appliqué aux réponses de l'opération donnée.

Dans le fichier Service.cs de l’exemple de projet de service, les opérations `GetCustomer` et `GetCustomers` sont marquées avec le <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, qui fournit le nom de profil de cache « CacheFor60Seconds ». Dans le fichier Web. config du projet de service, le profil de cache « CacheFor60Seconds » est fourni sous l’élément <`caching`> de <`system.web`>. Pour ce profil de cache, la valeur de l’attribut `duration` est « 60 », donc les réponses associées à ce profil sont mises en cache dans le cache de sortie ASP.NET pendant 60 secondes. En outre, pour ce profil de cache, l’attribut `varmByParam` est défini sur « format », de sorte que les réponses des demandes avec des valeurs différentes pour le paramètre de chaîne de requête `format` sont mises en cache séparément. Enfin, l’attribut `varyByHeader` du profil de cache est défini sur « accepter », de sorte que les réponses des demandes avec différentes valeurs d’en-tête Accept soient mises en cache séparément.

Le fichier program.cs du projet Client montre comment un tel client peut être créé à l'aide de <xref:System.Net.HttpWebRequest>. Notez qu'il ne s'agit là que de l'un des moyens d'accéder à un service WCF. Il est également possible d’accéder au service à l’aide d’autres classes de .NET Framework, telles que la fabrique de canal WCF et <xref:System.Net.WebClient>. D’autres exemples du kit de développement logiciel (SDK), tels que l’exemple de [service http de base](../../../../docs/framework/wcf/samples/basic-http-service.md) , montrent comment utiliser ces classes pour communiquer avec un service WCF.

## <a name="to-run-the-sample"></a>Pour exécuter l’exemple

Cet exemple est composé de trois projets :

- **Service**: projet d’application Web qui comprend un service HTTP WCF hébergé dans ASP.net.

- **Client**: un projet d’application console qui effectue des appels au service.

- **Commun**: bibliothèque partagée qui contient le type de client utilisé par le client et le service.

Lorsque l'application console Client s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.

#### <a name="to-run-the-sample"></a>Pour exécuter l’exemple

1. Ouvrez la solution de l'exemple ASP.NET Caching Integration.

2. Appuyez sur Ctrl+Maj+B pour générer la solution.

3. Si la fenêtre de **Explorateur de solutions** n’est pas déjà ouverte, appuyez sur CTRL + W + S.

4. Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le projet de **service** , puis sélectionnez **Démarrer une nouvelle instance**. Cette opération lance le serveur de développement ASP.NET, qui héberge le service.

5. Dans la fenêtre **Explorateur de solutions** , cliquez avec le bouton droit sur le projet **client** , puis sélectionnez **Démarrer une nouvelle instance**.

6. La fenêtre de console du client apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML. Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur.

7. Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.

8. Appuyez sur une touche quelconque pour arrêter l'application console Client.

9. Appuyez sur MAJ+F5 pour arrêter le débogage du service.

10. Dans la zone de notification Windows, cliquez avec le bouton droit sur l’icône du serveur de développement ASP.NET et sélectionnez **arrêter**.
