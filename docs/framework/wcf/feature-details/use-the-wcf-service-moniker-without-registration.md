---
title: 'Comment : utiliser le moniker de service Windows Communication Foundation sans inscription'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: f69314948a0e0a69e49ec148f94572f17d0b8e3c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595048"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>Comment : utiliser le moniker de service Windows Communication Foundation sans inscription
Pour vous connecter à un service Windows Communication Foundation (WCF) et communiquer avec celui-ci, une application cliente WCF doit avoir les détails de l’adresse du service, de la configuration de liaison et du contrat de service.  
  
 Le moniker de service WCF obtient généralement le contrat requis via l’inscription antérieure des types d’attributs requis, mais il peut y avoir des cas où cela n’est pas possible. À la place de l'inscription, le moniker peut obtenir la définition du contrat sous la forme d'un document WSDL (Web Services Definition Language) en utilisant le paramètre `wsdl` ou par le biais de l'échange de métadonnées en utilisant le paramètre `mexAddress`.  
  
 Cela permet de prendre en charge des scénarios comme la distribution d'une feuille de calcul Excel dans laquelle certaines valeurs de cellules sont calculées par le biais d'interactions de services Web. Dans ce scénario, il peut ne pas être possible d'inscrire l'assembly de contrat de service sur tous les clients susceptibles d'ouvrir le document. Les paramètres `wsdl` et `mexAddress` offrent une solution autonome.  
  
> [!NOTE]
> L'authentification mutuelle doit être utilisée pour la protection contre la falsification ou l'usurpation de demandes et de réponses. Il est en particulier important pour les clients d'avoir la garantie que le point de terminaison d'échange de métadonnées qui répond est le tiers de confiance attendu.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre l'utilisation du moniker de service avec un contrat MEX. Un service associé au contrat suivant est exposé avec un wsHttpBinding.  
  
```csharp
using System.ServiceModel;  
  
// ...
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 Pour construire un client WCF pour le service distant, l’exemple de chaîne de moniker suivante peut être utilisé.  
  
```
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 Pendant l'exécution de l'application cliente, le client exécute un `WS-MetadataExchange` avec le paramètre `mexAddress`. Les détails de l'adresse, de la liaison et du contrat peuvent alors être retournés pour un certains nombre de services. Les paramètres `address`, `contract`, `contractNamespace`, `binding` et `bindingNamespace` sont utilisés pour identifier le service concerné. Une fois ces paramètres mis en correspondance, le moniker construit un client WCF avec la définition de contrat appropriée et les appels peuvent être effectués à l’aide du client WCF, comme avec le contrat typé.  
  
> [!NOTE]
> Si le moniker est incorrect ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide. Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.  
  
## <a name="see-also"></a>Voir aussi

- [Comment : inscrire et configurer un moniker de service](how-to-register-and-configure-a-service-moniker.md)
