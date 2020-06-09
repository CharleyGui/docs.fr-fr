---
title: Types XML et ADO.NET dans les contrats de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 975d4f4f37bbbd895cab4e87686f15017e90f382
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600073"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Types XML et ADO.NET dans les contrats de données
Le modèle de contrat de données Windows Communication Foundation (WCF) prend en charge certains types qui représentent directement du code XML. Lorsque ces types sont sérialisés en XML, le sérialiseur écrit le contenu XML de ces types sans traitement supplémentaire. Les types pris en charge sont <xref:System.Xml.XmlElement>, les tableaux de <xref:System.Xml.XmlNode> (mais pas le type `XmlNode` lui-même), ainsi que les types qui implémentent <xref:System.Xml.Serialization.IXmlSerializable>. Le type <xref:System.Data.DataSet> et <xref:System.Data.DataTable>, ainsi que les groupes de données typés, sont utilisés couramment dans la programmation de base de données. Ces types implémentent l'interface `IXmlSerializable` et sont par conséquent sérialisables dans le modèle de contrat de données. Des considérations particulières pour ces types sont répertoriées à la fin de cette rubrique.  
  
## <a name="xml-types"></a>Types XML  
  
### <a name="xml-element"></a>Élément xml  
 Le type `XmlElement` est sérialisé à l'aide de son contenu XML. Par exemple, utilisez le type ci-dessous.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 Ce type est sérialisé en XML comme suit :  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Notez qu'un élément du membre de données du wrapper `<myDataMember>` est encore présent. Il est impossible de supprimer cet élément dans le modèle de contrat de données. Les sérialiseurs qui gèrent ce modèle (<xref:System.Runtime.Serialization.DataContractSerializer> et <xref:System.Runtime.Serialization.NetDataContractSerializer>) peuvent émettre des attributs spéciaux dans cet élément wrapper. Ces attributs incluent l'attribut « nil » de l'instance de schéma Xml standard (qui permet à `XmlElement` d'être `null`) et l'attribut « type" (qui permet une utilisation polymorphe de `XmlElement`). En outre, les attributs XML suivants sont spécifiques à WCF : « ID », « ref », « type » et « assembly ». Ces attributs peuvent être émis pour prendre en charge l'utilisation de `XmlElement` avec le mode de conservation des graphiques d'objet activé ou avec <xref:System.Runtime.Serialization.NetDataContractSerializer>. (Pour plus d’informations sur le mode de conservation des graphiques d’objets, consultez [sérialisation et désérialisation](serialization-and-deserialization.md).)  
  
 Les tableaux ou les collections de `XmlElement` sont autorisés et gérés comme les autres tableaux ou collections. Autrement dit, il y a un élément wrapper pour la collection entière, et un élément wrapper séparé (semblable à `<myDataMember>` dans l’exemple précédent) pour chaque `XmlElement` du tableau.  
  
 Au moment de la désérialisation, un `XmlElement` est créé par le désérialiseur à partir du XML entrant. Un parent valide <xref:System.Xml.XmlDocument> est fourni par le désérialiseur.  
  
 Veillez à ce que le fragment XML qui est désérialisé en `XmlElement` définit tous les préfixes qu'il utilise et ne repose pas sur des définitions de préfixe d'éléments ancêtres. Ce problème se pose uniquement au cours de l'utilisation du `DataContractSerializer` pour accéder au XML d'une source différente (qui n'est pas `DataContractSerializer`).  
  
 En cas d’utilisation avec `DataContractSerializer` , le `XmlElement` peut se voir assigner manière polymorphe, mais uniquement à un membre de données de type <xref:System.Object> . Même s’il implémente <xref:System.Collections.IEnumerable>, un `XmlElement` ne peut pas être utilisé comme un type de collection et ne peut pas être assigné à un membre de données <xref:System.Collections.IEnumerable>. Comme avec toutes les assignations polymorphes, le `DataContractSerializer` émet le nom de contrat de données dans le XML résultant. dans ce cas, il s’agit de « XmlElement » dans l' http://schemas.datacontract.org/2004/07/System.Xml espace de noms «».  
  
 Avec le `NetDataContractSerializer`, toute assignation polymorphe valide de `XmlElement` (à `Object` ou `IEnumerable`) est prise en charge.  
  
 N'essayez pas d'utiliser l'un ou l'autre sérialiseur avec des types dérivés de `XmlElement`, qu'il soit assigné de manière polymorphe ou non.  
  
### <a name="array-of-xmlnode"></a>Tableau de XmlNode  
 L'utilisation de tableaux de <xref:System.Xml.XmlNode> est très semblable à l'utilisation de `XmlElement`. Utiliser les tableaux de `XmlNode` offre plus de souplesse que `XmlElement`. Vous pouvez écrire plusieurs éléments à l'intérieur de l'élément d'habillage du membre de données. Vous pouvez injecter également un autre contenu que des éléments dans l'élément d'habillage du membre de données, tel que des commentaires XML. Enfin, vous pouvez injecter des attributs dans l'élément d'habillage du membre de données. Toutes ces opérations sont possibles en remplissant le tableau de `XmlNode` avec les classes dérivées spécifiques de `XmlNode` telles que <xref:System.Xml.XmlAttribute>, `XmlElement` ou <xref:System.Xml.XmlComment>. Par exemple, utilisez le type ci-dessous.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 En cas de sérialisation, le XML résultant est semblable au code suivant.  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
  <myDataMember myAttribute="myValue">  
     <!--myComment-->  
     <myElement xmlns="" myAttribute="myValue">  
 myContents  
     </myElement>  
     <myElement xmlns="" myAttribute="myValue">  
       myContents  
     </myElement>  
  </myDataMember>  
</MyDataContract>  
```  
  
 Notez que l'élément wrapper du membre de données `<myDataMember>` contient un attribut, un commentaire et deux éléments. Ce sont les quatre instances `XmlNode` ayant été sérialisées.  
  
 Un tableau de `XmlNode` qui produit un XML non valide ne peut pas être sérialisé. Par exemple, un tableau de deux instances `XmlNode` où la première est un `XmlElement` et la deuxième est un <xref:System.Xml.XmlAttribute> n'est pas valide, parce que cette séquence ne correspond pas à une instance XML valide (pas d'espace pour y joindre l'attribut).  
  
 Au moment de la désérialisation d'un tableau de `XmlNode`, les nœuds sont créés et remplis avec les informations XML entrantes. Un parent valide <xref:System.Xml.XmlDocument> est fourni par le désérialiseur. Tous les nœuds sont désérialisés, y compris tous les attributs de l’élément de données de wrappers de wrapper, mais à l’exclusion des attributs qui y sont placés par les sérialiseurs WCF (tels que les attributs utilisés pour indiquer une assignation polymorphe). La restriction liée à la définition de tous les préfixes d’espace de noms dans le fragment XML s’applique à la désérialisation des tableaux de `XmlNode` au même titre que la désérialisation de `XmlElement`.  
  
 Lorsque vous utilisez des sérialiseurs avec la conservation des graphiques d'objet activée, l'égalité d'objet est conservée uniquement au niveau des tableaux `XmlNode`, pas des instances `XmlNode` individuelles.  
  
 N'essayez pas de sérialiser un tableau de `XmlNode` qui contient un ou plusieurs nœuds de valeur `null`. Les membres du tableau entier sont autorisés à être `null`, mais pas pour les `XmlNode` individuels contenus dans le tableau. Si le membre du tableau entier est null, l'élément du membre de données du wrapper contient un attribut spécial qui indique qu'il est null. Au moment de la désérialisation, le membre du tableau entier prend aussi la valeur null.  
  
 Seuls les tableaux réguliers de `XmlNode` font l'objet d'un traitement particulier par le sérialiseur. Les membres de données déclarés comme d'autres types de collection qui contiennent `XmlNode`, ou les membres de données déclarés comme tableaux de types dérivés de `XmlNode`, ne font pas l'objet d'un traitement particulier. Par conséquent, elles ne sont pas normalement sérialisables sauf si elles correspondent aussi à l'un des autres critères pour la sérialisation.  
  
 Les tableaux ou collections de tableaux de `XmlNode` sont autorisés. Il existe un élément wrapper pour la collection entière, et un élément wrapper séparé (semblable à `<myDataMember>` dans l’exemple précédent) pour chaque tableau du `XmlNode` de la collection ou du tableau externe.  
  
 Le remplissage d'un membre de données de type <xref:System.Array> de `Object` ou `Array` de `IEnumerable` avec les instances `XmlNode` n'entraîne pas le traitement du membre de données en tant que `Array` des instances `XmlNode`. Chaque membre de tableau est sérialisé séparément.  
  
 Lorsqu'ils sont utilisés avec `DataContractSerializer`, les tableaux `XmlNode` peuvent être assignés d'une manière polymorphe mais uniquement à un membre de données de type `Object`. Même s'il implémente `IEnumerable`, un tableau de `XmlNode` ne peut pas être utilisé comme un type de collection et ne peut pas être assigné à un membre de données `IEnumerable`. Comme avec toutes les assignations polymorphes, le `DataContractSerializer` émet le nom de contrat de données dans le XML résultant. dans ce cas, il s’agit de « ArrayOfXmlNode » dans l' http://schemas.datacontract.org/2004/07/System.Xml espace de noms «». En cas d’utilisation avec `NetDataContractSerializer` , toute attribution valide d’un `XmlNode` tableau est prise en charge.  
  
### <a name="schema-considerations"></a>Considérations sur le schéma  
 Pour plus d’informations sur le mappage de schéma des types XML, consultez [Référence du schéma de contrat de données](data-contract-schema-reference.md). Cette section fournit un résumé des points importants.  
  
 Un membre de données de type `XmlElement` est mappé à un élément défini à l'aide du type anonyme suivant.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Un membre de données de type Array de `XmlNode` est mappé à un élément défini à l'aide du type anonyme suivant.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>Types qui implémentent l'interface IXmlSerializable  
 Les types qui implémentent l'interface `IXmlSerializable` sont pleinement pris en charge par le `DataContractSerializer`. L'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> doit toujours être appliqué à ces types pour contrôler leur schéma.  
  
 Trois variétés de types implémentent `IXmlSerializable` : les types représentant le contenu arbitraire, les types représentant un élément unique et les types <xref:System.Data.DataSet> hérités.  
  
- Les types de contenu utilisent une méthode du fournisseur de schéma spécifiée par l'attribut `XmlSchemaProviderAttribute`. La méthode ne retourne pas `null`, et la propriété <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> sur l'attribut conserve sa valeur par défaut `false`. Il s'agit de l'utilisation la plus courante des types `IXmlSerializable`.  
  
- Les types d'élément sont utilisés lorsqu'un type `IXmlSerializable` doit contrôler son propre nom d'élément racine. Pour marquer un type comme un type élément, affectez à la propriété <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> sur l'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> la valeur `true` ou retournez null à partir de la méthode du fournisseur de schéma. L'utilisation d'une méthode du fournisseur de schéma est facultative pour les types élément. Vous pouvez spécifier null au lieu du nom de méthode dans `XmlSchemaProviderAttribute`. Toutefois, si `IsAny` a la valeur `true` et qu'une méthode du fournisseur de schéma est spécifiée, la méthode doit retourner null.  
  
- Les types <xref:System.Data.DataSet> hérités sont des types `IXmlSerializable` qui ne sont pas marqués avec l'attribut `XmlSchemaProviderAttribute`. À la place, ils comptent sur la méthode <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> pour la génération de schéma. Ce modèle est utilisé pour le type `DataSet` et son groupe de données typés dérive une classe dans les versions antérieures du .NET Framework, mais il est désormais obsolète et pris en charge uniquement pour des raisons d'héritage. Ne vous fiez pas à ce modèle et appliquez toujours `XmlSchemaProviderAttribute` à vos types `IXmlSerializable`.  
  
### <a name="ixmlserializable-content-types"></a>Types de contenu IXmlSerializable  
 Lors de la sérialisation d'un membre de données d'un type qui implémente `IXmlSerializable` et qui est un type de contenu défini précédemment, le sérialiseur écrit l'élément wrapper pour le membre de données et transmet le contrôle à la méthode <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>. L'implémentation <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> peut écrire n'importe quel code XML, y compris ajouter des attributs à l'élément wrapper. Au terme de l'écriture de `WriteXml`, le sérialiseur ferme l'élément.  
  
 Lors de la désérialisation d'un membre de données d'un type qui implémente `IXmlSerializable` et qui est un type de contenu défini précédemment, le désérialiseur positionne le lecteur XML sur l'élément wrapper du membre de données et transmet le contrôle à la méthode <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>. La méthode doit lire l'élément en entier, y compris les balises de début et de fin. Assurez-vous que votre code `ReadXml` gère le cas où l'élément est vide. En outre, votre implémentation `ReadXml` ne doit pas dépendre d'un nom particulier qui affecterait l'élément wrapper. Le nom est choisi par le sérialiseur et peut varier.  
  
 Il est possible d'assigner de manière polymorphe des types de contenu `IXmlSerializable` par exemple aux membres de données de type <xref:System.Object>. Les instances de types peuvent aussi être Null. Enfin, il est possible d'utiliser des types `IXmlSerializable` avec la conservation des graphiques d'objet activée et avec <xref:System.Runtime.Serialization.NetDataContractSerializer>. Toutes ces fonctionnalités nécessitent que le sérialiseur WCF joigne certains attributs dans l’élément wrapper (« Nil » et « type » dans l’espace de noms de l’instance du schéma XML et « ID », « ref », « type » et « assembly » dans un espace de noms spécifique à WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Attributs à ignorer lors de l'implémentation de ReadXml  
 Avant de passer le contrôle à votre code `ReadXml`, le désérialiseur examine l'élément XML, détecte les attributs XML spéciaux et effectue des actions sur ceux-ci. Par exemple, si « nil » est `true`, une valeur Null sera désérialisée et `ReadXml` n'est pas appelée. Si le polymorphisme est détecté, le contenu de l'élément est désérialisé comme s'il s'agissait d'un type différent. L'implémentation de `ReadXml` du type assigné de manière polymorphe est appelée. Dans tous les cas, une implémentation `ReadXml` doit ignorer les attributs spéciaux puisqu'ils sont contrôlés par le désérialiseur.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Considérations sur le schéma pour les types de contenu IXmlSerializable  
 Lors de l'exportation du schéma d'un type de contenu `IXmlSerializable`, la méthode du fournisseur de schéma est appelée. Un <xref:System.Xml.Schema.XmlSchemaSet> est passé à la méthode du fournisseur de schéma. La méthode peut ajouter un schéma valide au jeu de schémas. Le jeu de schémas contient le schéma déjà connu au moment où se produit l'exportation de schéma. Lorsque la méthode du fournisseur de schéma doit ajouter un élément au jeu de schémas, elle doit déterminer si un <xref:System.Xml.Schema.XmlSchema> avec l'espace de noms approprié existe déjà dans le jeu. Si tel est le cas, la méthode du fournisseur de schéma doit ajouter le nouvel élément au `XmlSchema` existant. Sinon, il doit créer une nouvelle instance `XmlSchema`. Cette opération est importante si les tableaux de types `IXmlSerializable` sont utilisés. Par exemple, si vous avez un type `IXmlSerializable` exporté comme type « A » dans l'espace de noms « B », il est possible qu'au moment où la méthode du fournisseur de schéma est appelée, le jeu de schémas contienne déjà le schéma pour que « B » contienne le type « ArrayOfA ».  
  
 En plus d'ajouter des types à <xref:System.Xml.Schema.XmlSchemaSet>, la méthode du fournisseur de schéma pour les types de contenu doit retourner une valeur non NULL. Elle peut retourner un <xref:System.Xml.XmlQualifiedName> qui spécifie le nom du type de schéma à utiliser pour le type `IXmlSerializable` donné. Ce nom qualifié sert également comme nom et espace de noms de contrat de données pour le type. Il est possible de retourner un type qui n'existe pas immédiatement dans le jeu de schémas lorsque la méthode du fournisseur de schéma est retournée. Toutefois, au moment de l'exportation de tous les types connexes (la méthode <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> est appelée pour tous les types pertinents sur <xref:System.Runtime.Serialization.XsdDataContractExporter> et la propriété <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> est accessible), le type est dans le jeu de schémas. Accéder à la propriété `Schemas` avant d'effectuer tous les appels `Export` pertinents peut provoquer une <xref:System.Xml.Schema.XmlSchemaException>. Pour plus d’informations sur le processus d’exportation, consultez [exportation de schémas à partir de classes](exporting-schemas-from-classes.md).  
  
 La méthode du fournisseur de schéma peut aussi retourner le <xref:System.Xml.Schema.XmlSchemaType> à utiliser. Le type peut ou ne peut pas être anonyme. S'il est anonyme, le schéma du type `IXmlSerializable` est exporté sous la forme d'un type anonyme à chaque fois que le type `IXmlSerializable` est utilisé comme un membre de données. Le type `IXmlSerializable` a encore un nom et un espace de noms de contrat de données. (Cela est déterminé comme décrit dans [noms des contrats de données](data-contract-names.md) , sauf que l' <xref:System.Runtime.Serialization.DataContractAttribute> attribut ne peut pas être utilisé pour personnaliser le nom.) S’il n’est pas anonyme, il doit s’agir de l’un des types dans le `XmlSchemaSet` . Ce cas revient à retourner le `XmlQualifiedName` du type.  
  
 En outre, une déclaration d'élément globale est exportée pour le type. Si l'attribut <xref:System.Xml.Serialization.XmlRootAttribute> n'est pas appliqué au type, l'élément a le même nom et espace de noms comme contrat de données, et sa propriété « nillable » a la valeur true. La seule exception est l’espace de noms de schéma (" http://www.w3.org/2001/XMLSchema ") : si le contrat de données du type se trouve dans cet espace de noms, l’élément global correspondant se trouve dans l’espace de noms vide, car il est interdit d’ajouter de nouveaux éléments à l’espace de noms du schéma. Si l'attribut `XmlRootAttribute` s'applique au type, la déclaration d'élément globale est exportée à l'aide des propriétés suivantes : <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> et <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A>. Les valeurs par défaut appliquées avec `XmlRootAttribute` sont le nom de contrat de données, un espace de noms vide et « nillable » ayant pour valeur true.  
  
 Les mêmes règles de déclaration d'élément globale s'appliquent aux types de groupes de données hérités. Notez que `XmlRootAttribute` ne peut pas substituer de déclarations d'élément globales ajoutées par l'intermédiaire du code personnalisé, ajoutées soit à `XmlSchemaSet` à l'aide de la méthode du fournisseur de schéma, soit à l'aide de `GetSchema` pour les types de groupes de données hérités.  
  
### <a name="ixmlserializable-element-types"></a>Types d'élément IXmlSerializable  
 La propriété `IXmlSerializable` des types d'élément `IsAny` a la valeur `true` ou leur méthode du fournisseur de schéma retourne `null`.  
  
 La sérialisation et la désérialisation d'un type d'élément est très semblable à la sérialisation et la désérialisation d'un type de contenu. Toutefois, il y a des différences importantes :  
  
- L'implémentation `WriteXml` est censée écrire exactement un élément (qui peut contenir évidemment plusieurs éléments enfants). Elle ne doit pas écrire d'attributs en dehors de cet élément unique, plusieurs éléments frères ou de contenu mixte. L'élément peut être vide.  
  
- L'implémentation `ReadXml` ne doit pas lire l'élément wrapper. Elle est censée lire l'élément unique produit par `WriteXml`.  
  
- Lors de la sérialisation régulière d'un type d'élément (par exemple, comme membre de données dans un contrat de données), le sérialiseur produit un élément wrapper avant d'appeler `WriteXml`, comme avec les types de contenu. Cependant, lors de la sérialisation d'un type d'élément au niveau supérieur, le sérialiseur ne produit pas normalement un élément wrapper autour de l'élément écrit par `WriteXml`, sauf si un nom racine et l'espace de noms ont été spécifiés explicitement lors de l'élaboration du sérialiseur dans les constructeurs `DataContractSerializer` ou `NetDataContractSerializer`. Pour plus d’informations, consultez [sérialisation et désérialisation](serialization-and-deserialization.md).  
  
- Si vous sérialisez un type d'élément au niveau supérieur sans spécifier le nom racine et l'espace de noms au moment de la construction, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> et <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> n'effectuent essentiellement aucune tâche et <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> appelle `WriteXml`. Dans ce mode, l'objet qui est sérialisé ne peut pas être null et ne peut pas être assigné d'une manière polymorphe. La conservation des graphiques d'objet ne peut pas non plus être activée et le `NetDataContractSerializer` ne peut pas être utilisé.  
  
- Si vous désérialisez un type d'élément au niveau supérieur sans spécifier le nom racine et l'espace de noms au moment de la construction, <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> retourne `true` s'il trouve le début d'un élément. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>, avec le paramètre `verifyObjectName` ayant la valeur `true`, se comporte de la même façon que `IsStartObject` avant de lire l'objet. `ReadObject` passe ensuite le contrôle à la méthode `ReadXml`.  
  
 Le schéma exporté pour les types d'élément est le même que pour le type `XmlElement` décrit dans une section antérieure, sauf que la méthode du fournisseur de schéma peut ajouter tout schéma supplémentaire au <xref:System.Xml.Schema.XmlSchemaSet> comme avec les types de contenu. L'utilisation de l'attribut `XmlRootAttribute` avec les types d'élément n'est pas autorisé, et les déclarations d'élément globales ne sont jamais émises pour ces types.  
  
### <a name="differences-from-the-xmlserializer"></a>Différences par rapport au XmlSerializer  
 L'interface `IXmlSerializable` et les attributs `XmlSchemaProviderAttribute` et `XmlRootAttribute` sont également compris par le <xref:System.Xml.Serialization.XmlSerializer>. Cependant, il existe des différences dans la manière dont ils sont traités dans le modèle de contrat de données. Ces différences importantes sont répertoriées comme suit :  
  
- La méthode du fournisseur de schéma doit être publique pour être utilisable dans le `XmlSerializer`, mais ne doit pas être nécessairement publique pour être utilisable dans le modèle de contrat de données.  
  
- La méthode du fournisseur de schéma est appelée lorsque `IsAny` est true dans le modèle de contrat de données mais pas avec le `XmlSerializer`.  
  
- Lorsque l'attribut `XmlRootAttribute` n'est pas présent pour les types de contenu ou de groupes de données hérités, le `XmlSerializer` exporte une déclaration d'élément globale dans l'espace de noms vide. Dans le modèle de contrat de données, l'espace de noms utilisé est normalement l'espace de noms de contrat de données décrit précédemment.  
  
 Gardez ces différences à l'esprit lors de la création des types qui sont utilisés avec les deux technologies de sérialisation.  
  
### <a name="importing-ixmlserializable-schema"></a>Importation du schéma IXmlSerializable  
 Lorsque vous importez un schéma généré à partir des types `IXmlSerializable`, plusieurs possibilités sont offertes :  
  
- Le schéma généré peut être un schéma de contrat de données valide, comme décrit dans [référence de schéma de contrat de données](data-contract-schema-reference.md). Dans ce cas, le schéma peut être importé comme d'habitude et les types de contrat de données normaux sont générés.  
  
- Le schéma généré peut ne pas être un schéma de contrat de données valide. Par exemple, votre méthode du fournisseur de schéma peut générer un schéma qui implique des attributs XML pris en charge dans le modèle de contrat de données. Dans ce cas, vous pouvez importer le schéma comme des types `IXmlSerializable`. Ce mode d’importation n’est pas activé par défaut, mais peut être facilement activé, par exemple avec le `/importXmlTypes` commutateur de ligne de commande de l' [outil ServiceModel Metadata Utility (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Cela est décrit en détail dans le [schéma d’importation pour générer des classes](importing-schema-to-generate-classes.md). Notez que vous devez utiliser directement le XML pour vos instances de type. Vous pouvez envisager d'utiliser également une technologie de sérialisation différente qui prend en charge une plage de schéma plus large. Consultez la rubrique sur l'utilisation du `XmlSerializer`.  
  
- Vous pouvez réutiliser vos types `IXmlSerializable` existants dans le proxy au lieu d'en générer de nouveaux. Dans ce cas, la fonctionnalité des types référencés décrite dans la rubrique « Importation du schéma pour générer des types » peut être utilisée pour indiquer le type à réutiliser. Cela revient à utiliser le commutateur `/reference` sur svcutil.exe qui spécifie l'assembly qui contient les types à réutiliser.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Représentation du XML arbitraire dans les contrats de données  
 Le `XmlElement`, le tableau de `XmlNode` et les types `IXmlSerializable` vous permettent d'injecter du code XML arbitraire dans le modèle de contrat de données. Les `DataContractSerializer` et `NetDataContractSerializer` transmettent ce contenu XML au writer XML utilisé, sans intervenir dans le processus. Toutefois, les writers XML peuvent appliquer certaines restrictions dans le code XML qu'ils écrivent. En voici quelques exemples importants :  
  
- Les enregistreurs XML n’autorisent généralement pas une déclaration de document XML (par exemple, \<?xml version=’1.0’ ?> ) au milieu de l’écriture d’un autre document. Vous ne pouvez pas prendre un document XML complet et le sérialiser comme un `Array` d'un membre de données `XmlNode`. Pour cela, vous devez supprimer la déclaration de document ou utiliser votre propre méthode d'encodage pour la représenter.  
  
- Tous les enregistreurs XML fournis avec WCF rejettent les instructions de traitement XML ( \<? … ?> ) et les définitions de type de document ( \<! … > ), car ils ne sont pas autorisés dans les messages SOAP. Là encore, vous pouvez utiliser votre propre mécanisme d'encodage pour contourner cette restriction. Si vous devez inclure celles-ci dans votre code XML résultant, vous pouvez écrire un encodeur personnalisé qui fait appel à des writers XML pour les prendre en charge.  
  
- Lors de l'implémentation de `WriteXml`, évitez d'appeler la méthode <xref:System.Xml.XmlWriter.WriteRaw%2A> sur l'enregistreur XML. WCF utilise un large éventail d’encodages XML (y compris binaire), il est très difficile, voire impossible, d’utiliser de `WriteRaw` telle sorte que le résultat soit utilisable dans n’importe quel encodage.  
  
- Lors de l’implémentation de `WriteXml` , évitez d’utiliser les <xref:System.Xml.XmlWriter.WriteEntityRef%2A> <xref:System.Xml.XmlWriter.WriteNmToken%2A> méthodes et qui ne sont pas prises en charge sur les Writers XML fournis avec WCF.  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Utilisation de DataSet, Typed DataSet et DataTable  
 L'utilisation de ces types est prise en charge pleinement dans le modèle de contrat de données. Lorsque vous utilisez ces types, considérez les points suivants :  
  
- Le schéma de ces types (en particulier <xref:System.Data.DataSet> et ses classes dérivées typées) ne peut pas être interopérable avec certaines plateformes non-WCF, ou peut entraîner une mauvaise utilisation avec ces plateformes. En outre, l'utilisation du type `DataSet` peut avoir un impact sur les performances. Enfin, il peut compliquer la gestion de la version de votre application dans le futur. Utilisez des types de contrat de données définis explicitement plutôt que des types `DataSet` dans vos contrats.  
  
- Lorsque vous importez le schéma `DataSet` ou `DataTable`, il est important de référencer ces types. Avec l’outil en ligne de commande Svcutil. exe, vous pouvez le faire en passant le nom de l’assembly System. Data. dll au `/reference` commutateur. Si vous importez un schéma de groupe de données typé, vous devez référencer le type du groupe de données typé. Avec Svcutil. exe, passez l’emplacement de l’assembly du DataSet typé au `/reference` commutateur. Pour plus d’informations sur le référencement des types, consultez [importation du schéma pour générer des classes](importing-schema-to-generate-classes.md).  
  
 La prise en charge des groupes de données typés dans le modèle de contrat de données est limitée. Les groupes de données typés peuvent être sérialisés et désérialisés et exportés à partir de leur schéma. Cependant, l'importation du schéma de contrat de données ne peut pas générer de nouveaux types DataSet typés depuis le schéma, elle ne peut que réutiliser les types existants. Vous pouvez pointer vers un DataSet typé existant à l'aide du commutateur `/r` sur Svcutil.exe. Si vous tentez d'utiliser Svcutil.exe sans le commutateur `/r` sur un service qui utilise un groupe de données typé, un autre sérialiseur est automatiquement (XmlSerializer) sélectionné. Si vous devez utiliser DataContractSerializer et générer des DataSets à partir du schéma, procédez comme suit : générez les types DataSet typés (à l'aide de l'outil Xsd.exe et du commutateur `/d` sur le service), compilez les types, et pointez vers eux à l'aide du commutateur `/r` sur Svcutil.exe.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [Using Data Contracts](using-data-contracts.md)
- [Types pris en charge par le sérialiseur de contrat de données](types-supported-by-the-data-contract-serializer.md)
