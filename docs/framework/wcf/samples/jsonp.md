---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9e27d4e73f43f004ac1de078db6a73cd42b24bbc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237662"
---
# <a name="jsonp"></a>JSONP

Cet exemple montre comment prendre en charge JSON with Padding (JSONP) dans les services WCF REST. JSONP est une convention servant à appeler des scripts entre domaines en générant des balises de script dans le document actif. Le résultat est retourné dans une fonction de rappel spécifiée. JSONP repose sur l’idée que des balises telles que `<script src="http://..." >` peuvent évaluer des scripts de n’importe quel domaine et que le script récupéré par ces balises est évalué dans une étendue dans laquelle d’autres fonctions peuvent déjà être définies.

## <a name="demonstrates"></a>Illustre le

 Script entre domaines avec JSONP.

## <a name="discussion"></a>Discussions

 L'exemple inclut une page Web qui ajoute dynamiquement un bloc de script après que la page a été rendue dans le navigateur. Ce bloc de script appelle un service WCF REST qui a une seule opération, `GetCustomer`. Le service WCF REST retourne le nom et l'adresse d'un client encapsulés dans un nom de fonction de rappel. Lorsque le service WCF REST répond, la fonction de rappel de la page web est appelée avec les données client et la fonction de rappel affiche les données dans la page web. L'injection de la balise de script et l'exécution de la fonction de rappel sont gérées automatiquement par le contrôle ASP.NET AJAX ScriptManager. Le modèle d’utilisation est le même qu’avec tous les proxys ASP.NET AJAX, mais comprend une ligne supplémentaire pour activer JSONP, comme le montre le code suivant :

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 La page web peut appeler le service WCF REST, car le service utilise le <xref:System.ServiceModel.Description.WebScriptEndpoint> avec `crossDomainScriptAccessEnabled` ayant la valeur `true`. Ces deux configurations sont effectuées dans le fichier Web.config sous l' \<system.serviceModel> élément.

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 ScriptManager gère l'interaction avec le service et cache la complexité de l'implémentation manuelle de l'accès JSONP. Lorsque `crossDomainScriptAccessEnabled` a la valeur `true` et que le format de la réponse d’une opération est JSON, l’infrastructure WCF inspecte l’URI de la demande pour un paramètre de chaîne de requête de rappel et encapsule la réponse JSON avec la valeur du paramètre de chaîne de requête de rappel. Dans l'exemple, la page Web appelle le service WCF REST avec l'URI suivant.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Étant donné que le paramètre de chaîne de requête de rappel a la valeur `JsonPCallback`, le service WCF retourne une réponse JSONP représentée dans l'exemple suivant.

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Cette réponse JSONP inclut les données client mises au format JSON et encapsulées avec le nom de la fonction de rappel que la page web a demandée. ScriptManager exécute ce rappel à l'aide d'une balise de script pour effectuer la demande entre domaines, puis passe le résultat au gestionnaire onSuccess qui a été passé à l'opération GetCustomer du proxy ASP.NET AJAX.

 L’exemple se compose de deux applications Web ASP.NET : l’une contient uniquement un service WCF, tandis que l’autre contient la page Web. aspx, qui appelle le service. Lors de l’exécution de la solution, Visual Studio 2012 héberge les deux sites Web sur des ports différents, ce qui crée un environnement dans lequel le service et le client se trouvent sur des domaines différents.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Exécution de l'exemple  
  
1. Ouvrez la solution de l'exemple JSONP.  
  
2. Appuyez sur F5 pour lancer `http://localhost:26648/JSONPClientPage.aspx` dans le navigateur.  
  
3. Notez qu’après le chargement de la page, les entrées de texte pour « name » et « Address » sont renseignées par des valeurs.  Ces valeurs ont été fournies par un appel au service WCF une fois que le navigateur a terminé le rendu de la page.
