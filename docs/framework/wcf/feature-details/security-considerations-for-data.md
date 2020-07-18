---
title: Considérations sur la sécurité des données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
ms.openlocfilehash: 530bb54936f97f1d7460d63cfa316c760cbd449d
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441815"
---
# <a name="security-considerations-for-data"></a>Considérations sur la sécurité des données

Lorsque vous traitez des données dans Windows Communication Foundation (WCF), vous devez prendre en compte un certain nombre de catégories de menaces. Le tableau suivant répertorie les classes de menace les plus importantes concernant le traitement de données. WCF fournit des outils pour atténuer ces menaces.

Déni de service lors de la réception de données non fiables, les données peuvent amener le côté réception à accéder à une quantité disproportionnée de diverses ressources, telles que la mémoire, les threads, les connexions disponibles ou les cycles de processeur, en provoquant des calculs de longue durée. Une attaque par déni de service contre un serveur peut engendrer son blocage et son incapacité à traiter les messages en provenance d'autres clients légitimes.

L’exécution de code malveillant des données non fiables entrantes provoque l’exécution par le côté réception du code qu’il n’avait pas prévu.

Divulgation d’informations : l’attaquant distant force le tiers destinataire à répondre à ses demandes de manière à divulguer plus d’informations que prévu.

## <a name="user-provided-code-and-code-access-security"></a>Code fourni par l'utilisateur et sécurité d'accès du code

Un certain nombre d’emplacements dans l’infrastructure Windows Communication Foundation (WCF) exécutent du code fourni par l’utilisateur. Par exemple, le moteur de sérialisation <xref:System.Runtime.Serialization.DataContractSerializer> peut appeler des accesseurs `set` de propriété fournis par l'utilisateur et des accesseurs `get` . L’infrastructure de canal WCF peut également appeler des classes dérivées fournies par l’utilisateur de la <xref:System.ServiceModel.Channels.Message> classe.

Il incombe à l'auteur du code de garantir qu'aucune faille de sécurité n'existe. Par exemple, si vous créez un type de contrat de données avec une propriété de membre de données de type entier, et que dans l'implémentation de l'accesseur `set` vous allouez un tableau en fonction de la valeur de la propriété, vous risquez une attaque par déni de service si un message malveillant contient une valeur extrêmement élevée pour ce membre. En général, évitez toutes les allocations basées sur des données entrantes ou un long traitement dans le code fourni par l'utilisateur (surtout si ce long traitement peut être provoqué par une petite quantité de données entrantes). Lorsque vous exécutez une analyse de sécurité du code fourni par l'utilisateur, assurez-vous de considérer également tous les cas d'échec (c'est-à-dire, toutes les branches de code où des exceptions sont levées).

Le dernier exemple de code fourni par l'utilisateur correspond au code figurant à l'intérieur de votre implémentation de service pour chaque opération. La sécurité de votre implémentation de service relève de votre responsabilité. Il est facile de créer par inadvertance des implémentations d'opérations incertaines qui peuvent provoquer des vulnérabilités au déni de service. Par exemple, une opération qui prend une chaîne et renvoie la liste des clients d'une base de données dont le nom commence par cette chaîne. Si vous utilisez une base de données volumineuse et que la chaîne passée comporte une seule lettre, votre code risque d'essayer de créer un message plus volumineux que toute la mémoire disponible, ce qui entraîne l'échec du service entier. (Un <xref:System.OutOfMemoryException> n’est pas récupérable dans le .NET Framework et entraîne toujours l’arrêt de votre application.)

Vous devez garantir qu'aucun code malveillant n'est intégré dans les divers points d'extensibilité. Cela est particulièrement vrai pour l'exécution en confiance partielle, pour le traitement des types issus d'assemblys d'un niveau de confiance partiel ou pour créer des composants utilisables par un code de niveau de confiance partiel. Pour plus d'informations, consultez « Menaces liées à une confiance partielle » dans une section ultérieure.

Notez que lors de l'exécution en confiance partielle, l'infrastructure de sérialisation de contrat de données prend en charge uniquement un sous-ensemble limité du modèle de programmation de contrat de données, par exemple, des types ou des membres de données privés qui utilisent l'attribut <xref:System.SerializableAttribute> ne sont pas pris en charge. Pour plus d’informations, consultez [confiance partielle](partial-trust.md).

## <a name="avoiding-unintentional-information-disclosure"></a>Éviter la divulgation d'informations involontaire

Dans le cadre de la conception de types sérialisables en gardant la sécurité à l'esprit, la divulgation d'informations est une préoccupation possible.

Observez les points suivants :

- Le modèle de programmation <xref:System.Runtime.Serialization.DataContractSerializer> autorise l'exposition de données privées et internes en dehors du type ou assembly pendant la sérialisation. En outre, la forme d'un type peut être exposée pendant l'exportation de schéma. Veillez à comprendre la projection de sérialisation de votre type. Si vous souhaitez que rien ne soit exposé, désactivez-en la sérialisation (par exemple, en n'appliquant pas l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> dans le cas d'un contrat de données).

- Soyez conscient que le même type peut avoir plusieurs projections de sérialisation, selon le sérialiseur utilisé. Le même type peut exposer un jeu de données lorsqu'il est utilisé avec <xref:System.Runtime.Serialization.DataContractSerializer> et un autre jeu de données lorsqu'il est utilisé avec <xref:System.Xml.Serialization.XmlSerializer>. Une utilisation accidentelle du mauvais sérialiseur peut entraîner une divulgation d'informations.

- L'utilisation de <xref:System.Xml.Serialization.XmlSerializer> en mode d'appel de procédure distante (RPC)/encodé hérité peut exposer involontairement la forme du graphique d'objets située sur le côté envoi au côté réception.

## <a name="preventing-denial-of-service-attacks"></a>Prévention des attaques par déni de service

### <a name="quotas"></a>Quotas

Entraîner le côté réception à allouer une quantité de mémoire importante constitue une attaque par déni de service potentielle. Alors que cette section se concentre sur les problèmes de consommation de mémoire provenant de messages volumineux, d'autres attaques peuvent se produire. Par exemple, les messages peuvent utiliser une quantité disproportionnée de temps de traitement.

Les attaques par déni de service sont habituellement atténuées à l'aide de quotas. Lorsqu'un quota est dépassé, une exception <xref:System.ServiceModel.QuotaExceededException> est normalement levée. Sans le quota, un message malveillant peut provoquer l'accès à toute la mémoire disponible, ce qui engendre une exception <xref:System.OutOfMemoryException> , ou l'accès à toutes les piles disponibles, ce qui engendre une <xref:System.StackOverflowException>.

Le scénario du dépassement de quota est récupérable ; s'il se produit dans un service en cours d'exécution, le message en cours de traitement est ignoré et le service continue à s'exécuter et traite d'autres messages. Toutefois, les scénarios de mémoire insuffisante et de dépassement de capacité de la pile ne sont pas récupérables dans le .NET Framework ; le service s’arrête s’il rencontre de telles exceptions.

Dans WCF, les quotas n’impliquent pas de pré-allocation. Par exemple, si le quota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> (existant sur différentes classes) a la valeur 128 Ko, cela ne signifie pas que 128 Ko sont automatiquement alloués pour chaque message. La quantité réelle allouée dépend de la taille réelle du message entrant.

De nombreux quotas sont disponibles au niveau de la couche transport. Il s'agit de quotas appliqués par le canal de transport spécifique en cours d'utilisation (HTTP, TCP, et ainsi de suite). Même si cette rubrique présente une partie de ces quotas, ceux-ci sont décrits de manière détaillée dans [Transport Quotas](transport-quotas.md).

### <a name="hashtable-vulnerability"></a>Vulnérabilité de table de hachage

Il existe une vulnérabilité lorsque les contrats de données contiennent des tables de hachage ou des collections. Ce problème se pose si un grand nombre de valeurs sont insérées dans une table de hachage où un grand nombre de ces valeurs génèrent la même valeur de hachage. Cela peut être utilisé comme attaque par déni de service.  Cette vulnérabilité peut être atténuée en définissant le quota de liaison MaxReceivedMessageSize. La prudence est de mise lors de la définition de ce quota, de façon à empêcher de telles attaques. Ce quota spécifie une limite supérieure pour la taille du message WCF. En outre, évitez d'utiliser des tables de hachage ou des collections dans les contrats de données.

## <a name="limiting-memory-consumption-without-streaming"></a>Limitation de la consommation de mémoire sans la diffusion en continu

Le modèle de sécurité lié aux messages volumineux dépend de l'utilisation de la diffusion en continu. Dans le cas simple de la non-diffusion en continu, les messages sont mis en mémoire tampon. Dans ce cas, utilisez le quota <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> sur <xref:System.ServiceModel.Channels.TransportBindingElement> ou sur les liaisons fournies par le système à des fins de protection contre les messages volumineux en limitant la taille maximale des messages auxquels accéder. Notez qu'un service peut traiter plusieurs messages en même temps. Dans ce cas, ils sont tous en mémoire. Utilisez la fonctionnalité de limitation pour atténuer cette menace.

Notez également que `MaxReceivedMessageSize` n'impose pas de limite supérieure à la consommation de mémoire par message, mais la restreint à un facteur constant. Par exemple, si `MaxReceivedMessageSize` s'élève à 1 Mo et qu'un message de 1 Mo est reçu puis désérialisé, de la mémoire supplémentaire est nécessaire pour contenir le graphique d'objets désérialisé, ce qui engendre une consommation de mémoire totale bien supérieure à 1 Mo. Pour cette raison, évitez de créer des types sérialisables qui pourraient provoquer une consommation de mémoire importante sans beaucoup de données entrantes. Par exemple, un contrat de données « MonContrat » avec 50 champs de données membres facultatifs et un 100 de champs privés supplémentaires pourraient être instanciés avec la construction XML « \<MyContract/> ». Ce XML provoque un accès de la mémoire pour 150 champs. Notez que les membres de données sont facultatifs par défaut. Le problème est aggravé lorsqu'un tel type fait partie d'un tableau.

`MaxReceivedMessageSize` uniquement ne suffit pas à empêcher toutes les attaques par déni de service. Par exemple, le désérialiseur peut être forcé à désérialiser un graphique d'objets très imbriqué (un objet qui contient un autre objet qui en contient encore un autre, et ainsi de suite) par un message entrant. <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Xml.Serialization.XmlSerializer> appellent des méthodes d'une manière imbriquée pour désérialiser de tels graphiques. L'imbrication profonde des appels de méthode peut provoquer une <xref:System.StackOverflowException>irrécupérable. Cette menace est atténuée en définissant le quota <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> de sorte à limiter le niveau d'imbrication XML, comme indiqué dans la section « Utilisation du XML en toute sécurité » plus loin dans cette rubrique.

L'affectation de la valeur `MaxReceivedMessageSize` à des quotas supplémentaires s'avère particulièrement importante lors de l'utilisation de l'encodage XML binaire. L'utilisation de l'encodage binaire équivaut presque à la compression : un petit groupe d'octets dans le message entrant peut représenter beaucoup de données. Ainsi, même un message qui respecte la limite `MaxReceivedMessageSize` peut consommer beaucoup plus de mémoire dans sa forme complètement développée. Pour atténuer de telles menaces propres au XML, tous les quotas de lecteur XML doivent être définis correctement, comme indiqué dans la section « Utilisation du XML en toute sécurité » plus loin dans cette rubrique.

## <a name="limiting-memory-consumption-with-streaming"></a>Limitation de la consommation de mémoire avec la diffusion en continu

Dans le cadre de la diffusion en continu, vous pouvez utiliser un petit paramètre `MaxReceivedMessageSize` à des fins de protection contre les attaques par déni de service. Toutefois, des scénarios plus compliqués sont possibles avec la diffusion en continu. Par exemple, un service de téléchargement de fichiers accepte des fichiers plus volumineux que toute la mémoire disponible. Dans ce cas, affectez à `MaxReceivedMessageSize` une valeur extrêmement élevée, en pensant que quasiment aucune donnée n'est mise en mémoire tampon et que le message se diffuse en continu directement sur le disque. Si un message malveillant peut forcer WCF à mettre en mémoire tampon des données au lieu de le diffuser dans ce cas, `MaxReceivedMessageSize` ne protège plus le message qui accède à toute la mémoire disponible.

Pour atténuer cette menace, des paramètres de quota spécifiques existent sur différents composants de traitement de données WCF qui limitent la mise en mémoire tampon. Le plus important de ces quotas est la propriété `MaxBufferSize` sur différents éléments de liaison de transport et liaisons standard. Dans le cadre de la diffusion en continu, ce quota doit être défini en tenant compte de la quantité de mémoire maximale que vous êtes disposé à allouer par message. Comme avec `MaxReceivedMessageSize`, le paramètre n'impose pas de maximum absolu à la consommation de mémoire mais il la limite à un facteur constant. En outre, comme avec `MaxReceivedMessageSize`, soyez conscient de la possibilité de traiter plusieurs messages en même temps.

### <a name="maxbuffersize-details"></a>Détails sur MaxBufferSize

La `MaxBufferSize` propriété limite la mise en mémoire tampon en bloc WCF. Par exemple, WCF met toujours en mémoire tampon les en-têtes SOAP et les erreurs SOAP, ainsi que toutes les parties MIME qui ne sont pas dans l’ordre de lecture naturel dans un message MTOM (Message Transmission Optimization Mechanism). Ce paramètre limite la quantité de mise en mémoire tampon dans tous ces cas.

WCF effectue cette opération en passant la `MaxBufferSize` valeur aux divers composants qui peuvent être mis en mémoire tampon. Par exemple, certaines surcharges <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> de la classe <xref:System.ServiceModel.Channels.Message> acceptent un paramètre `maxSizeOfHeaders` . WCF passe la `MaxBufferSize` valeur à ce paramètre pour limiter la quantité de mise en mémoire tampon d’en-tête SOAP. Il est important de définir ce paramètre lors de l'utilisation directe de la classe <xref:System.ServiceModel.Channels.Message> . En général, lors de l’utilisation d’un composant dans WCF qui prend des paramètres de quota, il est important de comprendre les implications en matière de sécurité de ces paramètres et de les définir correctement.

L'encodeur de message MTOM possède également un paramètre `MaxBufferSize` . Lorsque vous utilisez des liaisons standard, la valeur `MaxBufferSize` au niveau du transport est automatiquement affectée à ce paramètre. Toutefois, lorsque vous utilisez l'élément de la liaison de l'encodeur de message MTOM pour construire une liaison personnalisée, il est important d'affecter à la propriété `MaxBufferSize` une valeur sûre lorsque la diffusion en continu est utilisée.

## <a name="xml-based-streaming-attacks"></a>Attaques de diffusion en continu basées sur XML

`MaxBufferSize`seul n’est pas suffisant pour s’assurer que WCF ne peut pas être forcé dans la mise en mémoire tampon lorsque la diffusion en continu est attendue. Par exemple, les lecteurs XML WCF met toujours en mémoire tampon l’intégralité de la balise de début de l’élément XML lors du démarrage de la lecture d’un nouvel élément. Cette mise en mémoire tampon permet de traiter correctement les espaces de noms et les attributs. Si le paramètre `MaxReceivedMessageSize` est configuré afin d'être élevé (par exemple, pour permettre un scénario de diffusion en continu d'un fichier volumineux directement sur le disque), un message malveillant peut être construit dans lequel le corps du message entier est une balise de début d'élément XML volumineuse. Une tentative de le lire provoque une <xref:System.OutOfMemoryException>. Il s’agit de l’une des nombreuses attaques par déni de service XML possibles qui peuvent toutes être atténuées à l’aide de quotas de lecteur XML, abordés dans la section « utilisation du XML en toute sécurité » plus loin dans cette rubrique. Dans le cadre de la diffusion en continu, il s'avère particulièrement important de définir tous ces quotas.

### <a name="mixing-streaming-and-buffering-programming-models"></a>Combinaison des modèles de programmation de diffusion en continu et de mise en mémoire tampon

De nombreuses attaques possibles émanent du mélange de modèles de programmation de diffusion en continu et de non-diffusion en continu dans le même service. Supposez qu'il existe un contrat de service contenant deux opérations : une qui prend un <xref:System.IO.Stream> et une autre qui prend un tableau de type personnalisé. Supposez également qu'une valeur élevée est affectée à `MaxReceivedMessageSize` pour permettre à la première opération de traiter des flux volumineux. Malheureusement, cela signifie que des messages volumineux peuvent à présent être envoyés à la seconde opération, et que le désérialiseur met en mémoire tampon des données sous la forme d'un tableau avant d'appeler l'opération. Il s'agit d'une attaque par déni de service potentielle : le quota `MaxBufferSize` ne limite pas la taille du corps du message, avec laquelle le désérialiseur fonctionne.

Pour cette raison, évitez de combiner des opérations de diffusion et des opérations non diffusées dans le même contrat. Si vous devez absolument associer les deux modèles de programmation, prenez les précautions suivantes :

- Désactivez la fonctionnalité <xref:System.Runtime.Serialization.IExtensibleDataObject> en affectant à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> de <xref:System.ServiceModel.ServiceBehaviorAttribute> la valeur `true`. Cette désactivation permet de veiller à ce que seuls les membres qui font partie du contrat soient désérialisés.

- Affectez à la propriété <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> de <xref:System.Runtime.Serialization.DataContractSerializer> une valeur sûre. Ce quota est également disponible sur l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> ou via la configuration. Ce quota limite le nombre d'objets désérialisés au cours d'un épisode de désérialisation. Normalement, chaque paramètre d'opération ou partie de corps du message dans un contrat de message sont désérialisés dans un seul épisode. Lors de la désérialisation de tableaux, chaque entrée de tableau est comptée comme un objet distinct.

- Affectez à tous les quotas de lecteurs XML des valeurs sûres. Faites attention à <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>et <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> et évitez les chaînes dans les opérations de non-diffusion en continu.

- Consultez la liste des types connus, en n'oubliant pas que l'un d'eux peut être instancié à tout moment (consultez la section « Prévention du chargement de types involontaires » plus loin dans cette rubrique).

- N'utilisez pas les types qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable> qui met beaucoup de données en mémoire tampon. N'ajoutez pas de tels types à la liste des types connus.

- N'utilisez pas les tableaux <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> , <xref:System.Byte> ou des types qui implémentent <xref:System.Runtime.Serialization.ISerializable> dans un contrat.

- N'utilisez pas les tableaux <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> , <xref:System.Byte> ou des types qui implémentent <xref:System.Runtime.Serialization.ISerializable> dans la liste des types connus.

Les précautions précédentes s'appliquent lorsque l'opération de non-diffusion en continu utilise <xref:System.Runtime.Serialization.DataContractSerializer>. Ne mélangez jamais les modèles de programmation de diffusion en continu et de non-diffusion en continu sur le même service si vous utilisez <xref:System.Xml.Serialization.XmlSerializer>, parce qu'il ne possède pas la protection du quota <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> .

### <a name="slow-stream-attacks"></a>Attaques de flux lent

Une classe d'attaques par déni de service de diffusion en continu n'implique pas la consommation de mémoire. Cette attaque implique plutôt un expéditeur ou destinataire lent des données. En attendant que les données soient envoyées ou reçues, des ressources telles que des threads et des connexions disponibles s'épuisent. Cette situation peut survenir soit à la suite d'une attaque malveillante, soit à partir d'un expéditeur/destinataire légitime sur une connexion réseau lente.

Pour réduire ces attaques, définissez correctement les délais d'attente de transport. Pour plus d’informations, consultez [quotas de transport](transport-quotas.md). Deuxièmement, n’utilisez jamais `Read` des opérations synchrones ou `Write` lorsque vous utilisez des flux dans WCF.

## <a name="using-xml-safely"></a>Utilisation du XML en toute sécurité

> [!NOTE]
> Même si cette section est consacrée au XML, les informations s'appliquent aussi aux documents JSON (JavaScript Object Notation). Les quotas fonctionnent de manière identique et utilisent [Mapping Between JSON and XML](mapping-between-json-and-xml.md).

### <a name="secure-xml-readers"></a>Lecteurs XML sécurisés

Le jeu d’informations XML forme la base de tout le traitement des messages dans WCF. Lors de l'acceptation de données XML provenant d'une source non fiable, il existe plusieurs possibilités d'attaques par déni de service qu'il convient d'atténuer. WCF fournit des lecteurs XML spécifiques et sécurisés. Ces lecteurs sont créés automatiquement lors de l’utilisation de l’un des encodages standard dans WCF (texte, binaire ou MTOM).

Certaines des fonctionnalités de sécurité sur ces lecteurs sont toujours actives. Par exemple, les lecteurs ne traitent jamais les définitions de type de document (DTD), qui constituent une source potentielle d'attaques par déni de service et ne doivent jamais apparaître dans les messages SOAP légitimes. D'autres fonctionnalités de sécurité incluent des quotas de lecteurs à configurer, lesquels sont décrits dans la section suivante.

Quand vous travaillez directement avec des lecteurs XML (par exemple, lors de l’écriture de votre propre encodeur personnalisé ou lorsque vous travaillez directement avec la <xref:System.ServiceModel.Channels.Message> classe), utilisez toujours les lecteurs sécurisés WCF lorsqu’il existe un risque d’utilisation de données non fiables. Créez les lecteurs sécurisés en appelant l'une des surcharges de méthode de fabrique statique de <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>ou <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> sur la classe <xref:System.Xml.XmlDictionaryReader> . Lorsque vous créez un lecteur, passez des valeurs de quotas sécurisées. N'appelez pas les surcharges de la méthode `Create` . Celles-ci ne créent pas de lecteur WCF. Elles créent un lecteur qui n'est pas protégé par les fonctionnalités de sécurité décrites dans cette section.

### <a name="reader-quotas"></a>Quotas de lecteurs

Les lecteurs XML sécurisés possèdent cinq quotas configurables. Ceux-ci sont normalement configurés à l'aide de la propriété `ReaderQuotas` sur les éléments de liaison d'encodage ou les liaisons standard, ou encore en utilisant un objet <xref:System.Xml.XmlDictionaryReaderQuotas> passé lors de la création d'un lecteur.

#### <a name="maxbytesperread"></a>MaxBytesPerRead

Ce quota limite le nombre d'octets lus dans une seule opération `Read` lors de la lecture de la balise de début d'élément et ses attributs. (Dans les cas non diffusés en continu, le nom de l’élément lui-même n’est pas compté dans le quota.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> est importante pour les raisons suivantes :

- Le nom de l'élément et ses attributs sont toujours mis en mémoire tampon lorsqu'ils sont lus. Par conséquent, il est important de définir correctement ce quota en mode de diffusion en continu afin d'empêcher une mise en mémoire tampon excessive lorsqu'une diffusion en continu est prévue. Reportez-vous à la section sur les quotas `MaxDepth` ci-dessous pour plus d'informations sur l'importance réelle de la mise en mémoire tampon qui se produit.

- Un nombre trop élevé d'attributs XML risque d'utiliser un temps de traitement disproportionné parce que le caractère unique des noms d'attributs doit être vérifié. `MaxBytesPerRead` atténue cette menace.

#### <a name="maxdepth"></a>MaxDepth

Ce quota limite la profondeur d'imbrication maximale des éléments XML. Par exemple, le document « \<A> \<B> \<C/> \</B> \</A> » a une profondeur d’imbrication de trois. La propriété<xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> est importante pour les raisons suivantes :

- `MaxDepth` interagit avec `MaxBytesPerRead`: le lecteur conserve toujours des données en mémoire pour l'élément actuel et tous ses ancêtres, donc la consommation de mémoire maximale du lecteur est proportionnelle au produit de ces deux paramètres.

- Lors de la désérialisation d'un graphique d'objets très imbriqué, le désérialiseur est obligé d'accéder à la pile entière et de lever une exception <xref:System.StackOverflowException>irrécupérable. Une corrélation directe existe entre l'imbrication XML et l'imbrication d'objets pour <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Xml.Serialization.XmlSerializer>. Utilisez `MaxDepth` pour atténuer cette menace.

#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount

Ce quota limite la taille du *nametable*du lecteur. Le nametable contient certaines chaînes (telles que des espaces de noms et des préfixes) rencontrées lors du traitement d'un document XML. Étant donné que ces chaînes sont mises en mémoire tampon, définissez ce quota afin d'empêcher une mise en mémoire tampon excessive lorsqu'une diffusion en continu est prévue.

#### <a name="maxstringcontentlength"></a>MaxStringContentLength

Ce quota limite la taille maximale de la chaîne que le lecteur XML renvoie. Ce quota ne limite pas la consommation de mémoire dans le lecteur XML lui-même, mais dans le composant qui utilise le lecteur. Par exemple, lorsque <xref:System.Runtime.Serialization.DataContractSerializer> utilise un lecteur sécurisé avec <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, il ne désérialise pas les chaînes supérieures à ce quota. Lorsque vous utilisez directement la classe <xref:System.Xml.XmlDictionaryReader> , toutes les méthodes ne respectent pas ce quota, mais uniquement les méthodes particulièrement conçues pour lire des chaînes, telles que la méthode <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> . La propriété <xref:System.Xml.XmlReader.Value%2A> sur le lecteur n'est pas affectée par ce quota. Vous ne devez donc pas utiliser cette propriété lorsque la protection que ce quota fournit est nécessaire.

#### <a name="maxarraylength"></a>MaxArrayLength

Ce quota limite la taille maximale d'un tableau de primitives que le lecteur XML renvoie, notamment un tableau d'octets. Ce quota ne limite pas la consommation de mémoire dans le lecteur XML lui-même, mais dans le composant qui utilise le lecteur. Par exemple, lorsque <xref:System.Runtime.Serialization.DataContractSerializer> utilise un lecteur sécurisé avec <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, il ne désérialise pas les tableaux d'octets supérieurs à ce quota. Il est important de définir ce quota lorsque vous essayez de combiner des modèles de programmation mis en mémoire tampon et de diffusion en continu dans un contrat unique. N'oubliez pas que lorsque vous utilisez directement la classe <xref:System.Xml.XmlDictionaryReader> , seules les méthodes particulièrement conçues pour lire les tableaux de taille arbitraire de certains types de primitives, tels que <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, respectent ce quota.

## <a name="threats-specific-to-the-binary-encoding"></a>Menaces propres à l'encodage binaire

L’encodage XML binaire pris en charge par WCF comprend une fonctionnalité de *chaînes de dictionnaire* . Une grande chaîne peut être encodée à l'aide de seulement quelques octets. Cette fonctionnalité permet des gains de performance significatifs, mais introduit de nouvelles menaces de déni de service à atténuer.

Il existe deux types de dictionnaires : *statiques* et *dynamiques*. Le dictionnaire statique est une liste intégrée de longues chaînes qui peuvent être représentées à l'aide d'un code court dans l'encodage binaire. Cette liste de chaînes est déterminée lorsque le lecteur est créé et ne peut pas être modifiée. Aucune des chaînes du dictionnaire statique que WCF utilise par défaut n’est suffisamment grande pour poser une menace de déni de service sérieuse, bien qu’elles puissent toujours être utilisées dans une attaque par expansion de dictionnaire. Dans les scénarios complexes où vous fournissez votre propre dictionnaire statique, faites preuve de prudence lorsque vous introduisez de grandes chaînes de dictionnaire.

Les dictionnaires dynamiques permettent aux messages de définir leurs propres chaînes et de les associer à des codes courts. Ces mappages de chaînes à du code sont conservés en mémoire pendant toute la session de communication, de sorte à ce que les messages suivants n'aient pas à renvoyer les chaînes et puissent utiliser les codes déjà définis. Ces chaînes peuvent être de longueur arbitraire et représentent donc une menace plus sérieuse que celles du dictionnaire statique.

La première menace à atténuer est la possibilité qu'a le dictionnaire dynamique (le tableau de mappage des chaînes à du code) de devenir trop volumineux. Ce dictionnaire peut se développer au cours de plusieurs messages, et ainsi, le quota `MaxReceivedMessageSize` n'offre aucune protection parce qu'il s'applique uniquement à chaque message séparément. Par conséquent, une propriété <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> distincte existe sur <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> qui limite la taille du dictionnaire.

À la différence de la plupart des autres quotas, ce quota s'applique également lors de l'écriture de messages. S'il est dépassé lors de la lecture d'un message, `QuotaExceededException` est levée comme d'habitude. S'il est dépassé lors de l'écriture d'un message, toutes les chaînes qui provoquent le dépassement du quota sont écrites en l'état, sans utiliser la fonctionnalité des dictionnaires dynamiques.

### <a name="dictionary-expansion-threats"></a>Menaces d'expansion de dictionnaire

Une importante classe d'attaques propres au binaire provient de l'expansion des dictionnaires. Un petit message au format binaire peut devenir un message très volumineux au format texte complètement développé s'il utilise de manière excessive la fonctionnalité des dictionnaires de chaînes. Le facteur d'expansion pour les chaînes de dictionnaires dynamiques est limité par le quota <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> , parce qu'aucune chaîne de dictionnaire dynamique ne dépasse la taille maximale du dictionnaire entier.

Les propriétés <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`et `MaxArrayLength` limitent seulement la consommation de mémoire. Elles ne sont normalement pas nécessaires pour atténuer toutes les menaces liées à la non-diffusion en continu parce que l'utilisation de la mémoire est déjà limitée par `MaxReceivedMessageSize`. Toutefois, `MaxReceivedMessageSize` compte les octets de préexpansion. Lorsque vous utilisez l'encodage binaire, la consommation de mémoire peut dépasser la valeur `MaxReceivedMessageSize`, uniquement limitée par un facteur de <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Pour cette raison, il est important de toujours définir tous les quotas de lecteurs (surtout <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) lors de l'utilisation de l'encodage binaire.

Lors de l'utilisation de l'encodage binaire avec <xref:System.Runtime.Serialization.DataContractSerializer>, l'interface `IExtensibleDataObject` peut être employée à mauvais escient pour monter une attaque par expansion de dictionnaire. Cette interface fournit principalement le stockage illimité des données arbitraires qui ne font pas partie du contrat. S'il n'est pas possible de définir les quotas à un niveau suffisamment bas pour que la valeur `MaxSessionSize` multipliée par la valeur `MaxReceivedMessageSize` ne pose pas de problème, désactivez la fonctionnalité `IExtensibleDataObject` lors de l'utilisation de l'encodage binaire. Affectez à la propriété `IgnoreExtensionDataObject` la valeur `true` sur l'attribut `ServiceBehaviorAttribute` . Vous pouvez également ne pas implémenter l'interface `IExtensibleDataObject` . Pour plus d’informations, consultez [Contrats de données compatibles avec des versions ultérieures](forward-compatible-data-contracts.md).

### <a name="quotas-summary"></a>Résumé des quotas

Le tableau suivant résume les conseils relatifs aux quotas.

|Condition|Quotas importants à définir|
|---------------|-----------------------------|
|Aucune diffusion en continu ou diffusion en continu de petits messages, texte ou encodage MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead` et `MaxDepth`|
|Aucune diffusion en continu ou diffusion en continu de petits messages, encodage binaire|`MaxReceivedMessageSize`, `MaxSessionSize`et tous les `ReaderQuotas`|
|Diffusion en continu de messages, texte ou encodage MTOM volumineux|`MaxBufferSize` et tous les `ReaderQuotas`|
|Diffusion en continu de messages, encodage binaire volumineux|`MaxBufferSize`, `MaxSessionSize`et tous les `ReaderQuotas`|

- Les délais d'attente au niveau du transport doivent toujours être définis et ne jamais utiliser des lectures/écritures synchrones lorsque la diffusion en continu est utilisée, que vous diffusiez en continu des messages volumineux ou non.

- Lorsque vous n'êtes pas sûr d'un quota, affectez-lui une valeur sûre plutôt que de le laisser ouvert.

## <a name="preventing-malicious-code-execution"></a>Prévention de l'exécution de code malveillant

Les classes générales suivantes de menaces peuvent exécuter du code et avoir des effets involontaires :

- Le désérialiseur charge un type malveillant, potentiellement dangereux ou sensible pour la sécurité.

- Un message entrant provoque la construction par le désérialiseur d'une instance d'un type normalement sûr de façon à ce qu'elle engendre des conséquences involontaires.

Les sections suivantes présentent de manière plus approfondie ces classes de menaces.

## <a name="datacontractserializer"></a>DataContractSerializer

(Pour obtenir des informations de sécurité sur le <xref:System.Xml.Serialization.XmlSerializer> , consultez la documentation correspondante.) Le modèle de sécurité de <xref:System.Xml.Serialization.XmlSerializer> est similaire à celui de <xref:System.Runtime.Serialization.DataContractSerializer> , et diffère principalement en détail. Par exemple, l'attribut <xref:System.Xml.Serialization.XmlIncludeAttribute> est utilisé pour l'inclusion de type au lieu de l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute> . Toutefois, certaines menaces propres à <xref:System.Xml.Serialization.XmlSerializer> sont présentées plus loin dans cette rubrique.

### <a name="preventing-unintended-types-from-being-loaded"></a>Prévention du chargement de types involontaires

Le chargement de types involontaires peut avoir de lourdes conséquences, que le type soit malveillant ou qu'il implique simplement des effets secondaires sensibles pour la sécurité. Un type peut contenir une faille de sécurité exploitable, exécuter des actions sensibles pour la sécurité dans son constructeur ou son constructeur de classe, subir un grand encombrement de mémoire qui facilite les attaques par déni de service ou lever des exceptions irrécupérables. Les types peuvent avoir des constructeurs de classe qui s'exécutent dès que le type est chargé et avant qu'une instance ne soit créée. Pour ces raisons, il est important de contrôler le jeu de types que le désérialiseur peut charger.

<xref:System.Runtime.Serialization.DataContractSerializer> désérialise d'une manière faiblement couplée. Il ne lit jamais le type CLR (Common Language Runtime) ni les noms d'assembly à partir des données entrantes. Ce comportement est similaire à celui de <xref:System.Xml.Serialization.XmlSerializer>, mais diffère de celui de <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>et de <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Le couplage faible introduit un degré de sécurité, parce que l'intrus distant ne peut pas indiquer un type arbitraire à charger en se contentant de le nommer dans le message.

<xref:System.Runtime.Serialization.DataContractSerializer> est toujours autorisé à charger un type actuellement prévu conformément au contrat. Par exemple, si un contrat de données comporte un membre de données du type `Customer`, <xref:System.Runtime.Serialization.DataContractSerializer> est autorisé à charger le type `Customer` lorsqu'il désérialise ce membre de données.

En outre, <xref:System.Runtime.Serialization.DataContractSerializer> prend en charge le polymorphisme. Un membre de données peut être déclaré comme <xref:System.Object>, mais les données entrantes peuvent contenir une instance `Customer` . Cette situation est possible uniquement si le type `Customer` a été indiqué au désérialiseur via l'un de ces mécanismes :

- attribut<xref:System.Runtime.Serialization.KnownTypeAttribute> appliqué à un type ;

- attribut`KnownTypeAttribute` qui spécifie une méthode qui renvoie une liste de types ;

- attribut`ServiceKnownTypeAttribute` ;

- section de configuration `KnownTypes` ;

- liste des types connus passée explicitement à <xref:System.Runtime.Serialization.DataContractSerializer> pendant la construction, en cas d'utilisation directe du sérialiseur.

Chacun de ces mécanismes augmente la surface d'exposition en introduisant plus de types que le désérialiseur est capable de charger. Contrôlez chacun de ces mécanismes pour vérifier qu'aucun type malveillant ou involontaire n'est ajouté à la liste des types connus.

Une fois qu'un type connu se trouve dans la portée, il peut être chargé à tout moment, et des instances du type peuvent être créées, même si le contrat en interdit l'utilisation. Par exemple, supposez que le type « MyDangerousType » soit ajouté à la liste des types connus à l'aide de l'un des mécanismes ci-dessus. Cela signifie que :

- `MyDangerousType` est chargé et son constructeur de classe s'exécute.

- Même lors de la désérialisation d'un contrat de données avec un membre de données de chaîne, un message malveillant peut quand même provoquer la création d'une instance de `MyDangerousType` . Le code inclus dans `MyDangerousType`, tel que les accesseurs Set de propriété, peuvent s'exécuter. À l'issue de cette exécution, le désérialiseur essaie d'assigner cette instance au membre de données de chaîne et échoue avec une exception.

Lors de l'écriture d'une méthode qui renvoie la liste des types connus, ou lors du passage directe d'une liste au constructeur <xref:System.Runtime.Serialization.DataContractSerializer> , vérifiez que le code qui prépare la liste est sécurisé et qu'il fonctionne uniquement sur les données approuvées.

Lors de la spécification de types connus dans la configuration, vérifiez que le fichier de configuration est sécurisé. Utilisez toujours des noms forts dans la configuration (en spécifiant la clé publique de l'assembly signé où le type réside), mais ne spécifiez pas la version du type à charger. Le chargeur de type choisit automatiquement la version la plus récente, si possible. Si vous spécifiez une version particulière dans la configuration, vous exécutez le risque suivant : un type peut comporter une faille de sécurité qui peut être résolue dans une future version, mais la version vulnérable continue de se charger parce qu'elle sera spécifiée explicitement dans la configuration.

Un nombre trop élevé de types connus a une autre conséquence : <xref:System.Runtime.Serialization.DataContractSerializer> crée un cache de code de sérialisation/désérialisation dans le domaine d'application, avec une entrée pour chaque type qu'il doit sérialiser et désérialiser. Ce cache n'est jamais effacé tant que le domaine d'application s'exécute. Par conséquent, un intrus qui sait qu'une application utilise de nombreux types connus peut provoquer la désérialisation de tous ces types, ce qui engendre la consommation d'une quantité de mémoire disproportionnellement élevée par le cache.

### <a name="preventing-types-from-being-in-an-unintended-state"></a>Prévention des états involontaires affectés aux types

Un type peut avoir des contraintes de cohérence interne qui doivent être appliquées. Il faut veiller à ne pas violer ces contraintes pendant la désérialisation.

L'exemple de type suivant représente l'état d'un sas dans un vaisseau spatial et applique la contrainte selon laquelle les portes intérieure et extérieure ne peuvent pas être ouvertes en même temps.

[!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
[!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]

Un intrus peut envoyer un message malveillant comme celui-ci, qui contourne les contraintes et fait passer l'objet dans un état non valide, susceptible d'avoir des conséquences involontaires et imprévisibles.

```xml
<SpaceStationAirlock>
    <innerDoorOpen>true</innerDoorOpen>
    <outerDoorOpen>true</outerDoorOpen>
</SpaceStationAirlock>
```

Cette situation peut être évitée en prenant conscience des points suivants :

- Lorsque <xref:System.Runtime.Serialization.DataContractSerializer> désérialise la plupart des classes, les constructeurs ne s'exécutent pas. Par conséquent, ne comptez pas sur la gestion d'état effectuée dans le constructeur.

- Utilisez des rappels pour veiller à ce que l'objet soit dans un état valide. Le rappel marqué avec l'attribut <xref:System.Runtime.Serialization.OnDeserializedAttribute> s'avère particulièrement utile parce qu'il s'exécute à la fin de la désérialisation et parce qu'il obtient une occasion d'examiner et de corriger l'état global. Pour plus d’informations, consultez [rappels de sérialisation avec tolérance de version](version-tolerant-serialization-callbacks.md).

- Ne concevez pas de types de contrat de données de sorte à compter sur un ordre particulier dans lequel les accesseurs Set de propriété doivent être appelés.

- Faites preuve de prudence lorsque vous utilisez des types hérités marqués avec l'attribut <xref:System.SerializableAttribute> . Un grand nombre d’entre eux ont été conçus pour fonctionner avec .NET Framework Remoting pour une utilisation avec des données approuvées uniquement. Les types existants marqués avec cet attribut n'ont peut-être pas été conçus en tenant compte de la sécurité des états.

- Ne comptez pas sur la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> de l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> pour garantir la présence des données en ce qui concerne la sécurité des états. Les données pourraient toujours être `null`, `zero`ou `invalid`.

- N'approuvez jamais un graphique d'objets désérialisé provenant d'une source de données non fiable sans le valider au préalable. Chaque objet individuel peut être dans un état cohérent, à la différence du graphique d'objets dans son ensemble. En outre, même si le mode de conservation des graphiques d'objets est désactivé, le graphique désérialisé peut avoir plusieurs références au même objet ou des références circulaires. Pour plus d’informations, consultez [sérialisation et désérialisation](serialization-and-deserialization.md).

### <a name="using-the-netdatacontractserializer-securely"></a>Utilisation de NetDataContractSerializer en toute sécurité

<xref:System.Runtime.Serialization.NetDataContractSerializer> est un moteur de sérialisation qui utilise le couplage étroit des types. Ce moteur est similaire à <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> et à <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Autrement dit, il détermine le type à instancier en lisant l’assembly de .NET Framework et le nom de type à partir des données entrantes. Bien qu’il fasse partie de WCF, il n’existe aucun moyen de brancher ce moteur de sérialisation. le code personnalisé doit être écrit. `NetDataContractSerializer`Est fourni principalement pour faciliter la migration de .NET Framework communication à distance vers WCF. Pour plus d’informations, consultez la section relative à la [sérialisation et à la désérialisation](serialization-and-deserialization.md).

Parce que le message lui-même peut indiquer la possibilité de charger tout type, le mécanisme <xref:System.Runtime.Serialization.NetDataContractSerializer> est par sa nature incertain et doit être utilisé uniquement avec des données approuvées. Pour plus d’informations, consultez le [Guide de sécurité BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide).

Même en cas d'utilisation avec des données approuvées, les données entrantes peuvent spécifier insuffisamment le type à charger, surtout si la propriété <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> a la valeur <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Toute personne ayant accès au répertoire de l'application ou au Global Assembly Cache peut remplacer par un type malveillant celui qui est supposé se charger. Vérifiez toujours la sécurité du répertoire de votre application et du Global Assembly Cache en définissant correctement les autorisations.

En général, si vous autorisez l'accès du code de niveau de confiance partiel à votre instance `NetDataContractSerializer` ou le contrôle du sélecteur de substitut (<xref:System.Runtime.Serialization.ISurrogateSelector>) ou le binder de sérialisation (<xref:System.Runtime.Serialization.SerializationBinder>), le code risque de contrôler en grande partie le processus de sérialisation/désérialisation. Par exemple, il peut injecter des types arbitraires, entraîner la divulgation d'informations, falsifier les données sérialisées ou le graphique résultant ou dépasser le flux sérialisé résultant.

Un autre problème de sécurité avec `NetDataContractSerializer` est le déni de service, qui n'est pas une menace d'exécution de code malveillant. Lorsque vous utilisez `NetDataContractSerializer`, affectez toujours au quota <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> une valeur sûre. Il est facile de construire un petit message malveillant qui alloue un tableau d'objets dont la taille est limitée uniquement par ce quota.

### <a name="xmlserializer-specific-threats"></a>Menaces propres à XmlSerializer

Le modèle de sécurité <xref:System.Xml.Serialization.XmlSerializer> est similaire à celui de <xref:System.Runtime.Serialization.DataContractSerializer>. Toutefois, quelques menaces sont propres à <xref:System.Xml.Serialization.XmlSerializer>.

<xref:System.Xml.Serialization.XmlSerializer> génère des *assemblys de sérialisation* au moment de l'exécution qui contiennent du code qui sérialise et désérialise réellement ; ces assemblys sont créés dans un répertoire de fichiers temporaires. Si un autre processus ou utilisateur a des droits d'accès à ce répertoire, il peut remplacer le code de sérialisation/désérialisation par du code arbitraire. <xref:System.Xml.Serialization.XmlSerializer> exécute alors ce code à l'aide de son contexte de sécurité, au lieu du code de sérialisation/désérialisation. Assurez-vous que les autorisations sont correctement définies sur le répertoire de fichiers temporaires afin d'empêcher ce remplacement.

<xref:System.Xml.Serialization.XmlSerializer> possède également un mode dans lequel il utilise des assemblys de sérialisation préalablement générés au lieu de les générer au moment de l'exécution. Ce mode est déclenché chaque fois que <xref:System.Xml.Serialization.XmlSerializer> peut détecter un assembly de sérialisation approprié. <xref:System.Xml.Serialization.XmlSerializer> vérifie si l'assembly de sérialisation a été signé ou non par la même clé que celle utilisée pour signer l'assembly qui contient les types en cours de sérialisation. Cette vérification offre une protection contre les assemblys malveillants déguisés en assemblys de sérialisation. Toutefois, si l'assembly qui contient vos types sérialisables n'est pas signé, <xref:System.Xml.Serialization.XmlSerializer> ne peut pas effectuer cette vérification et utilise alors tout assembly dont le nom est correct. L'exécution de code malveillant est alors possible. Signez toujours les assemblys qui contiennent vos types sérialisables ou contrôlez de près l'accès au répertoire de votre application et au Global Assembly Cache pour empêcher l'introduction d'assemblys malveillants.

<xref:System.Xml.Serialization.XmlSerializer> peut être l'objet d'une attaque par déni de service. <xref:System.Xml.Serialization.XmlSerializer> n'a pas de quota `MaxItemsInObjectGraph` (tel que celui disponible sur <xref:System.Runtime.Serialization.DataContractSerializer>). Ainsi, il désérialise une quantité arbitraire d'objets, limitée uniquement par la taille du message.

### <a name="partial-trust-threats"></a>Menaces liées à une confiance partielle

Notez les préoccupations suivantes concernant des menaces liées à l'exécution de code avec un niveau de confiance partielle. Ces menaces incluent le code malveillant de niveau de confiance partiel aussi bien que le code malveillant de niveau de confiance partiel en association avec d'autres scénarios d'attaque (par exemple, du code de niveau de confiance partiel qui construit une chaîne spécifique, puis qui la désérialise).

- Lorsque vous utilisez des composants de sérialisation, ne déclarez jamais des autorisations avant cette utilisation, même si le scénario de sérialisation entier s'intègre dans la portée de votre assertion et si vous ne traitez pas des données ou objets non fiables. Une telle utilisation peut engendrer des failles de sécurité.

- Dans les cas où le code de confiance partielle contrôle le processus de sérialisation, soit par le biais des points d'extensibilité (substituts), des types sérialisés, soit par d'autres moyens, ce code peut forcer le sérialiseur à générer une grande quantité de données dans le flux sérialisé, ce qui peut entraîner un déni de service auprès du récepteur du flux. Si vous sérialisez des données destinées à une cible exposée à des menaces de déni de service, ne sérialisez pas les types de confiance partielle, ou sinon laissez le code de confiance partielle contrôler la sérialisation.

- Si vous autorisez l’accès du code de confiance partielle à votre <xref:System.Runtime.Serialization.DataContractSerializer> instance ou si vous contrôlez les [substituts de contrat de données](../extending/data-contract-surrogates.md), cela peut exercer un grand contrôle sur le processus de sérialisation/désérialisation. Par exemple, il peut injecter des types arbitraires, entraîner la divulgation d'informations, falsifier les données sérialisées ou le graphique résultant ou dépasser le flux sérialisé résultant. Une menace <xref:System.Runtime.Serialization.NetDataContractSerializer> équivalente est décrite dans la section « Utilisation de NetDataContractSerializer en toute sécurité ».

- Si l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> est appliqué à un type (ou au type marqué comme <xref:System.SerializableAttribute> mais qu'il n'est pas <xref:System.Runtime.Serialization.ISerializable>), le désérialiseur peut créer une instance d'un tel type même si tous les constructeurs sont non publics ou protégés par des demandes.

- N'approuvez jamais le résultat de la désérialisation sauf si les données à désérialiser sont approuvées et que vous êtes certain que tous les types connus sont des types que vous approuvez. Notez que les types connus ne sont pas chargés depuis le fichier de configuration de l'application (mais sont chargés depuis le fichier de configuration de l'ordinateur) lorsqu'ils s'exécutent en confiance partielle.

- Si vous passez une instance <xref:System.Runtime.Serialization.DataContractSerializer> avec un substitut ajouté au code de niveau de confiance partiel, le code peut modifier tous les paramètres modifiables sur ce substitut.

- Pour un objet désérialisé, si le lecteur XML (ou les données qui s'y trouvent) vient de code de niveau de confiance partiel, traitez l'objet désérialisé obtenu comme des données non fiables.

- Le fait que le type <xref:System.Runtime.Serialization.ExtensionDataObject> n'ait pas de membres publics ne signifie pas que les données qu'il contient sont sécurisées. Par exemple, si vous désérialisez à partir d'une source de données privilégiée dans un objet dans lequel certaines données résident, puis remettez cet objet à du code de niveau de confiance partiel, le code de niveau de confiance partiel peut lire les données dans `ExtensionDataObject` en sérialisant l'objet. Envisagez d'affecter à <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> la valeur `true` lors d'une désérialisation à partir d'une source de données privilégiée dans un objet qui est passé ultérieurement à du code de niveau de confiance partiel.

- <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> prennent en charge la sérialisation de membres privés, protégés, internes et publics en mode de confiance totale. Toutefois, en mode de confiance partielle, seuls les membres publics peuvent être sérialisés. Une <xref:System.Security.SecurityException> est levée si une application tente de sérialiser un membre qui n'est pas public.

    Pour autoriser la sérialisation de membres internes ou protégés en mode de confiance partielle, utilisez l'attribut d'assembly <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> . Cet attribut permet à un assembly de déclarer que ses membres internes sont visibles à certains autres assemblys. Dans ce cas, un assembly qui souhaite sérialiser ses membres internes déclare que ces derniers sont visibles à System.Runtime.Serialization.dll.

    L'avantage de cette approche réside dans le fait qu'elle ne nécessite pas de chemin de génération de code élevé.

    Toutefois, elle présente deux inconvénients principaux.

    Le premier étant que la propriété de sélection de l'attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> est au niveau de l'assembly. En d'autres termes, vous ne pouvez pas spécifier que seule une certaine classe peut avoir ses membres internes sérialisés. Il va de soi que vous pouvez toujours choisir de ne pas sérialiser un membre interne spécifique, en n'ajoutant pas d'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à ce membre. De la même façon, un développeur peut aussi choisir de rendre un membre interne au lieu de privé ou protégé, avec de légers problèmes de visibilité.

    Le second réside dans le fait que cette approche ne prend pas encore en charge les membres privés ou protégés.

    Pour illustrer l'utilisation de l'attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> en mode de confiance partielle, prenons l'exemple du programme suivant :

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]

    Dans l'exemple ci-dessus, l'objet `PermissionsHelper.InternetZone` correspond à l'objet <xref:System.Security.PermissionSet> en mode de confiance partielle. Désormais, sans l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut, l’application échouera, en levant une <xref:System.Security.SecurityException> indiquant que les membres non publics ne peuvent pas être sérialisés en confiance partielle.

    Toutefois, si nous ajoutons la ligne suivante au fichier source, le programme s'exécute.

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]

## <a name="other-state-management-concerns"></a>Autres préoccupations liées à la gestion d'état

Il est judicieux de mentionner quelques autres préoccupations liées à la gestion d'état d'objet :

- Lors de l'utilisation du modèle de programmation basé sur le flux avec un transport de diffusion en continu, le traitement du message se produit au moment où le message arrive. L'expéditeur du message peut abandonner l'opération d'envoi en cours de flux, ce qui laisse votre code dans un état imprévisible si davantage de contenu était attendu. En général, ne comptez pas sur l'exhaustivité du flux et n'exécutez rien dans une opération basée sur le flux qui ne puisse pas être restauré au cas où le flux de données serait abandonné. Ces recommandations s'appliquent également au cas dans lequel un message peut s'avérer incorrect après la diffusion en continu du corps (par exemple, il peut manquer une balise de fin pour l'enveloppe SOAP ou le message peut comporter un deuxième corps).

- L'utilisation de la fonctionnalité `IExtensibleDataObject` peut engendrer l'émission de données sensibles. Si vous acceptez des données d'une source non fiable dans des contrats de données avec `IExtensibleObjectData` , puis vous les émettez de nouveau sur un canal sécurisé où les messages sont signés, vous vous portez potentiellement garant de données dont vous ne savez rien. De plus, l'état global que vous envoyez risque de ne pas être valide si vous prenez à la fois en considération les morceaux de données connus et inconnus. Évitez cette situation en affectant sélectivement à la propriété des données d'extension la valeur `null` ou en désactivant sélectivement la fonctionnalité `IExtensibleObjectData` .

## <a name="schema-import"></a>Importation de schéma

Normalement, le processus d’importation du schéma pour générer des types s’exécute uniquement au moment de la conception, par exemple, lors de l’utilisation de [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) sur un service web pour générer une classe de client. Toutefois, dans des scénarios plus avances, vous pouvez traiter le schéma au moment de l'exécution. N'oubliez pas que ce traitement peut vous exposer à des risques de déni de service. L'importation de certains schémas peut nécessiter beaucoup de temps. N'utilisez jamais le composant d'importation de schéma <xref:System.Xml.Serialization.XmlSerializer> dans de tels scénarios si les schémas peuvent venir d'une source non fiable.

## <a name="threats-specific-to-aspnet-ajax-integration"></a>Menaces spécifiques à l'intégration ASP.NET AJAX

Lorsque l’utilisateur implémente <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> ou <xref:System.ServiceModel.Description.WebHttpBehavior> , WCF expose un point de terminaison qui peut accepter à la fois les messages XML et JSON. Cependant, il n'existe qu'un jeu de quotas de lecteurs utilisés par les lecteurs XML et JSON. Certains paramètres de quota peuvent convenir à un lecteur mais sont trop grands pour l'autre.

Lors de l'implémentation de `WebScriptEnablingBehavior`, l'utilisateur peut exposer un proxy JavaScript au point de terminaison. Tenez compte des éléments suivants en examinant les questions de sécurité :

- Les informations sur le service (noms d'opération, noms de paramètre etc.) peuvent être obtenues par l'examen du proxy JavaScript.

- Lors de l'utilisation du point de terminaison JavaScript, des informations privées et sensibles peuvent être conservées dans le cache du navigateur Web du client.

## <a name="a-note-on-components"></a>Remarque sur les composants

WCF est un système flexible et personnalisable. La majeure partie du contenu de cette rubrique se concentre sur les scénarios d’utilisation WCF les plus courants. Toutefois, il est possible de composer les composants fournis par WCF de différentes manières. Il est important de comprendre les implications en matière de sécurité de l'utilisation de chaque composant. En particulier :

- Lorsque vous devez utiliser des lecteurs XML, utilisez les lecteurs que la classe <xref:System.Xml.XmlDictionaryReader> fournit au lieu de tous les autres lecteurs. Les lecteurs sûrs sont créés à l'aide des méthodes <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>ou <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> . N'utilisez pas la méthode <xref:System.Xml.XmlReader.Create%2A> . Configurez toujours les lecteurs avec des quotas sûrs. Les moteurs de sérialisation dans WCF sont sécurisés uniquement lorsqu’ils sont utilisés avec des lecteurs XML sécurisés de WCF.

- Lorsque vous utilisez <xref:System.Runtime.Serialization.DataContractSerializer> pour désérialiser des données potentiellement non fiables, affectez toujours une valeur à la propriété <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> .

- Lorsque vous créez un message, définissez le paramètre `maxSizeOfHeaders` si `MaxReceivedMessageSize` n'offre pas assez de protection.

- Lorsque vous créez un encodeur, configurez toujours les quotas correspondants, tels que `MaxSessionSize` et `MaxBufferSize`.

- Lorsque vous utilisez un filtre de message XPath, affectez une valeur à <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> de sorte à limiter le nombre de nœuds XML visités par le filtre. N'utilisez pas les expressions XPath qui peuvent nécessiter beaucoup de temps de calcul sans pour autant visiter de nombreux nœuds.

- En général, lorsque vous utilisez un composant qui accepte un quota, comprenez ses implications en matière de sécurité et affectez-lui une valeur sûre.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.XmlDictionaryReader>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Types connus de contrats de données](data-contract-known-types.md)
