---
title: Création de liaisons définies par l’utilisateur
ms.date: 03/30/2017
helpviewer_keywords:
- user-defined bindings [WCF]
ms.assetid: c4960675-d701-4bc9-b400-36a752fdd08b
ms.openlocfilehash: e1e776a42ca63e4b862e307cbcae1bab2847d0ca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587296"
---
# <a name="creating-user-defined-bindings"></a>Création de liaisons définies par l’utilisateur
Il existe plusieurs méthodes pour créer des liaisons non fournies par le système :  
  
- Créez une liaison personnalisée basés sur la classe <xref:System.ServiceModel.Channels.CustomBinding> qui est un conteneur que vous remplissez avec les éléments de liaison. La liaison personnalisée est ensuite ajoutée à un point de terminaison de service. Vous pouvez créer la liaison personnalisée soit par programmation soit dans un fichier de configuration d’application. Pour utiliser un élément de liaison d’un fichier de configuration d’application, l’élément doit étendre les liaisons personnalisées <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>. Pour plus d’informations sur les liaisons personnalisées, consultez [liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md) et <xref:System.ServiceModel.Channels.CustomBinding>.  
  
- Vous pouvez créer une classe qui dérive d’une liaison standard. Par exemple, vous pouvez dériver une classe de <xref:System.ServiceModel.WSHttpBinding> et remplacer la méthode <xref:System.ServiceModel.Channels.CustomBinding.CreateBindingElements%2A> pour obtenir les éléments de liaison et insérer un élément de liaison personnalisé ou établir une valeur particulière pour la sécurité.  
  
- Vous pouvez créer un nouveau type <xref:System.ServiceModel.Channels.Binding> pour contrôler complètement l’ensemble de l’implémentation de la liaison.  
  
## <a name="the-order-of-binding-elements"></a>Ordre des éléments de liaison  
 Chaque élément de liaison représente une étape de traitement lors de l’envoi ou de la réception des messages. Pendant l’exécution, les éléments de liaison créent les canaux et les écouteurs nécessaires pour générer des piles de canaux entrants et sortants.  
  
 Il existe trois principaux types d’éléments de liaison : Protocole de liaison des éléments, encodage des éléments de liaison et des éléments de liaison de Transport.  
  
 Éléments de liaison de protocole – Ces éléments représentent des étapes de traitement de niveau supérieur qui agissent sur les messages. Les canaux et les écouteurs créés par ces éléments de liaison peuvent ajouter, supprimer ou modifier le contenu du message. Une liaison donnée peut avoir un nombre arbitraire d’éléments de liaison de protocole, chacun héritant d’un objet <xref:System.ServiceModel.Channels.BindingElement>. Windows Communication Foundation (WCF) inclut plusieurs éléments de liaison de protocole, y compris le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> et <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.  
  
 Élément de liaison d’encodage – Ces éléments représentent des transformations entre un message et un encodage prêt pour la transmission sur le fil. Les liaisons WCF standard incluent exactement un élément de liaison d’encodage. Des exemples d’éléments de liaison d’encodage incluent <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> et <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>. Si un élément de liaison d'encodage n'est pas spécifié pour une liaison, un encodage par défaut est utilisé. La valeur par défaut est Text lorsque le transport est HTTP, sinon la valeur est Binary.  
  
 Élément de liaison de transport – Ces éléments représentent la transmission d’un message d’encodage sur un protocole de transport. Les liaisons WCF standard incluent exactement un élément de liaison de transport, qui hérite de <xref:System.ServiceModel.Channels.TransportBindingElement>. Des exemples d’éléments de liaison de transport incluent <xref:System.ServiceModel.Channels.TcpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpTransportBindingElement> et <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>.  
  
 Lors de la création de nouvelles liaisons, l’ordre des éléments de liaison ajoutés est important. Ajoutez toujours les éléments de liaison dans l'ordre suivant :  
  
|Couche|Options|Obligatoire|  
|-----------|-------------|--------------|  
|Flux de transaction|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement?displayProperty=nameWithType>|Non|  
|Fiabilité|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType>|Non|  
|Sécurité|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|Non|  
|Duplex composite|<xref:System.ServiceModel.Channels.CompositeDuplexBindingElement?displayProperty=nameWithType>|Non|  
|Encodage|Text, Binary, MTOM, Custom|Oui*|  
|Transport|TCP, Named Pipes, HTTP, HTTPS, MSMQ, Custom|Oui|  
  
 *, Car un encodage est requis pour chaque liaison, si aucun encodage n’est pas spécifié, WCF ajoute un codage par défaut. La valeur par défaut est Text/XML pour les transports HTTP et HTTPS, et Binary pour les autres transports.  
  
## <a name="creating-a-new-binding-element"></a>Création d’un nouvel élément de liaison  
 Outre les types dérivés de <xref:System.ServiceModel.Channels.BindingElement> qui sont fournies par WCF, vous pouvez créer vos propres éléments de liaison. Vous pouvez personnaliser la façon dont la pile des liaisons est créée et les composants qu'elle inclut en créant votre propre <xref:System.ServiceModel.Channels.BindingElement> qui peut être composé dans la pile avec les autres types fournis par le système.  
  
 Par exemple, si vous implémentez un `LoggingBindingElement` qui fournit la capacité d'enregistrer le message dans une base de données, vous devez le placer au-dessus d'un canal de transport dans la pile des canaux. Dans ce cas, l'application crée une liaison personnalisée qui compose le `LoggingBindingElement` avec `TcpTransportBindingElement`, comme dans l'exemple suivant.  
  
```csharp  
Binding customBinding = new CustomBinding(  
  new LoggingBindingElement(),   
  new TcpTransportBindingElement()  
);  
```  
  
 La façon dont vous écrivez votre nouvel élément de liaison dépend de ses fonctionnalités exactes. Un des exemples, [Transport : UDP](../../../../docs/framework/wcf/samples/transport-udp.md), fournit une description détaillée de l’implémentation d’un type d’élément de liaison.  
  
## <a name="creating-a-new-binding"></a>Création d’une nouvelle liaison  
 Un élément de liaison créé par l’utilisateur peut être utilisé de deux façons. La section précédente illustre la première méthode : via une liaison personnalisée. Une liaison personnalisée permet à l’utilisateur de créer sa propre la liaison basée sur un jeu arbitraire d’éléments de liaison, y compris ceux créés par l’utilisateur.  
  
 Si vous utilisez la liaison dans plusieurs applications, créez votre propre liaison et étendez <xref:System.ServiceModel.Channels.Binding>. Cela évite de créer manuellement une liaison personnalisée à chaque fois que vous souhaitez l’utiliser. Une liaison définie par l’utilisateur vous permet de définir le comportement de la liaison et d’inclure des éléments de liaison définis par l’utilisateur. Et il est *préconçue*: vous n’êtes pas obligé de reconstruire la liaison chaque fois que vous l’utilisez.  
  
 Au minimum, une liaison définie par l’utilisateur doit implémenter la méthode <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> et la propriété <xref:System.ServiceModel.Channels.Binding.Scheme%2A>.  
  
 La méthode <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> retourne un nouveau <xref:System.ServiceModel.Channels.BindingElementCollection> qui contient les éléments de liaison pour la liaison. La collection est ordonnée et doit contenir en premier les éléments de liaison de protocole, suivis par l'élément de liaison d'encodage, suivi par l'élément de liaison de transport. Lorsque vous utilisez les éléments de liaison fournie par le système WCF, vous devez suivre l’élément de liaison spécifiés dans des règles de classement [liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md). Cette collection ne doit jamais référencer des objets référencés dans la classe de liaison définie par l’utilisateur ; par conséquent, les auteurs de la liaison doivent retourner un `Clone()` de <xref:System.ServiceModel.Channels.BindingElementCollection> sur chaque appel à <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A>.  
  
 La propriété <xref:System.ServiceModel.Channels.Binding.Scheme%2A> représente le modèle URI pour le protocole de transport utilisé sur la liaison. Par exemple, le *WSHttpBinding* et *NetTcpBinding* retournent « http » et « net.tcp » à partir de leurs détenteurs respectifs <xref:System.ServiceModel.Channels.Binding.Scheme%2A> propriétés.  
  
 Pour une liste exhaustive des méthodes et des propriétés optionnelles relatives aux liaisons définies par l'utilisateur, consultez <xref:System.ServiceModel.Channels.Binding>.  
  
### <a name="example"></a>Exemple  
 Cet exemple implémente la liaison de profil dans `SampleProfileUdpBinding`, lequel dérive de <xref:System.ServiceModel.Channels.Binding>. Le `SampleProfileUdpBinding` contient jusqu'à quatre éléments de liaison : un utilisateur créé `UdpTransportBindingElement`; et trois fournie par le système : `TextMessageEncodingBindingElement`, `CompositeDuplexBindingElement`, et `ReliableSessionBindingElement`.  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
## <a name="security-restrictions-with-duplex-contracts"></a>Restrictions de sécurité avec les contrats duplex  
 Tous les éléments de liaison ne sont pas compatibles les uns avec les autres. Notamment, il existe des restrictions concernant les éléments de liaison de sécurité en cas d'utilisation avec les contrats duplex.  
  
### <a name="one-shot-security"></a>Sécurité « one-shot »  
 Vous pouvez implémenter une sécurité « One-Shot », où toutes les informations d’identification de sécurité nécessaires sont envoyées dans un seul message, en définissant le `negotiateServiceCredential` attribut de la \<message > élément de configuration `false`.  
  
 L'authentification « one-shot » ne fonctionne pas avec les contrats duplex.  
  
 Pour les contrats de demande-réponse, l’authentification « one-shot » fonctionne uniquement si la pile des liaisons au-dessous de l’élément de liaison de sécurité prend en charge la création d’instances <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel>.  
  
 Pour les contrats unidirectionnels, l’authentification « one-shot » fonctionne si la pile des liaisons au-dessous de l’élément de liaison de sécurité prend en charge la création d’instances <xref:System.ServiceModel.Channels.IRequestChannel>, <xref:System.ServiceModel.Channels.IRequestSessionChannel>, <xref:System.ServiceModel.Channels.IOutputChannel> ou <xref:System.ServiceModel.Channels.IOutputSessionChannel>.  
  
### <a name="cookie-mode-security-context-tokens"></a>Jetons de contexte de sécurité en mode Cookie  
 Les jetons de contexte de sécurité en mode Cookie ne peuvent pas être utilisés avec les contrats duplex.  
  
 Pour les contrats de demande-réponse, les jetons de contexte de sécurité en mode Cookie fonctionnent uniquement si la pile des liaisons au-dessous de l'élément de liaison de sécurité prend en charge la création d'instances <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel>.  
  
 Pour les contrats unidirectionnels, les jetons de contexte de sécurité en mode Cookie fonctionnent si la pile des liaisons au-dessous de l'élément de liaison de sécurité prend en charge la création d'instances <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel>.  
  
### <a name="session-mode-security-context-tokens"></a>Jetons de contexte de sécurité en mode session  
 Le jeton de contexte de sécurité en mode session fonctionne pour les contrats duplex si la pile des liaisons au-dessous de l’élément de liaison de sécurité prend en charge la création d’instances <xref:System.ServiceModel.Channels.IDuplexChannel> ou <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
 Le jeton de contexte de sécurité en mode session fonctionne pour les contrats de demande-réponse si la pile des liaisons au-dessous de l'élément de liaison de sécurité prend en charge la création d'instances <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel>.  
  
 Le jeton de contexte de sécurité en mode session fonctionne pour les contrats unidirectionnels si la pile des liaisons au-dessous de l’élément de liaison de sécurité prend en charge la création d’instances <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, <xref:System.ServiceModel.Channels.IRequestChannel> ou <xref:System.ServiceModel.Channels.IRequestSessionChannel>.  
  
## <a name="deriving-from-a-standard-binding"></a>Dérivation à partir d’une liaison standard  
 Au lieu de créer une classe de liaison totalement nouvelle, il est possible d’étendre l’une des liaisons fournies par le système existantes. Comme dans le cas précédent, vous devez substituer la méthode <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> et la propriété <xref:System.ServiceModel.Channels.Binding.Scheme%2A>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.Binding>
- [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)
