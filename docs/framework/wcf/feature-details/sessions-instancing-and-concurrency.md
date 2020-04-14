---
title: Sessions, instanciation et accès concurrentiel
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 19dedddadad2f27acdeeaceb2c186a731fa79c32
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243113"
---
# <a name="sessions-instancing-and-concurrency"></a>Sessions, instanciation et accès concurrentiel
Une *session* est une corrélation de tous les messages envoyés entre deux points de terminaison. L'*instanciation* fait référence au contrôle de la durée de vie des objets de service définis par l'utilisateur et de leurs objets <xref:System.ServiceModel.InstanceContext> connexes. La*concurrence* est le terme donné au contrôle du nombre des threads qui s'exécutent simultanément dans un <xref:System.ServiceModel.InstanceContext> .  
  
 Cette rubrique décrit ces paramètres, comment les utiliser et les diverses interactions entre eux.  
  
## <a name="sessions"></a>Sessions  
 Lorsqu'un contrat de service affecte <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> à la propriété <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>, ce contrat indique que tous les appels (c'est-à-dire, les échanges de messages sous-jacents qui prennent en charge les appels) doivent faire partie de la même conversation. Si un contrat spécifie qu'il autorise les sessions mais n'en requiert pas, les clients peuvent se connecter et établir ou non une session. Si la session se termine et qu'un message est envoyé sur le même canal basé sur session, une exception est levée.  
  
 Les sessions WCF ont les principales caractéristiques conceptuelles suivantes :  
  
- Elles sont explicitement initialisées et terminées par l'application appelante.  
  
- Les messages remis pendant une session sont traités dans l'ordre dans lequel ils sont reçus.  
  
- Les sessions corrèlent un groupe de messages dans une conversation. La signification de cette corrélation est une abstraction. Par exemple, un canal basé sur session peut corréler des messages sur la base d'une connexion réseau partagée, pendant qu'un autre canal basé sur session corrèle des messages sur la base d'une balise partagée dans le corps du message. Les fonctionnalités qui peuvent être dérivées de la session varient en fonction de la nature de la corrélation.  
  
- Il n’y a pas de magasin de données générale associé à une session WCF.  
  
 Si vous connaissez <xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType> la classe dans ASP.NET applications et la fonctionnalité qu’il fournit, vous remarquerez peut-être les différences suivantes entre ce type de session et les sessions WCF :  
  
- ASP.NET sessions sont toujours initiées par le serveur.  
  
- ASP.NET sessions sont implicitement désorganisées.  
  
- ASP.NET sessions fournissent un mécanisme général de stockage des données entre les demandes.  
  
 Les applications clientes et de service interagissent avec les sessions de manière différente. Les applications clientes initialisent des sessions, puis reçoivent et traitent les messages envoyés dans la session. Les applications de service peuvent utiliser des sessions comme point d'extensibilité pour ajouter un comportement supplémentaire. Pour ce faire, utilisez directement <xref:System.ServiceModel.InstanceContext> ou implémentez un fournisseur de contexte d'instance personnalisé.  
  
## <a name="instancing"></a>instanciation  
 Le comportement d'instanciation (défini à l'aide de propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> ) contrôle la façon dont le <xref:System.ServiceModel.InstanceContext> est créé en réponse à des messages entrants. Par défaut, chaque <xref:System.ServiceModel.InstanceContext> est associé à un objet de service défini par l'utilisateur ; par conséquent (dans le cas par défaut), la définition de la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> contrôle également l'instanciation des objets de service définis par l'utilisateur. L'énumération <xref:System.ServiceModel.InstanceContextMode> définit les modes d'instanciation.  
  
 Les modes d'instanciation disponibles sont les suivants :  
  
- <xref:System.ServiceModel.InstanceContextMode.PerCall>: un nouveau <xref:System.ServiceModel.InstanceContext> (et par conséquent un objet de service) est créé pour chaque demande du client.  
  
- <xref:System.ServiceModel.InstanceContextMode.PerSession>: un nouveau <xref:System.ServiceModel.InstanceContext> (et par conséquent un objet de service) est créé pour chaque nouvelle session cliente et est conservé pendant toute la durée de vie de celle-ci (cela requiert une liaison capable de prendre les sessions en charge).  
  
- <xref:System.ServiceModel.InstanceContextMode.Single>: un <xref:System.ServiceModel.InstanceContext> unique (et par conséquent un objet de service) gère toutes les demandes du client pendant toute la durée de vie de l'application.  
  
 L'exemple de code suivant présente la valeur <xref:System.ServiceModel.InstanceContextMode> par défaut, <xref:System.ServiceModel.InstanceContextMode.PerSession> étant explicitement défini sur une classe de service.  
  
```csharp  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorInstance
{
    ...  
}  
```  
  
 Et pendant que la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> contrôle la fréquence à laquelle <xref:System.ServiceModel.InstanceContext> est diffusé, les propriétés <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> et <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> contrôlent le moment auquel l'objet de service est diffusé.  
  
### <a name="well-known-singleton-services"></a>Services singleton connus  
 L'une des variantes des objets de service d'instance unique s'avère parfois utile : vous pouvez créer un objet de service vous-même, puis créer l'hôte de service à l'aide de cet objet. Pour ce faire, vous devez également affecter <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> à la propriété <xref:System.ServiceModel.InstanceContextMode.Single> , sans quoi une exception est levée lorsque l'hôte de service est ouvert.  
  
 Utilisez le constructeur <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29> pour créer un service de ce type. Il fournit une alternative à l'implémentation d'un <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> personnalisé lorsque vous souhaitez fournir une instance d'objet spécifique qui sera utilisée par un service singleton. Vous pouvez utiliser cette surcharge lorsque votre type de mise en œuvre de service est difficile à construire (par exemple, s’il ne met pas en œuvre un constructeur public sans paramètres).  
  
 Notez que lorsqu’un objet est fourni à ce constructeur, certaines fonctionnalités liées à la Windows Communication Foundation (WCF) instancing comportement fonctionnent différemment. Par exemple, l'appel de <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> n'a aucun effet lorsqu'une instance d'objet singleton est fournie. De même, tout autre mécanisme de libération d'instance est ignoré. <xref:System.ServiceModel.ServiceHost> se comporte systématiquement comme si la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> avait la valeur <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> pour toutes les opérations.  
  
### <a name="sharing-instancecontext-objects"></a>Partage d'objets InstanceContext  
 Vous pouvez également contrôler l'appel ou le canal de session associé à tel ou tel objet <xref:System.ServiceModel.InstanceContext> en effectuant vous-même l'association.  
  
## <a name="concurrency"></a>Accès concurrentiel  
 La concurrence est le contrôle du nombre de threads actifs simultanément dans un <xref:System.ServiceModel.InstanceContext> . Cela est contrôlé en utilisant <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> avec l'énumération <xref:System.ServiceModel.ConcurrencyMode> .  
  
 Les trois modes de concurrence disponibles sont les suivants :  
  
- <xref:System.ServiceModel.ConcurrencyMode.Single>: chaque contexte d'instance est autorisé à avoir au maximum un seul thread à la fois qui traite des messages dans le contexte d'instance. Les autres threads qui souhaitent utiliser le même contexte d'instance doivent se bloquer jusqu'à ce que le thread d'origine quitte le contexte d'instance.  
  
- <xref:System.ServiceModel.ConcurrencyMode.Multiple>: chaque instance de service peut avoir plusieurs threads qui traitent des messages simultanément. Pour utiliser ce mode, l'implémentation de service doit être « thread-safe ».  
  
- <xref:System.ServiceModel.ConcurrencyMode.Reentrant>: chaque instance de service traite un seul message à la fois, mais accepte les appels réentrants. Le service n’accepte ces appels que lorsqu’il appelle via un objet client WCF.  
  
> [!NOTE]
> Le fonctionnement et le développement de code utilisant plusieurs threads en toute sécurité peuvent s'avérer difficile à écrire. Avant d'utiliser les valeurs <xref:System.ServiceModel.ConcurrencyMode.Multiple> ou <xref:System.ServiceModel.ConcurrencyMode.Reentrant> , assurez-vous que votre service est correctement conçu pour ces modes. Pour plus d’informations, consultez <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>.  
  
 L'utilisation de l'accès concurrentiel est associée au mode d'instanciation. Dans <xref:System.ServiceModel.InstanceContextMode.PerCall> l’instancing, la concurrence n’est pas pertinente, <xref:System.ServiceModel.InstanceContext> parce que chaque message est traité <xref:System.ServiceModel.InstanceContext>par un nouveau et, par conséquent, jamais plus d’un thread est actif dans le .  
  
 L'exemple de code suivant présente l'affectation de <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> à la propriété <xref:System.ServiceModel.ConcurrencyMode.Multiple>.  
  
```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]
public class CalculatorService : ICalculatorConcurrency
{
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>Sessions interagissant avec les paramètres InstanceContext  
 Les sessions et <xref:System.ServiceModel.InstanceContext> interagissent en fonction de la combinaison de la valeur de l'énumération <xref:System.ServiceModel.SessionMode> dans un contrat et la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> sur l'implémentation de service, qui contrôle l'association entre les canaux et des objets de service spécifiques.  
  
 Le tableau suivant présente le résultat d'un canal entrant prenant ou non en charge les sessions en fonction de la combinaison des valeurs de la propriété <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> et de la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> d'un service.  
  
|Valeur InstanceContextMode|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|- Comportement avec canal session: <xref:System.ServiceModel.InstanceContext> Une session et pour chaque appel.<br />- Comportement avec canal sans session: Une exception est lancée.|- Comportement avec canal session: <xref:System.ServiceModel.InstanceContext> Une session et pour chaque appel.<br />- Comportement avec canal <xref:System.ServiceModel.InstanceContext> sans session: Un pour chaque appel.|- Comportement avec le canal de session : Une exception est lancée.<br />- Comportement avec canal <xref:System.ServiceModel.InstanceContext> sans session: Un pour chaque appel.|  
|PerSession|- Comportement avec le canal <xref:System.ServiceModel.InstanceContext> sessionnel : Une session et pour chaque canal.<br />- Comportement avec canal sans session: Une exception est lancée.|- Comportement avec le canal <xref:System.ServiceModel.InstanceContext> sessionnel : Une session et pour chaque canal.<br />- Comportement avec canal <xref:System.ServiceModel.InstanceContext> sans session: Un pour chaque appel.|- Comportement avec le canal de session : Une exception est lancée.<br />- Comportement avec canal <xref:System.ServiceModel.InstanceContext> sans session: Un pour chaque appel.|  
|Unique|- Comportement avec canal session: <xref:System.ServiceModel.InstanceContext> Une session et une pour tous les appels.<br />- Comportement avec canal sans session: Une exception est lancée.|- Comportement avec le canal <xref:System.ServiceModel.InstanceContext> de session : Une session et pour le singleton créé ou spécifié par l’utilisateur.<br />- Comportement avec le <xref:System.ServiceModel.InstanceContext> canal sans session: Un singleton créé ou spécifié par l’utilisateur.|- Comportement avec le canal de session : Une exception est lancée.<br />- Comportement avec le <xref:System.ServiceModel.InstanceContext> canal sans session: Un pour chaque singleton créé ou pour le singleton spécifié par l’utilisateur.|  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de sessions](../../../../docs/framework/wcf/using-sessions.md)
- [Comment : créer un service qui requiert des sessions](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [Guide pratique pour contrôler l’instanciation de service](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [Concurrence](../../../../docs/framework/wcf/samples/concurrency.md)
- [instanciation](../../../../docs/framework/wcf/samples/instancing.md)
- [session](../../../../docs/framework/wcf/samples/session.md)
