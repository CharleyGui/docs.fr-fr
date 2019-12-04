---
title: Service HTTP de base
ms.date: 03/30/2017
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
ms.openlocfilehash: 8dfcd5a751bcef6aa24b5cb4a200c8820c43fe81
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716100"
---
# <a name="basic-http-service"></a>Service HTTP de base

Cet exemple montre comment implémenter un service basé sur HTTP et RPC, communément appelé « POX » (Plain Old XML) service, à l’aide du modèle de programmation REST Windows Communication Foundation (WCF). Cet exemple se compose de deux composants : un service HTTP WCF auto-hébergé (Service.cs) et une application console (Program.cs) qui crée le service et effectue des appels à ce dernier.

## <a name="sample-details"></a>Détails de l'exemple

Le service WCF expose 2 opérations, `EchoWithGet` et `EchoWithPost`, qui retourne la chaîne passée comme entrée.

L’opération `EchoWithGet` est annotée avec <xref:System.ServiceModel.Web.WebGetAttribute>, ce qui indique que l’opération traite des requêtes HTTP `GET`. Comme le <xref:System.ServiceModel.Web.WebGetAttribute> ne spécifie pas explicitement d'<xref:System.UriTemplate>, l'opération attend le passage de la chaîne d'entrée à l'aide d'un paramètre de chaîne de requête mentionnant le nom `s`. Notez que le format de l'URI attendu par le service peut être personnalisé à l'aide de la propriété <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A>.

L’opération `EchoWithPost` est annotée avec <xref:System.ServiceModel.Web.WebInvokeAttribute>, ce qui indique qu’il ne s’agit pas d’une opération `GET` (elle a des effets secondaires). Comme le <xref:System.ServiceModel.Web.WebInvokeAttribute> ne spécifie pas explicitement de `Method`, l'opération traite les requêtes HTTP `POST` dont le corps contient la chaîne (au format XML, par exemple). Notez que la méthode HTTP et le format de l'URI de la requête peuvent être personnalisés à l'aide des propriétés <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> et <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate>, respectivement.

Le fichier App.config configure le service WCF avec un <xref:System.ServiceModel.Description.WebHttpEndpoint> par défaut dont la propriété <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> a la valeur `true`. Par conséquent, l’infrastructure WCF crée une page d’aide HTML automatique à `http://localhost:8000/Customers/help` qui fournit des informations sur la construction de requêtes HTTP pour le service et sur l’utilisation de la réponse HTTP du service.

Program.cs montre comment une fabrique de canaux WCF peut être utilisée pour effectuer des appels au service et traiter les réponses. Notez qu'il ne s'agit là que de l'un des moyens d'accéder à un service WCF. Il est également possible d'accéder au service à l'aide d'autres classes .NET Framework, comme <xref:System.Net.HttpWebRequest> et <xref:System.Net.WebClient>.

L'exemple est constitué d'un service auto-hébergé et d'un client qui s'exécutent tous deux dans une application console. Lorsque l'application console s'exécute, le client adresse des requêtes au service et affiche les informations pertinentes des réponses dans la fenêtre de console.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. Ouvrez la solution de l'exemple Basic HTTP Service. Lors du lancement de Visual Studio 2012, vous devez exécuter en tant qu’administrateur pour que l’exemple s’exécute correctement. Pour ce faire, cliquez avec le bouton droit sur l’icône Visual Studio 2012 et sélectionnez **exécuter en tant qu’administrateur** dans le menu contextuel.

2. Appuyez sur CTRL+MAJ+B pour générer la solution, puis appuyez sur Ctrl+F5 pour exécuter l'application console sans débogage. La fenêtre de console apparaît et fournit l'URI du service en cours d'exécution, ainsi que l'URI de sa page d'aide HTML. Vous pouvez à tout moment consulter la page d'aide HTML en tapant son URI dans un navigateur. Lorsque l'exemple s'exécute, le client écrit l'état de l'activité actuelle.

3. Appuyez sur une touche quelconque pour arrêter l'exemple.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`
