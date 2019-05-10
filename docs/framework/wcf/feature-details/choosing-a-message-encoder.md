---
title: Sélection d'un encodeur de message
ms.date: 03/30/2017
ms.assetid: 2204d82d-d962-4922-a79e-c9a231604f19
ms.openlocfilehash: 93024258ddcf76444d48a19c071b0a18248ea46b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645450"
---
# <a name="choosing-a-message-encoder"></a>Sélection d'un encodeur de message
Cette rubrique traite des critères permettant de choisir parmi les encodeurs de message sont inclus dans Windows Communication Foundation (WCF) : fichier binaire, texte et Message Transmission Optimization Mechanism (MTOM).  
  
 Dans WCF, vous spécifiez comment transférer des données sur un réseau entre les points de terminaison au moyen d’un *liaison*, qui se compose d’une séquence de *éléments de liaison*. Un encodeur de message est représenté par un élément de liaison d’encodage de message dans la pile de liaison. Une liaison inclut des éléments de liaison de protocole facultatifs, tels qu’un élément de liaison de sécurité ou un élément de liaison de messagerie fiable, un élément de liaison d’encodage de message requis, et un élément de liaison de transport requis.  
  
 L'élément de liaison d'encodage de message se trouve au-dessous des éléments de liaison de protocole facultatifs et au-dessus de l'élément de liaison de transport requis. Sur le côté sortant, un encodeur de message sérialise le <xref:System.ServiceModel.Channels.Message> sortant et le transmet au transport. Sur le côté entrant, un encodeur de message reçoit le formulaire sérialisé d'un <xref:System.ServiceModel.Channels.Message> du transport et le passe à la couche de protocole supérieure, si celle-ci est présente, ou à l'application, dans le cas contraire.  
  
 Lors de la connexion à un client ou serveur préexistant, il se peut que vous n'ayez pas le choix de l'utilisation d'un encodage de message spécifique car vous devez encoder vos messages conformément à ce que l'autre côté attend. Toutefois, si vous écrivez un service WCF, vous pouvez exposer votre service via plusieurs points de terminaison, chacun utilisant un encodage de message différent. Cela permet aux clients de choisir l'encodage le plus approprié pour communiquer avec votre service sur le point de terminaison le plus adapté pour eux, et à vos clients de choisir l'encodage le plus adéquat. L’utilisation de plusieurs points de terminaison vous permet également de combiner les avantages d’encodages de message différents avec d’autres éléments de liaison.  
  
## <a name="system-provided-encoders"></a>Encodeurs fournis par le système  
 WCF inclut trois encodeurs de message, qui sont représentées par les trois classes suivantes :  
  
- L'encodeur de message texte <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> prend à la fois en charge l'encodage XML brut et l'encodage SOAP. Le mode d'encodage XML brut de l'encodeur de message texte est appelé POX (Plain Old XML) afin de le distinguer de l'encodage SOAP basé sur le texte. Pour activer le mode POX, affectez la valeur <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement.MessageVersion%2A> à la propriété <xref:System.ServiceModel.Channels.MessageVersion.None%2A>. Utiliser l’encodeur de message texte pour interagir avec les points de terminaison non-WCF.  
  
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>, l’encodeur de message binaire utilise un format binaire compact et est optimisé pour WCF pour la communication WCF et par conséquent, n’est pas interopérable. Il s’agit également l’encodeur performante la plupart de tous les codeurs que WCF fournit.  
  
- L'élément de liaison <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> spécifie l'encodage de caractères et le contrôle de version des messages encodés avec MTOM. MTOM est une technologie efficace de transmission de données binaires dans les messages WCF. L'encodeur MTOM tente de créer un équilibre entre rendement et interopérabilité. L'encodage MTOM transmet la plupart du XML sous forme textuelle, mais optimise les grands blocs de données binaires en les transmettant tels quels, sans conversion en texte. En termes d’efficacité, parmi les encodeurs que WCF fournit, MTOM est texte intermédiaires (la plus lente) et binaire (la plus rapide).  
  
## <a name="how-to-choose-a-message-encoder"></a>Comment choisir un encodeur de message  
 Le tableau suivant décrit les facteurs courants utilisés pour choisir un encodeur de message. Donnez la priorité aux facteurs significatifs pour votre application, puis choisissez les encodeurs de message qui fonctionnent le mieux avec ceux-ci. Assurez-vous de prendre en compte les facteurs supplémentaires non répertoriés dans ce tableau et les encodeurs de message personnalisés qui peuvent s'avérer nécessaires dans votre application.  
  
|Facteur|Description|Encodeurs qui prennent en charge ce facteur|  
|------------|-----------------|---------------------------------------|  
|Jeux de caractères pris en charge|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> et <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> prennent en charge uniquement le UTF8 et UTF16 Unicode (*big-endian* et *little endian*) encodages. Si d'autres encodages sont requis, tels qu'UTF7 ou ASCII, un encodeur personnalisé doit être utilisé. Pour un exemple d’encodeur personnalisé, consultez [encodeur de Message personnalisé](https://go.microsoft.com/fwlink/?LinkId=119857).|Texte|  
|Inspection|L'inspection désigne la capacité à examiner des messages pendant la transmission. Les encodages de texte, avec ou sans l'utilisation de SOAP, autorisent l'inspection et l'analyse des messages par de nombreuses applications sans l'utilisation d'outils spécialisés. Notez que l'utilisation de sécurité de transfert, au niveau du message ou du transport, affecte votre capacité à inspecter des messages. La confidentialité et l'intégrité empêchent respectivement l'examen et la modification d'un message.|Texte|  
|Fiabilité|La fiabilité désigne la résilience d'un encodeur aux erreurs de transmission. La fiabilité peut également être fournie au niveau du message, du transport ou de la couche d'application. Toutes les encodeurs WCF standards supposent qu’une autre couche fournit la fiabilité. L'encodeur a peu de possibilité de récupérer d'une erreur de transmission.|None|  
|Simplicité|La simplicité représente la facilité avec laquelle vous pouvez créer des encodeurs et décodeurs pour une spécification d'encodage. Les encodages de texte sont particulièrement avantageux en termes de simplicité, et l'encodage de texte POX présente l'avantage supplémentaire de ne requérir aucune prise en charge pour le traitement SOAP.|Texte (POX)|  
|Size|L'encodage détermine la quantité de charge mémoire imposée sur le contenu. La taille des messages encodés est directement associée au débit maximal des opérations de service. Les encodages binaires sont en général plus compacts que les encodages de texte. Lorsque la taille de message est importante, compressez également le contenu du message lors de l'encodage. Cependant, la compression augmente les coûts de traitement à la fois de l'expéditeur et du récepteur du message.|Binaire|  
|Diffusion en continu|La diffusion en continu permet aux applications de commencer à traiter un message avant qu'il ne soit totalement arrivé. L'utilisation efficace de la diffusion en continu requiert que les données importantes d'un message soient disponibles au début de celui-ci afin que l'application de réception n'ait pas à attendre qu'elles arrivent. De plus, les applications qui utilisent le transfert en continu doivent organiser les données du message de façon incrémentielle afin que le contenu n'ait pas de dépendances ascendantes. Dans de nombreux cas, vous devez trouver un compromis entre diffuser du contenu en continu et avoir la taille de transfert la plus petite possible pour celui-ci.|None|  
|Prise en charge des outils tiers|La prise en charge d'un encodage inclut le développement et le diagnostic. Des développeurs tiers ont fait un investissement substantiel dans les bibliothèques et trousses à outils permettant de gérer les messages encodés au format POX.|Texte (POX)|  
|Interopérabilité|Ce facteur fait référence à la capacité d’un encodeur de WCF pour interagir avec les services non-WCF.|Texte<br /><br /> MTOM (partiel)|  
  
Remarque : Lorsque vous utilisez l’encodeur binaire, à l’aide du paramètre IgnoreWhitespace lors de la création d’un XMLReader aura aucun effet.  Par exemple, si vous procédez comme suit dans une opération de service :  

```csharp
public void OperationContract(XElement input)
{
    Console.WriteLine("{0}", input.Value);
    int counter = 0;
    var xreader = input.CreateReader();
    var reader = XmlReader.Create(xreader, new XmlReaderSettings() { IgnoreWhitespace = true });
    while (reader.Read())
    {
        counter++;
    }

    Console.WriteLine("Read {0} lines with reader", counter);
}
```  
  
Le paramètre IgnoreWhitespace est ignoré.  
  
## <a name="compression-and-the-binary-encoder"></a>Compression et encodeur binaire

Depuis WCF 4.5, l'encodeur binaire WCF ajoute la prise en charge de la compression. Cela vous permet d'utiliser l'algorithme gzip/deflate pour envoyer des messages compressés d'un client WCF et répondre avec les messages compressés d'un service WCF auto-hébergé. Cette fonctionnalité permet la compression sur les transports HTTP et TCP. Un service WCF hébergé par IIS peut toujours être activé pour envoyer des réponses compressées en configurant le serveur hôte IIS. Le type de compression est configuré avec la propriété <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.CompressionFormat%2A?displayProperty=nameWithType>. Cette propriété a l'une des valeurs d'énumération <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType> :

- <xref:System.ServiceModel.Channels.CompressionFormat.Deflate>
- <xref:System.ServiceModel.Channels.CompressionFormat.GZip>
- <xref:System.ServiceModel.Channels.CompressionFormat.None>
  
Dans la mesure où cette propriété est exposée uniquement sur le binaryMessageEncodingBindingElement, vous devez créer une liaison personnalisée comme suit pour utiliser cette fonctionnalité :

 ```xml
 <customBinding>
   <binding name="BinaryCompressionBinding">
     <binaryMessageEncoding compressionFormat ="GZip" />
     <httpTransport />
  </binding>
</customBinding>
 ```

Le client et le service doivent accepter envoyer et recevoir des messages compressés et par conséquent, la propriété compressionFormat doit être configurée sur l’élément binaryMessageEncoding sur le client et le service. Une exception ProtocolException est levée si le service ou le client n'est pas configuré pour la compression, mais la compression is.Enabling de l'autre côté doit être soigneusement étudiée. La compression est essentiellement utile si la bande passante réseau est un goulot d'étranglement. Dans le cas où l'UC est un goulot d'étranglement, la compression diminuera le débit. Le test approprié doit être effectué dans un environnement simulé pour déterminer si cela offre des avantages à l'application  
  
## <a name="see-also"></a>Voir aussi

- [Liaisons](../../../../docs/framework/wcf/feature-details/bindings.md)
