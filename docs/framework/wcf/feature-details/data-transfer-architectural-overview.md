---
title: Vue d'ensemble de l'architecture de transfert de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WCF], architectural overview
ms.assetid: 343c2ca2-af53-4936-a28c-c186b3524ee9
ms.openlocfilehash: efb6933ba90975d5ba35deb2bf22af12fc7c2cdc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291685"
---
# <a name="data-transfer-architectural-overview"></a>Vue d'ensemble de l'architecture de transfert de données

Windows Communication Foundation (WCF) peut être considéré comme une infrastructure de messagerie. Il peut recevoir des messages, les traiter et les distribuer au code utilisateur pour action ultérieure, ou il peut construire des messages à partir des données fournies par le code utilisateur et les transmettre vers une destination. Cette rubrique, conçue à l'attention des développeurs avancés, décrit l'architecture de gestion des messages et des données qu'ils contiennent. Pour une approche plus simple des tâches d’envoi et de réception des données, consultez [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).  
  
> [!NOTE]
> Cette rubrique traite des détails de l’implémentation de WCF qui ne sont pas visibles en examinant le modèle objet WCF. Deux mots d'avertissement s'imposent concernant les détails d'implémentation documentés. Premièrement, les descriptions sont simplifiées ; l'implémentation réelle peut s'avérer plus complexe en raison des optimisations ou pour d'autres raisons. Deuxièmement, vous ne devez jamais vous appuyer sur des détails d'implémentation spécifiques, même s'ils sont documentés, car ils peuvent changer sans préavis d'une version à une autre, voire même dans une version de maintenance.  
  
## <a name="basic-architecture"></a>Architecture de base  

 La <xref:System.ServiceModel.Channels.Message> classe, qui est décrite en détail dans [utilisation de la classe message](using-the-message-class.md), est au cœur des fonctionnalités de gestion des messages WCF. Les composants runtime de WCF peuvent être divisés en deux parties principales : la pile de canaux et l’infrastructure de service, la <xref:System.ServiceModel.Channels.Message> classe étant le point de connexion.  
  
 La pile de canaux est chargée d'effectuer la conversion entre une instance <xref:System.ServiceModel.Channels.Message> valide et des actions qui correspondent à l'émission ou à la réception de données de message. Du côté envoi, la pile de canaux prend une instance <xref:System.ServiceModel.Channels.Message> valide et, après traitement, exécute des actions qui logiquement correspondent à l'envoi du message. L'action peut envoyer des paquets TCP ou HTTP, mettre le message en file d'attente dans Message Queuing, écrire le message dans une base de données, l'enregistrer dans un partage de fichiers, ou effectuer toute autre action, selon l'implémentation. L'action la plus courante consiste à envoyer les messages sur un protocole réseau. Du côté réception, c'est la procédure inverse qui se produit : l'action est détectée (il peut s'agir de paquets TCP ou HTTP qui arrivent ou de toute autre action), et, après traitement, la pile de canaux convertit cette action en instance <xref:System.ServiceModel.Channels.Message> valide.  
  
 Vous pouvez utiliser WCF à l’aide de la <xref:System.ServiceModel.Channels.Message> classe et de la pile de canaux directement. Cependant, cette procédure s'avère difficile et fastidieuse. En outre, l' <xref:System.ServiceModel.Channels.Message> objet ne fournit aucune prise en charge des métadonnées. vous ne pouvez donc pas générer de clients WCF fortement typés si vous utilisez WCF de cette manière.  
  
 Par conséquent, WCF inclut une infrastructure de service qui fournit un modèle de programmation facile à utiliser que vous pouvez utiliser pour construire et recevoir des `Message` objets. L’infrastructure de service mappe des services aux types de .NET Framework via la notion de contrats de service et distribue des messages aux opérations utilisateur qui sont simplement .NET Framework méthodes marquées avec l' <xref:System.ServiceModel.OperationContractAttribute> attribut (pour plus d’informations, consultez [conception de contrats de service](../designing-service-contracts.md)). Ces méthodes peuvent avoir des paramètres et des valeurs de retour. Du côté service, l'infrastructure de service convertit les instances entrantes <xref:System.ServiceModel.Channels.Message> en paramètres, et convertit les valeurs de retour en instances sortantes <xref:System.ServiceModel.Channels.Message> . Du côté client, elle fait le contraire. Examinons, par exemple, l'opération `FindAirfare` ci-dessous.  
  
 [!code-csharp[c_DataArchitecture#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#1)]
 [!code-vb[c_DataArchitecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#1)]  
  
 Supposons que `FindAirfare` est appelé sur le client. L'infrastructure de service sur le client convertit les paramètres `FromCity` et `ToCity` en instance sortante <xref:System.ServiceModel.Channels.Message> et la passe à la pile de canaux afin de l'envoyer.  
  
 Du côté service, lorsqu'une instance <xref:System.ServiceModel.Channels.Message> arrive de la pile de canaux, l'infrastructure de service extrait les données pertinentes du message afin de renseigner les paramètres `FromCity` et `ToCity` , puis appelle la méthode `FindAirfare` côté service. Lorsque la méthode retourne, l'infrastructure de service prend la valeur entière retournée et le paramètre de sortie `IsDirectFlight` , puis crée une instance d'objet <xref:System.ServiceModel.Channels.Message> qui contient ces informations. Elle passe ensuite l'instance `Message` à la pile de canaux afin de la renvoyer au client.  
  
 Du côté client, une instance <xref:System.ServiceModel.Channels.Message> qui contient le message de réponse émerge de la pile de canaux. L'infrastructure de service extrait la valeur de retour et la valeur `IsDirectFlight` , puis les retourne à l'appelant du client.  
  
## <a name="message-class"></a>Classe Message  

 La classe <xref:System.ServiceModel.Channels.Message> est destinée à être la représentation abstraite d'un message, mais sa conception est fortement associée au message SOAP. <xref:System.ServiceModel.Channels.Message> contient trois éléments d'information principaux : corps du message, en-têtes de message et propriétés de message.  
  
## <a name="message-body"></a>Corps du message  

 Le corps du message est destiné à représenter la charge utile de données réelle du message. Le corps du message est toujours représenté sous forme d'un ensemble d'informations XML. Cela ne signifie pas que tous les messages créés ou reçus dans WCF doivent être au format XML. C'est à la pile de canaux qu'il revient de décider de l'interprétation du corps du message. Elle peut l'émettre au format XML, le convertir dans un autre, ou même l'omettre entièrement. Bien entendu, avec la plupart des liaisons fournies par WCF, le corps du message est représenté sous forme de contenu XML dans la section de corps d’une enveloppe SOAP.  
  
 Il est important de savoir que la classe `Message` ne contient pas nécessairement de mémoire tampon avec des données XML représentant le corps. Logiquement, `Message` contient un ensemble d'informations XML, mais celui-ci peut être construit dynamiquement et peut ne jamais exister physiquement en mémoire.  
  
### <a name="putting-data-into-the-message-body"></a>Placement de données dans le corps du message  

 Il n'existe pas de mécanisme uniforme pour placer des données dans le corps d'un message. La classe <xref:System.ServiceModel.Channels.Message> a une méthode abstraite, <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, qui prend un <xref:System.Xml.XmlDictionaryWriter>. Chaque sous-classe de la classe <xref:System.ServiceModel.Channels.Message> est chargée de substituer cette méthode et d'écrire son propre contenu. Le corps du message contient logiquement l'ensemble d'informations XML généré par `OnWriteBodyContent` . Examinons, par exemple, la classe `Message` suivante :  
  
 [!code-csharp[c_DataArchitecture#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#2)]
 [!code-vb[c_DataArchitecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#2)]  
  
 Physiquement, une instance `AirfareRequestMessage` contient uniquement deux chaînes (« fromCity » et « toCity »). Cependant, le message contient logiquement l'ensemble d'informations XML suivant :  
  
```xml  
<airfareRequest>  
    <from>Tokyo</from>  
    <to>London</to>  
</airfareRequest>  
```  
  
 Bien évidemment, vous ne créez pas de message de cette manière normalement, car vous pouvez utiliser l'infrastructure de service pour créer un message comme le précédent à partir des paramètres de contrat d'opération. En outre, la classe <xref:System.ServiceModel.Channels.Message> a des méthodes `CreateMessage` statiques qui vous permettent de créer des messages avec des types courants de contenu : un message vide, un message contenant un objet sérialisé en XML avec <xref:System.Runtime.Serialization.DataContractSerializer>, un message contenant une erreur SOAP, un message contenant du XML représenté par <xref:System.Xml.XmlReader>, etc.  
  
### <a name="getting-data-from-a-message-body"></a>Extraction des données du corps d'un message  

 Vous pouvez extraire les données stockées dans le corps d'un message de deux principales manières :  
  
- Vous pouvez extraire l'ensemble du corps du message en une seule opération en appelant la méthode <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29> et en le passant dans un enregistreur XML. L'ensemble du corps du message est écrit dans cet enregistreur. L'extraction de l'ensemble du corps du message en une seule opération est également appelée *écriture de message*. L'écriture est principalement effectuée par la pile de canaux lors de l'envoi des messages : certaines parties de la pile de canaux accèdent généralement à l'ensemble du corps du message, l'encodent et l'envoient.  
  
- Une autre méthode consiste à appeler <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents> et à placer un lecteur XML. Le corps du message peut être accédé séquentiellement si nécessaire en appelant des méthodes sur le lecteur. L'extraction du corps du message élément par élément est également appelée *lecture de message*. La lecture du message est principalement utilisée par l'infrastructure de service lors de la réception des messages. Par exemple, lorsque <xref:System.Runtime.Serialization.DataContractSerializer> est en cours d'utilisation, l'infrastructure de service place un lecteur XML sur le corps et le passe au moteur de désérialisation, qui commence ensuite à lire le message élément par élément et à construire le graphique d'objets correspondant.  
  
 Le corps d'un message ne peut être récupéré qu'une seule fois. Cela permet d'utiliser des flux avant uniquement. Par exemple, vous pouvez écrire une substitution <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> que lit à partir de <xref:System.IO.FileStream> et retourne les résultats sous forme d'un ensemble d'informations XML. Vous n’aurez jamais besoin de « rembobiner » au début du fichier.  
  
 Les méthodes `WriteBodyContents` et `GetReaderAtBodyContents` vérifient simplement que le corps du message n'a jamais été récupéré auparavant, puis appellent `OnWriteBodyContents` ou `OnGetReaderAtBodyContents`, respectivement.  
  
## <a name="message-usage-in-wcf"></a>Utilisation des messages dans WCF  

 La plupart des messages peuvent être classés comme étant *sortants* (ceux créés par l'infrastructure de service pour être envoyés par la pile de canaux) ou *entrants* (ceux qui proviennent de la pile de canaux et qui sont interprétés par l'infrastructure de service). En outre, la pile de canaux peut fonctionner en mode de mise en mémoire tampon ou en mode de diffusion en continu. L'infrastructure de service peut également exposer un modèle de programmation avec ou sans diffusion en continu. Cela conduit aux cas répertoriés dans le tableau suivant, accompagnés des détails simplifiés de leur implémentation.  
  
|type de message|Données relatives au corps du message|Implémentation de l'écriture (OnWriteBodyContents)|Implémentation de la lecture (OnGetReaderAtBodyContents)|  
|------------------|--------------------------|--------------------------------------------------|-------------------------------------------------------|  
|Sortant, créé à partir du modèle de programmation sans diffusion en continu|Les données nécessaires pour écrire le message (par exemple, un objet et l'instance <xref:System.Runtime.Serialization.DataContractSerializer> nécessaires pour le sérialiser)*|Logique personnalisée d'écriture du message basée sur les données stockées (par exemple, appelez `WriteObject` sur `DataContractSerializer` s'il s'agit du sérialiseur utilisé)*|Appelle `OnWriteBodyContents`, met les résultats en mémoire tampon, retourne un lecteur XML sur la mémoire tampon|  
|Sortant, créé à partir du modèle de programmation avec diffusion en continu|`Stream` dans lequel les données doivent être écrites*|Écrit les données provenant du flux stocké à l'aide du mécanisme <xref:System.Xml.IStreamProvider> *|Appelle `OnWriteBodyContents`, met les résultats en mémoire tampon, retourne un lecteur XML sur la mémoire tampon|  
|Entrant, provenant de la pile de canaux de diffusion en continu|Objet `Stream` qui représente les données entrant sur le réseau avec un <xref:System.Xml.XmlReader> placé sur celui-ci|Écrit le contenu provenant du `XmlReader` stocké à l'aide de `WriteNode`|Retourne le `XmlReader`stocké|  
|Entrant, provenant de la pile de canaux sans diffusion en continu|Mémoire tampon qui contient les données relatives au corps avec un `XmlReader` placé sur celle-ci|Écrit le contenu provenant du `XmlReader` stocké à l'aide de `WriteNode`|Retourne le langage stocké|  
  
 \* Ces éléments ne sont pas implémentés directement dans les sous- `Message` classes, mais dans les sous-classes de la <xref:System.ServiceModel.Channels.BodyWriter> classe. Pour plus d'informations sur le <xref:System.ServiceModel.Channels.BodyWriter>, consultez [Using the Message Class](using-the-message-class.md).  
  
## <a name="message-headers"></a>En-têtes de message  

 Un message peut contenir des en-têtes. Un en-tête se compose logiquement d'un ensemble d'informations XML associé à un nom, à un espace de noms et à d'autres propriétés. Les en-têtes de message sont accessibles à l'aide de la propriété `Headers` sur <xref:System.ServiceModel.Channels.Message>. Chaque en-tête est représenté par une classe <xref:System.ServiceModel.Channels.MessageHeader> . En général, les en-têtes de message sont mappés vers les en-têtes de message SOAP lors de l'utilisation d'une pile de canaux configurée pour fonctionner avec des messages SOAP.  
  
 Placer des informations dans un en-tête de message et les en extraire est un processus similaire à celui qui consiste à utiliser le corps du message. Il est quelque peu simplifié car la diffusion en continu n'est pas prise en charge. Il est possible d'accéder plusieurs fois au contenu du même en-tête, et les en-têtes sont accessibles dans un ordre arbitraire, en forçant systématiquement leur mise en mémoire tampon. Il n’existe pas de mécanisme à usage général pour obtenir un lecteur XML sur un en-tête, mais il existe une `MessageHeader` sous-classe interne à WCF qui représente un en-tête lisible avec une telle fonctionnalité. Ce type de `MessageHeader` est créé par la pile de canaux lors de la réception d'un message avec en-têtes d'application personnalisés. Cela permet à l'infrastructure de service d'utiliser un moteur de désérialisation, tel que l'objet <xref:System.Runtime.Serialization.DataContractSerializer>, pour interpréter ces en-têtes.  
  
 Pour plus d’informations, consultez [utilisation de la classe message](using-the-message-class.md).  
  
## <a name="message-properties"></a>Propriétés de message  

 Un message peut contenir des propriétés. Une *propriété* est un objet .NET Framework associé à un nom de chaîne. Les propriétés sont accessibles via la propriété `Properties` sur `Message`.  
  
 Contrairement au corps et aux en-têtes de message (qui mappent normalement vers le corps et les en-têtes SOAP, respectivement), les propriétés de message ne sont en général pas envoyées ou reçues avec les messages. Les propriétés de message constituent principalement un mécanisme de communication permettant de passer les données sur le message entre les divers canaux de la pile, et entre la pile de canaux et le modèle de service.  
  
 Par exemple, le canal de transport HTTP inclus dans le cadre de WCF est en mesure de produire divers codes d’état HTTP, tels que « 404 (introuvable) » et « 500 (erreur de serveur interne) », lorsqu’il envoie des réponses aux clients. Avant d’envoyer un message de réponse, il vérifie si le `Properties` du `Message` contient une propriété appelée « HttpResponse » qui contient un objet de type <xref:System.ServiceModel.Channels.HttpResponseMessageProperty> . Si une propriété de ce type est trouvée, il regardera au niveau de la propriété <xref:System.ServiceModel.Channels.HttpResponseMessageProperty.StatusCode%2A> et utilisera ce code d'état. Dans le cas contraire, le code "200 (OK)" par défaut est utilisé.  
  
 Pour plus d’informations, consultez [utilisation de la classe message](using-the-message-class.md).  
  
### <a name="the-message-as-a-whole"></a>Le message dans son ensemble  

 Nous avons jusqu'à maintenant présenté les méthodes d'accès aux diverses parties du message indépendamment les unes des autres. Toutefois, la classe <xref:System.ServiceModel.Channels.Message> fournit également des méthodes permettant d'utiliser le message dans son ensemble. Par exemple, la méthode `WriteMessage` écrit l'ensemble du message dans un enregistreur XML.  
  
 Pour que cela soit possible, un mappage doit être défini entre l'instance `Message` entière et un ensemble d'informations XML. En fait, un mappage de ce type existe : WCF utilise la norme SOAP pour définir ce mappage. Lorsqu'une instance `Message` est écrite en tant qu'ensemble d'informations XML, l'ensemble d'informations résultant est l'enveloppe SOAP valide qui contient le message. Par conséquent, `WriteMessage` exécute normalement les étapes suivantes :  
  
1. Écrire la balise d'ouverture de l'élément d'enveloppe SOAP.  
  
2. Écrire la balise d'ouverture de l'élément d'en-tête SOAP, écrire tous les en-têtes et fermer l'élément d'en-tête.  
  
3. Écrire la balise d'ouverture de l'élément de corps SOAP.  
  
4. Appeler `WriteBodyContents` ou une méthode équivalente pour écrire le corps.  
  
5. Fermer les éléments de corps et d'enveloppe.  
  
 Les étapes précédentes sont étroitement liées au standard SOAP. Cela est compliqué par le fait que plusieurs versions de SOAP existent ; à titre d'exemple, il est impossible d'écrire l'élément d'enveloppe SOAP correctement sans connaître la version SOAP utilisée. Par ailleurs, il peut dans certains cas s'avérer souhaitable de désactiver complètement ce mappage complexe spécifique à SOAP.  
  
 À ces fins, une propriété `Version` est fournie sur `Message`. Elle peut être définie à la version SOAP à utiliser lors de l'écriture du message, ou avoir la valeur `None` afin d'empêcher tout mappage spécifique à SOAP. Si la propriété `Version` a la valeur `None`, les méthodes qui utilisent l'ensemble du message agissent comme si le message était uniquement composé de son corps ; par exemple, `WriteMessage` appelle simplement `WriteBodyContents` au lieu d'exécuter les multiples étapes répertoriées ci-dessus. `Version` est supposé être détecté automatiquement et être défini correctement sur les messages entrants.  
  
## <a name="the-channel-stack"></a>Pile de canaux  
  
### <a name="channels"></a>Canaux  

 Comme indiqué précédemment, la pile de canaux est chargée de convertir les instances <xref:System.ServiceModel.Channels.Message> sortantes en actions (par exemple envoyer des paquets sur le réseau), ou de convertir des actions (par exemple recevoir des paquets réseau) en instances `Message` entrantes.  
  
 La pile de canaux est composée d'un ou de plusieurs canaux ordonnés dans une séquence. Une instance `Message` sortante est passée au premier canal dans la pile (également appelé *canal le plus haut*), qui le passe au canal immédiatement inférieur dans la pile, et ainsi de suite. Le message se termine dans le dernier canal, appelé *canal de transport*. Les messages entrants sont générés dans le canal de transport et sont passés d'un canal à l'autre vers le haut de la pile. Lorsqu'il se trouve dans le canal le plus haut, le message est généralement passé dans l'infrastructure de service. Bien qu'il s'agisse du modèle habituel pour les messages d'application, certains canaux peuvent fonctionner légèrement différemment ; ils peuvent, par exemple, envoyer leurs propres messages d'infrastructure sans passer de message à partir d'un canal supérieur.  
  
 Les canaux peuvent agir sur le message de diverses façons lorsqu'il traverse la pile. L'opération la plus courante consiste à ajouter un en-tête à un message sortant et à lire les en-têtes sur un message entrant. Par exemple, un canal peut calculer la signature numérique d'un message et l'ajouter en tant qu'en-tête. Un canal peut également inspecter cet en-tête de signature numérique sur les messages entrants et empêcher ceux qui n'ont pas de signature valide d'atteindre le haut de la pile de canaux. Les canaux définissent ou inspectent également souvent les propriétés de message. Le corps du message n’est généralement pas modifié, bien que cela soit autorisé, par exemple, le canal de sécurité WCF peut chiffrer le corps du message.  
  
### <a name="transport-channels-and-message-encoders"></a>Canaux de transport et encodeurs de message  

 Le canal le plus bas dans la pile est chargé de transformer réellement en actions un <xref:System.ServiceModel.Channels.Message>sortant, tel qu'il a été modifié par d'autres canaux. Du côté réception, c'est le canal qui convertit des actions en `Message` que les autres canaux traitent.  
  
 Comme indiqué précédemment, les actions peuvent être diverses : envoyer ou recevoir des paquets réseau sur différents protocoles, lire ou écrire le message dans une base de données, mettre le message en file d'attente ou le supprimer de la file d'attente Message Queuing, pour ne citer que quelques exemples. Toutes ces actions ont une chose en commun : elles requièrent une transformation entre l' `Message` instance WCF et un groupe réel d’octets qui peut être envoyé, reçu, lu, écrit, mis en file d’attente ou supprimé de la file d’attente. Le processus de conversion d'un `Message` en groupe d'octets est appelé *encodage*, et le processus inverse de création d'un `Message` à partir d'un groupe d'octets est appelé *décodage*.  
  
 La plupart des canaux de transport utilisent des composants appelés *encodeurs de message* pour procéder à l'encodage et au décodage. Un encodeur de message est une sous-classe de la classe <xref:System.ServiceModel.Channels.MessageEncoder> . `MessageEncoder` inclut différentes surcharges de méthode `ReadMessage` et `WriteMessage` pour effectuer la conversion entre `Message` et des groupes d'octets.  
  
 Du côté envoi, un canal de transport de mise en mémoire tampon passe l'objet `Message` qu'il a reçu d'un canal supérieur à `WriteMessage`. Il récupère un tableau d'octets, qu'il utilise ensuite pour exécuter son action (par exemple emballer ces octets sous forme de paquets TCP valides et les envoyer vers la destination correcte). Un canal de transport de diffusion en continu crée d'abord un `Stream` (par exemple, sur la connexion TCP sortante), puis passe à la fois le `Stream` et le `Message` qu'il doit envoyer à la surcharge `WriteMessage` appropriée, qui écrit le message.  
  
 Du côté réception, un canal de transport de mise en mémoire tampon extrait les octets entrants (provenant par exemple des paquets TCP entrants) dans un tableau et appelle `ReadMessage` pour obtenir un objet `Message` qu'il peut remonter plus haut dans la pile de canaux. Un canal de transport de diffusion en continu crée un objet `Stream` (par exemple, un flux réseau sur la connexion TCP entrante) et le passe à `ReadMessage` pour récupérer un objet `Message` .  
  
 La séparation entre les canaux de transport et l'encodeur de message n'est pas obligatoire ; il est possible d'écrire un canal de transport qui n'utilise pas d'encodeur de message. Toutefois, l'avantage de cette séparation est la facilité de composition. Tant qu’un canal de transport utilise uniquement la base <xref:System.ServiceModel.Channels.MessageEncoder> , il peut fonctionner avec n’importe quel encodeur de message WCF ou tiers. En outre, le même encodeur peut normalement être utilisé dans n'importe quel canal de transport.  
  
### <a name="message-encoder-operation"></a>Opération d'encodeur de message  

 Pour décrire l'opération classique d'un encodeur, il est utile de prendre en compte les quatre cas suivants.  
  
|Opération|Commentaire|  
|---------------|-------------|  
|Encodage, mise en mémoire tampon|En mode de mise en mémoire tampon, l'encodeur crée normalement une mémoire tampon de taille variable, puis crée un enregistreur XML sur celle-ci. Il appelle ensuite <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> sur le message encodé, qui écrit les en-têtes, puis le corps à l'aide de <xref:System.ServiceModel.Channels.Message.WriteBodyContents%28System.Xml.XmlDictionaryWriter%29>, tel qu'expliqué dans la section portant sur `Message` précédemment développée dans cette rubrique. Le contenu de la mémoire tampon (représenté sous forme d'un tableau d'octets) est ensuite retourné pour être utilisé par le canal de transport.|  
|Encodage, avec diffusion en continu|En mode avec diffusion en continu, l'opération est semblable à celle ci-dessus, mais elle est plus simple. Une mémoire tampon n'est pas nécessaire. Un enregistreur XML est normalement créé sur le flux et <xref:System.ServiceModel.Channels.Message.WriteMessage%28System.Xml.XmlWriter%29> est appelé sur `Message` pour l'écrire dans cet enregistreur.|  
|Décodage, mise en mémoire tampon|Lors du décodage en mode de mise en mémoire tampon, une sous-classe `Message` spéciale qui contient les données mises en mémoire tampon est normalement créée. Les en-têtes du message sont lus, et un lecteur XML positionné sur le corps du message est créé. Il s'agit du lecteur qui sera retourné avec <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
|Décodage, avec diffusion en continu|Lors du décodage en mode avec diffusion en continu, une sous-classe Message spéciale est normalement créée. Le flux est avancé juste assez suffisamment pour lire tous les en-têtes et le positionner sur le corps du message. Un lecteur XML est ensuite créé sur le flux. Il s'agit du lecteur qui sera retourné avec <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents>.|  
  
 Les encodeurs peuvent également exécuter d'autres fonctions. Ils peuvent, par exemple, regrouper des lecteurs et des enregistreurs XML. La création d'un lecteur ou d'un enregistreur XML chaque fois que cela s'avère nécessaire est très coûteuse. Par conséquent, les encodeurs conservent normalement un pool de lecteurs et d'enregistreurs de taille configurable. Dans les descriptions de l’opération d’encodeur décrite précédemment, chaque fois que l’expression « créer un lecteur/enregistreur XML » est utilisée, cela signifie généralement « prendre un du pool ou en créer un s’il n’est pas disponible ». L’encodeur (et les sous-classes `Message` créées durant le décodage) contient une logique renvoyant les lecteurs et les enregistreurs au pool une fois qu’ils ne sont plus nécessaires (par exemple, lorsque le `Message` est fermé).  
  
 WCF fournit trois encodeurs de message, bien qu’il soit possible de créer des types personnalisés supplémentaires. Les types fournis sont de type texte, binaire et MTOM (Message Transmission Optimization Mechanism). Ils sont décrits en détail dans [Choosing a Message Encoder](choosing-a-message-encoder.md).  
  
### <a name="the-istreamprovider-interface"></a>Interface IStreamProvider  

 Lors de l'écriture d'un message sortant contenant un corps avec diffusion en continu vers un enregistreur XML, <xref:System.ServiceModel.Channels.Message> utilise une séquence d'appels similaire à la suivante dans son implémentation <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> :  
  
- Écrivez toutes les informations nécessaires précédant le flux (par exemple, la balise XML d'ouverture).  
  
- Écrire le flux.  
  
- Écrivez toutes les informations suivant le flux (par exemple, la balise XML de fermeture).  
  
 Cela fonctionne correctement avec des encodages similaires à l'encodage XML textuel. Toutefois, certains encodages ne placent pas l'ensemble d'informations XML (par exemple, les balises permettant de démarrer et de terminer les éléments XML) avec les données contenues dans des éléments. Avec l'encodage MTOM par exemple, le message est fractionné en plusieurs parties. Une partie contient l'ensemble d'informations XML, qui peut contenir des références à d'autres parties du contenu d'éléments réels. La taille de l'ensemble d'informations XML étant normalement réduite par rapport à celle du contenu avec diffusion en continu, il est donc logique de mettre cet ensemble en mémoire tampon, de l'écrire, puis d'écrire le contenu avec diffusion en continu. Cela signifie que lorsque la balise d'élément de fermeture est écrite, le flux ne doit pas encore avoir été écrit.  
  
 L'interface <xref:System.Xml.IStreamProvider> est utilisée à cette fin. Elle dispose d'une méthode <xref:System.Xml.IStreamProvider.GetStream> qui retourne le flux à écrire. Pour écrire un corps de message avec diffusion en continu dans <xref:System.ServiceModel.Channels.Message.OnWriteBodyContents%28System.Xml.XmlDictionaryWriter%29> , procédez comme suit :  
  
1. Écrivez toutes les informations nécessaires précédant le flux (par exemple, la balise XML d'ouverture).  
  
2. Appelez la surcharge `WriteValue` sur le <xref:System.Xml.XmlDictionaryWriter> qui accepte <xref:System.Xml.IStreamProvider>, avec une implémentation `IStreamProvider` qui retourne le flux à écrire.  
  
3. Écrivez toutes les informations suivant le flux (par exemple, la balise XML de fermeture).  
  
 Avec cette approche, l'enregistreur XML peut choisir à quel moment appeler <xref:System.Xml.IStreamProvider.GetStream> et écrire les données avec diffusion en continu. Par exemple, les enregistreurs XML textuels et binaires l'appellent immédiatement et écrivent le contenu avec diffusion en continu entre les balises de début et de fin. L'enregistreur MTOM peut décider d'appeler <xref:System.Xml.IStreamProvider.GetStream> ultérieurement, lorsqu'il est prêt à écrire la partie appropriée du message.  
  
## <a name="representing-data-in-the-service-framework"></a>Représentation des données dans l'infrastructure de service  

 Comme indiqué dans la section « architecture de base » de cette rubrique, l’infrastructure de service est la partie de WCF qui, entre autres choses, est responsable de la conversion entre un modèle de programmation convivial pour les données de message et les `Message` instances réelles. Normalement, un échange de messages est représenté dans l’infrastructure de service sous la forme d’une méthode .NET Framework marquée avec l' <xref:System.ServiceModel.OperationContractAttribute> attribut. La méthode peut prendre quelques paramètres et retourner une valeur de retour ou des paramètres de sortie (ou les deux). Du côté service, les paramètres d'entrée représentent le message entrant, et la valeur de retour et les paramètres de sortie représentent le message sortant. Du côté client, l'inverse est vérifié. Le modèle de programmation permettant de décrire des messages à l’aide de paramètres et de la valeur de retour est présenté en détail dans [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md). Cependant, cette section fournit une brève vue d'ensemble.  
  
## <a name="programming-models"></a>Modèles de programmation  

 L’infrastructure de service WCF prend en charge cinq modèles de programmation différents pour la description des messages :  
  
### <a name="1-the-empty-message"></a>1. Message vide  

 C'est le cas le plus simple. Pour décrire un message entrant vide, n'utilisez pas de paramètre d'entrée.  
  
 [!code-csharp[C_DataArchitecture#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#3)]
 [!code-vb[C_DataArchitecture#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#3)]  
  
 Pour décrire un message sortant vide, utilisez une valeur de retour void et n'utilisez pas de paramètre de sortie :  
  
 [!code-csharp[C_DataArchitecture#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#4)]
 [!code-vb[C_DataArchitecture#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#4)]  
  
 Notez que cela est différent à partir d'un contrat d'opération monodirectionnel :  
  
 [!code-csharp[C_DataArchitecture#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#5)]
 [!code-vb[C_DataArchitecture#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#5)]  
  
 Dans l'exemple `SetDesiredTemperature` , un modèle d'échange de messages bidirectionnel est décrit. Un message est retourné par l'opération, mais il est vide. Il est possible de retourner une erreur à partir de l'opération. Dans l'exemple « Set Lightbulb », le modèle d'échange de messages est monodirectionnel, il n'y a donc pas de message sortant à décrire. Dans ce cas, le service ne peut pas communiquer d'état au client.  
  
### <a name="2-using-the-message-class-directly"></a>2. Utilisation de la classe Message directement  

 Il est possible d'utiliser la classe <xref:System.ServiceModel.Channels.Message> (ou l'une de ses sous-classes) directement dans un contrat d'opération. Dans ce cas, l'infrastructure de service passe uniquement le `Message` de l'opération à la pile de canaux et vice versa, sans traitement supplémentaire.  
  
 Il existe deux principaux cas dans lesquels utiliser `Message` directement. Dans le cas de scénarios avancés, lorsqu'aucun des autres modèles de programmation ne vous donne suffisamment de souplesse pour décrire votre message. Par exemple, vous souhaitez utiliser des fichiers sur disque pour décrire un message, les propriétés du fichier devenant les en-têtes de message et le contenu du fichier devenant le corps du message. Vous pouvez ensuite créer du code similaire au suivant.  
  
 [!code-csharp[C_DataArchitecture#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#6)]
 [!code-vb[C_DataArchitecture#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#6)]  
  
 Le deuxième cas d'utilisation courante de `Message` dans un contrat d'opération est lorsqu'un service ne se soucie pas du contenu de message spécifique et agit sur le message comme sur une boîte noire. Par exemple, vous pouvez avoir un service qui transfère des messages à plusieurs autres destinataires. Le contrat peut être écrit comme suit.  
  
 [!code-csharp[C_DataArchitecture#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#7)]
 [!code-vb[C_DataArchitecture#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#7)]  
  
 La ligne action = "*" désactive la distribution des messages et s’assure que tous les messages envoyés au `IForwardingService` contrat sont en mesure de l' `ForwardMessage` opération. (Normalement, le répartiteur examine l’en-tête « action » du message pour déterminer l’opération à laquelle il est destiné. Action = " \* " signifie "toutes les valeurs possibles de l’en-tête d’action".) La combinaison de action = " \* " et de l’utilisation de message en tant que paramètre est appelée « contrat universel », car elle est en mesure de recevoir tous les messages possibles. Pour être en mesure d’envoyer tous les messages possibles, utilisez le message comme valeur de retour et affectez-lui la valeur `ReplyAction` " \* ". Cela empêche l'infrastructure de service d'ajouter son propre en-tête Action, et vous permet ainsi de contrôler cet en-tête à l'aide de l'objet `Message` que vous retournez.  
  
### <a name="3-message-contracts"></a>3. Contrats de message  

 WCF fournit un modèle de programmation déclaratif pour la description des messages, appelés *contrats de message*. Ce modèle est décrit en détail dans [Using Message Contracts](using-message-contracts.md). Fondamentalement, l’ensemble du message est représenté par un type de .NET Framework unique qui utilise des attributs tels que <xref:System.ServiceModel.MessageBodyMemberAttribute> et <xref:System.ServiceModel.MessageHeaderAttribute> pour décrire les parties de la classe de contrat de message qui doivent être mappées à une partie du message.  
  
 Les contrats de message offrent un contrôle important sur les instances `Message` résultantes (bien que celui-ci ne soit évidemment pas aussi complet qu'en utilisant la classe `Message` directement). Par exemple, les corps de message sont souvent composés de plusieurs éléments d'information, chacun représenté par son propre élément XML. Ces éléments peuvent se produire directement dans le corps (mode *nu* ) ou être *encapsulés* dans un élément XML englobant. Le modèle de programmation de contrat de message vous permet de prendre une décision de type « nu ou encapsulé » et de contrôler le nom de wrapper et d'espace de noms.  
  
 L'exemple de code suivant d'un contrat de message présente ces fonctionnalités.  
  
 [!code-csharp[C_DataArchitecture#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#9)]
 [!code-vb[C_DataArchitecture#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#9)]  
  
 Les éléments marqués pour la sérialisation (avec <xref:System.ServiceModel.MessageBodyMemberAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>ou d'autres attributs associés) doivent être sérialisables pour participer à un contrat de message. Pour plus d’informations, consultez la section « sérialisation » plus loin dans cette rubrique.  
  
### <a name="4-parameters"></a>4. Paramètres  

 Bien souvent, un développeur qui souhaite décrire une opération qui agit sur plusieurs éléments de données n'a pas besoin du niveau de contrôle fourni par les contrats de message. Par exemple, lors de la création de services, on ne souhaite généralement pas prendre de décision de type « nu ou encapsulé » et décider du nom de l'élément wrapper. Prendre ces décisions requiert souvent une connaissance approfondie des services Web et de SOAP.  
  
 L’infrastructure de service WCF peut sélectionner automatiquement la représentation SOAP la mieux adaptée et la plus interopérable pour l’envoi ou la réception de plusieurs éléments d’information connexes, sans imposer ces choix à l’utilisateur. Cela s'effectue en décrivant tout simplement ces éléments d'informations comme paramètres ou valeurs de retour d'un contrat d'opération. Examinons, par exemple, le contrat d'opération suivant :  
  
 [!code-csharp[C_DataArchitecture#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_dataarchitecture/cs/source.cs#11)]
 [!code-vb[C_DataArchitecture#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_dataarchitecture/vb/source.vb#11)]  
  
 L'infrastructure de service décide automatiquement de mettre l'ensemble des trois éléments d'information (`customerID`, `item`et `quantity`) dans le corps du message et de les encapsuler dans un élément wrapper appelé `SubmitOrderRequest`.  
  
 Décrire les informations à envoyer ou à recevoir sous forme d'une liste simple de paramètres de contrat d'opération est l'approche que nous recommandons, à moins qu'il existe des raisons particulières de passer à des modèles de programmation basée sur `Message`ou de contrat de message plus complexes.  
  
### <a name="5-stream"></a>5. Flux de données  

 L'utilisation de `Stream` ou de l'une de ses sous-classes dans un contrat d'opération en tant que partie de corps de message unique dans un contrat de message peut être considérée comme un modèle de programmation distincts de ceux décrits précédemment. L'utilisation de `Stream` de cette manière est le seul moyen de garantir que votre contrat sera utilisable dans le cadre d'une diffusion en continu, en écrivant en abrégé votre propre sous-classe `Message` compatible avec la diffusion en continu. Pour plus d’informations, consultez [données volumineuses et diffusion en continu](large-data-and-streaming.md).  
  
 Lorsque `Stream` ou l'une de ses sous-classes est utilisée de cette manière, le sérialiseur n'est pas appelé. Pour les messages sortants, une sous-classe `Message` de diffusion en continu spéciale est créée et le flux est écrit tel qu'indiqué dans la section sur l'interface <xref:System.Xml.IStreamProvider> . Pour les messages entrants, l'infrastructure de service crée une sous-classe `Stream` sur le message entrant et la fournit à l'opération.  
  
## <a name="programming-model-restrictions"></a>Restrictions du modèle de programmation  

 Les modèles de programmation décrits précédemment ne peuvent pas être combinés de manière arbitraire. Par exemple, si une opération accepte un type de contrat de message, le contrat de message doit être son seul paramètre d'entrée. En outre, l'opération doit ensuite retourner un message vide (type de retour void) ou un autre contrat de message. Ces restrictions sont décrites dans les rubriques relatives à chaque modèle de programmation spécifique : [Using Message Contracts](using-message-contracts.md), [Using the Message Class](using-the-message-class.md)et [Large Data and Streaming](large-data-and-streaming.md).  
  
## <a name="message-formatters"></a>Formateurs de messages  

 Les modèles de programmation décrits précédemment sont pris en charge en branchant des composants appelés *formateurs de messages* dans l'infrastructure de service. Les formateurs de messages sont des types qui implémentent l' <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> interface ou, ou les deux, pour une utilisation dans les clients et les clients WCF de service, respectivement.  
  
 Les formateurs de messages sont normalement branchés par les comportements. Par exemple, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> branche le formateur de messages de contrat de données. Cette opération s'effectue du côté service en affectant <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> au formateur correct dans la méthode <xref:System.ServiceModel.Description.IOperationBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.DispatchOperation%29> , ou du côté client en affectant <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> au formateur correct dans la méthode <xref:System.ServiceModel.Description.IOperationBehavior.ApplyClientBehavior%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Dispatcher.ClientOperation%29> .  
  
 Le tableau suivant répertorie les méthodes qu'un formateur de messages peut implémenter.  
  
|Interface|Méthode|Action|  
|---------------|------------|------------|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.DeserializeRequest%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Convertit un `Message` entrant en paramètres d'opération|  
|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter.SerializeReply%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%2CSystem.Object%29>|Crée un `Message` sortant à partir de la valeur de retour/des paramètres de sortie d'opération|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%28System.ServiceModel.Channels.MessageVersion%2CSystem.Object%5B%5D%29>|Crée un `Message` sortant à partir des paramètres d'opération|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%28System.ServiceModel.Channels.Message%2CSystem.Object%5B%5D%29>|Convertit un `Message` entrant en valeur de retour/paramètres de sortie|  
  
## <a name="serialization"></a>Sérialisation  

 Chaque fois que vous utilisez des contrats de message ou des paramètres pour décrire le contenu d’un message, vous devez utiliser la sérialisation pour effectuer la conversion entre les types .NET Framework et la représentation XML Infoset. La sérialisation est utilisée à d’autres emplacements dans WCF, par exemple, <xref:System.ServiceModel.Channels.Message> a une <xref:System.ServiceModel.Channels.Message.GetBody%2A> méthode générique que vous pouvez utiliser pour lire l’ensemble du corps du message désérialisé dans un objet.  
  
 WCF prend en charge deux technologies de sérialisation « prêtes à l’emploi » pour la sérialisation et la désérialisation des paramètres et des parties de message : <xref:System.Runtime.Serialization.DataContractSerializer> et `XmlSerializer` . En outre, vous pouvez écrire des sérialiseurs personnalisés. Toutefois, d’autres parties de WCF (telles que la `GetBody` méthode générique ou la sérialisation d’erreur SOAP) peuvent être restreintes pour utiliser uniquement les <xref:System.Runtime.Serialization.XmlObjectSerializer> sous-classes ( <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.NetDataContractSerializer> , mais pas <xref:System.Xml.Serialization.XmlSerializer> ), ou peuvent même être codées en dur pour utiliser uniquement <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 `XmlSerializer`Est le moteur de sérialisation utilisé dans les services Web ASP.net. `DataContractSerializer` est le nouveau moteur de sérialisation qui comprend le nouveau modèle de programmation de contrat de données. `DataContractSerializer` est l'option par défaut, et le choix d'utiliser `XmlSerializer` peut s'effectuer par opération à l'aide de l'attribut <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractFormatAttribute%2A> .  
  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> et <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> sont les comportements d'opération chargés de brancher les formateurs de messages de `DataContractSerializer` et `XmlSerializer`, respectivement. Le comportement <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> peut réellement fonctionner avec n'importe quel sérialiseur qui dérive de <xref:System.Runtime.Serialization.XmlObjectSerializer>, y compris <xref:System.Runtime.Serialization.NetDataContractSerializer> (décrit en détail dans Utilisation de la sérialisation autonome). Le comportement appelle l'une des surcharges de méthode virtuelle `CreateSerializer` pour obtenir le sérialiseur. Pour brancher un autre sérialiseur, créez une sous-classe <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> et substituez les deux surcharges `CreateSerializer` .  
  
## <a name="see-also"></a>Voir aussi

- [Spécification du transfert de données dans des contrats de service](specifying-data-transfer-in-service-contracts.md)
