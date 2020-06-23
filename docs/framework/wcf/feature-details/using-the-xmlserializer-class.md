---
title: Utilisation de la classe XmlSerializer
description: Découvrez le XmlSerializer, que WCF utilise pour sérialiser les données de votre application en XML transmis entre les clients et les services.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: f7473de3f34ba543b4fabfe93167ea267f16dda5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246378"
---
# <a name="using-the-xmlserializer-class"></a>Utilisation de la classe XmlSerializer

Windows Communication Foundation (WCF) peut utiliser deux technologies de sérialisation différentes pour transformer les données de votre application en XML transmises entre les clients et les services, un processus appelé sérialisation.

## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer comme classe par défaut

Par défaut, WCF utilise la <xref:System.Runtime.Serialization.DataContractSerializer> classe pour sérialiser les types de données. Ce sérialiseur prend en charge les types suivants :

- Types primitifs (par exemple, entiers, chaînes et tableaux d'octets), ainsi que quelques types spéciaux, tels que <xref:System.Xml.XmlElement> et <xref:System.DateTime>, traités comme des types primitifs.

- Types de contrat de données (types marqués avec l'attribut <xref:System.Runtime.Serialization.DataContractAttribute>).

- Types marqués avec l'attribut <xref:System.SerializableAttribute>, qui comprennent les types implémentant l'interface <xref:System.Runtime.Serialization.ISerializable>.

- Types qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable>.

- Nombreux types de collections courants, notamment de nombreux types de collections génériques.

De nombreux types de .NET Framework appartiennent aux deux dernières catégories et sont donc sérialisables. Les tableaux de types sérialisables sont également sérialisables. Pour obtenir une liste complète, consultez [spécification de transfert de données dans les contrats de service](specifying-data-transfer-in-service-contracts.md).

<xref:System.Runtime.Serialization.DataContractSerializer>, Utilisé avec les types de contrat de données, est la méthode recommandée pour écrire de nouveaux services WCF. Pour plus d’informations, consultez [utilisation de contrats de données](using-data-contracts.md).

## <a name="when-to-use-the-xmlserializer-class"></a>Quand utiliser la classe XmlSerializer ?

WCF prend également en charge la <xref:System.Xml.Serialization.XmlSerializer> classe. La <xref:System.Xml.Serialization.XmlSerializer> classe n’est pas propre à WCF. Il s’agit du même moteur de sérialisation que celui utilisé par les services Web ASP.NET. La classe <xref:System.Xml.Serialization.XmlSerializer> prend en charge un ensemble de types beaucoup plus restreint que la classe <xref:System.Runtime.Serialization.DataContractSerializer>, mais elle permet un meilleur contrôle sur le code XML résultant et prend en charge une plus grande partie de la norme XSD (XML Schema Definition). En outre, elle ne requiert aucun attribut déclaratif sur les types sérialisables. Pour plus d’informations, consultez la rubrique relative à la sérialisation XML dans la documentation de .NET Framework. La classe <xref:System.Xml.Serialization.XmlSerializer> ne prend pas en charge les types de contrats de données.

Lorsque vous utilisez Svcutil.exe ou la fonctionnalité **Ajouter une référence de service** dans Visual Studio pour générer le code client pour un service tiers, ou pour accéder à un schéma tiers, un sérialiseur approprié est automatiquement sélectionné pour vous. Si le schéma est incompatible avec le <xref:System.Runtime.Serialization.DataContractSerializer>, le <xref:System.Xml.Serialization.XmlSerializer> est sélectionné.

## <a name="manually-switching-to-the-xmlserializer"></a>Basculement manuel vers le XmlSerializer

Il peut arriver parfois que vous deviez basculer manuellement vers le <xref:System.Xml.Serialization.XmlSerializer>. Cela peut arriver, par exemple, dans les cas suivants :

- Lors de la migration d’une application à partir de services Web ASP.NET vers WCF, vous souhaiterez peut-être réutiliser <xref:System.Xml.Serialization.XmlSerializer> les types existants compatibles existants au lieu de créer de nouveaux types de contrat de données.

- Lorsqu'il est important de contrôler de manière précise le code XML qui apparaît dans les messages, mais qu'aucun document WSDL (Web Services Description Language) n'est disponible, par exemple lors de la création d'un service avec des types qui doivent se conformer à un certain schéma publié standardisé qui n'est pas compatible avec le DataContractSerializer.

- Lors de la création de services qui respectent la norme d'encodage SOAP héritée.

Dans les cas évoqués mais aussi dans d'autres cas, vous pouvez basculer manuellement vers la classe <xref:System.Xml.Serialization.XmlSerializer> en appliquant l'attribut `XmlSerializerFormatAttribute` à votre service, comme illustré dans le code suivant.

[!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
[!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]

## <a name="security-considerations"></a>Considérations relatives à la sécurité

> [!NOTE]
> Il est important d'être prudent lorsque vous basculez d'un moteur de sérialisation à un autre. Le même type peut sérialiser en XML différemment selon le sérialiseur utilisé. Si vous utilisez par inadvertance le mauvais sérialiseur, vous risquez de divulguer des informations sur le type que vous ne souhaitiez pas divulguer.

Par exemple, la classe <xref:System.Runtime.Serialization.DataContractSerializer> sérialise uniquement les membres marqués avec l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> lors de la sérialisation de types de contrats de données. La classe <xref:System.Xml.Serialization.XmlSerializer> sérialise tout membre public. Examinez le type dans le code suivant.

[!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
[!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]

Si le type est utilisé par inadvertance dans un contrat de service où la classe <xref:System.Xml.Serialization.XmlSerializer> est sélectionnée, le membre `creditCardNumber` est sérialisé, ce qui n'est sans doute pas voulu.

Bien que la classe <xref:System.Runtime.Serialization.DataContractSerializer> soit la classe par défaut, vous pouvez la sélectionner explicitement pour votre service (bien que cela ne doive jamais être requis) en appliquant l'attribut <xref:System.ServiceModel.DataContractFormatAttribute> au type de contrat de service.

Le sérialiseur utilisé pour le service est une partie intégrante du contrat et ne peut pas être changé en sélectionnant une liaison différente ou en modifiant d'autres paramètres de configuration.

D'autres considérations importantes relatives à la sécurité s'appliquent à la classe <xref:System.Xml.Serialization.XmlSerializer>. Tout d’abord, il est fortement recommandé que toute application WCF qui utilise la <xref:System.Xml.Serialization.XmlSerializer> classe soit signée avec une clé qui est préservée de la divulgation. Cette recommandation s'applique à la fois lorsqu'un basculement manuel vers le <xref:System.Xml.Serialization.XmlSerializer> est exécuté et lorsqu'un basculement automatique est exécuté (par Svcutil.exe, la fonctionnalité Ajouter une référence de service ou un outil semblable). Cela est dû au fait que le <xref:System.Xml.Serialization.XmlSerializer> moteur de sérialisation prend en charge le chargement d' *assemblys de sérialisation prégénérés* tant qu’ils sont signés avec la même clé que l’application. Une application non signée n’est pas du tout protégée contre le risque qu’un assembly nuisible correspondant au nom attendu de l’assembly de sérialisation prégénéré soit placé dans le dossier d’application ou le cache GAC (Global Assembly Cache). Bien entendu, un intrus doit tout d'abord accéder en écriture à l'un de ces deux emplacements pour tenter cette action.

Une autre menace qui existe lorsque vous utilisez <xref:System.Xml.Serialization.XmlSerializer> concerne l'accès en écriture au dossier système temporaire. Le <xref:System.Xml.Serialization.XmlSerializer> moteur de sérialisation crée et utilise des *assemblys de sérialisation* temporaires dans ce dossier. Vous devez savoir que tout processus ayant un accès en écriture au dossier temporaire peut remplacer ces assemblys de sérialisation par du code malveillant.

## <a name="rules-for-xmlserializer-support"></a>Règles pour la prise en charge de XmlSerializer

Vous ne pouvez pas appliquer directement des attributs compatibles avec <xref:System.Xml.Serialization.XmlSerializer> à des paramètres d'opération de contrat ou des valeurs de retour. Toutefois, ils peuvent être appliqués à des messages typés (parties du corps du contrat de message), comme illustré dans le code suivant.

[!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
[!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]

En cas d'application à des membres de messages typés, ces attributs substituent les propriétés qui sont en conflit sur les attributs de messages typés. Par exemple, dans le code suivant, `ElementName` substitue `Name`.

[!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
[!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]

L'attribut <xref:System.ServiceModel.MessageHeaderArrayAttribute> n'est pas pris en charge lors de l'utilisation du <xref:System.Xml.Serialization.XmlSerializer>.

> [!NOTE]
> Dans ce cas, le <xref:System.Xml.Serialization.XmlSerializer> lève l’exception suivante, qui est publiée avant WCF : «un élément déclaré au niveau supérieur d’un schéma ne peut pas avoir `maxOccurs` > 1. Fournissez un élément wrapper pour « more » en utilisant `XmlArray` ou `XmlArrayItem` à la place de `XmlElementAttribute` ou en utilisant le style de paramètre Wrapped. ».
>
> Si vous recevez une telle exception, vérifiez si cette situation s'applique.

WCF ne prend pas en charge les <xref:System.Xml.Serialization.SoapIncludeAttribute> attributs et dans les contrats <xref:System.Xml.Serialization.XmlIncludeAttribute> de message et les contrats d’opération ; utilisez l’attribut à la <xref:System.Runtime.Serialization.KnownTypeAttribute> place.

## <a name="types-that-implement-the-ixmlserializable-interface"></a>Types qui implémentent l'interface IXmlSerializable

Les types qui implémentent l'interface `IXmlSerializable` sont pleinement pris en charge par le `DataContractSerializer`. L'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> doit toujours être appliqué à ces types pour contrôler leur schéma.

> [!WARNING]
> Si vous sérialisez des types polymorphes, vous devez appliquer le <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> au type pour vous assurer que le type correct est sérialisé.

Trois variétés de types implémentent `IXmlSerializable` : les types représentant le contenu arbitraire, les types représentant un élément unique et les types <xref:System.Data.DataSet> hérités.

- Les types de contenu utilisent une méthode du fournisseur de schéma spécifiée par l'attribut `XmlSchemaProviderAttribute`. La méthode ne retourne pas `null`, et la propriété <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> sur l'attribut conserve sa valeur par défaut `false`. Il s'agit de l'utilisation la plus courante des types `IXmlSerializable`.

- Les types d'élément sont utilisés lorsqu'un type `IXmlSerializable` doit contrôler son propre nom d'élément racine. Pour marquer un type comme type élément, affectez à la propriété <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> sur l'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> la valeur `true` ou retournez `null` à partir de la méthode du fournisseur de schéma. L'utilisation d'une méthode du fournisseur de schéma est facultative pour les types d'élément. Vous pouvez spécifier `null` au lieu du nom de méthode dans `XmlSchemaProviderAttribute`. Toutefois, si `IsAny` a la valeur `true` et qu'une méthode du fournisseur de schéma est spécifiée, la méthode doit retourner `null`.

- Les types <xref:System.Data.DataSet> hérités sont des types `IXmlSerializable` qui ne sont pas marqués avec l'attribut `XmlSchemaProviderAttribute`. À la place, ils comptent sur la méthode <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> pour la génération de schéma. Ce modèle est utilisé pour le type `DataSet` et son groupe de données typés dérive une classe dans les versions antérieures du .NET Framework, mais il est désormais obsolète et pris en charge uniquement pour des raisons d'héritage. Ne vous fiez pas à ce modèle et appliquez toujours `XmlSchemaProviderAttribute` à vos types `IXmlSerializable`.

### <a name="ixmlserializable-content-types"></a>Types de contenu IXmlSerializable

Lors de la sérialisation d'un membre de données d'un type qui implémente `IXmlSerializable` et qui est un type de contenu défini précédemment, le sérialiseur écrit l'élément wrapper pour le membre de données et transmet le contrôle à la méthode <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>. L'implémentation <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> peut écrire n'importe quel code XML, y compris ajouter des attributs à l'élément wrapper. Au terme de l'écriture de `WriteXml`, le sérialiseur ferme l'élément.

Lors de la désérialisation d'un membre de données d'un type qui implémente `IXmlSerializable` et qui est un type de contenu défini précédemment, le désérialiseur positionne le lecteur XML sur l'élément wrapper du membre de données et transmet le contrôle à la méthode <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>. La méthode doit lire l'élément en entier, y compris les balises de début et de fin. Assurez-vous que votre code `ReadXml` gère le cas où l'élément est vide. En outre, votre implémentation `ReadXml` ne doit pas dépendre d'un nom particulier qui affecterait l'élément wrapper. Le nom est choisi par le sérialiseur et peut varier.

Il est possible d'assigner de manière polymorphe des types de contenu `IXmlSerializable` par exemple aux membres de données de type <xref:System.Object>. Les instances de types peuvent aussi être Null. Enfin, il est possible d'utiliser des types `IXmlSerializable` avec la conservation des graphiques d'objet activée et avec <xref:System.Runtime.Serialization.NetDataContractSerializer>. Toutes ces fonctionnalités nécessitent que le sérialiseur WCF joigne certains attributs dans l’élément wrapper (« Nil » et « type » dans l’espace de noms de l’instance du schéma XML et « ID », « ref », « type » et « assembly » dans un espace de noms spécifique à WCF).

#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Attributs à ignorer lors de l'implémentation de ReadXml

Avant de passer le contrôle à votre code `ReadXml`, le désérialiseur examine l'élément XML, détecte les attributs XML spéciaux et effectue des actions sur ceux-ci. Par exemple, si « nil » est `true`, une valeur Null sera désérialisée et `ReadXml` n'est pas appelée. Si le polymorphisme est détecté, le contenu de l'élément est désérialisé comme s'il s'agissait d'un type différent. L'implémentation de `ReadXml` du type assigné de manière polymorphe est appelée. Dans tous les cas, une implémentation `ReadXml` doit ignorer les attributs spéciaux puisqu'ils sont contrôlés par le désérialiseur.

### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Considérations sur le schéma pour les types de contenu IXmlSerializable

Lors de l'exportation du schéma et d'un type de contenu `IXmlSerializable`, la méthode du fournisseur de schéma est appelée. Un <xref:System.Xml.Schema.XmlSchemaSet> est passé à la méthode du fournisseur de schéma. La méthode peut ajouter un schéma valide au jeu de schémas. Le jeu de schémas contient le schéma déjà connu au moment où se produit l'exportation de schéma. Lorsque la méthode du fournisseur de schéma doit ajouter un élément au jeu de schémas, elle doit déterminer si un <xref:System.Xml.Schema.XmlSchema> avec l'espace de noms approprié existe déjà dans le jeu. Si tel est le cas, la méthode du fournisseur de schéma doit ajouter le nouvel élément au `XmlSchema` existant. Sinon, il doit créer une nouvelle instance `XmlSchema`. Cette opération est importante si les tableaux de types `IXmlSerializable` sont utilisés. Par exemple, si vous avez un type `IXmlSerializable` exporté comme type « A » dans l'espace de noms « B », il est possible qu'au moment où la méthode du fournisseur de schéma est appelée, le jeu de schémas contienne déjà le schéma pour que « B » contienne le type « ArrayOfA ».

En plus d'ajouter des types à <xref:System.Xml.Schema.XmlSchemaSet>, la méthode du fournisseur de schéma pour les types de contenu doit retourner une valeur non NULL. Elle peut retourner un <xref:System.Xml.XmlQualifiedName> qui spécifie le nom du type de schéma à utiliser pour le type `IXmlSerializable` donné. Ce nom qualifié sert également comme nom et espace de noms de contrat de données pour le type. Il est possible de retourner un type qui n'existe pas immédiatement dans le jeu de schémas lorsque la méthode du fournisseur de schéma est retournée. Toutefois, au moment de l'exportation de tous les types connexes (la méthode <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> est appelée pour tous les types pertinents sur <xref:System.Runtime.Serialization.XsdDataContractExporter> et la propriété <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> est accessible), le type est dans le jeu de schémas. Accéder à la propriété `Schemas` avant d'effectuer tous les appels `Export` pertinents peut provoquer une <xref:System.Xml.Schema.XmlSchemaException>. Pour plus d’informations sur le processus d’exportation, consultez [exportation de schémas à partir de classes](exporting-schemas-from-classes.md).

La méthode du fournisseur de schéma peut aussi retourner le <xref:System.Xml.Schema.XmlSchemaType> à utiliser. Le type peut ou ne peut pas être anonyme. S'il est anonyme, le schéma du type `IXmlSerializable` est exporté sous la forme d'un type anonyme à chaque fois que le type `IXmlSerializable` est utilisé comme un membre de données. Le type `IXmlSerializable` a encore un nom et un espace de noms de contrat de données. (Cela est déterminé comme décrit dans [noms des contrats de données](data-contract-names.md) , sauf que l' <xref:System.Runtime.Serialization.DataContractAttribute> attribut ne peut pas être utilisé pour personnaliser le nom.) S’il n’est pas anonyme, il doit s’agir de l’un des types dans le `XmlSchemaSet` . Ce cas revient à retourner le `XmlQualifiedName` du type.

En outre, une déclaration d'élément globale est exportée pour le type. Si l'attribut <xref:System.Xml.Serialization.XmlRootAttribute> n'est pas appliqué au type, l'élément a le même nom et espace de noms que le contrat de données, et sa propriété « nillable » a la valeur `true`. La seule exception est l’espace de noms du schéma ( `http://www.w3.org/2001/XMLSchema` ) : si le contrat de données du type se trouve dans cet espace de noms, l’élément global correspondant se trouve dans l’espace de noms vide, car il est interdit d’ajouter de nouveaux éléments à l’espace de noms du schéma. Si l'attribut `XmlRootAttribute` s'applique au type, la déclaration d'élément globale est exportée à l'aide des propriétés suivantes : <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> et <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A>. Les valeurs par défaut appliquées avec `XmlRootAttribute` sont le nom de contrat de données, un espace de noms vide et « nillable » ayant pour valeur `true`.

Les mêmes règles de déclaration d'élément globale s'appliquent aux types de groupes de données hérités. Notez que `XmlRootAttribute` ne peut pas substituer de déclarations d'élément globales ajoutées par l'intermédiaire du code personnalisé, ajoutées soit à `XmlSchemaSet` à l'aide de la méthode du fournisseur de schéma, soit à l'aide de `GetSchema` pour les types de groupes de données hérités.

### <a name="ixmlserializable-element-types"></a>Types d'élément IXmlSerializable

La propriété `IXmlSerializable` des types d'élément `IsAny` a la valeur `true` ou leur méthode du fournisseur de schéma retourne `null`.

La sérialisation et la désérialisation d'un type d'élément est très semblable à la sérialisation et la désérialisation d'un type de contenu. Toutefois, il y a des différences importantes :

- L'implémentation `WriteXml` est censée écrire exactement un élément (qui peut contenir évidemment plusieurs éléments enfants). Elle ne doit pas écrire d'attributs en dehors de cet élément unique, plusieurs éléments frères ou de contenu mixte. L'élément peut être vide.

- L'implémentation `ReadXml` ne doit pas lire l'élément wrapper. Elle est censée lire l'élément unique produit par `WriteXml`.

- Lors de la sérialisation régulière d'un type d'élément (par exemple, comme membre de données dans un contrat de données), le sérialiseur produit un élément wrapper avant d'appeler `WriteXml`, comme avec les types de contenu. Cependant, lors de la sérialisation d'un type d'élément au niveau supérieur, le sérialiseur ne produit normalement pas un élément wrapper autour de l'élément écrit par `WriteXml`, sauf si un nom racine et l'espace de noms sont spécifiés explicitement lors de l'élaboration du sérialiseur dans les constructeurs `DataContractSerializer` ou `NetDataContractSerializer`. Pour plus d’informations, consultez [sérialisation et désérialisation](serialization-and-deserialization.md).

- Si vous sérialisez un type d'élément au niveau supérieur sans spécifier le nom racine et l'espace de noms au moment de la construction, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> et <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> n'effectuent essentiellement aucune tâche et <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> appelle `WriteXml`. Dans ce mode, l'objet qui est sérialisé ne peut être `null` et ne peut pas être assigné d'une manière polymorphe. La conservation des graphiques d'objet ne peut pas non plus être activée et le `NetDataContractSerializer` ne peut pas être utilisé.

- Si vous désérialisez un type d'élément au niveau supérieur sans spécifier le nom racine et l'espace de noms au moment de la construction, <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> retourne `true` s'il trouve le début d'un élément. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>, avec le paramètre `verifyObjectName` ayant la valeur `true`, se comporte de la même façon que `IsStartObject` avant de lire l'objet. `ReadObject` passe ensuite le contrôle à la méthode `ReadXml`.

Le schéma exporté pour les types d'élément est le même que pour le type `XmlElement` décrit dans une section antérieure, sauf que la méthode du fournisseur de schéma peut ajouter tout schéma supplémentaire au <xref:System.Xml.Schema.XmlSchemaSet> comme avec les types de contenu. L'utilisation de l'attribut `XmlRootAttribute` avec les types d'élément n'est pas autorisé, et les déclarations d'élément globales ne sont jamais émises pour ces types.

### <a name="differences-from-the-xmlserializer"></a>Différences par rapport au XmlSerializer

L'interface `IXmlSerializable` et les attributs `XmlSchemaProviderAttribute` et `XmlRootAttribute` sont également compris par le <xref:System.Xml.Serialization.XmlSerializer>. Cependant, il existe des différences dans la manière dont ils sont traités dans le modèle de contrat de données. Ces différences importantes sont répertoriées dans la liste suivante :

- La méthode du fournisseur de schéma doit être publique pour être utilisée dans le `XmlSerializer`, mais ne doit pas être nécessairement publique pour être utilisée dans le modèle de contrat de données.

- La méthode du fournisseur de schéma est appelée lorsque `IsAny` a la valeur `true` dans le modèle de contrat de données mais pas avec le `XmlSerializer`.

- Lorsque l'attribut `XmlRootAttribute` n'est pas présent pour les types de contenu ou de groupes de données hérités, le `XmlSerializer` exporte une déclaration d'élément globale dans l'espace de noms vide. Dans le modèle de contrat de données, l'espace de noms utilisé est normalement l'espace de noms de contrat de données décrit précédemment.

Gardez ces différences à l'esprit lors de la création des types qui sont utilisés avec les deux technologies de sérialisation.

### <a name="importing-ixmlserializable-schema"></a>Importation du schéma IXmlSerializable

Lorsque vous importez un schéma généré à partir des types `IXmlSerializable`, plusieurs possibilités sont offertes :

- Le schéma généré peut être un schéma de contrat de données valide, comme décrit dans [référence de schéma de contrat de données](data-contract-schema-reference.md). Dans ce cas, le schéma peut être importé comme d'habitude et les types de contrat de données normaux sont générés.

- Le schéma généré peut ne pas être un schéma de contrat de données valide. Par exemple, votre méthode du fournisseur de schéma peut générer un schéma qui implique des attributs XML qui ne sont pas pris en charge dans le modèle de contrat de données. Dans ce cas, vous pouvez importer le schéma comme des types `IXmlSerializable`. Ce mode d’importation n’est pas activé par défaut, mais peut être facilement activé, par exemple avec le `/importXmlTypes` commutateur de ligne de commande de l' [outil ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Cela est décrit en détail dans le [schéma d’importation pour générer des classes](importing-schema-to-generate-classes.md). Notez que vous devez utiliser directement le XML pour vos instances de type. Vous pouvez envisager d'utiliser également une technologie de sérialisation différente qui prend en charge une plage de schéma plus large. Consultez la rubrique sur l'utilisation du `XmlSerializer`.

- Vous pouvez réutiliser vos types `IXmlSerializable` existants dans le proxy au lieu d'en générer de nouveaux. Dans ce cas, la fonctionnalité des types référencés décrite dans la rubrique « Importation du schéma pour générer des types » peut être utilisée pour indiquer le type à réutiliser. Cela revient à utiliser le commutateur `/reference` sur svcutil.exe qui spécifie l'assembly qui contient les types à réutiliser.

### <a name="xmlserializer-legacy-behavior"></a>Comportement hérité de XmlSerializer

Dans le .NET Framework 4.0 et versions antérieures, le XmlSerializer a généré les assemblys de sérialisation temporaires en écrivant le code C# dans un fichier. Le fichier a ensuite été compilé dans un assembly.  Ce comportement a eu certaines conséquences indésirables, comme ralentir le temps de démarrage du sérialiseur. Dans le .NET Framework 4.5, ce comportement a été modifié pour générer des assemblys sans exiger l'utilisation du compilateur. Certains développeurs peuvent souhaiter consulter le code C# généré. Vous pouvez spécifier d'utiliser ce comportement hérité par la configuration suivante :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.xml.serialization>
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />
  </system.xml.serialization>
  <system.diagnostics>
    <switches>
      <add name="XmlSerialization.Compilation" value="1" />
    </switches>
  </system.diagnostics>
</configuration>
```

Si vous rencontrez des problèmes de compatibilité, tels que l' `XmlSerializer` échec de la sérialisation d’une classe dérivée avec un nouveau remplacement non public, vous pouvez revenir au `XMLSerializer` comportement hérité à l’aide de la configuration suivante :

```xml
<configuration>
  <appSettings>
    <add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />
  </appSettings>
</configuration>
```

En guise d’alternative à la configuration ci-dessus, vous pouvez utiliser la configuration suivante sur un ordinateur exécutant .NET Framework 4,5 ou version ultérieure :

```xml
<configuration>
  <system.xml.serialization>
    <xmlSerializer useLegacySerializerGeneration="true"/>
  </system.xml.serialization>
</configuration>
```

> [!NOTE]
> Le `<xmlSerializer useLegacySerializerGeneration="true"/>` commutateur fonctionne uniquement sur un ordinateur exécutant .NET Framework 4,5 ou version ultérieure. L’approche ci-dessus `appSettings` fonctionne sur toutes les versions de .NET Framework.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md)
- [Using Data Contracts](using-data-contracts.md)
- [Comment : améliorer le temps de démarrage des applications clientes WCF à l'aide de XmlSerializer](startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
