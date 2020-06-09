---
title: Types de collections dans les contrats de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
ms.openlocfilehash: a10b7c5295407cfbb36446581a4b75670e37bc6a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579747"
---
# <a name="collection-types-in-data-contracts"></a>Types de collections dans les contrats de données

Une *collection* est une liste d'éléments d'un certain type. Dans le .NET Framework, ces listes peuvent être représentées à l’aide de tableaux ou de divers autres types (liste générique, générique <xref:System.ComponentModel.BindingList%601> , <xref:System.Collections.Specialized.StringCollection> ou <xref:System.Collections.ArrayList> ). Par exemple, une collection peut contenir une liste d'adresses pour un client donné. Ces collections sont appelées *collections liste*, indépendamment de leur type réel.

Il existe une forme spéciale de collection qui représente une association entre un élément (la "clé") et un autre élément (la "valeur"). Dans le .NET Framework, ils sont représentés par des types tels que <xref:System.Collections.Hashtable> et le dictionnaire générique. Par exemple, une collection association peut mapper une ville ("clé") à sa population ("valeur"). Ces collections sont appelées *collections dictionnaire*, indépendamment de leur type réel.

Les collections reçoivent un traitement spécial dans le modèle de contrat de données.

Les types qui implémentent l'interface <xref:System.Collections.IEnumerable> , y compris des tableaux et des collections génériques, sont reconnus en tant que collections. Parmi eux, les types qui implémentent les interfaces <xref:System.Collections.IDictionary> ou <xref:System.Collections.Generic.IDictionary%602> générique sont des collections dictionnaire ; tous les autres sont des collections liste.

Des exigences supplémentaires sur les types de collections, telles que le fait d’avoir une méthode appelée `Add` et un constructeur sans paramètre, sont décrites en détail dans les sections suivantes. Cela garantit que les types de collections peuvent être à la fois sérialisés et désérialisés. Cela signifie que certaines collections ne sont pas prises en charge directement, telles que le générique <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (car elle n’a aucun constructeur sans paramètre). Toutefois, pour plus d'informations sur la façon de contourner ces restrictions, consultez la section « Utilisation des types d'interfaces de collection et des collections en lecture seule » plus loin dans cette rubrique.

Les types contenus dans les collections doivent être des types de contrat de données ou, dans le cas contraire, ils doivent être sérialisables. Pour plus d’informations, consultez [types pris en charge par le sérialiseur de contrat de données](types-supported-by-the-data-contract-serializer.md).

Pour plus d’informations sur ce qui est et ce qui n’est pas considéré comme une collection valide, ainsi que sur la façon dont les collections sont sérialisées, consultez les informations relatives à la sérialisation des collections dans la section « règles de collection avancées » de cette rubrique.

## <a name="interchangeable-collections"></a>Collections interchangeables

Toutes les collections liste du même type sont considérées comme ayant le même contrat de données (à moins d'être personnalisées à l'aide de l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> , comme cela est présenté ultérieurement dans cette rubrique). Ainsi, par exemple, les contrats de données suivants sont équivalents :

[!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
[!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]

Les deux contrats de données génèrent un XML semblable au code suivant :

```xml
<PurchaseOrder>
    <customerName>...</customerName>
    <items>
        <Item>...</Item>
        <Item>...</Item>
        <Item>...</Item>
        ...
    </items>
    <comments>
        <string>...</string>
        <string>...</string>
        <string>...</string>
        ...
    </comments>
</PurchaseOrder>
```

L'interchangeabilité des collections vous permet d'utiliser, par exemple, un type de collection optimisé pour les performances sur le serveur, et un type de collection conçu pour être lié aux composants de l'interface utilisateur sur le client.

Semblables aux collections liste, toutes les collections dictionnaire qui ont les mêmes types de clé et de valeur sont considérées comme ayant le même contrat de données (à moins d'être personnalisées à l'aide de l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> ).

Seul le type de contrat de données importe en ce qui concerne l'équivalence de collections, pas les types .NET. Autrement dit, une collection de Type1 est considérée équivalente à une collection de Type2 si Type1 et Type2 ont des contrats de données équivalents.

Les collections non génériques sont considérées comme ayant le même contrat de données que les collections génériques de type `Object`. (Par exemple, les contrats de données pour <xref:System.Collections.ArrayList> et la <xref:System.Collections.Generic.List%601> générique de type `Object` sont les mêmes.)

## <a name="using-collection-interface-types-and-read-only-collections"></a>Utilisation des types d'interfaces de collection et des collections en lecture seule

Les types d'interfaces de collection (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>, <xref:System.Collections.Generic.IDictionary%602>générique, ou les interfaces dérivées de ces interfaces) sont également considérés comme ayant des contrats de données de collection équivalents aux contrats de données de collection pour les types de collections réels. Par conséquent, il est possible de déclarer le type en cours de sérialisation comme type d'interface de collection et les résultats sont les mêmes que si un type de collection réel était utilisé. Par exemple, les contrats de données suivants sont équivalents.

[!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
[!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]

Pendant la sérialisation, lorsque le type déclaré est une interface, le type d'instance réel utilisé peut être tout type qui implémente cette interface. Les restrictions présentées précédemment (avec un constructeur sans paramètre et une `Add` méthode) ne s’appliquent pas. Par exemple, vous pouvez définir les adresses dans Customer2 sur une instance de <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> générique d'adresse, bien que vous ne puissiez pas déclarer directement un membre de données de type <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>générique.

Pendant la désérialisation, lorsque le type déclaré est une interface, le moteur de sérialisation choisit un type qui implémente l'interface déclarée, et ce type est instancié. Le mécanisme des types connus (décrit dans [types de contrat de données connus](data-contract-known-types.md)) n’a aucun effet ici ; le choix du type est intégré à WCF.

## <a name="customizing-collection-types"></a>Personnalisation des types de collections

Vous pouvez personnaliser les types de collections à l'aide de l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> , qui présente plusieurs utilisations.

Notez que la personnalisation de types collection compromet l'interchangeabilité des collections. Il est donc généralement recommandé d'éviter d'appliquer cet attribut chaque fois que cela est possible. Pour plus d’informations sur ce problème, consultez la section « règles de collection avancées » plus loin dans cette rubrique.

### <a name="collection-data-contract-naming"></a>Attribution de noms aux contrats de données de collection

Les règles d’attribution de noms aux types de collections sont semblables à celles d’attribution de noms aux types de contrat de données classiques, comme cela est décrit dans [Data Contract Names](data-contract-names.md), bien que certaines différences importantes existent :

- L'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> permet de personnaliser le nom, à la place de l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> . L'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> possède également les propriétés `Name` et `Namespace` .

- Lorsque l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> n'est pas appliqué, le nom et l'espace de noms par défaut pour les types de collections dépendent des noms et des espaces de noms des types inclus dans la collection. Ils ne sont pas affectés par le nom et l'espace de noms du type de collection lui-même. Pour obtenir un exemple, consultez les types suivants.

  ```csharp
  public CustomerList1 : Collection<string> {}
  public StringList1 : Collection<string> {}
  ```

Le nom de contrat de données des deux types est "ArrayOfstring" et non pas "CustomerList1" ou "StringList1". Cela signifie que la sérialisation de n'importe lequel de ces types au niveau racine retourne un XML semblable au code suivant.

```xml
<ArrayOfstring>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</ArrayOfstring>
```

Cette règle d'attribution de noms a été choisie pour garantir que tous les types non personnalisés représentant une liste de chaînes aient les mêmes contrat de données et représentation XML. Cela permet l'interchangeabilité des collections. Dans cet exemple, CustomerList1 et StringList1 sont complètement interchangeables.

Toutefois, lorsque l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> est appliqué, la collection devient un contrat de données de collection personnalisé, même si aucune propriété n'est définie sur l'attribut. Le nom et l'espace de noms du contrat de données de collection dépendent alors du type de collection lui-même. Pour obtenir un exemple, consultez le type suivant.

[!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
[!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]

En cas de sérialisation, le XML obtenu est semblable au code ci-dessous.

```xml
<CustomerList2>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</CustomerList2>
```

Vous remarquerez qu'il n'est plus équivalent à la représentation XML des types non personnalisés.

- Vous pouvez utiliser les propriétés `Name` et `Namespace` pour personnaliser encore plus l'attribution de noms. Consultez la classe suivante.

  [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
  [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]

Le XML obtenu est semblable au code suivant :

```xml
<cust_list>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</cust_list>
```

Pour plus d’informations, consultez la section « règles de collection avancées » plus loin dans cette rubrique.

### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Personnalisation du nom d'élément répétitif dans les collections liste

Les collections liste contiennent des entrées répétitives. Normalement, chaque entrée répétitive est représentée comme un élément nommé en fonction du nom de contrat de données du type contenu dans la collection.

Dans les exemples `CustomerList` , les collections contenaient des chaînes. Le nom du contrat de données pour le type primitif de chaîne est « String », donc l’élément répété était « \<string> ».

Toutefois, le nom de cet élément répétitif peut être personnalisé à l'aide de la propriété <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> sur l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> . Pour obtenir un exemple, consultez le type suivant.

[!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
[!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]

Le XML obtenu est semblable au code suivant :

```xml
<CustomerList4>
    <customer>...</customer>
    <customer>...</customer>
    <customer>...</customer>
    ...
</CustomerList4>
```

L'espace de noms de l'élément répétitif est toujours identique à celui du contrat de données de collection, qui peut être personnalisé à l'aide de la propriété `Namespace` , comme décrit précédemment.

### <a name="customizing-dictionary-collections"></a>Personnalisation des collections dictionnaire

Les collections dictionnaire sont essentiellement des listes d'entrées dans lesquelles chaque entrée a une clé suivie par une valeur. Comme avec les listes normales, vous pouvez modifier le nom d'élément qui correspond à l'élément répétitif en utilisant la propriété <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> .

En outre, vous pouvez modifier les noms d'élément qui représentent la clé et la valeur en utilisant les propriétés <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> et <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> . Les espaces de noms pour ces éléments sont les mêmes que l'espace de noms du contrat de données de collection.

Pour obtenir un exemple, consultez le type suivant.

[!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
[!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]

En cas de sérialisation, le XML obtenu est semblable au code ci-dessous.

```xml
<CountriesOrRegionsWithCapitals>
    <entry>
        <countryorregion>USA</countryorregion>
        <capital>Washington</capital>
    </entry>
    <entry>
        <countryorregion>France</countryorregion>
        <capital>Paris</capital>
    </entry>
    ...
</CountriesOrRegionsWithCapitals>
```

Pour plus d’informations sur les collections de dictionnaires, consultez la section « règles de collection avancées » plus loin dans cette rubrique.

## <a name="collections-and-known-types"></a>Collections et types connus

Vous n'avez pas besoin d'ajouter de types de collections aux types connus lorsqu'ils sont utilisés de manière polymorphe à la place d'autres collections ou interfaces de collection. Par exemple, si vous déclarez un membre de données de type <xref:System.Collections.IEnumerable> et l'utilisez pour envoyer une instance de <xref:System.Collections.ArrayList>, vous n'avez pas besoin d'ajouter <xref:System.Collections.ArrayList> aux types connus.

Lorsque vous utilisez des collections de manière polymorphe au lieu de types qui ne sont pas des collections, elles doivent être ajoutées aux types connus. Par exemple, si vous déclarez un membre de données de type `Object` et l'utilisez pour envoyer une instance de <xref:System.Collections.ArrayList>, ajoutez <xref:System.Collections.ArrayList> aux types connus.

Cela ne vous permet pas de sérialiser toute collection équivalente de manière polymorphe. Par exemple, lorsque vous ajoutez <xref:System.Collections.ArrayList> à la liste des types connus dans l'exemple précédent, cela ne vous permet pas d'assigner la classe `Array of Object` , bien qu'elle ait un contrat de données équivalent. Ce comportement n'est pas différent du comportement normal des types connus sur la sérialisation des types qui ne sont pas des collections, mais il est particulièrement important de le comprendre dans le cas des collections car celles-ci sont très souvent équivalentes.

Pendant la sérialisation, un seul type peut être connu dans toute portée donnée d'un contrat de données particulier et toutes les collections équivalentes ont les mêmes contrats de données. Cela signifie que, dans l'exemple précédent, vous ne pouvez pas ajouter à la fois <xref:System.Collections.ArrayList> et `Array of Object` aux types connus au niveau de la même portée. Encore une fois, cela est équivalent au comportement des types connus pour les types qui ne sont pas des collections, mais cela est particulièrement important à comprendre pour les collections.

Les types connus peuvent également être requis pour le contenu des collections. Par exemple, si un <xref:System.Collections.ArrayList> contient réellement des instances de `Type1` et `Type2`, ces deux types doivent être ajoutés aux types connus.

L'exemple ci-dessous montre un graphique d'objet construit correctement à l'aide de collections et des types connus. Cet exemple est quelque peu inventé car, dans une application réelle, vous ne définiriez normalement pas les membres de données suivants comme `Object`et, par conséquent, vous ne rencontreriez aucun problème de polymorphisme ou de type connu.

[!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
[!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]

Lors de la désérialisation, si le type déclaré est un type de collection, le type déclaré est instancié indépendamment du type qui a été réellement envoyé. Si le type déclaré est une interface de collection, le désérialiseur choisit un type à instancier sans se soucier des types connus.

De plus, lors de la désérialisation, si le type déclaré n'est pas un type de collection mais un type de collection est envoyé, un type de collection correspondant est choisi dans la liste des types connus. Il est possible d'ajouter des types d'interfaces de collection à la liste des types connus lors de la désérialisation. Dans ce cas, le moteur de désérialisation choisit de nouveau un type à instancier.

## <a name="collections-and-the-netdatacontractserializer-class"></a>Collections et classe NetDataContractSerializer

Lorsque la classe <xref:System.Runtime.Serialization.NetDataContractSerializer> est utilisée, les types de collections non personnalisés (sans l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> ) qui ne sont pas des tableaux perdent leur signification spéciale.

Les types de collections non personnalisés marqués avec l'attribut <xref:System.SerializableAttribute> peuvent encore être sérialisés par la classe <xref:System.Runtime.Serialization.NetDataContractSerializer> en fonction de l'attribut <xref:System.SerializableAttribute> ou des règles d'interface <xref:System.Runtime.Serialization.ISerializable> .

Les types de collections personnalisés, les interfaces de collection et les tableaux sont encore traités comme des collections, même lorsque la classe <xref:System.Runtime.Serialization.NetDataContractSerializer> est utilisée.

## <a name="collections-and-schema"></a>Collections et schéma

Toutes les collections équivalentes ont la même représentation dans le schéma XSD (XML Schema Definition). C'est pourquoi vous n'obtiendrez normalement pas le même type de collection dans le code client généré que sur le serveur. Par exemple, le serveur peut utiliser un contrat de données avec un membre de données <xref:System.Collections.Generic.List%601> générique d'éléments Integer, alors que, dans le code client généré, le même membre de données peut devenir un tableau d'entiers.

Les collections dictionnaire sont marquées avec une annotation de schéma spécifique à WCF qui indique qu’il s’agit de dictionnaires ; dans le cas contraire, ils ne peuvent pas être différenciés des listes simples qui contiennent des entrées avec une clé et une valeur. Pour une description exacte de la façon dont les collections sont représentées dans le schéma de contrat de données, consultez [Data Contract Schema Reference](data-contract-schema-reference.md).

Par défaut, les types ne sont pas générés pour les collections non personnalisées dans le code importé. Les membres de données des types de collections liste sont importés en tant que tableaux, alors que les membres de données des types de collections dictionnaire sont importés en tant que dictionnaire générique.

Toutefois, pour les collections personnalisées, des types distincts sont générés, marqués avec l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> . (Un type de collection personnalisé dans le schéma est un type qui n’utilise pas l’espace de noms, le nom, le nom d’élément répétitif ou les noms d’éléments clé/valeur par défaut.) Ces types sont des types vides qui dérivent de generic <xref:System.Collections.Generic.List%601> pour les types de liste et le dictionnaire générique pour les types de dictionnaire.

Par exemple, vous pouvez avoir les types ci-dessous sur le serveur.

[!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
[!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]

Lorsque le schéma est exporté puis importé de nouveau, le code client généré est semblable à ce qui suit (les propriétés sont remplacées par des champs pour une meilleure lisibilité).

[!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
[!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]

Vous pouvez utiliser des types différents dans le code généré à la place des types par défaut. Par exemple, vous pouvez utiliser le <xref:System.ComponentModel.BindingList%601> générique à la place de tableaux normaux pour vos membres de données pour pouvoir les lier plus facilement aux composants d'interface utilisateur.

Pour choisir des types de collections à générer, passez une liste de types de collections que vous souhaitez utiliser dans la propriété <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> de l'objet <xref:System.Runtime.Serialization.ImportOptions> lors de l'importation du schéma. Ces types sont appelés *types de collections référencés*.

Lorsque des types génériques sont référencés, il doit s'agir de génériques complètement ouverts ou complètement fermés.

> [!NOTE]
> Lorsque vous utilisez l’outil Svcutil.exe, cette référence peut être réalisée à l’aide du commutateur de ligne de commande **/collectionType** (forme abrégée : **/ct**). N’oubliez pas que vous devez également spécifier l’assembly pour les types de collections référencés à l’aide du commutateur **/reference** (forme abrégée : **/r**). Si le type est générique, il doit être suivi par une apostrophe inverse et le nombre de paramètres génériques. Le guillemet () ne doit \` pas être confondu avec le caractère guillemet simple ('). Vous pouvez spécifier plusieurs types de collections référencés en utilisant plusieurs fois le commutateur **/collectionType** .

Par exemple, pour provoquer l'importation de toutes les listes en tant que <xref:System.Collections.Generic.List%601>générique.

```console
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1
```

Lors de l'importation d'une collection quelconque, cette liste de types de collections référencés est analysée et la collection qui correspond le mieux est utilisée, le cas échéant, soit comme type de membre de données (pour les collections non personnalisées), soit comme type de base à partir duquel dériver (pour les collections personnalisées). Les dictionnaires sont comparés uniquement à des dictionnaires, tandis que les listes sont comparées à des listes.

Par exemple, si vous ajoutez le <xref:System.ComponentModel.BindingList%601> générique et <xref:System.Collections.Hashtable> à la liste des types référencés, le code client généré pour l'exemple précédent sera semblable au code ci-dessous.

[!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
[!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]

Vous pouvez spécifier des types d'interfaces de collection dans le cadre de vos types de collections référencés, mais vous ne pouvez pas spécifier de types de collections non valides (tels que des types sans méthode `Add` ou sans constructeur public).

Un générique fermé est considéré comme la solution la mieux adaptée. (Les types non génériques sont considérés équivalents aux génériques fermés d' `Object`.) Par exemple, si les types <xref:System.Collections.Generic.List%601> générique de <xref:System.DateTime>, <xref:System.ComponentModel.BindingList%601> générique (générique ouvert) et <xref:System.Collections.ArrayList> sont les types de collections référencés, le code ci-dessous est généré.

[!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
[!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]

Pour les collections liste, seuls les cas indiqués dans le tableau suivant sont pris en charge.

|Type référencé|Interface implémentée par le type référencé|Exemple|Type traité comme :|
|---------------------|----------------------------------------------|-------------|----------------------|
|Non générique ou générique fermé (nombre de paramètres quelconque)|Non générique|`MyType : IList`<br /><br /> or<br /><br /> `MyType<T> : IList`<br /><br /> où T= `int`|Générique fermé d' `Object` (par exemple, `IList<object>`)|
|Non générique ou générique fermé (nombre quelconque de paramètres qui ne correspondent pas nécessairement au type de collection)|Générique fermé|`MyType : IList<string>`<br /><br /> or<br /><br /> `MyType<T> : IList<string>` où T=`int`|Générique fermé (par exemple, `IList<string>`)|
|Générique fermé avec un nombre quelconque de paramètres|Générique ouvert utilisant un des paramètres du type|`MyType<T,U,V> : IList<U>`<br /><br /> où T=`int`, U=`string`, V=`bool`|Générique fermé (par exemple, `IList<string>`)|
|Générique ouvert avec un paramètre|Générique ouvert utilisant le paramètre du type|`MyType<T> : IList<T>`, T est ouvert|Générique ouvert (par exemple, `IList<T>`)|

Si un type implémente plusieurs interfaces de collection liste, les restrictions suivantes s'appliquent :

- Si le type implémente le <xref:System.Collections.Generic.IEnumerable%601> générique (ou ses interfaces dérivées) plusieurs fois pour des types différents, le type n'est pas considéré comme un type de collection référencé valide et il est ignoré. Cela est vrai même si certaines implémentations ne sont pas valides ou utilisent des génériques ouverts. Par exemple, un type qui implémente le <xref:System.Collections.Generic.IEnumerable%601> générique d' `int` et le <xref:System.Collections.Generic.IEnumerable%601> générique de T ne serait jamais utilisé comme collection référencée d' `int` ou tout autre type, que le type ait ou non une méthode `Add` qui accepte `int` ou une méthode `Add` qui accepte un paramètre de type T, ou les deux.

- Si le type implémente une interface de collection générique ainsi que <xref:System.Collections.IList>, le type ne sera jamais utilisé comme type de collection référencé à moins que l'interface de collection générique ne soit un générique fermé de type <xref:System.Object>.

Pour les collections dictionnaire, seuls les cas indiqués dans le tableau suivant sont pris en charge.

|Type référencé|Interface implémentée par le type référencé|Exemple|Type traité comme|
|---------------------|----------------------------------------------|-------------|---------------------|
|Non générique ou générique fermé (nombre de paramètres quelconque)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> or<br /><br /> `MyType<T> : IDictionary` où T=`int`|Générique fermé `IDictionary<object,object>`|
|Générique fermé (nombre quelconque de paramètres)|<xref:System.Collections.Generic.IDictionary%602>, fermé|`MyType<T> : IDictionary<string, bool>` où T=`int`|Générique fermé (par exemple, `IDIctionary<string,bool>`)|
|Générique fermé (nombre quelconque de paramètres)|<xref:System.Collections.Generic.IDictionary%602>générique, la clé ou la valeur est fermée, l'autre est ouverte et utilise un des paramètres du type|`MyType<T,U,V> : IDictionary<string,V>` où T=`int`, U=`float`, V=`bool`<br /><br /> or<br /><br /> `MyType<Z> : IDictionary<Z,bool>` où Z=`string`|Générique fermé (par exemple, `IDictionary<string,bool>`)|
|Générique fermé (nombre quelconque de paramètres)|<xref:System.Collections.Generic.IDictionary%602>générique, la clé et la valeur sont ouvertes et chacune d'elles utilise un des paramètres du type|`MyType<T,U,V> : IDictionary<V,U>` où T=`int`, U=`bool`, V=`string`|Générique fermé (par exemple, `IDictionary<string,bool>`)|
|Générique ouvert (deux paramètres)|<xref:System.Collections.Generic.IDictionary%602>générique, ouvert, utilise les deux paramètres génériques du type dans l'ordre où ils apparaissent|`MyType<K,V> : IDictionary<K,V>`, K et V sont ouverts tous les deux|Générique ouvert (par exemple, `IDictionary<K,V>`)|

Si le type implémente <xref:System.Collections.IDictionary> et le <xref:System.Collections.Generic.IDictionary%602>générique, seul le <xref:System.Collections.Generic.IDictionary%602> générique est pris en compte.

Le référencement de types génériques partiels n'est pas pris en charge.

Les doublons ne sont pas autorisés. Par exemple, vous ne pouvez pas ajouter à la fois la <xref:System.Collections.Generic.List%601> générique d'éléments `Integer` et la collection générique d'éléments `Integer` à <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, car cela empêche de déterminer laquelle utiliser si une liste d'entiers est détectée dans le schéma. Les doublons sont détectés uniquement si un type présent dans le schéma expose le problème des doublons. Par exemple, si le schéma en cours d'importation ne contient pas de listes d'entiers, il est autorisé d'avoir à la fois la <xref:System.Collections.Generic.List%601> générique d'éléments `Integer` et la collection générique d'éléments `Integer` dans <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, mais aucune d'elles n'a un quelconque effet.

## <a name="advanced-collection-rules"></a>Règles de collection avancées

### <a name="serializing-collections"></a>Sérialisation de collections

La liste suivante répertorie les règles de collection pour la sérialisation :

- L'association de types de collections (avoir des collections de collections) est autorisée. Les tableaux en escalier sont traités comme des collections de collections. Les tableaux multidimensionnels ne sont pas pris en charge.

- Les tableaux d'octets et les tableaux de <xref:System.Xml.XmlNode> sont des types de tableau spéciaux qui sont traités comme des primitifs, pas comme des collections. La sérialisation d'un tableau d'octets génère un élément XML unique qui contient un segment de données encodées en Base64, au lieu d'un élément distinct pour chaque octet. Pour plus d’informations sur la façon dont un tableau de <xref:System.Xml.XmlNode> est traité, consultez [types XML et ADO.net dans les contrats de données](xml-and-ado-net-types-in-data-contracts.md). Naturellement, ces types spéciaux peuvent eux-mêmes participer aux collections : un tableau de tableaux d'octets génère plusieurs éléments XML contenant chacun un segment de données encodées en Base64.

- Si l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> est appliqué à un type de collection, le type est traité comme un type de contrat de données standard, pas comme une collection.

- Si un type de collection implémente l'interface <xref:System.Xml.Serialization.IXmlSerializable> , les restrictions suivantes s'appliquent, s'il s'agit d'un type `myType:IList<string>, IXmlSerializable`:

  - Si le type déclaré est `IList<string>`, le type est sérialisé en tant que liste.

  - Si le type déclaré est `myType`, il est sérialisé en tant que `IXmlSerializable`.

  - Si le type déclaré est `IXmlSerializable`, il est sérialisé en tant que `IXmlSerializable`, mais uniquement si vous ajoutez `myType` à la liste des types connus.

- Les collections sont sérialisées et désérialisées à l'aide des méthodes indiquées dans le tableau ci-dessous.

|Le type de collection implémente|Méthodes appelées lors de la sérialisation|Méthodes appelées lors de la désérialisation|
|--------------------------------|-----------------------------------------|-------------------------------------------|
|Generic <ph id="ph1">&lt;xref:System.Collections.Generic.IDictionary%602&gt;</ph>|`get_Keys`, `get_Values`|Generic Add|
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|
|Generic <ph id="ph1">&lt;xref:System.Collections.Generic.IList%601&gt;</ph>|Indexeur <xref:System.Collections.Generic.IList%601> générique|Generic Add|
|Generic <ph id="ph1">&lt;xref:System.Collections.Generic.ICollection%601&gt;</ph>|Énumérateur|Generic Add|
|<xref:System.Collections.IList>|Indexeur<xref:System.Collections.IList>|`Add`|
|Generic <ph id="ph1">&lt;xref:System.Collections.Generic.IEnumerable%601&gt;</ph>|`GetEnumerator`|Méthode non statique nommée `Add` qui accepte un paramètre du type approprié (le type du paramètre générique ou un de ses types de base). Une telle méthode doit exister pour que le sérialiseur traite un type de collection comme une collection lors de la sérialisation et de la désérialisation.|
|<xref:System.Collections.IEnumerable> (et donc <xref:System.Collections.ICollection>, qui en dérive)|`GetEnumerator`|Méthode non statique nommée `Add` qui accepte un paramètre de type `Object`. Une telle méthode doit exister pour que le sérialiseur traite un type de collection comme une collection lors de la sérialisation et de la désérialisation.|

Le tableau précédent répertorie les interfaces de collection dans l'ordre de priorité décroissant. Cela signifie, par exemple, que si un type implémente à la fois <xref:System.Collections.IList> et <xref:System.Collections.Generic.IEnumerable%601>générique, la collection est sérialisée et désérialisée en fonction des règles <xref:System.Collections.IList> :

- Lors de la désérialisation, toutes les collections sont désérialisées en créant d’abord une instance du type en appelant le constructeur sans paramètre, qui doit être présent pour que le sérialiseur traite un type de collection comme une collection lors de la sérialisation et de la désérialisation.

- Si la même interface de collection générique est implémentée plusieurs fois (par exemple, si un type implémente à la fois le <xref:System.Collections.Generic.ICollection%601> générique d'éléments `Integer` et le <xref:System.Collections.Generic.ICollection%601> générique d'éléments <xref:System.String>) et qu'aucune interface de priorité supérieure n'est trouvée, la collection n'est pas traitée comme une collection valide.

- L'attribut <xref:System.SerializableAttribute> peut être appliqué aux types de collections et ces derniers peuvent implémenter l'interface <xref:System.Runtime.Serialization.ISerializable> . Ces deux éléments sont ignorés. Toutefois, si le type ne satisfait pas pleinement les spécifications de type de collection (par exemple, si la méthode `Add` est manquante), le type n'est pas considéré comme un type de collection, et par conséquent l'attribut <xref:System.SerializableAttribute> et l'interface <xref:System.Runtime.Serialization.ISerializable> sont utilisés pour déterminer si le type peut être sérialisé.

- L'application de l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> à une collection pour la personnaliser supprime le mécanisme de secours <xref:System.SerializableAttribute> mentionné précédemment. À la place, si une collection personnalisée ne satisfait pas les spécifications de type de collection, une exception <xref:System.Runtime.Serialization.InvalidDataContractException> est levée. La chaîne d’exception contient souvent des informations qui expliquent pourquoi un type donné n’est pas considéré comme une collection valide (aucune `Add` méthode, aucun constructeur sans paramètre, etc.). il est donc souvent utile d’appliquer l' <xref:System.Runtime.Serialization.CollectionDataContractAttribute> attribut à des fins de débogage.

### <a name="collection-naming"></a>Attribution des noms de collections

La liste suivante répertorie les règles d'attribution des noms des collections :

- L’espace de noms par défaut pour tous les contrats de données de collection de dictionnaires, ainsi que pour les contrats de données de collection de listes qui contiennent des types primitifs, est, `http://schemas.microsoft.com/2003/10/Serialization/Arrays` sauf s’il est substitué à l’aide de l’espace Les types qui correspondent aux types XSD intégrés, ainsi que les types `char`, `Timespan`et `Guid` , sont considérés comme des primitifs à cette fin.

- L'espace de noms par défaut des types de collections contenant des types non primitifs, à moins qu'il soit remplacé à l'aide de Namespace, est le même que celui des noms de contrat de données du type inclus dans la collection.

- Le nom par défaut pour les contrats de données de collection de liste, à moins qu'il ne soit remplacé à l'aide de Name, est la chaîne "ArrayOf" associée au nom du contrat de données du type inclus dans la collection. Par exemple, le nom du contrat de données pour une liste générique d'éléments Integer est "ArrayOfint". N'oubliez pas que le nom de contrat de données d' `Object` est "anyType", afin que le nom de contrat de données de listes non génériques comme <xref:System.Collections.ArrayList> soit "ArrayOfanyType".

Le nom par défaut pour les contrats de données de collection dictionnaire, à moins qu'il soit remplacé à l'aide de `Name`, est la chaîne "ArrayOfKeyValueOf" associée au nom du contrat de données du type de clé suivie par le nom du contrat de données du type de valeur. Par exemple, le nom du contrat de données pour un dictionnaire générique d'éléments String et Integer est "ArrayOfKeyValueOfstringint". En outre, si les types de clé ou de valeur ne sont pas des types primitifs, un hachage d'espace de noms des espaces de noms de contrat de données des types de clé et de valeur est ajouté au nom. Pour plus d’informations sur les hachages d’espaces de noms, consultez [noms de contrat de données](data-contract-names.md).

Chaque contrat de données de collection dictionnaire possède un contrat de données auxiliaire qui représente une entrée dans le dictionnaire. Son nom est le même que pour le contrat de données de dictionnaire, à l'exception du préfixe "ArrayOf", et son espace de noms est le même que pour le contrat de données de dictionnaire. Par exemple, pour le contrat de données de dictionnaire "ArrayOfKeyValueOfstringint", le contrat de données "KeyValueofstringint" représente une entrée dans le dictionnaire. Vous pouvez personnaliser le nom de ce contrat de données en utilisant la propriété `ItemName` tel que cela est décrit dans la section suivante.

Les règles d’attribution de noms de type générique, comme décrit dans [Data Contract Names](data-contract-names.md), s’appliquent pleinement aux types de collections ; en d’autres termes, vous pouvez utiliser des accolades dans Name pour indiquer des paramètres de type générique. Toutefois, notez que les nombres indiqués entre les accolades font référence aux paramètres génériques et non aux types inclus dans la collection.

## <a name="collection-customization"></a>Personnalisation des collections

Les utilisations suivantes de l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> sont interdites et entraînent une exception <xref:System.Runtime.Serialization.InvalidDataContractException> :

- Application de l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à un type auquel l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> a été appliqué, ou à l'un de ses types dérivés.

- Application de l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> à un type qui implémente l'interface <xref:System.Xml.Serialization.IXmlSerializable> .

- Application de l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> à un type qui n'est pas une collection.

- Tentative de définir <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> ou <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> sur un attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> appliqué à un type qui n'est pas un dictionnaire.

### <a name="polymorphism-rules"></a>Règles de polymorphisme

Comme cela a été mentionné précédemment, la personnalisation de collections à l'aide de l'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> peut interférer avec l'interchangeabilité des collections. Deux types de collections personnalisés peuvent être considérés équivalents uniquement si leurs noms, leurs espaces de noms, leurs noms d'élément, ainsi que leurs noms de clé et de valeur (si ce sont des collections dictionnaire) correspondent.

En raison des personnalisations, il est possible d'utiliser par inadvertance un contrat de données de collection lorsqu'un autre contrat est attendu. Cela doit être évité. Consultez les types suivants.

[!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
[!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]

Dans ce cas, une instance de `Marks1` peut être assignée à `testMarks`. Toutefois, `Marks2` ne doit pas être utilisé car son contrat de données n'est pas considéré équivalent au contrat de données `IList<int>` . Le nom du contrat de données est « marks2 » et non « ArrayOfint », et le nom de l’élément répétitif est « \<mark> » et non «» \<int> .

Les règles indiquées dans le tableau ci-dessous s'appliquent à l'assignation polymorphe de collections.

|Type déclaré|Assignation d'une collection non personnalisée|Assignation d'une collection personnalisée|
|-------------------|--------------------------------------------|---------------------------------------|
|Object|Le nom de contrat est sérialisé.|Le nom de contrat est sérialisé.<br /><br /> La personnalisation est utilisée.|
|Interface de collection|Le nom de contrat n'est pas sérialisé.|Le nom de contrat n'est pas sérialisé.<br /><br /> La personnalisation n’est pas utilisée.\*|
|Collection non personnalisée|Le nom de contrat n'est pas sérialisé.|Le nom de contrat est sérialisé.<br /><br /> La personnalisation est utilisée.**|
|Collection personnalisée|Le nom de contrat est sérialisé. La personnalisation n’est pas utilisée.\*\*|Le nom de contrat est sérialisé.<br /><br /> La personnalisation du type assigné est utilisée.\*\*|

\*Avec la <xref:System.Runtime.Serialization.NetDataContractSerializer> classe, la personnalisation est utilisée dans ce cas. La classe <xref:System.Runtime.Serialization.NetDataContractSerializer> sérialise également le nom de type réel dans ce cas, si bien que la désérialisation fonctionne comme prévu.

\*\*Ces cas entraînent des instances de schéma non valides et doivent donc être évitées.

Dans les cas où le nom de contrat est sérialisé, le type de collection assigné doit figurer dans la liste des types connus. Le contraire est également vrai : dans les cas où le nom n'est pas sérialisé, l'ajout du type dans la liste des types connus n'est pas nécessaire.

Un tableau d'un type dérivé peut être assigné à un tableau d'un type de base. Dans ce cas, le nom de contrat pour le type dérivé est sérialisé pour chaque élément répétitif. Par exemple, si un type `Book` dérive du type `LibraryItem`, vous pouvez assigner un tableau d'éléments `Book` à un tableau d'éléments `LibraryItem`. Cela ne s'applique pas aux autres types de collections. Par exemple, vous ne pouvez pas assigner une `Generic List of Book` à une `Generic List of LibraryItem`. Toutefois, vous pouvez assigner une `Generic List of LibraryItem` qui contient des instances `Book` . Dans les deux cas avec tableau et sans tableau, `Book` doit figurer dans la liste des types connus.

## <a name="collections-and-object-reference-preservation"></a>Collections et conservation des références aux objets

Lorsqu'un sérialiseur fonctionne dans un mode où il conserve les références aux objets, la conservation des références aux objets s'applique également aux collections. Spécifiquement, l'identité des objets est conservée à la fois pour les collections entières et pour les éléments individuels inclus dans les collections. Pour les dictionnaires, l'identité des objets est conservée à la fois pour les objets paire clé/valeur et pour les objets clé et valeur individuels.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
