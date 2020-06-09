---
title: Services monodirectionnels
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 0d69af40e4b9a0133e44b64b45466f9aac84ffe2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598747"
---
# <a name="one-way-services"></a>Services monodirectionnels
Le comportement par défaut d'une opération de service est le modèle demande-réponse. Dans un modèle demande-réponse, le client attend le message de réponse, même si l'opération de service est représentée dans le code en tant que méthode `void`. Avec une opération monodirectionnelle, un seul message est transmis. Le récepteur n'envoie pas de message de réponse, l'expéditeur n'en attend pas.  
  
 Utilisez le modèle de design monodirectionnel :  
  
- Lorsque le client doit appeler des opérations et n'est pas affecté par le résultat de l'opération au niveau de l'opération.  
  
- Lorsque vous utilisez la classe <xref:System.ServiceModel.NetMsmqBinding> ou <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. (Pour plus d’informations sur ce scénario, consultez [files d’attente dans WCF](queues-in-wcf.md).)  
  
 Lorsqu'une opération est monodirectionnelle, il n'y a pas de message pour renvoyer des informations sur l'erreur au client. Vous pouvez détecter des conditions d’erreur à l’aide de fonctionnalités de la liaison sous-jacente, telle que les sessions fiables, ou en concevant un contrat de service duplex qui utilise deux opérations monodirectionnelles : un contrat monodirectionnel du client au service afin d’appeler l’opération de service, et un autre contrat monodirectionnel entre le service et le client afin que le service puisse renvoyer des erreurs au client à l’aide d’un rappel que le client implémente.  
  
 Pour créer un contrat de service monodirectionnel, définissez votre contrat de service, appliquez la classe <xref:System.ServiceModel.OperationContractAttribute> à chaque opération et affectez <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> à la propriété `true`, tel qu'indiqué dans l'exemple de code suivant.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Pour obtenir un exemple complet, consultez l’exemple [unidirectionnel](../samples/one-way.md) .  
  
## <a name="clients-blocking-with-one-way-operations"></a>Blocage de clients à l'aide d'opérations monodirectionnelles  
 Il est important de se rendre compte que bien que certaines applications monodirectionnelles retournent dès que les données sortantes sont écrites dans la connexion réseau, dans plusieurs scénarios, l’implémentation d’une liaison ou d’un service peut provoquer le blocage d’un client WCF à l’aide d’opérations unidirectionnelles. Dans les applications clientes WCF, l’objet client WCF ne retourne pas de valeur tant que les données sortantes n’ont pas été écrites dans la connexion réseau. Cela se vérifie pour l'ensemble des modèles d'échange de messages, dont les opérations monodirectionnelles ; cela signifie que les problèmes d'écriture de données sur le transport empêchent le client de retourner. Selon le problème, le résultat peut être une exception ou un retard d'envoi des messages au service.  
  
 Par exemple, si le transport ne peut pas trouver le point de terminaison, une exception <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> est levée sans beaucoup de retard. Toutefois, il est également possible que le service ne puisse pas lire les données du câble pour une raison quelconque, ce qui empêche l'opération d'envoi du transport client de retourner. Dans ce cas, si le délai <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> sur la liaison de transport client est dépassé, une exception <xref:System.TimeoutException?displayProperty=nameWithType> est levée, mais pas tant que le délai d’attente n’a pas été dépassé. Il est également possible qu'il y ait un nombre si élevé de messages sur un service que celui-ci ne puisse pas les traiter passé un certain stade. Dans ce cas également, le client monodirectionnel se bloque jusqu'à ce que le service puisse traiter les messages ou jusqu'à ce qu'une exception soit levée.  
  
 Une autre variante est le cas où la propriété de service <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> a la valeur <xref:System.ServiceModel.ConcurrencyMode.Single> et la liaison utilise des sessions. Dans ce cas, le répartiteur applique un classement sur les messages entrants (exigence de sessions), ce qui empêche les messages suivants d’être lus sur le réseau tant que le service n’a pas traité le message précédent de cette session. À nouveau, le client se bloque, mais la survenue d'une exception repose sur la capacité du service à traiter les données en attente avant le dépassement du délai défini sur le client.  
  
 Vous pouvez limiter ce problème en insérant une mémoire tampon entre l'objet client et l'opération d'envoi du transport client. Par exemple, l'utilisation d'appels asynchrones ou d'une file d'attente de messages en mémoire permet à l'objet client de retourner rapidement. Ces deux approches peuvent augmenter la fonctionnalité, mais la taille du pool de threads et de la file d'attente de messages pose encore des limites.  
  
 Nous vous recommandons, à la place, d'examinez les divers contrôles sur le service ainsi que sur le client, puis de tester vos scénarios d'application afin de déterminer la meilleure configuration de part et d'autre. Par exemple, si l'utilisation de sessions bloque le traitement de messages sur votre service, vous pouvez affecter <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> à la propriété <xref:System.ServiceModel.InstanceContextMode.PerCall> afin que chaque message puisse être traité par une instance de service différente, et affecter <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> à <xref:System.ServiceModel.ConcurrencyMode.Multiple> afin de permettre à plusieurs threads de distribuer des messages simultanément. Une autre approche consiste à augmenter les quotas de lecture du service et les liaisons clientes.  
  
## <a name="see-also"></a>Voir aussi

- [One-Way](../samples/one-way.md)
