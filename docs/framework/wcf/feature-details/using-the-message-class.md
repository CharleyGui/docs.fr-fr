---
title: Utilisation de la classe Message
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d62bfb-2aa3-4170-b6f8-c93d3afdbbed
ms.openlocfilehash: 142578ef76a70fed27dc0137378b59e228cd25c9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585647"
---
# <a name="using-the-message-class"></a>Utilisation de la classe Message
La <xref:System.ServiceModel.Channels.Message> classe est fondamentale pour Windows Communication Foundation (WCF). Toute la communication entre les clients et les services a pour résultat l'envoi et la réception d'instances <xref:System.ServiceModel.Channels.Message>.  
  
 Aucune interaction directe n'a généralement lieu avec la classe <xref:System.ServiceModel.Channels.Message>. Au lieu de cela, les constructions de modèle de service WCF, telles que les contrats de données, les contrats de message et les contrats d’opération, sont utilisées pour décrire les messages entrants et sortants. Toutefois, dans certains scénarios avancés, vous pouvez programmer directement à l'aide de la classe <xref:System.ServiceModel.Channels.Message>. Par exemple, il est possible que vous souhaitiez utiliser la classe <xref:System.ServiceModel.Channels.Message> :  
  
- Lorsque vous avez besoin d’une autre façon de créer le contenu des messages sortants (par exemple, créer un message directement à partir d’un fichier sur le disque) au lieu de sérialiser des objets .NET Framework.  
  
- Lorsque vous avez besoin d’une autre façon d’utiliser le contenu des messages entrants (par exemple, lorsque vous souhaitez appliquer une transformation XSLT au contenu XML brut) au lieu de désérialiser dans .NET Framework objets.  
  
- Lorsque vous devez gérer des messages d'une manière générale indépendamment du contenu de message (par exemple, lors du routage ou du transfert de messages lors de la création d'un routeur, d'un équilibreur de charge ou d'un système de publication-souscription).  
  
 Avant d’utiliser la <xref:System.ServiceModel.Channels.Message> classe, familiarisez-vous avec l’architecture de transfert de données WCF dans [transfert de données vue d’ensemble](data-transfer-architectural-overview.md)de l’architecture.  
  
 Un <xref:System.ServiceModel.Channels.Message> est un conteneur de données à usage général, mais sa conception suit étroitement celle d'un message dans le protocole SOAP. Tout comme dans SOAP, un message possède à la fois un en-tête et un corps de message. Le corps du message contient les données de charge utile, tandis que les en-têtes contiennent des conteneurs de données nommés supplémentaires. Les règles de lecture et d'écriture du corps et des en-têtes sont différentes ; par exemple, les en-têtes sont toujours mis en mémoire tampon et sont accessibles dans un ordre quelconque et un nombre de fois quelconque, alors que le corps peut être lu une seule fois et peut être transmis en continu. Normalement, lors de l'utilisation de SOAP, le corps du message est mappé au corps SOAP et les en-têtes de messages sont mappés aux en-têtes SOAP.  
  
## <a name="using-the-message-class-in-operations"></a>Utilisation de la classe Message dans des opérations  
 Vous pouvez utiliser la classe <xref:System.ServiceModel.Channels.Message> comme paramètre d'entrée d'une opération, valeur de retour d'une opération ou les deux. Si <xref:System.ServiceModel.Channels.Message> est utilisé dans une opération, les restrictions suivantes s'appliquent :  
  
- L'opération ne peut pas avoir de paramètres `out` ou `ref`.  
  
- Il ne peut pas y avoir plusieurs paramètres `input`. Si le paramètre est présent, il doit s'agir de Message ou d'un type de contrat de message.  
  
- Le type de retour doit être `void`, `Message` ou un type de contrat de message.  
  
 L'exemple de code suivant contient un contrat d'opération valide.  
  
 [!code-csharp[C_UsingTheMessageClass#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#1)]
 [!code-vb[C_UsingTheMessageClass#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#1)]  
  
## <a name="creating-basic-messages"></a>Création de messages simples  
 La classe <xref:System.ServiceModel.Channels.Message> fournit des méthodes de fabrique `CreateMessage` statiques que vous pouvez utiliser pour créer des messages simples.  
  
 Toutes les surcharges `CreateMessage` prennent un paramètre de version de type <xref:System.ServiceModel.Channels.MessageVersion> qui indique les versions SOAP et WS-Addressing à utiliser pour le message. Si vous souhaitez utiliser les mêmes versions de protocole que le message entrant, vous pouvez utiliser la propriété <xref:System.ServiceModel.OperationContext.IncomingMessageVersion%2A> sur l'instance <xref:System.ServiceModel.OperationContext> obtenue à partir de la propriété <xref:System.ServiceModel.OperationContext.Current%2A>. La plupart des surcharges `CreateMessage` ont également un paramètre de chaîne qui indique l'action SOAP à utiliser pour le message. La version peut avoir la valeur `None` pour désactiver la génération d'enveloppe SOAP ; le message est uniquement composé du corps.  
  
## <a name="creating-messages-from-objects"></a>Création de messages à partir d'objets  
 La surcharge `CreateMessage` la plus simple qui prend uniquement une version et une action crée un message dont le corps est vide. Une autre surcharge prend un paramètre <xref:System.Object> supplémentaire ; cela crée un message dont le corps est la représentation sérialisée de l'objet donné. Utilisez le <xref:System.Runtime.Serialization.DataContractSerializer> avec les paramètres par défaut pour la sérialisation. Si vous souhaitez utiliser un sérialiseur différent ou si vous souhaitez configurer le `DataContractSerializer` différemment, utilisez la surcharge `CreateMessage` qui prend également un paramètre `XmlObjectSerializer`.  
  
 Par exemple, pour retourner un objet dans un message, vous pouvez utiliser le code suivant.  
  
 [!code-csharp[C_UsingTheMessageClass#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#2)]
 [!code-vb[C_UsingTheMessageClass#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#2)]  
  
## <a name="creating-messages-from-xml-readers"></a>Création de messages à partir de lecteurs XML  
 Il existe des surcharges `CreateMessage` qui prennent un <xref:System.Xml.XmlReader> ou un <xref:System.Xml.XmlDictionaryReader> pour le corps au lieu d'un objet. Dans ce cas, le corps du message contient le XML résultant de la lecture du lecteur XML passé. Par exemple, le code suivant retourne un message dont le contenu du corps est lu à partir d'un fichier XML.  
  
 [!code-csharp[C_UsingTheMessageClass#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#3)]
 [!code-vb[C_UsingTheMessageClass#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#3)]  
  
 De plus, il existe des surcharges `CreateMessage` qui prennent un <xref:System.Xml.XmlReader> ou un <xref:System.Xml.XmlDictionaryReader> qui représente le message entier, et non simplement le corps. Ces surcharges prennent également un paramètre `maxSizeOfHeaders` entier. Les en-têtes sont toujours mis en mémoire tampon dès que le message est créé, et ce paramètre limite la quantité de mise en mémoire tampon qui a lieu. Il est important d'affecter à ce paramètre une valeur sûre si le XML provient d'une source non fiable, afin d'atténuer le risque d'attaque par déni de service. Les versions SOAP et WS-Addressing du message que le lecteur XML représente doivent correspondre aux versions indiquées à l'aide du paramètre de version.  
  
## <a name="creating-messages-with-bodywriter"></a>Création de messages avec BodyWriter  
 Une surcharge `CreateMessage` prend une instance `BodyWriter` pour décrire le corps du message. Un `BodyWriter` est une classe abstraite qui peut être dérivée afin de personnaliser la façon dont les corps de message sont créés. Vous pouvez créer votre propre classe dérivée `BodyWriter` pour décrire les corps de message de manière personnalisée. Vous devez substituer la méthode `BodyWriter.OnWriteBodyContents` qui prend un <xref:System.Xml.XmlDictionaryWriter> ; cette méthode est responsable de l'écriture du corps.  
  
 Les enregistreurs de corps peuvent être mis en mémoire tampon ou transmis en continu. Les enregistreurs de corps mis en mémoire tampon peuvent écrire leur contenu un nombre de fois quelconque, tandis que les enregistreurs transmis en continu peuvent écrire leur contenu une seule fois. La propriété `IsBuffered` indique si un enregistreur de corps est mis en mémoire tampon ou non. Vous pouvez définir cette propriété pour votre enregistreur de corps en appelant le constructeur `BodyWriter` protégé qui prend un paramètre booléen `isBuffered`. Les enregistreurs de corps prennent en charge la création d'un enregistreur de corps mis en mémoire tampon à partir d'un enregistreur de corps non mis en mémoire tampon. Vous pouvez substituer la méthode `OnCreateBufferedCopy` pour personnaliser ce processus. Par défaut, un tampon en mémoire qui contient le XML retourné par `OnWriteBodyContents` est utilisé. `OnCreateBufferedCopy` prend un paramètre entier `maxBufferSize` ; si vous substituez cette méthode, vous ne devez pas créer de mémoire tampon de taille supérieure à cette taille maximale.  
  
 La classe `BodyWriter` fournit les méthodes `WriteBodyContents` et `CreateBufferedCopy`, qui sont essentiellement des wrappers minces autour des méthodes `OnWriteBodyContents` et `OnCreateBufferedCopy`, respectivement. Ces méthodes effectuent un contrôle d'état afin de s'assurer que les utilisateurs n'accèdent pas à un enregistreur de corps non mis en mémoire tampon plus d'une fois. Ces méthodes sont appelées directement uniquement lors de la création de classes dérivées `Message` personnalisées selon les `BodyWriters`.  
  
## <a name="creating-fault-messages"></a>Création de messages d'erreur  
 Vous pouvez utiliser certaines surcharges `CreateMessage` pour créer des messages d'erreur SOAP. Le plus simple d'entre eux prend un objet <xref:System.ServiceModel.Channels.MessageFault> qui décrit l'erreur. D'autres surcharges sont fournies à des fins de commodité. La première de ces surcharges prend un `FaultCode` et une chaîne de raison et crée un `MessageFault` à l'aide de `MessageFault.CreateFault` avec ces informations. L'autre surcharge prend un objet de détail et le passe également à `CreateFault` avec le code d'erreur et la raison. Par exemple, l'opération suivante retourne une erreur.  
  
 [!code-csharp[C_UsingTheMessageClass#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#4)]
 [!code-vb[C_UsingTheMessageClass#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#4)]  
  
## <a name="extracting-message-body-data"></a>Extraction de données de corps de message  
 La classe `Message` prend en charge plusieurs façons d'extraire des informations de son corps. Celles-ci peuvent être classifiées en plusieurs catégories :  
  
- Faire en sorte que l'intégralité du corps de message soit écrit immédiatement dans un enregistreur XML. C’est ce que l’on appelle *écrire un message*.  
  
- Placer un lecteur XML sur le corps du message. Cela vous permet d'accéder ultérieurement au corps du message élément par élément selon vos besoins. C’est ce que l’on appelle *la lecture d’un message*.  
  
- L'intégralité du message, y compris son corps, peut être copiée vers un tampon en mémoire du type <xref:System.ServiceModel.Channels.MessageBuffer>. On parle alors de *copie d’un message*.  
  
 Vous pouvez accéder au corps d'un `Message` une seule fois, indépendamment du mode d'accès. Un objet de message possède une propriété `State`, qui a initialement la valeur Créé. Les trois méthodes d'accès décrites dans la liste précédente définissent respectivement l'état à Écrit, Lu et Copié. En outre, une méthode `Close` peut définir l'état à Fermé lorsque le contenu du corps de message n'est plus nécessaire. Le corps du message est accessible uniquement à l'état Créé et il n'existe aucun moyen de revenir à l'état Créé après que l'état a changé.  
  
## <a name="writing-messages"></a>Écriture de messages  
 La méthode <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> écrit le contenu du corps d'une instance `Message` donnée dans un enregistreur XML donné. La <xref:System.ServiceModel.Channels.Message.WriteBody%2A> méthode fait de même, mais elle englobe le contenu du corps dans l’élément wrapper approprié (par exemple, <`soap:body`>). Pour finir, <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> écrit le message entier, y compris l'enveloppe SOAP et les en-têtes. Si SOAP est désactivé ( <xref:System.ServiceModel.Channels.Message.Version> a <xref:System.ServiceModel.Channels.MessageVersion.None?displayProperty=nameWithType> la valeur), les trois méthodes font la même chose : elles écrivent le contenu du corps du message.  
  
 Par exemple, le code suivant écrit le corps d'un message entrant dans un fichier.  
  
 [!code-csharp[C_UsingTheMessageClass#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#5)]
 [!code-vb[C_UsingTheMessageClass#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#5)]  
  
 Deux méthodes d’assistance supplémentaires écrivent certaines étiquettes d’élément de début SOAP. Ces méthodes n'accèdent pas au corps du message ; elles ne modifient donc pas l'état du message. notamment :  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartBody%2A> écrit l'élément de corps de début, par exemple `<soap:Body>`.  
  
- <xref:System.ServiceModel.Channels.Message.WriteStartEnvelope%2A> écrit l'élément d'enveloppe de début, par exemple `<soap:Envelope>`.  
  
 Pour écrire les balises d'élément de fin correspondantes, appelez `WriteEndElement` sur l'enregistreur XML correspondant. Ces méthodes sont rarement appelées directement.  
  
## <a name="reading-messages"></a>Lecture de messages  
 La principale manière de lire un corps de message consiste à appeler <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>. Vous récupérez un <xref:System.Xml.XmlDictionaryReader> que vous pouvez utiliser pour lire le corps du message. Notez que le <xref:System.ServiceModel.Channels.Message> bascule à l'état Lu dès que <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> est appelée, et non lorsque vous utilisez le lecteur XML retourné.  
  
 La méthode <xref:System.ServiceModel.Channels.Message.GetBody%2A> vous permet également d'accéder au corps du message en tant qu'objet typé. En interne, cette méthode utilise `GetReaderAtBodyContents` et fait donc également basculer le message à l'état <xref:System.ServiceModel.Channels.MessageState.Read> (consultez la propriété <xref:System.ServiceModel.Channels.Message.State%2A>).  
  
 Il est conseillé de vérifier la propriété <xref:System.ServiceModel.Channels.Message.IsEmpty%2A>, auquel cas le corps du message est vide et <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> lève une <xref:System.InvalidOperationException>. En outre, s'il s'agit d'un message reçu (par exemple, la réponse), vous souhaiterez peut-être également vérifier <xref:System.ServiceModel.Channels.Message.IsFault%2A>, qui indique si le message contient une erreur.  
  
 La surcharge la plus simple de <xref:System.ServiceModel.Channels.Message.GetBody%2A> désérialise le corps du message dans une instance d'un type (indiqué par le paramètre générique) à l'aide d'un <xref:System.Runtime.Serialization.DataContractSerializer> configuré avec les paramètres par défaut et avec le quota <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> désactivé. Si vous souhaitez utiliser un moteur de sérialisation différent ou configurer le `DataContractSerializer` de manière personnalisée, utilisez la surcharge <xref:System.ServiceModel.Channels.Message.GetBody%2A> qui prend un <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 Par exemple, le code suivant extrait des données d'un corps de message qui contient un objet `Person` sérialisé et imprime le nom de la personne.  
  
 [!code-csharp[C_UsingTheMessageClass#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#6)]
 [!code-vb[C_UsingTheMessageClass#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#6)]  
  
## <a name="copying-a-message-into-a-buffer"></a>Copie d'un message dans une mémoire tampon  
 Il est parfois nécessaire d'accéder au corps de message à plusieurs reprises, par exemple pour transférer le même message vers plusieurs destinations dans le cadre d'un système éditeur-abonné. Dans ce cas, il est nécessaire de mettre en mémoire tampon l'intégralité du message (y compris le corps). Vous pouvez pour cela appeler <xref:System.ServiceModel.Channels.Message.CreateBufferedCopy%28System.Int32%29>. Cette méthode prend un paramètre entier qui représente la taille maximale de la mémoire tampon et crée une mémoire tampon inférieure à cette taille. Il est important d'affecter à ce paramètre une valeur sûre si le message provient d'une source non fiable.  
  
 Le tampon est retourné en tant qu'instance <xref:System.ServiceModel.Channels.MessageBuffer>. Vous pouvez accéder aux données de la mémoire tampon de plusieurs manières. La principale consiste à appeler <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> pour créer des instances `Message` à partir de la mémoire tampon.  
  
 Une autre manière d'accéder aux données dans la mémoire tampon consiste à implémenter l'interface <xref:System.Xml.XPath.IXPathNavigable> que la classe <xref:System.ServiceModel.Channels.MessageBuffer> implémente pour accéder directement au XML sous-jacent. Certaines surcharges <xref:System.ServiceModel.Channels.MessageBuffer.CreateNavigator%2A> vous permettent de créer des navigateurs <xref:System.Xml.XPath> protégés par un quota de nœud, qui limite le nombre de nœuds XML qui peuvent être visités. Cela aide à empêcher les attaques par déni de service basées sur les durées de traitement prolongées. Ce quota est désactivé par défaut. Certaines surcharges `CreateNavigator` vous permettent de spécifier la façon dont les caractères d'espace doivent être gérés dans le XML à l'aide de l'énumération <xref:System.Xml.XmlSpace>, la valeur par défaut étant `XmlSpace.None`.  
  
 La dernière manière d'accéder au contenu d'un tampon de messages consiste à écrire son contenu dans un flux à l'aide de <xref:System.ServiceModel.Channels.Message.WriteMessage%2A>.  
  
 L'exemple suivant illustre le processus d'utilisation d'un `MessageBuffer` : un message entrant est transféré à plusieurs destinataires, puis enregistré dans un fichier. Sans mise en mémoire tampon cela est impossible, car le corps du message est alors accessible une seule fois.  
  
 [!code-csharp[C_UsingTheMessageClass#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#7)]
 [!code-vb[C_UsingTheMessageClass#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#7)]  
  
 La classe `MessageBuffer` a d'autres membres dont il convient de parler. La méthode <xref:System.ServiceModel.Channels.MessageBuffer.Close%2A> peut être appelée pour libérer des ressources lorsque le contenu de la mémoire tampon n'est plus nécessaire. La propriété <xref:System.ServiceModel.Channels.MessageBuffer.BufferSize%2A> retourne la taille de la mémoire tampon allouée. La propriété <xref:System.ServiceModel.Channels.MessageBuffer.MessageContentType%2A> retourne le type de contenu MIME du message.  
  
## <a name="accessing-the-message-body-for-debugging"></a>Accès au corps de message à des fins de débogage  
 À des fins de débogage, vous pouvez appeler la méthode <xref:System.ServiceModel.Channels.Message.ToString%2A> pour obtenir une représentation du message sous forme de chaîne. Cette représentation correspond généralement à l'aspect qu'aurait un message sur le câble s'il était encodé avec l'encodeur de texte, mais le XML est mis en forme pour une meilleure lisibilité. L'unique exception concerne le corps du message. Le corps ne peut être lu qu'une seule fois et `ToString` ne modifie pas l'état du message. Par conséquent, la `ToString` méthode peut ne pas être en mesure d’accéder au corps et peut substituer un espace réservé (par exemple, « ... » ou trois points) au lieu du corps du message. Par conséquent, vous ne devez pas utiliser `ToString` pour enregistrer des messages si le contenu du corps des messages est important.  
  
## <a name="accessing-other-message-parts"></a>Accès à d'autres parties de message  
 Différentes propriétés sont fournies pour accéder aux informations relatives au message autres que le contenu de son corps. Toutefois, celles-ci ne peuvent pas être appelées une fois que le message a été fermé :  
  
- La propriété <xref:System.ServiceModel.Channels.Message.Headers%2A> représente les en-têtes de messages. Consultez la section « utilisation des en-têtes » plus loin dans cette rubrique.  
  
- La propriété <xref:System.ServiceModel.Channels.Message.Properties%2A> représente les propriétés du message, qui sont des éléments de données nommées joints au message qui ne sont généralement pas émis lorsque le message est envoyé. Consultez la section « Utilisation des propriétés » plus loin dans cette rubrique.  
  
- La propriété <xref:System.ServiceModel.Channels.Message.Version%2A> indique la version SOAP et WS-Addressing associée au message, ou `None` si SOAP est désactivé.  
  
- La propriété <xref:System.ServiceModel.Channels.Message.IsFault%2A> retourne la valeur `true` si le message est un message d'erreur SOAP.  
  
- La propriété <xref:System.ServiceModel.Channels.Message.IsEmpty%2A> retourne `true` si le message est vide.  
  
 Vous pouvez utiliser la méthode <xref:System.ServiceModel.Channels.Message.GetBodyAttribute%28System.String%2CSystem.String%29> pour accéder à un attribut particulier sur l'élément wrapper de corps (par exemple, `<soap:Body>`) identifié par un nom et un espace de noms particuliers. Si ce type d'attribut est introuvable, `null` est retourné. Cette méthode peut être appelée uniquement lorsque le `Message` est à l'état Créé (lorsque le corps du message n'a pas encore été accédé).  
  
## <a name="working-with-headers"></a>Utilisation des en-têtes  
 Un `Message` peut contenir un nombre quelconque de fragments XML nommés, appelés *en-têtes*. Chaque fragment est normalement mappé à un en-tête SOAP. Les en-têtes sont accessibles via la propriété `Headers` de type <xref:System.ServiceModel.Channels.MessageHeaders>. <xref:System.ServiceModel.Channels.MessageHeaders> est une collection d'objets <xref:System.ServiceModel.Channels.MessageHeaderInfo>, et des en-têtes sont accessibles via son interface <xref:System.Collections.IEnumerable> ou via son indexeur. Par exemple, le code suivant répertorie les noms de tous les en-têtes dans un `Message`.  
  
 [!code-csharp[C_UsingTheMessageClass#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#8)]
 [!code-vb[C_UsingTheMessageClass#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#8)]  
  
#### <a name="adding-removing-finding-headers"></a>Ajout, suppression et recherche d'en-têtes  
 Vous pouvez ajouter un nouvel en-tête à la fin de tous les en-têtes existants à l'aide de la méthode <xref:System.ServiceModel.Channels.MessageHeaders.Add%2A>. Vous pouvez utiliser la méthode <xref:System.ServiceModel.Channels.MessageHeaders.Insert%2A> pour insérer un en-tête à un index particulier. Les en-têtes existants sont décalés pour faire place à l'élément inséré. Les en-têtes sont ordonnés en fonction de leur index, le premier index disponible étant 0. Vous pouvez utiliser les différentes surcharges de méthodes <xref:System.ServiceModel.Channels.MessageHeaders.CopyHeadersFrom%2A> pour ajouter des en-têtes à partir d'une instance `Message` ou `MessageHeaders` différente. Certaines surcharges copient un en-tête individuel, tandis que d'autres les copient tous. La méthode <xref:System.ServiceModel.Channels.MessageHeaders.Clear%2A> supprime tous les en-têtes. La méthode <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAt%2A> supprime un en-tête à un index particulier (et décale tous les en-têtes situés après lui). La méthode <xref:System.ServiceModel.Channels.MessageHeaders.RemoveAll%2A> supprime tous les en-têtes avec un nom et un espace de noms particuliers.  
  
 Vous pouvez récupérer un en-tête particulier à l'aide de la méthode <xref:System.ServiceModel.Channels.MessageHeaders.FindHeader%2A>. Cette méthode prend le nom et l'espace de noms de l'en-tête à rechercher et retourne son index. Si l'en-tête est présent plus d'une fois, une exception est levée. Si l'en-tête est introuvable, la méthode retourne la valeur -1.  
  
 Dans le modèle d'en-tête SOAP, les en-têtes peuvent avoir une valeur `Actor` qui spécifie le destinataire prévu de l'en-tête. La surcharge `FindHeader` la plus simple recherche uniquement les en-têtes destinés au destinataire final du message. Toutefois, une autre surcharge vous permet de spécifier les valeurs `Actor` qui sont incluses dans la recherche. Pour plus d’informations, consultez la spécification SOAP.  
  
 Une méthode <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> est fournie pour copier des en-têtes depuis une collection <xref:System.ServiceModel.Channels.MessageHeaders> vers un tableau d’objets <xref:System.ServiceModel.Channels.MessageHeaderInfo>.  
  
 Pour accéder aux données XML dans un en-tête, vous pouvez appeler <xref:System.ServiceModel.Channels.MessageHeaders.GetReaderAtHeader%2A> et retourner un lecteur XML pour l'index d'en-tête spécifique. Si vous souhaitez désérialiser le contenu d'en-tête dans un objet, utilisez <xref:System.ServiceModel.Channels.MessageHeaders.GetHeader%60%601%28System.Int32%29> ou l'une des autres surcharges. Les surcharges les plus simples désérialisent les en-têtes à l'aide du <xref:System.Runtime.Serialization.DataContractSerializer> configuré de la manière par défaut. Si vous souhaitez utiliser un sérialiseur différent ou une configuration différente du `DataContractSerializer`, utilisez l'une des surcharges qui prennent un `XmlObjectSerializer`. Il existe également des surcharges qui prennent le nom d'en-tête, l'espace de noms et éventuellement une liste de valeurs `Actor` au lieu d'un index ; il s'agit d'une combinaison de `FindHeader` et `GetHeader`.  
  
## <a name="working-with-properties"></a>Utilisation des propriétés  
 Une instance de `Message` peut contenir un nombre arbitraire d'objets nommés de types arbitraires. Cette collection est accessible par le biais de la propriété `Properties` de type `MessageProperties`. La collection implémente l'interface <xref:System.Collections.Generic.IDictionary%602> et agit comme mappage de <xref:System.String> à <xref:System.Object>. Normalement, les valeurs de propriété ne correspondent pas directement à une partie du message sur le câble, mais fournissent plutôt des indications de traitement de message aux différents canaux de la pile de canaux WCF ou à l' <xref:System.ServiceModel.Channels.MessageHeaders.CopyTo%28System.ServiceModel.Channels.MessageHeaderInfo%5B%5D%2CSystem.Int32%29> infrastructure de service. Pour obtenir un exemple, consultez [transfert de données vue d’ensemble](data-transfer-architectural-overview.md)de l’architecture.  
  
## <a name="inheriting-from-the-message-class"></a>Héritage de la classe Message  
 Si les types de messages intégrés créés à l'aide de `CreateMessage` ne répondent pas à vos spécifications, créez une classe qui dérive de la classe `Message`.  
  
### <a name="defining-the-message-body-contents"></a>Définition du contenu du corps de message  
 Il existe trois techniques principales d'accès aux données dans un corps de message : écriture, lecture et copie des données vers une mémoire tampon. Ces opérations entraînent en fin de compte l'appel respectif des méthodes <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents%2A> et <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> sur votre classe dérivée de `Message`. La classe `Message` de base garantit qu'une seule de ces méthodes est appelée pour chaque instance `Message` et qu'elle n'est pas appelée plus d'une fois. La classe de base garantit également que les méthodes ne sont pas appelées sur un message fermé. Il n'est pas nécessaire d'effectuer le suivi de l'état du message dans votre implémentation.  
  
 <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> est une méthode abstraite qui doit être implémentée. La façon la plus simple de définir le contenu du corps de votre message consiste à écrire à l'aide de cette méthode. Par exemple, le message suivant contient 100 000 nombres aléatoires compris entre 1 et 20.  
  
 [!code-csharp[C_UsingTheMessageClass#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#9)]
 [!code-vb[C_UsingTheMessageClass#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#9)]  
  
 Les méthodes <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> et <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> ont des implémentations par défaut qui fonctionnent dans la plupart des cas. Les implémentations par défaut appellent <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A>, mettent en mémoire tampon les résultats et utilisent le tampon résultant. Toutefois, dans certains cas cela peut ne pas être suffisant. Dans l'exemple précédent, la lecture du message provoque la mise en mémoire tampon de 100 000 éléments XML, ce qui peut être indésirable. Vous souhaiterez peut-être substituer <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> pour retourner une classe dérivée <xref:System.Xml.XmlDictionaryReader> personnalisée qui sert des nombres aléatoires. Vous pouvez ensuite substituer <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%2A> pour utiliser le lecteur retourné par la <xref:System.ServiceModel.Channels.Message.OnGetReaderAtBodyContents> méthode, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[C_UsingTheMessageClass#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_usingthemessageclass/cs/source.cs#10)]
 [!code-vb[C_UsingTheMessageClass#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_usingthemessageclass/vb/source.vb#10)]  
  
 De même, vous souhaiterez peut-être substituer `OnCreateBufferedCopy` pour retourner votre propre classe dérivée `MessageBuffer`.  
  
 En plus de fournir le contenu du corps de message, votre classe de message dérivée doit également substituer les propriétés `Version`, `Headers` et `Properties`.  
  
 Notez que si vous créez une copie d'un message, la copie utilise les en-têtes de messages de l'original.  
  
### <a name="other-members-that-can-be-overridden"></a>Autres membres qui peuvent être substitués  
 Vous pouvez substituer les <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A> <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A> méthodes, et <xref:System.ServiceModel.Channels.Message.OnWriteStartBody%2A> pour spécifier le mode d’écriture de l’enveloppe SOAP, des en-têtes SOAP et des balises de début d’élément de corps SOAP. Celles-ci correspondent normalement à `<soap:Envelope>` , `<soap:Header>` et `<soap:Body>` . Ces méthodes ne doivent normalement rien écrire si la propriété <xref:System.ServiceModel.Channels.Message.Version> retourne <xref:System.ServiceModel.Channels.MessageVersion.None>.  
  
> [!NOTE]
> L'implémentation par défaut de `OnGetReaderAtBodyContents` appelle `OnWriteStartEnvelope` et `OnWriteStartBody` avant d'appeler `OnWriteBodyContents` et de mettre les résultats en mémoire tampon. Les en-têtes ne sont pas écrits.  
  
 Substituez la méthode <xref:System.ServiceModel.Channels.Message.OnWriteMessage%2A> pour modifier la façon dont le message entier est construit à partir de ses différents éléments. La méthode `OnWriteMessage` est appelée à partir de <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> et de l'implémentation <xref:System.ServiceModel.Channels.Message.OnCreateBufferedCopy%2A> par défaut. Notez que la substitution de <xref:System.ServiceModel.Channels.Message.WriteMessage%2A> n'est pas recommandée. Il est préférable de substituer les méthodes `On` appropriées (par exemple, <xref:System.ServiceModel.Channels.Message.OnWriteStartEnvelope%2A>, <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A> et <xref:System.ServiceModel.Channels.BodyWriter.OnWriteBodyContents%2A>.  
  
 Substituez <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A> afin de substituer la façon dont votre corps de message est représenté durant le débogage. Le paramètre par défaut consiste à le représenter sous la forme de trois points (« … »). Notez que cette méthode peut être appelée plusieurs fois lorsque l'état du message est autre que Fermé. Une implémentation de cette méthode ne doit jamais provoquer d'action qui doit être exécutée une seule fois (telle que la lecture d'un flux avant uniquement).  
  
 Substituez la méthode <xref:System.ServiceModel.Channels.Message.OnGetBodyAttribute%2A> pour autoriser l'accès aux attributs sur l'élément de corps SOAP. Cette méthode peut être appelée un nombre de fois quelconque, mais le type de base `Message` garantit son appel uniquement lorsque le message est à l'état Créé. Il n'est pas nécessaire de vérifier l'état dans une implémentation. L'implémentation par défaut retourne toujours `null`, ce qui indique qu'il n'y a pas d'attributs sur l'élément de corps.  
  
 Si votre objet `Message` doit effectuer un nettoyage spécial lorsque le corps du message n'est plus nécessaire, vous pouvez substituer <xref:System.ServiceModel.Channels.Message.OnClose%2A>. L'implémentation par défaut n'exécute aucune opération.  
  
 Les propriétés `IsEmpty` et `IsFault` peuvent être substituées. Par défaut, toutes deux retournent la valeur `false`.
