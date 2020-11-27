---
title: Sérialisation et désérialisation
description: En savoir plus sur le moteur de sérialisation WCF, qui se traduit par des objets .NET Framework et XML, dans les deux sens.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: 94328fc2b2d008202221bfb4c05132e1286666e3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253945"
---
# <a name="serialization-and-deserialization"></a>Sérialisation et désérialisation

Windows Communication Foundation (WCF) comprend un nouveau moteur de sérialisation, le <xref:System.Runtime.Serialization.DataContractSerializer> . Le <xref:System.Runtime.Serialization.DataContractSerializer> traduit entre les objets .NET Framework et XML, dans les deux sens. Cette rubrique explique comment le sérialiseur fonctionne.  
  
 Lors de la sérialisation d’objets .NET Framework, le sérialiseur comprend un large éventail de modèles de programmation de sérialisation, y compris le nouveau modèle de *contrat de données* . Pour obtenir une liste complète des types pris en charge, consultez [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md). Pour obtenir une introduction aux contrats de données, consultez [Using Data Contracts](using-data-contracts.md).  
  
 Lors de la désérialisation du XML, le sérialiseur utilise les classes <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter> . Il prend également en charge les <xref:System.Xml.XmlDictionaryReader> <xref:System.Xml.XmlDictionaryWriter> classes et pour lui permettre de produire du XML optimisé dans certains cas, par exemple lors de l’utilisation du format XML binaire WCF.  
  
 WCF comprend également un sérialiseur auxiliaire, le <xref:System.Runtime.Serialization.NetDataContractSerializer> . <xref:System.Runtime.Serialization.NetDataContractSerializer> :

* Est ***non** _ sécurisé. Pour plus d’informations, consultez le [Guide de sécurité BinaryFormatter](../../../standard/serialization/binaryformatter-security-guide.md).
_ Est semblable aux <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> sérialiseurs et, car il émet également des noms de type .NET Framework dans le cadre des données sérialisées.
* Est utilisé lorsque les mêmes types sont partagés sur les terminaisons de sérialisation et de désérialisation.

 <xref:System.Runtime.Serialization.DataContractSerializer>Et <xref:System.Runtime.Serialization.NetDataContractSerializer> dérivent à la fois d’une classe de base commune, <xref:System.Runtime.Serialization.XmlObjectSerializer> .  
  
> [!WARNING]
> <xref:System.Runtime.Serialization.DataContractSerializer> sérialise les chaînes contenant des caractères de contrôle avec une valeur hexadécimale inférieure à 20 comme entités XML. Cela peut entraîner un problème avec un client non-WCF lors de l’envoi de ces données à un service WCF.  
  
## <a name="creating-a-datacontractserializer-instance"></a>Création d'une instance DataContractSerializer  

 Construire une instance du <xref:System.Runtime.Serialization.DataContractSerializer> est une étape importante. Après la construction, vous ne pouvez pas en modifier les paramètres.  
  
### <a name="specifying-the-root-type"></a>Spécification du type racine  

 Le *type de racine* est le type à partir duquel les instances sont sérialisées ou désérialisées. Le <xref:System.Runtime.Serialization.DataContractSerializer> a de nombreuses surcharges de constructeur, mais, au minimum, un type racine doit être fourni à l'aide du paramètre `type` .  
  
 Un sérialiseur créé pour un certain type de racine ne peut pas être utilisé pour sérialiser (ou désérialiser) un autre type, sauf si le type est dérivé du type racine. L'exemple suivant illustre deux classes.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Ce code construit une instance du `DataContractSerializer` qui peut être utilisée uniquement pour sérialiser ou désérialiser des instances de la classe `Person` .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Spécification de types connus  

 Si le polymorphisme affecte les types qui sont sérialisés et n'est pas déjà géré par l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute> ou un autre mécanisme, une liste de types connus possibles doit être passée au constructeur du sérialiseur à l'aide du paramètre `knownTypes` . Pour plus d’informations sur les types connus, consultez [types connus de contrat de données](data-contract-known-types.md).  
  
 L'exemple suivant affiche une classe, `LibraryPatron`, qui inclut une collection d'un type spécifique, le `LibraryItem`. La deuxième classe définit le type `LibraryItem` . Les troisième et quatrième classes (`Book` et `Newspaper`) héritent de la classe `LibraryItem` .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Le code suivant construit une instance du sérialiseur à l'aide du paramètre `knownTypes` .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Spécification de l'espace de nom et du nom racine par défaut  

 Normalement, lorsqu'un objet est sérialisé, l'espace de noms et le nom par défaut de l'élément XML le plus à l'extérieur sont déterminés d'après l'espace de noms et le nom de contrat de données. Les noms de tous les éléments internes sont déterminés à partir des noms de membre de données, et leur espace de noms est l'espace de noms du contrat de données. L'exemple suivant définit les valeurs `Name` et `Namespace` dans les constructeurs des classes <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 La sérialisation d'une instance de la classe `Person` produit du XML semblable aux éléments suivants.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Toutefois, vous pouvez personnaliser le nom et l'espace de noms par défaut de l'élément racine en passant les valeurs des paramètres `rootName` et `rootNamespace` au constructeur <xref:System.Runtime.Serialization.DataContractSerializer> . Notez que le `rootNamespace` n'affecte pas l'espace de noms des éléments contenus qui correspondent aux membres de données. Il affecte uniquement l'espace de noms de l'élément le plus à l'extérieur.  
  
 Ces valeurs peuvent être passées comme chaînes ou instances de la classe <xref:System.Xml.XmlDictionaryString> pour permettre leur optimisation à l'aide du format XML binaire.  
  
### <a name="setting-the-maximum-objects-quota"></a>Définition du quota d'objets maximal  

 Certaines surcharges de constructeur `DataContractSerializer` ont un paramètre `maxItemsInObjectGraph` . Ce paramètre détermine le nombre maximal d'objets que le sérialiseur sérialise ou désérialise dans un appel de méthode <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> unique. (La méthode lit toujours un objet racine, mais cet objet peut avoir d'autres objets dans ses membres de données. Ces objets peuvent avoir d’autres objets, et ainsi de suite.) La valeur par défaut est 65536. Notez qu'en matière de sérialisation ou de désérialisation de tableaux, chaque entrée de tableau compte comme un objet distinct. Notez également que certains objets ont une grande représentation de mémoire, de sorte que ce quota peut ne pas suffire pour empêcher les attaques par déni de service. Pour plus d’informations, consultez Considérations sur la [sécurité pour les données](security-considerations-for-data.md). Si vous devez augmenter ce quota au delà de la valeur par défaut, il est important de le faire sur l'émission (sérialisation) et la réception (désérialisation) étant donné qu'il s'applique à la fois à la lecture et à l'écriture des données.  
  
### <a name="round-trips"></a>Allers-retours  

 Un *aller-retour* se produit lorsqu'un objet est désérialisé et ré-sérialisé dans une opération. Ainsi, celui-ci passe du format XML à une instance d'objet, puis est reconverti en un flux de données XML.  
  
 Certaines surcharges de constructeur `DataContractSerializer` ont un paramètre `ignoreExtensionDataObject` , affecté par défaut de la valeur `false` . Dans ce mode par défaut, les données peuvent être envoyées sur un aller-retour d'une version plus récente d'un contrat de données via une version antérieure puis retournées vers la version plus récente sans perte, à condition que le contrat de données implémente l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> . Par exemple, supposons que la version 1 du contrat de données `Person` contient les membres de données `Name` et `PhoneNumber` , et la version 2 ajoute un membre `Nickname` . Si `IExtensibleDataObject` est implémenté, lors de l'envoi d'informations de la version 2 à la version 1, les données `Nickname` sont stockées, et puis sont ré-émises lorsque les données sont encore sérialisées ; par conséquent, aucune donnée n'est perdue au cours de l'aller-retour. Pour plus d’informations, consultez [contrats de données à compatibilité ascendante](forward-compatible-data-contracts.md) et contrôle de [version des contrats de données](data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Problèmes liés à la sécurité et à la validation de schéma avec les allers-retours  

 Les allers-retours peuvent avoir des conséquences sur la sécurité. Par exemple, la désérialisation et le stockage de grandes quantités de données superflues peuvent présenter un risque pour la sécurité. Il peut y avoir des problèmes de sécurité invérifiables pour ré-émettre ces données, surtout si les signatures numériques sont concernées. Par exemple, dans le scénario précédent, le point de terminaison version 1 peut signer une valeur `Nickname` qui contient des données malveillantes. Enfin, il peut y avoir des problèmes concernant la validité du schéma : un point de terminaison peut toujours émettre des données qui sont strictement conformes à son contrat défini et aucune valeur supplémentaire. Dans l'exemple précédent, la version 1 du contrat de point de terminaison indique qu'il émet uniquement `Name` et `PhoneNumber`, et si la validation de schéma est utilisée, l'émission de la valeur `Nickname` supplémentaire fait échouer la validation.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Activation et désactivation de allers-retours  

 Pour désactiver les allers-retours, n'implémentez pas l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> . Si vous n'avez aucun contrôle sur les types, affectez au paramètre `ignoreExtensionDataObject` la valeur `true` pour accomplir le même effet.  
  
### <a name="object-graph-preservation"></a>Conservation de graphique d'objet  

 Normalement, le sérialiseur ne se soucie pas de l'identité d'objet, comme dans le code suivant.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Le code suivant crée un bon de commande.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Remarquez que les champs `billTo` et `shipTo` ont pour valeur la même instance d'objet. Toutefois, le XML généré duplique les informations dupliquées et ressemble au XML suivant.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Toutefois, cette approche a les caractéristiques suivantes, qui peuvent être indésirables :  
  
- Les performances. Répliquer des données est inefficace.  
  
- Références circulaires. Si les objets font référence à eux-mêmes, même par le biais d'autres objets, la sérialisation par réplication crée une boucle infinie. (Dans ce cas, le sérialiseur lève une exception <xref:System.Runtime.Serialization.SerializationException> .)  
  
- Sémantique. Parfois, il est important de conserver le fait qu'il existe deux références au même objet, et pas à deux objets identiques.  
  
 Pour ces raisons, certaines surcharges de constructeur `DataContractSerializer` ont un paramètre `preserveObjectReferences` (la valeur par défaut est `false`). Lorsque ce paramètre a la valeur `true` , une méthode spéciale d’encodage des références d’objet, uniquement interprété par WCF, est utilisée. Lorsque le paramètre a la valeur `true`, l'exemple de code XML ressemble aux éléments suivants.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 L’espace de noms "ser" fait référence à l’espace de noms de sérialisation standard, `http://schemas.microsoft.com/2003/10/Serialization/` . Chaque portion de données est sérialisée une seule fois seulement et reçoit un numéro d'ID, et les utilisations ultérieures génèrent une référence aux données déjà sérialisées.  
  
> [!IMPORTANT]
> Si à la fois, les attributs id et ref sont présents dans le contrat de données `XMLElement`, l'attribut ref est honoré tandis que l'attribut id est ignoré.  
  
 Il est important de comprendre les limitations de ce mode :  
  
- Le XML que `DataContractSerializer` produit avec `preserveObjectReferences` affecté de la valeur `true` n'est pas interopérable avec les autres technologies et n'est accessible qu'à une autre instance `DataContractSerializer` , également avec `preserveObjectReferences` affecté de la valeur `true`.  
  
- Il n'existe aucune prise en charge des métadonnées (schéma) pour cette fonctionnalité. Le schéma produit est uniquement valide lorsque `preserveObjectReferences` a la valeur `false`.  
  
- Cette fonctionnalité peut entraîner une exécution plus lente du processus de sérialisation et de désérialisation. Même si les données ne doivent pas à être répliquées, les comparaisons d'objet supplémentaires doivent être effectuées dans ce mode.  
  
> [!CAUTION]
> Lorsque le mode `preserveObjectReferences` est activé, il est particulièrement important d'affecter à la valeur `maxItemsInObjectGraph` le quota correct. En raison du traitement des tableaux dans ce mode, il est facile pour un intrus de construire un message malveillant de petite taille qui entraîne une consommation importante de la mémoire limitée uniquement par le quota `maxItemsInObjectGraph` .  
  
### <a name="specifying-a-data-contract-surrogate"></a>Spécification d'un substitut de contrat de données  

 Certaines surcharges de constructeur `DataContractSerializer` ont un paramètre `dataContractSurrogate` qui peut avoir la valeur `null`. Sinon, vous pouvez l'utiliser pour spécifier un *substitut de contrat de données* qui est un type qui implémente l'interface <xref:System.Runtime.Serialization.IDataContractSurrogate> . Vous pouvez utiliser ensuite l'interface pour personnaliser le processus de sérialisation et de désérialisation. Pour plus d’informations, consultez [substituts de contrat de données](../extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Sérialisation  

 Les informations suivantes s'appliquent à toute classe qui hérite du <xref:System.Runtime.Serialization.XmlObjectSerializer>, y compris les classes <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
### <a name="simple-serialization"></a>Sérialisation simple  

 La méthode la plus simple pour sérialiser un objet est de le passer à la méthode <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> . Il y a trois surcharges, chacune pour écrire dans un <xref:System.IO.Stream>, un <xref:System.Xml.XmlWriter>ou un <xref:System.Xml.XmlDictionaryWriter>. Avec la surcharge <xref:System.IO.Stream> , la sortie est XML dans l'encodage UTF-8. Avec la surcharge <xref:System.Xml.XmlDictionaryWriter> , le sérialiseur optimise sa sortie pour le XML binaire.  
  
 Lors de l’utilisation de la <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> méthode, le sérialiseur utilise le nom et l’espace de noms par défaut pour l’élément wrapper et l’écrit avec le contenu (consultez la section précédente « spécification de l’espace de noms et du nom racine par défaut »).  
  
 L'exemple de code suivant illustre l'écriture avec un <xref:System.Xml.XmlDictionaryWriter>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 Elle produit du XML similaire au code suivant.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Sérialisation pas à pas  

 Utilisez les méthodes <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>et <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> pour écrire l'élément de fin, écrivez le contenu d'objet et fermez l'élément wrapper, respectivement.  
  
> [!NOTE]
> Il n'y a pas de surcharges <xref:System.IO.Stream> de ces méthodes.  
  
 Cette sérialisation pas à pas fait l'objet de deux utilisations courantes. La première est d'insérer du contenu tel que des attributs ou des commentaires entre `WriteStartObject` et `WriteObjectContent`, comme indiqué dans l'exemple suivant.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Elle produit du XML similaire au code suivant.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 L'autre utilisation courante est d'éviter l'utilisation complète de <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> et <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> , et d'écrire votre propre élément wrapper personnalisé (voir d'ignorer entièrement l'écriture d'un wrapper), comme indiqué dans le code suivant.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 Elle produit du XML similaire au code suivant.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
> L'utilisation de la sérialisation pas à pas peut générer du XML de schéma non valide.  
  
## <a name="deserialization"></a>Désérialisation  

 Les informations suivantes s'appliquent à toute classe qui hérite du <xref:System.Runtime.Serialization.XmlObjectSerializer>, y compris les classes <xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
 La méthode la plus simple pour désérialiser un objet est d'appeler l'une des surcharges de méthode <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> . Il y a trois surcharges, chacune pour lire avec un <xref:System.Xml.XmlDictionaryReader>, un `XmlReader`ou un `Stream`. Notez que la surcharge `Stream` crée un <xref:System.Xml.XmlDictionaryReader> textuel qui n'est pas protégé par des quotas, et doit être utilisé uniquement pour lire des données approuvées.  
  
 Notez également que l'objet retourné par la méthode `ReadObject` doivent être converti au type approprié.  
  
 Le code suivant construit une instance du <xref:System.Runtime.Serialization.DataContractSerializer> et d'un <xref:System.Xml.XmlDictionaryReader>, puis désérialise une instance `Person` .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Avant d'appeler la méthode <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> , positionnez le lecteur XML sur l'élément wrapper ou sur un nœud qui n'est pas un nœud de contenu qui précède l'élément wrapper. Pour ce faire, appelez la méthode <xref:System.Xml.XmlReader.Read%2A> du <xref:System.Xml.XmlReader> ou sa dérivation, et testez le <xref:System.Xml.XmlReader.NodeType%2A>, comme indiquez dans le code suivant.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Notez que vous pouvez lire des attributs sur cet élément wrapper avant de passer le lecteur à `ReadObject`.  
  
 Lors de l’utilisation de l’une des `ReadObject` surcharges simples, le désérialiseur recherche le nom et l’espace de noms par défaut sur l’élément wrapper (consultez la section précédente, « spécification du nom et de l’espace de noms racine par défaut ») et lève une exception s’il trouve un élément inconnu. Dans l'exemple précédent, l'élément wrapper `<Person>` est attendu. La méthode <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> est appelée pour vérifier que le lecteur est positionné sur un élément dont le nom est attendu.  
  
 Une méthode permet de désactiver ce contrôle du nom de l'élément wrapper ; certaines surcharges de la méthode `ReadObject` acceptent le paramètre booléen `verifyObjectName`qui la valeur `true` par défaut. Lorsqu'il a la valeur `false`, le nom et l'espace de noms de l'élément wrapper sont ignorés. Ce procédé est utile pour lire le XML écrit à l'aide du mécanisme de sérialisation pas à pas décrit précédemment.  
  
## <a name="using-the-netdatacontractserializer"></a>Utilisation de NetDataContractSerializer  

 La principale différence entre les `DataContractSerializer` et <xref:System.Runtime.Serialization.NetDataContractSerializer> est que utilise des `DataContractSerializer` noms de contrat de données, tandis que les `NetDataContractSerializer` sorties sont complètes .NET Framework les noms d’assembly et de type dans le XML sérialisé. Cela signifie que les mêmes types exacts doivent être partagés entre les points de terminaison de sérialisation et de désérialisation. Cela signifie que le mécanisme de types connus n'est pas requis avec `NetDataContractSerializer` parce que les types exacts à désérialiser sont toujours connus.  
  
 Toutefois, plusieurs problèmes peuvent se produire :  
  
- Sécurité. Tout type trouvé dans le XML désérialisé est chargé. Cela peut être exploité pour forcer le chargement de types malveillants. L'utilisation de `NetDataContractSerializer` avec des données non fiables doit s'effectuer uniquement si un *binder de sérialisation* est utilisé (à l'aide de la propriété ou du paramètre de constructeur <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> ). Le binder autorise uniquement le chargement des types sûrs. Le mécanisme de binder est identique à celui utilisé par les types dans l'espace de noms <xref:System.Runtime.Serialization> .  
  
- Contrôle de version. L'utilisation des noms de type et d'assembly complets dans le XML limite fortement la gestion de la version des types. Les éléments suivants ne peuvent pas être modifiés : noms de type, espaces de noms, noms d'assembly et versions d'assembly. Affecter à la propriété ou au paramètre de constructeur <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> la valeur <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> au lieu de la valeur par défaut de <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> permet de modifier la version des assemblys, mais pas des types de paramètre génériques.  
  
- Interopérabilité. Étant donné que les noms de type et d’assembly .NET Framework sont inclus dans le XML, les plateformes autres que le .NET Framework ne peuvent pas accéder aux données résultantes.  
  
- Les performances. L'écriture des noms de type et d'assembly augmente nettement la taille du XML résultant.  
  
 Ce mécanisme est semblable à la sérialisation binaire ou SOAP utilisée par .NET Framework la communication à distance (plus précisément, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> et <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ).  
  
 L'utilisation du `NetDataContractSerializer` est semblable à l'utilisation du `DataContractSerializer`, avec les différences suivantes :  
  
- Les constructeurs n'exigent pas de spécifier un type racine. Vous pouvez sérialiser tout type avec la même instance du `NetDataContractSerializer`.  
  
- Les constructeurs n'acceptent pas une liste de types connus. Le mécanisme de types connus est inutile si les noms de type sont sérialisés dans le XML.  
  
- Les constructeurs n'acceptent pas de substitut de contrat de données. À la place, ils acceptent un paramètre <xref:System.Runtime.Serialization.ISurrogateSelector> appelé `surrogateSelector` (qui mappe à la propriété <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> ). Il s'agit d'un mécanisme de remplacement hérité.  
  
- Le constructeur accepte un paramètre appelé `assemblyFormat` du <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> qui mappe à la propriété <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> . Comme évoqué précédemment, cette opération peut servir à améliorer les fonctions de contrôle de version du sérialiseur. Elle est identique au mécanisme <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> dans la sérialisation binaire ou SOAP.  
  
- Les constructeurs acceptent un paramètre <xref:System.Runtime.Serialization.StreamingContext> appelé `context` qui mappe à la propriété <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> . Vous pouvez utiliser cela pour passer des informations dans les types qui sont sérialisés. Cette utilisation est identique à celle du mécanisme <xref:System.Runtime.Serialization.StreamingContext> utilisé dans d'autres classes <xref:System.Runtime.Serialization> .  
  
- Les méthodes <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> et <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> sont des alias pour les méthodes <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> et <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> . Elles existent pour fournir un modèle de programmation plus cohérent avec la sérialisation binaire ou SOAP.  
  
 Pour plus d’informations sur ces fonctionnalités, consultez [sérialisation binaire](../../../standard/serialization/binary-serialization.md).  
  
 Les formats XML utilisés par `NetDataContractSerializer` et `DataContractSerializer` ne sont pas normalement compatibles. Autrement dit, toute tentative de sérialiser avec l'un de ces sérialiseurs et de désérialiser avec l'autre n'est pas prise en charge.  
  
 Notez également que le `NetDataContractSerializer` n’affiche pas le type de .NET Framework complet et le nom de l’assembly pour chaque nœud dans le graphique d’objets. Il génère ces informations uniquement en cas d'ambiguïté. Autrement dit, il génère au niveau de l'objet racine et pour les cas polymorphes.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [Sérialisation binaire](../../../standard/serialization/binary-serialization.md)
- [Types pris en charge par le sérialiseur de contrat de données](types-supported-by-the-data-contract-serializer.md)
