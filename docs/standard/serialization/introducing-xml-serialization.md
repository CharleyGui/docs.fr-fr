---
title: Détails de la sérialisation XML
description: La sérialisation convertit un objet en un format qui peut être transporté. Cet article fournit une vue d’ensemble de la sérialisation XML et de la classe XmlSerializer.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, about XML serialization
- ICollection interface, serializing
- XmlSerializer class, serializing
- serialization, about serialization
- DataSet class, serializing
- XML Schema, serializing
ms.assetid: 8c63200d-db63-4a03-a93d-21641623df62
ms.openlocfilehash: 2971f5bbd587dabb62d095da3fef0b428ea9f039
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282282"
---
# <a name="xml-serialization"></a>sérialisation XML

La sérialisation correspond au processus de conversion d'un objet en un formulaire facilement transportable. Par exemple, vous pouvez sérialiser un objet et le transporter par Internet via HTTP entre un client et un serveur. À l'autre extrémité, la désérialisation reconstruit l'objet du flux de données.

 La sérialisation XML sérialise uniquement les champs publics et les valeurs de propriété d'un objet dans un flux de données XML. La sérialisation XML n'inclut pas d'informations de type. Par exemple, si un objet **Book** se trouve dans l’espace de noms **Library** , il n’y a aucune garantie qu’il soit désérialisé dans un objet du même type.

> [!NOTE]
> La sérialisation XML ne convertit pas les méthodes, les indexeurs, les champs privés ni les propriétés en lecture seule (à l'exception des collections en lecture seule). Pour sérialiser la totalité des champs et des propriétés d'un objet, publics et privés, utilisez <xref:System.Runtime.Serialization.DataContractSerializer> au lieu de la sérialisation XML.

 La classe centrale de la sérialisation XML est la classe <xref:System.Xml.Serialization.XmlSerializer>, et les méthodes les plus importantes de cette classe sont les méthodes **Serialize** et **Deserialize**. <xref:System.Xml.Serialization.XmlSerializer> crée des fichiers C# et les compile dans des fichiers .dll pour exécuter cette sérialisation. Le [XML Serializer Generator Tool (Sgen.exe)](xml-serializer-generator-tool-sgen-exe.md) est conçu pour générer ces assemblys de sérialisation à l’avance pour qu’ils soient déployés avec votre application et pour améliorer les performances de démarrage. Le flux de données XML généré par **XmlSerializer** est conforme à la [recommandation du langage XSD (XML Schema definition language)](https://www.w3.org/TR/xslt)World Wide Web Consortium (W3C) 1,0. En outre, les types de données générés sont conformes au document intitulé « XML Schema Part 2: Datatypes ».

 Les données de vos objets sont décrites à l’aide des constructions du langage de programmation, telles que les classes, les champs, les propriétés, les types primitifs, les tableaux et même du code XML incorporé sous forme d’objets **XmlElement** ou **XmlAttribute**. Vous pouvez créer vos propres classes, annotées avec des attributs ou utiliser l'outil XML Schema Definition pour générer des classes à partir d'un schéma XML existant.

 Si vous disposez d'un schéma XML, vous pouvez exécuter l'outil XML Schema Definition pour générer un ensemble de classes fortement typées sur le schéma et annotées avec des attributs. Lorsqu'une instance d'une telle classe est sérialisée, le code XML généré respecte le schéma XML. Lorsque vous disposez d'une telle classe, vous pouvez programmer à l'aide d'un modèle d'objet manipulé facilement tout en garantissant que le code XML généré se conforme au schéma XML. Il s’agit d’une alternative à l’utilisation d’autres classes dans .NET, telles que les classes **XmlReader** et **XmlWriter** , pour analyser et écrire un flux de données XML. Pour plus d’informations, consultez [Documents et données XML](../data/xml/index.md). Ces classes vous permettent d'analyser tout flux de données XML. À l’inverse, utilisez **XmlSerializer** si le flux de données XML est supposé se conformer à un schéma XML connu.

 Les attributs contrôlent le flux de données XML généré par la classe **XmlSerializer** , en vous permettant de définir l’espace de noms XML, le nom d’élément, le nom de l’attribut, etc. du flux de données XML. Pour plus d’informations sur ces attributs et sur la manière dont ils contrôlent la sérialisation XML, consultez [Contrôle de la sérialisation XML à l’aide d’attributs](controlling-xml-serialization-using-attributes.md). Pour obtenir une liste des attributs utilisés pour contrôler le code XML généré, consultez [Attributs qui contrôlent la sérialisation XML](attributes-that-control-xml-serialization.md).

 De plus, la classe **XmlSerializer** peut sérialiser un objet et générer un flux de données XML encodé selon le protocole SOAP. Le XML généré est conforme à la section 5 du document World Wide Web Consortium intitulé « Protocole SOAP (Simple Object Access Protocol) 1.1 ». Pour plus d’informations sur ce processus, consultez [Guide pratique pour sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Pour obtenir une liste des attributs utilisés pour contrôler le code XML généré, consultez [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md).

 La classe **XmlSerializer** génère les messages SOAP créés par les services web XML et passés à ces derniers. Pour contrôler les messages SOAP, vous pouvez appliquer des attributs aux classes, valeurs de retour, paramètres et champs trouvés dans un fichier de services Web XML (.asmx). Vous pouvez utiliser les attributs répertoriés dans « Attributs qui contrôlent la sérialisation XML » et « Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP » car un service Web XML peut utiliser le style SOAP littéral ou encodé. Pour plus d’informations sur l’utilisation d’attributs pour contrôler le code XML généré par un service web XML, consultez [Sérialisation XML avec les services web XML](xml-serialization-with-xml-web-services.md). Pour plus d’informations sur les services Web SOAP et XML, consultez Personnalisation de la [mise en forme des messages SOAP](/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)).

## <a name="security-considerations-for-xmlserializer-applications"></a>Considérations relatives à la sécurité des applications XmlSerializer

Lorsque vous créez une application qui utilise le **XmlSerializer** , tenez compte des éléments suivants et de leurs implications :

- **XmlSerializer** crée des fichiers C# (.cs) et les compile dans des fichiers .dll dans le répertoire nommé par la variable d’environnement TEMP. La sérialisation s’effectue ensuite avec ces DLL.

  > [!NOTE]
  > Ces assemblys de sérialisation peuvent être générés en avance et signés à l'aide de l'outil SGen.exe. Cela ne fonctionne pas avec un serveur de services Web. En d'autres termes, ces assemblys sont réservés à une utilisation par le client et à une sérialisation manuelle.

  Le code et les dll sont vulnérables face à un processus malveillant lors de leur création et de leur compilation. Lors de l'utilisation d'un ordinateur qui exécute Microsoft Windows NT 4.0 ou version ultérieure, deux utilisateurs ou plus peuvent partager le répertoire TEMP. Le partage d’un répertoire TEMP est dangereux si les deux comptes ont des privilèges de sécurité différents et que le compte doté des privilèges les plus élevés exécute une application utilisant **XmlSerializer**. Dans ce cas, un utilisateur peut percer la sécurité de l'ordinateur en remplaçant le fichier .cs ou .dll compilé. Pour éliminer ce problème, vérifiez toujours que chaque compte de l'ordinateur dispose de son propre profil. Par défaut, la variable d'environnement TEMP pointe vers un répertoire différent pour chaque compte.

- Si un utilisateur malveillant envoie un flux de données XML continu à un serveur web (attaque par déni de service), **XmlSerializer** continue de traiter les données jusqu’à ce que l’ordinateur manque de ressources.

  Ce type d'attaque est éliminé si vous utilisez un ordinateur qui exécute des Services Internet (IIS) et que votre application s'exécute dans IIS. IIS comprend une porte qui ne traite pas les flux de données supérieurs à une quantité définie (la valeur par défaut correspond à 4 Ko). Si vous créez une application qui n’utilise pas IIS et qui désérialise les données à l’aide de **XmlSerializer** , vous devez implémenter une porte semblable pour empêcher une attaque par déni de service.

- **XmlSerializer** sérialise les données et exécute tout type de code.

  Un objet malveillant présente une menace dans deux situations. Il peut exécuter du code malveillant ou injecter du code malveillant dans le fichier C# créé par **XmlSerializer**. Dans le premier cas, si un objet malveillant essaie d'exécuter une procédure destructrice, la sécurité d'accès du code empêche tout préjudice éventuel. Dans le deuxième cas, il est possible, en théorie, qu’un objet malveillant puisse injecter d’une façon ou d’une autre du code dans le fichier C# créé par **XmlSerializer**. Bien que ce problème ait été étudié de manière approfondie et qu'une telle attaque soit considérée comme improbable, veillez à ne jamais sérialiser de données de type inconnu et non fiable.

- Les données sensibles sérialisées peuvent être vulnérables.

  Une fois que le **XmlSerializer** a sérialisé des données, il peut être stocké sous la forme d’un fichier XML ou d’un autre magasin de données. Si d'autres processus peuvent accéder à votre magasin de données, ou que celui-ci est visible sur un intranet ou sur Internet, les données peuvent être volées et utilisées de manière malveillante. Par exemple, si vous créez une application qui sérialise des commandes qui incluent des numéros de carte de crédit, les données sont très sensibles. Pour empêcher cela, protégez toujours votre magasin de données et prenez les mesures nécessaires pour assurer sa confidentialité.

## <a name="serialization-of-a-simple-class"></a>Sérialisation d'une classe simple

L'exemple de code suivant affiche une classe de base avec un champ public.

```vb
Public Class OrderForm
    Public OrderDate As DateTime
End Class
```

```csharp
public class OrderForm
{
    public DateTime OrderDate;
}
```

Lorsqu'une instance de cette classe est sérialisée, elle peut se présenter comme suit.

```xml
<OrderForm>
    <OrderDate>12/12/01</OrderDate>
</OrderForm>
```

Pour obtenir plus d’exemples de sérialisation, consultez [Exemples de sérialisation XML](examples-of-xml-serialization.md).

## <a name="items-that-can-be-serialized"></a>Éléments qui peuvent être sérialisés

Les éléments suivants peuvent être sérialisés à l’aide de la classe **XmlSerializer** :

- Propriétés publiques de lecture/écriture et champs de classes publiques.

- Classes qui implémentent **ICollection** ou **IEnumerable**.

  > [!NOTE]
  > Seules les collections sont sérialisées, pas les propriétés publiques.

- Objets **XmlElement**.

- Objets **XmlNode**.

- Objets **DataSet**.

 Pour plus d’informations sur la sérialisation et la désérialisation d’objets, consultez [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md) et [Guide pratique pour désérialiser un objet](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>Avantages de l'utilisation de la sérialisation XML

La classe **XmlSerializer** vous donne un contrôle complet et flexible lorsque vous sérialisez un objet au format XML. Si vous créez un service Web XML, vous pouvez appliquer des attributs qui contrôlent la sérialisation des classes et des membres pour garantir que le résultat XML se conforme à un schéma spécifique.

Par exemple, **XmlSerializer** vous permet d’effectuer les opérations suivantes :

- Spécifier si un champ ou une propriété doit être encodé comme un attribut ou un élément.

- Spécifier un espace de noms XML à utiliser.

- Spécifier le nom d'un élément ou d'un attribut si le nom d'un champ ou d'une propriété n'est pas approprié.

Un autre avantage de la sérialisation XML est qu'aucune contrainte n'est définie sur les applications que vous développez, tant que le flux de données XML généré se conforme à un schéma donné. Imaginez un schéma utilisé pour décrire des livres. Il comprend un titre, un auteur, un éditeur et un élément de numéro ISBN. Vous pouvez développer une application qui traite les données XML de la manière dont vous le souhaitez, par exemple, comme une commande ou un inventaire de livres. Dans les deux cas, la seule spécification consiste en ce que le flux de données XML se conforme au schéma XSD spécifié.

## <a name="xml-serialization-considerations"></a>Considérations sur la sérialisation XML

Si vous utilisez la classe **XmlSerializer** , tenez compte des points suivants :

- L'outil Sgen.exe est conçu expressément pour générer des assemblys de sérialisation en vue d'obtenir des performances optimales.

- Les données sérialisées ne contiennent que les données elles-mêmes et la structure de vos classes. Les informations relatives à l'identité et aux assemblys ne sont pas incluses.

- Seuls les champs et les propriétés publics peuvent être sérialisés. Les propriétés doivent disposer d'accesseurs publics (méthodes get et set). Si vous devez sérialiser des données non publiques, utilisez la classe <xref:System.Runtime.Serialization.DataContractSerializer> plutôt que la sérialisation XML.

- Une classe doit avoir un constructeur sans paramètre pour être sérialisé par **XmlSerializer**.

- Les méthodes ne peuvent pas être sérialisées.

- **XmlSerializer** peut traiter des classes qui implémentent différemment **IEnumerable** ou **ICollection** si elles répondent aux exigences ci-après.

  Une classe qui implémente **IEnumerable** doit implémenter une méthode **Add** publique qui accepte un seul paramètre. Le paramètre de la méthode **Add** doit être cohérent (polymorphe) avec le type retourné par la propriété **IEnumerator.Current** qui est retournée par la méthode **GetEnumerator**.

  Une classe qui implémente **ICollection** en plus de **IEnumerable** (comme **CollectionBase** ) doit avoir une propriété **Item** publique indexée (un indexeur dans C#) qui accepte un entier et avoir une propriété **Count** publique de type **integer**. Le paramètre passé à la méthode **Add** doit être du même type que celui retourné par la propriété **Item** ou correspondre à l’une des bases de ce type.

  Dans le cas de classes qui implémentent **ICollection** , les valeurs à sérialiser sont récupérées à partir de la propriété **Item** indexée et non en appelant **GetEnumerator**. Par ailleurs, les propriétés et les champs publics ne sont pas sérialisés, à l’exception des champs publics qui retournent une autre classe de collection (une classe qui implémente **ICollection** ). Pour obtenir un exemple, consultez [Exemples de sérialisation XML](examples-of-xml-serialization.md).

## <a name="xsd-data-type-mapping"></a>Mappage de type de données XSD

Le document W3C intitulé [XML Schema Part 2 : Datatypes](https://www.w3.org/TR/xmlschema-2/) spécifie les types de données simples qui sont autorisés dans un schéma en langage XSD (XML Schema Definition). Pour la plupart d’entre eux (par exemple, **int** et **Decimal** ), il existe un type de données correspondant dans .net. Toutefois, certains types de données XML n’ont pas de type de données .NET correspondant, par exemple, le type de données **NMTOKEN** . Dans de tels cas, si vous utilisez l’ [outil XML Schema Definition (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md) pour créer des classes à partir d’un schéma, un attribut approprié est appliqué à un membre de type String et sa propriété **DataType** a pour valeur le nom du type de données XML. Par exemple, si un schéma contient un élément nommé « MyToken » et ayant le type de données XML **NMTOKEN** , la nouvelle classe peut contenir un membre tel qu’illustré dans l’exemple suivant.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

De la même façon, si vous créez une classe qui doit se conformer à un schéma XML spécifique (XSD), vous devez appliquer l’attribut approprié et assigner à sa propriété **DataType** le nom de type de données XML souhaité.

Pour obtenir une liste complète des mappages de types, consultez la propriété **DataType** pour chacune des classes d’attributs suivantes :

- <xref:System.Xml.Serialization.SoapAttributeAttribute>

- <xref:System.Xml.Serialization.SoapElementAttribute>

- <xref:System.Xml.Serialization.XmlArrayItemAttribute>

- <xref:System.Xml.Serialization.XmlAttributeAttribute>

- <xref:System.Xml.Serialization.XmlElementAttribute>

- <xref:System.Xml.Serialization.XmlRootAttribute>

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.IO.FileStream>
- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
- [Sérialisation binaire](binary-serialization.md)
- [Sérialisation](index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Exemples de sérialisation XML](examples-of-xml-serialization.md)
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)
- [Comment : désérialiser un objet](how-to-deserialize-an-object.md)
