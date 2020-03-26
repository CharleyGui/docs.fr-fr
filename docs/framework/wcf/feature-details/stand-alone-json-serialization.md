---
title: Sérialisation autonome de JSON à l’aide de DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 312bd7b2-1300-4b12-801e-ebe742bd2287
ms.openlocfilehash: 614776a905ec319624f76876762c25bfca15a357
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249446"
---
# <a name="stand-alone-json-serialization-using-datacontractjsonserializer"></a>Sérialisation autonome de JSON à l’aide de DataContractJsonSerializer

> [!NOTE]
> Cet article <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>est d’environ . Pour la plupart des scénarios qui impliquent la sérialisation et la désétération JSON, nous recommandons les API dans le [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).

JSON (JavaScript Object Notation) est un format de données spécialement conçu pour être utilisé par du code JavaScript exécuté sur les pages web dans le navigateur. Il s’agit du format de données par défaut utilisé par ASP.NET services AJAX créés par Windows Communication Foundation (WCF).

Ce format peut également être utilisé lors de la création de services AJAX sans intégration avec ASP.NET ; dans ce cas, XML est le format par défaut, mais il est possible de choisir le format JSON.

Enfin, si vous avez besoin d'une prise en charge du format JSON mais que vous ne créez pas de service AJAX, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> permet de sérialiser directement les objets .NET en données JSON, et de désérialiser ces données en instances de types .NET. Pour une description de la façon de le faire, voir [Comment: Serialize et Deserialize JSON Data](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).

Lorsque vous utilisez JSON, le types de données .NET pris en charge sont les mêmes que ceux pris en charge par <xref:System.Runtime.Serialization.DataContractSerializer>, à quelques exceptions près. Pour une liste des types pris en charge, voir [Types Pris en charge par le Serializer contrat de données](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Il s'agit de la plupart des types primitifs, des types de collections et de tableaux, ainsi que des types complexes qui utilisent <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute>.

## <a name="mapping-net-types-to-json-types"></a>Mappage de types .NET aux types JSON

Le tableau suivant indique la correspondance entre les types .NET et les types JSON/JavaScript lorsqu'ils sont mappés par les procédures de sérialisation et de désérialisation.

|Types .NET|JSON/JavaScript|Notes|
|----------------|----------------------|-----------|
|Tous les types numériques, par exemple <xref:System.Int32>, <xref:System.Decimal> ou <xref:System.Double>|Number|Les valeurs spéciales telles que `Double.NaN`, `Double.PositiveInfinity` et `Double.NegativeInfinity` ne sont pas prises en charge et entraînent des données JSON non valides.|
|<xref:System.Enum>|Number|Voir « Énumérations et JSON » ci-après dans cette rubrique.|
|<xref:System.Boolean>|Boolean|--|
|<xref:System.String>, <xref:System.Char>|String|--|
|<xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>|String|Le format de ces types dans JSON est le même que dans XML (essentiellement, TimeSpan dans le format ISO 8601 Durée, GUID dans le "12345678-ABCD-ABCD-ABCD-1234567890AB" format et URI sous sa forme de chaîne naturelle comme ").http://www.example.com Pour plus d’informations précises, voir [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).|
|<xref:System.Xml.XmlQualifiedName>|String|Le format est « nom:espacedenoms » (ce qui apparaît avant le premier signe deux-points constitue le nom). Le nom ou l'espace de noms peut être manquant. En l'absence d'espace de noms, le signe deux-points peut également être omis.|
|<xref:System.Array> de type <xref:System.Byte>|Tableau de nombres|Chaque chiffre représente la valeur d'un octet.|
|<xref:System.DateTime>|DateTime ou chaîne|Voir « Dates/heures et JSON » ci-après dans cette rubrique.|
|<xref:System.DateTimeOffset>|Type complexe|Voir « Dates/heures et JSON » ci-après dans cette rubrique.|
|Types XML et ADO.NET (objet <xref:System.Xml.XmlElement>,<br /><br /> <xref:System.Xml.Linq.XElement>. Tableaux d'objet <xref:System.Xml.XmlNode>,<br /><br /> <xref:System.Runtime.Serialization.ISerializable>,<br /><br /> <xref:System.Data.DataSet>).|String|Voir la section Types XML et JSON de cette rubrique.|
|<xref:System.DBNull>|Type complexe vide|--|
|Collections, dictionnaires et tableaux|Array|Voir la section Collections, dictionnaires et tableaux de cette rubrique.|
|Types complexes (avec <xref:System.Runtime.Serialization.DataContractAttribute> ou <xref:System.SerializableAttribute> appliqué)|Type complexe|Les membres de données deviennent membres du type complexe JavaScript.|
|Types complexes implémentant l'interface <xref:System.Runtime.Serialization.ISerializable>)|Type complexe|Identique à d'autres types complexes mais certains types <xref:System.Runtime.Serialization.ISerializable> ne sont pas pris en charge ; consultez Prise en charge de l'interface ISerializable dans la section Informations avancées de cette rubrique.|
|Valeur `Null` pour tout type|Null|Les types de valeur nulables sont également pris en charge et cartographient JSON de la même manière que les types de valeur non annulables.|

### <a name="enumerations-and-json"></a>Énumérations et JSON

Les valeurs de membre de l'énumération sont traitées comme des nombres dans JSON, ce qui diffère de la manière dont elles sont traitées dans les contrats de données, où elles sont incluses comme noms de membres. Pour plus d’informations sur le traitement des contrats de données, voir [Les types d’énumération dans les contrats de données](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Par exemple, si vous avez `public enum Color {red, green, blue, yellow, pink}`, `yellow` produit le nombre 3 et pas la chaîne "yellow".

- Tous les membres `enum` sont sérialisables. Les attributs <xref:System.Runtime.Serialization.EnumMemberAttribute> et <xref:System.NonSerializedAttribute> sont ignorés s'ils sont utilisés.

- Il est possible de désérialiser une valeur `enum` inexistante ; par exemple, la valeur 87 peut être désérialisée en l'énumération Color précédente même s'il n'existe aucun nom de couleur correspondant défini.

- Un indicateur `enum` n'est pas spécial et est traité comme tous les autres `enum`.

### <a name="datestimes-and-json"></a>Dates/heures et JSON

Le format JSON ne prend pas directement en charge les dates et heures. Cependant, elles sont fréquemment utilisées et ASP.NET AJAX assure une prise en charge spéciale de ces types. Lorsque vous utilisez des proxys ASP.NET AJAX, le type <xref:System.DateTime> dans .NET correspond exactement au type `DateTime` dans JavaScript.

- Lorsque vous n'utilisez pas ASP.NET, un type <xref:System.DateTime> est représenté dans JSON sous forme de chaîne avec un format spécial qui est décrit dans la section Informations avancées de cette rubrique.

- <xref:System.DateTimeOffset> est représenté dans JSON comme un type complexe : {"DateTime": dateTime, "OffsetMinutes": offsetMinutes}. Le membre `offsetMinutes` est le décalage de l'heure locale par rapport à l'heure de Greenwich (GMT, Greenwich Mean Time), également appelée heure universelle coordonnée (UTC, Coordinated Universal Time), associé à l'emplacement de l'événement concerné. Le membre `dateTime` représente l'instant où l'événement s'est produit (ici encore, il devient un `DateTime` dans JavaScript lorsque ASP.NET AJAX est utilisé, et une chaîne dans le cas contraire). Lors de la sérialisation, le membre `dateTime` est toujours sérialisé au format GMT. Par conséquent, si vous décrivez 3 h 00 du matin, heure de New York, `dateTime` a un composant horaire de 8 h 00 du matin et `offsetMinutes` correspond à 300 (moins 300 minutes ou 5 heures par rapport à GMT).

  > [!NOTE]
  > Les objets <xref:System.DateTime> et <xref:System.DateTimeOffset>, lorsqu'ils sont sérialisés en JSON, préservent uniquement les informations avec une précision égale à la milliseconde. Les valeurs plus précises que les millisecondes (micro/nanosecondes) sont perdues lors de la sérialisation.

### <a name="xml-types-and-json"></a>Types XML et JSON

Les types XML deviennent des chaînes JSON.

- Par exemple, si un membre de la donnée \<"q" de type XElement contient\<abc/>, le JSON est "q":" abc/>".

- Il existe des règles spéciales qui spécifient la manière dont le code XML est encapsulé. Pour plus d'informations, consultez la section Informations Avancées ci-après dans cette rubrique.

- Si vous utilisez ASP.NET AJAX et que vous ne souhaitez pas utiliser des chaînes dans JavaScript mais le type XML DOM à la place, définissez XML sur <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> pour la propriété <xref:System.ServiceModel.Web.WebGetAttribute> ou définissez XML sur <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> pour la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute>.

### <a name="collections-dictionaries-and-arrays"></a>Collections, dictionnaires et tableaux

Tous les dictionnaires, tableaux et collections sont représentés dans JSON sous forme de tableaux.

- Toute personnalisation qui utilise le <xref:System.Runtime.Serialization.CollectionDataContractAttribute> est ignorée dans la représentation JSON.

- Les dictionnaires ne permettent pas de travailler directement avec JSON. Chaîne\<de dictionnaire,> d’objet peuvent ne pas être pris en charge de la même manière dans WCF que prévu de travailler avec d’autres technologies JSON. Par exemple, si "abc" est mappé à "xyz" et "def" est mappé à 42 dans un dictionnaire, la représentation JSON n'est pas {"abc":"xyz","def":42}, mais [{"Key":"abc","Value":"xyz"},{"Key":"def","Value":42}].

- Si vous souhaitez travailler directement avec JSON (en accédant aux clés et aux valeurs dynamiquement sans prédéfinir un contrat rigide), vous disposez de plusieurs options :

  - Envisagez d’utiliser l’échantillon [de Sérialisation JSON (AJAX) de faible type.](../../../../docs/framework/wcf/samples/weakly-typed-json-serialization-sample.md)

  - Utilisez les constructeurs de désérialisation et l’interface <xref:System.Runtime.Serialization.ISerializable> : ces deux mécanismes vous permettent d’accéder aux paires clé/valeur JSON lors de la sérialisation et de la désérialisation respectivement, mais ils ne fonctionnent pas dans les scénarios de confiance partielle.

  - Envisagez de travailler avec la [cartographie entre JSON et XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md) au lieu d’utiliser un sérialisateur.

  - *Le polymorphisme* dans le contexte de la sérialisation se réfère à la capacité de sérialiser un type dérivé où son type de base est attendu. Il existe des règles spéciales propres à JSON lorsque les collections sont utilisées de manière polymorphique, lors de l’affectation d’une collection à un <xref:System.Object> par exemple. Ce problème est abordé de manière plus détaillée dans la section Informations avancées ci-après dans cette rubrique.

## <a name="additional-details"></a>Détails supplémentaires

### <a name="order-of-data-members"></a>Ordre des membres de données

L'ordre des membres de données n'est pas important lors de l'utilisation de JSON. Plus précisément, même si la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> est définie, les données JSON peuvent toujours être désérialisées dans n'importe quel ordre.

### <a name="json-types"></a>Types JSON

Le type JSON ne doit pas nécessairement correspondre au tableau précédent lors de la désérialisation. Par exemple, un type `Int` est normalement mappé à un nombre JSON, mais il peut également être correctement désérialisé à partir d'une chaîne JSON dans la mesure où cette chaîne contient un nombre valide. Autrement dit, {"q":42} et {"q":"42"} sont tous deux valides s'il existe un membre de données `Int` appelé "q".

### <a name="polymorphism"></a>Polymorphisme

La sérialisation polymorphique désigne la capacité à sérialiser un type dérivé lorsque son type de base est attendu. Ceci est pris en charge pour la sérialisation JSON par WCF comparable à la façon dont la sérialisation XML est pris en charge. Par exemple, vous `MyDerivedType` pouvez `MyBaseType` sérialiser `Int` où on s’attend, ou sérialiser où `Object` on s’attend.

Les informations de type peuvent être perdues lors de la désérialisation d'un type dérivé si le type de base est attendu, sauf si vous désérialisez un type complexe. Par exemple, si un <xref:System.Uri> est sérialisé lorsque <xref:System.Object> est attendu, il se traduit par une chaîne JSON. Si cette chaîne est désérialisée de nouveau en un <xref:System.Object>, un <xref:System.String> .NET  est retourné. Le désérialiseur ne sait pas que la chaîne était au départ de type <xref:System.Uri>. En général, lorsque <xref:System.Object> est attendu, toutes les chaînes JSON sont désérialisées en tant que chaînes .NET, et tous les tableaux JSON utilisés pour sérialiser des collections, dictionnaires et tableaux .NET sont désérialisés en tant que <xref:System.Array> .NET de type <xref:System.Object>, indépendamment du type initial réel. Un booléen JSON est mappé à un <xref:System.Boolean> .NET. Cependant, lorsqu'un <xref:System.Object> est attendu, les nombres JSON sont désérialisés en tant que types <xref:System.Int32>, <xref:System.Decimal> ou <xref:System.Double> .NET, le type le plus approprié étant automatiquement choisi.

Lors de la désérialisation en un type d'interface, le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> procède à la désérialisation comme si le type déclaré était Object.

Lorsque vous travaillez avec vos propres types dérivés et de base, l'utilisation du <xref:System.Runtime.Serialization.KnownTypeAttribute>, <xref:System.ServiceModel.ServiceKnownTypeAttribute> ou d'un mécanisme équivalent est généralement nécessaire. Par exemple, si vous avez `Animal` une opération qui a une `Cat` valeur `Animal`de retour et <xref:System.Runtime.Serialization.KnownTypeAttribute>qu’elle `Animal` renvoie <xref:System.ServiceModel.ServiceKnownTypeAttribute> en fait une `Cat` instance de (dérivée), vous devez soit appliquer le , sur le type ou l’opération et spécifier le type dans ces attributs. Pour plus d’informations, voir [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).

Pour obtenir des informations détaillées sur le fonctionnement de la sérialisation polymorphique et connaître certaines limitations qui doivent être respectées lors de son utilisation, consultez la section Informations avancées ci-après dans cette rubrique.

### <a name="versioning"></a>Gestion de version

Les fonctionnalités de contrôle de version des contrats de données, notamment l’interface <xref:System.Runtime.Serialization.IExtensibleDataObject>, sont intégralement prises en charge dans JSON. Qui plus est, dans la plupart des cas, il est possible de désérialiser un type dans un format (par exemple, XML) puis de le sérialiser dans un autre format (par exemple, JSON) tout en préservant les données dans <xref:System.Runtime.Serialization.IExtensibleDataObject>. Pour plus d’informations, consultez [Contrats de données compatibles avec des versions ultérieures](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Rappelez-vous que l'ordre n'intervient pas dans JSON et que les informations sur l'ordre sont donc perdues. De plus, JSON ne prend pas en charge plusieurs paires clé/valeur dotées du même nom de clé. En dernier lieu, toutes les opérations sur <xref:System.Runtime.Serialization.IExtensibleDataObject> sont polymorphiques par nature, c'est-à-dire que leur type dérivé est assigné à <xref:System.Object>, le type de base pour tous les types.

## <a name="json-in-urls"></a>JSON dans les URL

Lorsque vous utilisez des points de terminaison ASP.NET AJAX avec le verbe HTTP GET (en utilisant l'attribut <xref:System.ServiceModel.Web.WebGetAttribute>), les paramètres entrants apparaissent dans l'URL de demande au lieu du corps du message. JSON est pris en charge même dans l’URL `Int` de demande, donc `Person` si vous avez une opération qui prend un "numéro" appelé et un type complexe appelé "p", l’URL peut ressembler à l’URL suivante.

```html
http://example.com/myservice.svc/MyOperation?number=7&p={"name":"John","age":42}
```

Si vous utilisez un contrôle Script Manager ASP.NET AJAX et un proxy pour appeler le service, cette URL n'est pas automatiquement générée par le proxy et n'est pas visible. JSON ne peut pas être utilisé dans les URL sur les points de terminaison AJAX non-ASP.NET.

## <a name="advanced-information"></a>Informations avancées

### <a name="iserializable-support"></a>Prise en charge de ISerializable

#### <a name="supported-and-unsupported-iserializable-types"></a>Types ISerializable pris en charge et non pris en charge

En règle générale, les types qui implémentent l'interface <xref:System.Runtime.Serialization.ISerializable> sont totalement pris en charge lors de la sérialisation/désérialisation de données JSON. Cependant, certains de ces types (notamment certains types .NET Framework) sont implémentés de telle manière que les aspects de la sérialisation propres à JSON entraînent une désérialisation incorrecte de ces types :

- Avec <xref:System.Runtime.Serialization.ISerializable>, le type des différents membres de données n'est jamais connu à l'avance. Ceci conduit à une situation polymorphique similaire à la désérialisation des types en un objet. Comme nous l'avons mentionné précédemment, il est possible que les informations de type soient perdues dans JSON. Par exemple, un type qui sérialise un `enum` dans son implémentation <xref:System.Runtime.Serialization.ISerializable> et tente de le désérialiser directement en un `enum` (sans cast approprié) échoue, car un `enum` est sérialisé à l'aide de nombres dans JSON et les nombres JSON sont désérialisés en types numériques .NET intégrés (Int32, Decimal ou Double). Par conséquent, la valeur `enum` initiale du nombre n'est pas conservée.

- Un type <xref:System.Runtime.Serialization.ISerializable> qui repose sur un ordre de désérialisation spécifique dans son constructeur de désérialisation peut également ne pas parvenir à désérialiser certaines données JSON, car la plupart des sérialiseurs JSON ne garantissent pas un ordre spécifique.

#### <a name="factory-types"></a>Types de fabrique

Bien que l’interface <xref:System.Runtime.Serialization.IObjectReference> soit prise en charge dans JSON en général, tous les types qui nécessitent la fonctionnalité « type de fabrique » (qui retourne une instance d’un type de <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%28System.Runtime.Serialization.StreamingContext%29> différent de celui qui implémente l’interface) ne sont pas pris en charge.

### <a name="datetime-wire-format"></a>Format de transmission DateTime

Les valeurs <xref:System.DateTime> apparaissent en tant que chaînes JSON au format "/Date(700000+0500)/", où le premier nombre (700000, dans l'exemple fourni) est le nombre de millisecondes dans le fuseau horaire GMT, heure standard (n'appliquant pas l'heure d'été) depuis le 1er janvier 1970 à minuit. Le nombre peut être négatif pour représenter des heures antérieures. La partie composée de "+0500" dans l’exemple est facultative et indique que l’heure est de type <xref:System.DateTimeKind.Local> ; c’est-à-dire qu’elle doit être convertie dans le fuseau horaire local lors de la désérialisation. Si cette partie est omise, l'heure est désérialisée en tant que <xref:System.DateTimeKind.Utc>. Le nombre réel ("0500" dans cet exemple) et son signe (+ ou -) sont ignorés.

Lorsque vous sérialisez <xref:System.DateTime>, les heures <xref:System.DateTimeKind.Local> et <xref:System.DateTimeKind.Unspecified> sont écrites avec un offset, et <xref:System.DateTimeKind.Utc> est écrite sans offset.

Le code JavaScript client ASP.NET AJAX convertit automatiquement ces chaînes en instances `DateTime` JavaScript. S'il existe d'autres chaînes avec un format similaire qui ne sont pas de type <xref:System.DateTime> dans .NET, elles sont également converties.

La conversion n’a lieu que si les caractères "/"\\sont échappés (c’est-à-dire que le\\JSON ressemble à " /Date(700000-0500) /"), et pour cette raison WCF JSON encoder (activé par le <xref:System.ServiceModel.WebHttpBinding>) échappe toujours le "/" caractère.

### <a name="xml-in-json-strings"></a>XML dans les chaînes JSON

#### <a name="xmlelement"></a>XmlElement

<xref:System.Xml.XmlElement> est sérialisé tel quel, sans encapsulation. Par exemple, le membre des <xref:System.Xml.XmlElement> données \<« x » de type qui contient abc/> est représenté comme suit :

```json
{"x":"<abc/>"}
```

#### <a name="arrays-of-xmlnode"></a>Tableaux de XmlNode

Les objets <xref:System.Array> de type <xref:System.Xml.XmlNode> sont encapsulés dans un élément appelé ArrayOfXmlNode dans l'espace de noms de contrat de données standard du type. Si "x" est un tableau qui contient un nœud d'attribut "N" dans l'espace de noms "ns" qui contient "value" et un nœud d'élément vide "M", la représentation est la suivante.

```json
{"x":"<ArrayOfXmlNode xmlns=\"http://schemas.datacontract.org/2004/07/System.Xml\" a:N=\"value\" xmlns:a=\"ns\"><M/></ArrayOfXmlNode>"}
```

 Les attributs dans l'espace de noms vide au début des tableaux XmlNode (avant les autres éléments) ne sont pas pris en charge.

#### <a name="ixmlserializable-types-including-xelement-and-dataset"></a>Types IXmlSerializable y compris XElement et DataSet

Les types <xref:System.Runtime.Serialization.ISerializable> sont subdivisés en "types de contenu", "type DataSet" et "types d'éléments". Pour les définitions de ces types, voir [XML et ADO.NET Types dans les contrats de données](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

Le types "Contenu" et "DataSet" sont sérialisés de la même manière que les objets <xref:System.Array> de <xref:System.Xml.XmlNode> traités dans la section précédente. Ils sont encapsulés dans un élément dont le nom et l'espace de noms correspond au nom et à l'espace de noms de contrat de données du type en question.

Le types "Élément" tels que <xref:System.Xml.Linq.XElement> sont sérialisés tels quels, de la même manière que les types <xref:System.Xml.XmlElement> traités ci-avant dans cette rubrique.

### <a name="polymorphism"></a>Polymorphisme

#### <a name="preserving-type-information"></a>Préservation des informations de type

Comme nous l'avons indiqué précédemment, le polymorphisme est pris en charge dans JSON avec certaines limitations. JavaScript est un langage faiblement typé et l'identité des types ne constitue généralement pas un problème. Toutefois, lorsque vous utilisez JSON pour communiquer entre un système fortement typé (.NET) et un système faiblement typé (JavaScript), il est utile de préserver l'identité des types. Par exemple, les types avec les noms de contrat de données "Circle" et "Square" dérivent d'un type avec un nom de contrat de données "Shape". Si « Circle » est envoyé de .NET à Javascript et est ultérieurement retourné en une méthode .NET qui attend « Shape », il est utile pour le côté .NET de savoir que l'objet était initialement un « Circle » : dans le cas contraire, toutes les informations spécifiques au type dérivé (par exemple, le membre de données « radius » sur « Circle ») pourront être perdues.

Pour préserver l'identité des types lors de la sérialisation de types complexes au format JSON, un « affinage du type » peut être ajouté, et le désérialiseur reconnaît l'affinage et agit en conséquence. Le « indice de type » est une paire de\_\_touches/valeur JSON avec le nom clé de « type » (deux souligne suivis du mot « type »). La valeur est une chaîne JSON au format "NomContratDonnées:EspaceDeNomsContratDonnées" (les éléments qui précèdent le signe deux-points constituent le nom). Avec l'exemple précédent, "Circle" peut être sérialisé comme suit.

```json
{"__type":"Circle:http://example.com/myNamespace","x":50,"y":70,"radius":10}
```

L'affinage du type est très semblable à l'attribut `xsi:type` défini par la norme d'instance de schéma XML, et il est utilisé lors de la sérialisation/désérialisation XML.

Les membres\_\_de données appelés « type » sont interdits en raison d’un conflit potentiel avec l’indice de type.

#### <a name="reducing-the-size-of-type-hints"></a>Réduction de la taille des affinages de type

Pour réduire la taille des messages JSON, le`http://schemas.datacontract.org/2004/07/`préfixe de l’espace de nom de contrat de données par défaut () est remplacé par le caractère « ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' (Pour rendre ce remplacement réversible, une règle d’évasion est utilisée:\\si l’espace de nom commence\\par le " ou " caractères ", ils sont annexés par un caractère supplémentaire "). Ainsi, si "Circle" est un type dans le namespace .NET "MyApp.Shapes", son namespace contrat de données par défaut est `http://schemas.datacontract.org/2004/07/MyApp`. Les formes (shapes) et la représentation JSON sont les suivantes.

```json
{"__type":"Circle:#MyApp.Shapes","x":50,"y":70,"radius":10}
```

Tant le tronqué (#MyApp.Shapes) et lehttp://schemas.datacontract.org/2004/07/MyApp.Shapes) plein (noms sont compris sur la désétérialisation.

#### <a name="type-hint-position-in-json-objects"></a>Emplacement des affinages de type dans les objets  JSON

Notez que l'affinage du type doit apparaître en premier dans la représentation JSON. C'est le cas uniquement lorsque l'ordre des paires clé/valeur est important dans le traitement JSON. Par exemple, la méthode suivante n'est pas valide pour spécifier l'affinage du type.

```json
{"x":50,"y":70,"radius":10,"__type":"Circle:#MyApp.Shapes"}
```

Tant <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> l’utilisation par WCF et ASP.NET pages client AJAX émettent toujours l’indice de type en premier.

#### <a name="type-hints-apply-only-to-complex-types"></a>Les affinages de type s'appliquent uniquement à des types complexes

Il n'est pas possible d'émettre un affinage du type pour les types non complexes. Par exemple, si le type de retour d’une opération est <xref:System.Object> mais que l’opération retourne Circle, la représentation JSON peut être semblable à celle présentée précédemment et les informations de type sont préservées. Cependant, si Uri est retourné, la représentation JSON est une chaîne et les informations qui indiquaient que la chaîne représentait auparavant un Uri sont perdues. Ceci s’applique non seulement aux types primitifs mais également aux collections et aux tableaux.

#### <a name="when-are-type-hints-emitted"></a>Quand les affinages de type sont-ils émis ?

Les affinages de type peuvent générer une augmentation importante de la taille des messages (pour limiter ce problème, vous pouvez utiliser des espaces de noms de contrats de données plus courts si possible). Par conséquent, les règles suivantes déterminent si des affinages de type sont émis :

- Lorsque vous utilisez ASP.NET AJAX, les affinages de type sont toujours émis chaque fois que cela est possible, même s'il n'existe aucune attribution de type dérivé/de base ; par exemple, même si Circle est attribué à Circle. (Ceci est nécessaire pour activer totalement le processus d'appel depuis l'environnement JSON faiblement typé vers l'environnement .NET fortement typé sans perte d'informations inattendue.)

- Lorsque vous utilisez les services AJAX sans intégration ASP.NET, les affinages de type sont émis uniquement s'il existe une attribution de type dérivé/de base ; c'est-à-dire qu'ils sont émis lorsque Circle est attribué à Shape ou à <xref:System.Object> mais n'est pas attribué à Circle. Vous disposez ainsi des informations minimales requises pour implémenter correctement un client JavaScript et améliorer ainsi les performances, sans pour autant vous protéger contre les pertes d'informations de type dans les clients conçus de manière incorrecte. Évitez systématiquement les attributions de type de base/dérivé sur le serveur si vous ne voulez pas être contraint de gérer ce problème sur le client.

- Lorsque vous utilisez le type <xref:System.Runtime.Serialization.DataContractSerializer>, le paramètre de constructeur `alwaysEmitTypeInformation` vous permet de choisir entre les deux modes précédents, la valeur par défaut étant "`false`" (émission des affinages de type uniquement lorsqu'ils sont nécessaires).

#### <a name="duplicate-data-member-names"></a>Noms de membres de données dupliqués

Les informations de type dérivé sont présentes dans le même objet JSON avec les informations de type de base, et elles peuvent apparaître dans n'importe quel ordre. Par exemple, `Shape` peut être représenté comme suit.

```json
{"__type":"Shape:#MyApp.Shapes","x":50,"y":70}
```

Quant à Circle, il peut être représenté comme suit.

```json
{"__type":"Circle:#MyApp.Shapes","x":50, "radius":10,"y":70}
```

Si le `Shape` type de base contenait`radius`également un membre de données appelé « », cela conduit à une collision à la fois sur la sérialisation (parce que les objets JSON ne peuvent pas avoir des noms clés répétitifs) et la désétérialisation (parce qu’il n’est pas clair si «radius» se réfère à `Shape.radius` ou `Circle.radius`). Par conséquent, le concept de « masquage de propriété » (membres de données du même nom sur des classes de base et dérivées), qui est généralement déconseillé dans les classes de contrats de données, est en fait interdit dans le cas de JSON.

#### <a name="polymorphism-and-ixmlserializable-types"></a>Polymorphisme et types IXmlSerializable 

Les types <xref:System.Xml.Serialization.IXmlSerializable> peuvent être assignés de manière polymorphique les uns aux autres normalement, à condition que les impératifs de types connus soient respectés, conformément aux règles de contrats de données standard. Cependant, la sérialisation d'un type <xref:System.Xml.Serialization.IXmlSerializable> à la place de <xref:System.Object> entraîne la perte des informations de type et le résultat est une chaîne JSON.

#### <a name="polymorphism-and-certain-interface-types"></a>Polymorphisme et certains types d'interface

Il est interdit de sérialiser un type de collection ou un type qui implémente <xref:System.Xml.Serialization.IXmlSerializable> lorsqu’un type autre qu’une collection qui n’est pas <xref:System.Xml.Serialization.IXmlSerializable> (à l’exception de <xref:System.Object>) est attendu. Par exemple, une `IMyInterface` interface personnalisée `MyType` appelée <xref:System.Collections.Generic.IEnumerable%601> et `int` un `IMyInterface`type qui implémente à la fois le type et . Il est interdit `MyType` de revenir d’une opération dont le type de retour est `IMyInterface`. C’est `MyType` parce qu’il doit être sérialisé comme un tableau JSON et nécessite un indice de type, et comme indiqué avant vous ne pouvez pas inclure un indice de type avec des tableaux, seulement avec des types complexes.

#### <a name="known-types-and-configuration"></a>Types connus et configuration

Tous les mécanismes de types connus utilisés par le <xref:System.Runtime.Serialization.DataContractSerializer> sont pris en charge de la même manière par le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Les deux sérialisateurs lisent le même élément de configuration, [ \<dataContractSerializer>](../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md) dans [ \<system.runtime.serialization>](../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md), pour découvrir les types connus ajoutés à travers un fichier de configuration.

#### <a name="collections-assigned-to-object"></a>Collections assignées à Object

Les collections assignées à Object sont sérialisées comme s'il s'agissait de collections qui implémentent <xref:System.Collections.Generic.IEnumerable%601> : tableau JSON dont chaque entrée comporte un affinage de type s'il s'agit d'un type complexe. Par exemple, <xref:System.Collections.Generic.List%601> un `Shape` type <xref:System.Object> assigné à ressemble à ce qui suit.

```json
[{"__type":"Shape:#MyApp.Shapes","x":50,"y":70},
{"__type":"Shape:#MyApp.Shapes","x":58,"y":73},
{"__type":"Shape:#MyApp.Shapes","x":41,"y":32}]
```

Lorsque vous procédez à la désérialisation vers <xref:System.Object> :

- `Shape`doit figurer dans la liste des types connus. Avoir <xref:System.Collections.Generic.List%601> le `Shape` type dans les types connus n’a aucun effet. Notez que vous n’avez pas à ajouter `Shape` à des types connus sur la sérialisation dans ce cas - cela se fait automatiquement.

- La collection est déséialisée <xref:System.Object> comme `Shape` un <xref:System.Array> type qui contient des instances.

#### <a name="derived-collections-assigned-to-base-collections"></a>Collections dérivées assignées aux collections de base

Lorsqu’une collection dérivée est assignée à une collection de base, elle est généralement sérialisée comme s’il s’agissait d’une collection du type de base. Toutefois, si le type d'élément de la collection dérivée ne peut pas être assigné au type d'élément de la collection de base, une exception est levée.

#### <a name="type-hints-and-dictionaries"></a>Affinages de type et dictionnaires

Lorsqu'un dictionnaire est assigné à un <xref:System.Object>, chaque entrée de clé et de valeur du dictionnaire est traitée comme si elle était assignée à <xref:System.Object> et obtient un affinage du type.

Lors de la sérialisation des types de dictionnaire, l’objet JSON qui contient les membres "Clé" et "Valeur" n’est pas affecté par le paramètre `alwaysEmitTypeInformation` et contient un affinage du type uniquement lorsqu’il est requis par les règles de collection précédentes.

### <a name="valid-json-key-names"></a>Nom de clés JSON valides

Le sérialiseur encode au format XML les noms de clés qui ne constituent pas des noms XML valides. Par exemple, un membre de données ayant le nom de « 123 » aurait\_\_un nom\_\_codé tel que\_«\_x0031 x0032 x0033 » parce que « 123 » est un nom d’élément XML invalide (commence par un chiffre). Une situation similaire peut se produire avec certains jeux de caractères internationaux non valides dans les noms XML. Pour une explication de cet effet de XML sur le traitement JSON, voir [Cartographie entre JSON et XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

## <a name="see-also"></a>Voir aussi

- [Prise en charge du format JSON et d'autres formats de transfert de données](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
