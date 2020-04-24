---
title: Validation XmlSchemaValidator de type push
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: 6a0cc110c2b8bcd97b9f5c16a344db5a63046353
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709801"
---
# <a name="xmlschemavalidator-push-based-validation"></a>Validation XmlSchemaValidator de type push

La classe <xref:System.Xml.Schema.XmlSchemaValidator> fournit un mécanisme efficace et performant de validation des données XML par rapport aux schémas XML selon le modèle push. Par exemple, la classe <xref:System.Xml.Schema.XmlSchemaValidator> permet de valider un jeu d'informations XML sur place sans devoir le sérialiser dans un document XML et réanalyser ensuite le document à l'aide d'un lecteur XML de validation.

La classe <xref:System.Xml.Schema.XmlSchemaValidator> peut être utilisée dans des scénarios avancés tels que la création de moteurs de validation pour des sources de données XML personnalisées ou la génération d’un writer XML de validation.

L'exemple suivant illustre l'utilisation de la classe <xref:System.Xml.Schema.XmlSchemaValidator> pour valider le fichier `contosoBooks.xml` par rapport au schéma `contosoBooks.xsd`. Cet exemple utilise la classe <xref:System.Xml.Serialization.XmlSerializer> pour désérialiser le fichier `contosoBooks.xml` et transmettre la valeur des nœuds aux méthodes de la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

> [!NOTE]
> Cet exemple est utilisé dans toutes les sections de cette rubrique.

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

L'exemple prend le fichier `contosoBooks.xml` comme entrée.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <xs:element name="bookstore">
        <xs:complexType>
            <xs:sequence>
                <xs:element maxOccurs="unbounded" name="book">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="title" type="xs:string" />
                            <xs:element name="author">
                                <xs:complexType>
                                    <xs:sequence>
                                        <xs:element minOccurs="0" name="name" type="xs:string" />
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />
                                    </xs:sequence>
                                </xs:complexType>
                            </xs:element>
                            <xs:element name="price" type="xs:decimal" />
                        </xs:sequence>
                        <xs:attribute name="genre" type="xs:string" use="required" />
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />
                        <xs:attribute name="ISBN" type="xs:string" use="required" />
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

## <a name="validating-xml-data-using-xmlschemavalidator"></a>Validation de données XML à l'aide de XmlSchemaValidator

Pour commencer à valider un jeu d'informations XML, vous devez d'abord initialiser une nouvelle instance de la classe <xref:System.Xml.Schema.XmlSchemaValidator> à l'aide du constructeur <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>.

Le constructeur <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> prend comme paramètres des objets <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet> et <xref:System.Xml.XmlNamespaceManager> ainsi qu'une valeur <xref:System.Xml.Schema.XmlSchemaValidationFlags>. L'objet <xref:System.Xml.XmlNameTable> permet d'atomiser des chaînes d'espace de noms bien connues telles que l'espace de noms de schéma, l'espace de noms XML, etc., et est transmis à la méthode <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> lors de la validation d'un contenu simple. L'objet <xref:System.Xml.Schema.XmlSchemaSet> contient les schémas XML permettant de valider le jeu d'informations XML. L'objet <xref:System.Xml.XmlNamespaceManager> permet de résoudre les espaces de noms rencontrés pendant la validation. La valeur <xref:System.Xml.Schema.XmlSchemaValidationFlags> permet de désactiver certaines fonctions de validation.

Pour plus d'informations sur le constructeur <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="initializing-validation"></a>Initialisation de la validation

Une fois qu'un objet <xref:System.Xml.Schema.XmlSchemaValidator> a été construit, deux méthodes <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> surchargées permettent d'initialiser l'état de l'objet <xref:System.Xml.Schema.XmlSchemaValidator>. Voici les deux méthodes <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

La méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> par défaut initialise un objet <xref:System.Xml.Schema.XmlSchemaValidator> à son état de départ, tandis que la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> surchargée, qui prend un objet <xref:System.Xml.Schema.XmlSchemaObject> comme paramètre, initialise un objet <xref:System.Xml.Schema.XmlSchemaValidator> à son état de départ pour une validation partielle.

Les deux méthodes <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> ne peuvent être appelées qu'immédiatement après la construction d'un objet <xref:System.Xml.Schema.XmlSchemaValidator> ou après un appel à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.

Pour un exemple de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, voir l'exemple donné dans l'introduction. Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="partial-validation"></a>Validation partielle

La méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, qui prend un objet <xref:System.Xml.Schema.XmlSchemaObject> comme paramètre, initialise un objet <xref:System.Xml.Schema.XmlSchemaValidator> à son état de départ pour une validation partielle.

Dans l'exemple suivant, un objet <xref:System.Xml.Schema.XmlSchemaObject> est initialisé en vue d'une validation partielle à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>. L'élément de schéma `orderNumber` est transmis lorsque l'objet <xref:System.Xml.XmlQualifiedName> sélectionne l'élément de schéma dans la collection <xref:System.Xml.Schema.XmlSchemaObjectTable> retournée par la propriété <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>. L'objet <xref:System.Xml.Schema.XmlSchemaValidator> valide ensuite cet élément spécifique.

```vb
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
schemaSet.Compile()
Dim nameTable As NameTable = New NameTable()
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)

Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))

validator.ValidateElement("orderNumber", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateText("123")
validator.ValidateEndElement(Nothing)
```

```csharp
XmlSchemaSet schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
schemaSet.Compile();
NameTable nameTable = new NameTable();
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);

XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);

validator.ValidateElement("orderNumber", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateText("123");
validator.ValidateEndElement(null);
```

L'exemple prend le schéma XML suivant comme entrée.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="adding-additional-schemas"></a>Ajout de schémas supplémentaires

La méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> de la classe <xref:System.Xml.Schema.XmlSchemaValidator> permet d'ajouter un schéma XML à l'ensemble de schémas utilisés pendant la validation. La méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> peut être utilisée pour simuler l'effet de la rencontre d'un schéma XML inline dans le jeu d'informations XML en cours de validation.

> [!NOTE]
> L'espace de noms cible du paramètre <xref:System.Xml.Schema.XmlSchema> ne peut pas correspondre à celui d'un élément ou attribut déjà rencontré par l'objet <xref:System.Xml.Schema.XmlSchemaValidator>.
>
> Si la valeur <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> n'a pas été transmise comme paramètre au constructeur <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> ne fait rien.

Le résultat de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> dépend du contexte de nœuds XML actuel en cours de validation. Pour plus d’informations sur les contextes de validation, voir la section « Contexte de validation » de cette rubrique.

Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="validating-elements-attributes-and-content"></a>Validation d'éléments, d'attributs et de contenu

La classe <xref:System.Xml.Schema.XmlSchemaValidator> fournit plusieurs méthodes permettant de valider des éléments, des attributs et du contenu se trouvant dans un jeu d'informations XML par rapport à des schémas XML. Le tableau suivant décrit chacune de ces méthodes.

|Méthode|Description|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Valide le nom de l'élément dans le contexte actuel.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Valide l'attribut dans le contexte de l'élément actuel ou par rapport à l'objet <xref:System.Xml.Schema.XmlSchemaAttribute> transmis comme paramètre à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Vérifie si tous les attributs obligatoires dans le contexte de l'élément sont présents et prépare l'objet <xref:System.Xml.Schema.XmlSchemaValidator> à la validation du contenu enfant de l'élément.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Vérifie si du texte est autorisé dans le contexte de l’élément actuel et accumule le texte pour une validation si l’élément actuel a un contenu simple.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Vérifie si des espaces blancs sont autorisés dans le contexte de l’élément actuel et accumule les espaces blancs pour une validation si l’élément actuel a un contenu simple.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Pour les éléments ayant un contenu simple, vérifie si le contenu textuel de l'élément est valide par rapport à son type de données ; pour les éléments ayant un contenu complexe, vérifie si le contenu de l'élément actuel est complet.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Ignore la validation du contenu de l'élément actuel et prépare l'objet <xref:System.Xml.Schema.XmlSchemaValidator> à la validation du contenu dans le contexte de l'élément parent.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Termine la validation et vérifie les contraintes d’identité pour l’ensemble du document XML si l’option de validation <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> est activée.|

> [!NOTE]
> La classe <xref:System.Xml.Schema.XmlSchemaValidator> a une transition d'état définie qui veille à la séquence et l'occurrence des appels effectués à chacune des méthodes décrites dans le tableau ci-dessus. La transition d'état spécifique de la classe <xref:System.Xml.Schema.XmlSchemaValidator> est décrite dans la section « Transition d'état de XmlSchemaValidator » de cette rubrique.

Pour un exemple des méthodes utilisées pour valider des éléments, des attributs et du contenu dans un jeu d'informations XML, voir l'exemple de la section précédente. Pour plus d'informations sur ces méthodes, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="validating-content-using-an-xmlvaluegetter"></a>Validation de contenu à l'aide un objet XmlValueGetter

L'objet <xref:System.Xml.Schema.XmlValueGetter>`delegate` permet de transmettre la valeur de nœuds d'attribut, de texte ou d'espace blanc comme un type CLR (Common Language Runtime) compatible avec le type XSD (XML Schema Definition) de ces nœuds. Un objet <xref:System.Xml.Schema.XmlValueGetter>`delegate` s’avère utile si la valeur CLR d’un nœud d’attribut, de texte ou d’espace blanc est déjà disponible ; il évite de devoir la convertir en une `string` et la réanalyser pour la valider.

Les méthodes <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> sont surchargées et acceptent la valeur des nœuds d'attribut, de texte ou d'espace blanc comme `string` ou comme <xref:System.Xml.Schema.XmlValueGetter>`delegate`.

Les méthodes suivantes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> prennent un objet <xref:System.Xml.Schema.XmlValueGetter>`delegate` comme paramètre.

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

L'exemple de <xref:System.Xml.Schema.XmlValueGetter>`delegate` suivant est pris de l'exemple de classe <xref:System.Xml.Schema.XmlSchemaValidator> donné dans l'introduction. L'objet <xref:System.Xml.Schema.XmlValueGetter>`delegate` retourne la valeur d'un attribut sous la forme d'un objet <xref:System.DateTime>. Pour valider cet objet <xref:System.DateTime> retourné par l'objet <xref:System.Xml.Schema.XmlValueGetter>, l'objet <xref:System.Xml.Schema.XmlSchemaValidator> commence par le convertir en un ValueType (ValueType est le mappage CLR par défaut pour le type XSD) correspondant au type de données de l'attribut, puis il vérifie les facettes de la valeur convertie.

```vb
Shared dateTimeGetterContent As Object

Shared Function DateTimeGetterHandle() As Object
    Return dateTimeGetterContent
End Function

Shared Function DateTimeGetter(dateTime As DateTime) As XmlValueGetter
    dateTimeGetterContent = dateTime
    Return New XmlValueGetter(AddressOf DateTimeGetterHandle)
End Function
```

```csharp
static object dateTimeGetterContent;

static object DateTimeGetterHandle()
{
    return dateTimeGetterContent;
}

static XmlValueGetter DateTimeGetter(DateTime dateTime)
{
    dateTimeGetterContent = dateTime;
    return new XmlValueGetter(dateTimeGetterHandle);
}
```

Pour un exemple complet de l'objet <xref:System.Xml.Schema.XmlValueGetter>`delegate`, voir l'exemple donné dans l'introduction. Pour plus d'informations sur l'objet <xref:System.Xml.Schema.XmlValueGetter>`delegate`, voir la documentation de référence sur les classes <xref:System.Xml.Schema.XmlValueGetter> et <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="post-schema-validation-information"></a>Informations de post-validation de schéma

La classe <xref:System.Xml.Schema.XmlSchemaInfo> représente certaines informations de post-validation de schéma d’un nœud XML validé par la classe <xref:System.Xml.Schema.XmlSchemaValidator>. Diverses méthodes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> acceptent un objet <xref:System.Xml.Schema.XmlSchemaInfo> comme paramètre `null` (`out`) facultatif.

Si la validation réussit, des propriétés de l'objet <xref:System.Xml.Schema.XmlSchemaInfo> sont définies avec les résultats de la validation. Par exemple, en cas de validation réussie d'un attribut à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, les propriétés <xref:System.Xml.Schema.XmlSchemaInfo>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A> et <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> (s'il est spécifié) sont définies à l'aide des résultats de la validation.

Les méthodes suivantes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> acceptent un objet <xref:System.Xml.Schema.XmlSchemaInfo> comme paramètre out.

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

Pour un exemple complet de la classe <xref:System.Xml.Schema.XmlSchemaInfo>, voir l'exemple donné dans l'introduction. Pour plus d'informations sur la classe <xref:System.Xml.Schema.XmlSchemaInfo>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaInfo>.

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Extraction des particules attendues, attributs attendus et attributs par défaut non spécifiés

La classe <xref:System.Xml.Schema.XmlSchemaValidator> fournit les méthodes <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> pour extraire les particules, attributs et attributs par défaut non spécifiés attendus dans le contexte de validation actuel.

#### <a name="retrieving-expected-particles"></a>Extraction des particules attendues

La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau d'objets <xref:System.Xml.Schema.XmlSchemaParticle> contenant les particules attendues dans le contexte de l'élément actuel. Les particules valides qui peuvent être retournées par la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sont des instances des classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaAny>.

Lorsque le constructeur du modèle de contenu est `xs:sequence`, seule la particule suivante dans la séquence est retournée. Si le constructeur du modèle de contenu est `xs:all` ou `xs:choice`, toutes les particules valides pouvant suivre dans le contexte de l'élément actuel sont retournées.

> [!NOTE]
> Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> est appelée immédiatement après l'appel à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne tous les éléments globaux.

Par exemple, dans le schéma de langage XSD (XML Schema Definition) et le document XML qui suivent, après la validation de l'élément `book`, l'élément `book` est le contexte d'élément actuel. La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau contenant un seul objet <xref:System.Xml.Schema.XmlSchemaElement> représentant l'élément `title`. Lorsque le contexte de validation est l'élément `title`, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide. Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> est appelée après que l'élément `title` a été validé mais avant que l'élément `description` soit validé, elle retourne un tableau contenant un seul objet <xref:System.Xml.Schema.XmlSchemaElement> représentant l'élément `description`. Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> est appelée après que l'élément `description` a été validé, elle retourne un tableau contenant un seul objet <xref:System.Xml.Schema.XmlSchemaAny> représentant le caractère générique.

```vb
Dim reader As XmlReader =  XmlReader.Create("input.xml")

Dim schemaSet As New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
Dim manager As New XmlNamespaceManager(reader.NameTable)

Dim validator As New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)
validator.Initialize()

validator.ValidateElement("book", "", Nothing)

validator.ValidateEndOfAttributes(Nothing)
For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next

validator.ValidateElement("title", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next
validator.ValidateEndElement(Nothing)

For Each element As XmlSchemaElement In validator.GetExpectedParticles()
    Console.WriteLine(element.Name)
Next

validator.ValidateElement("description", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateEndElement(Nothing)

For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()
    Console.WriteLine(particle.GetType())
Next

validator.ValidateElement("namespace", "", Nothing)
validator.ValidateEndOfAttributes(Nothing)
validator.ValidateEndElement(Nothing)

validator.ValidateEndElement(Nothing)
```

```csharp
XmlReader reader = XmlReader.Create("input.xml");

var schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
var manager = new XmlNamespaceManager(reader.NameTable);

var validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
validator.Initialize();

validator.ValidateElement("book", "", null);

validator.ValidateEndOfAttributes(null);
foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}

validator.ValidateElement("title", "", null);
validator.ValidateEndOfAttributes(null);
foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}
validator.ValidateEndElement(null);

foreach (XmlSchemaElement element in validator.GetExpectedParticles())
{
    Console.WriteLine(element.Name);
}

validator.ValidateElement("description", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateEndElement(null);

foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())
{
    Console.WriteLine(particle.GetType());
}

validator.ValidateElement("namespace", "", null);
validator.ValidateEndOfAttributes(null);
validator.ValidateEndElement(null);

validator.ValidateEndElement(null);
```

 L’exemple prend le code XML suivant comme entrée :

```xml
<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:sequence>
      <xs:element name="title" type="xs:string" />
      <xs:element name="description" type="xs:string" />
      <xs:any processContent="lax" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:element>
</xs:schema>
```

L’exemple prend le schéma XSD suivant comme entrée :

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> Les résultats des méthodes <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> de la classe <xref:System.Xml.Schema.XmlSchemaValidator> dépendent du contexte actuel en cours de validation. Pour plus d’informations, voir la section « Contexte de validation » de cette rubrique.

Pour un exemple de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, voir l'exemple donné dans l'introduction. Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="retrieving-expected-attributes"></a>Extraction des attributs attendus

La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau d'objets <xref:System.Xml.Schema.XmlSchemaAttribute> contenant les attributs attendus dans le contexte de l'élément actuel.

Par exemple, dans l'exemple donné dans l'introduction, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> permet d'extraire tous les attributs de l'élément `book`.

Si vous appelez la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> immédiatement après la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>, elle retourne tous les attributs pouvant apparaître dans le document XML. Toutefois, si vous appelez la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> après un ou plusieurs appels à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, elle retourne les attributs qui n'ont pas encore été validés pour l'élément actuel.

> [!NOTE]
> Les résultats des méthodes <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> de la classe <xref:System.Xml.Schema.XmlSchemaValidator> dépendent du contexte actuel en cours de validation. Pour plus d’informations, voir la section « Contexte de validation » de cette rubrique.

Pour un exemple de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, voir l'exemple donné dans l'introduction. Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

#### <a name="retrieving-unspecified-default-attributes"></a>Extraction des attributs par défaut non spécifiés

La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> remplit l'objet <xref:System.Collections.ArrayList> spécifié avec des objets <xref:System.Xml.Schema.XmlSchemaAttribute> pour tous les attributs ayant des valeurs par défaut qui n'ont pas encore été validés à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> dans le contexte de l'élément. La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> doit être appelée après la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> pour chaque attribut du contexte de l'élément. La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> doit être utilisée pour déterminer les attributs par défaut à insérer dans le document XML en cours de validation.

Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

### <a name="handling-schema-validation-events"></a>Gestion des événements de validation de schéma

Les avertissements et erreurs de validation de schéma rencontrés pendant la validation sont gérés par l’événement <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> de la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

Les avertissements de validation de schéma ont une valeur <xref:System.Xml.Schema.XmlSeverityType> de <xref:System.Xml.Schema.XmlSeverityType.Warning> ; les erreurs de validation de schéma ont une valeur <xref:System.Xml.Schema.XmlSeverityType> de <xref:System.Xml.Schema.XmlSeverityType.Error>. Si aucun événement <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> n’a été assigné, un objet <xref:System.Xml.Schema.XmlSchemaValidationException> est levé pour toutes les erreurs de validation de schéma ayant <xref:System.Xml.Schema.XmlSeverityType> comme valeur <xref:System.Xml.Schema.XmlSeverityType.Error>. Toutefois, cet objet <xref:System.Xml.Schema.XmlSchemaValidationException> n’est pas levé pour les avertissements de validation de schéma dont l’objet <xref:System.Xml.Schema.XmlSeverityType> a pour valeur <xref:System.Xml.Schema.XmlSeverityType.Warning>.

L'exemple suivant illustre un objet <xref:System.Xml.Schema.ValidationEventHandler> qui reçoit des avertissements et erreurs de validation de schéma pendant une validation de schéma, provenant de l'exemple donné dans l'introduction.

```vb
Shared Sub SchemaValidationEventHandler(sender As Object, e As ValidationEventArgs)

    Select Case e.Severity
        Case XmlSeverityType.Error
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)
            Exit Sub
        Case XmlSeverityType.Warning
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)
            Exit Sub
    End Select
End Sub
```

```csharp
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)
{
    switch (e.Severity)
    {
        case XmlSeverityType.Error:
            Console.WriteLine("\nError: {0}", e.Message);
            break;
        case XmlSeverityType.Warning:
            Console.WriteLine("\nWarning: {0}", e.Message);
            break;
    }
}
```

Pour un exemple complet de l'objet <xref:System.Xml.Schema.ValidationEventHandler>, voir l'exemple donné dans l'introduction. Pour plus d’informations, consultez la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaInfo>.

## <a name="xmlschemavalidator-state-transition"></a>Transition d'état de XmlSchemaValidator

La classe <xref:System.Xml.Schema.XmlSchemaValidator> a une transition d'état définie qui veille à la séquence et l'occurrence des appels effectués à chacune des méthodes utilisées pour valider des éléments, des attributs et du contenu dans un jeu d'informations XML.

Le tableau suivant décrit la transition d'état de la classe <xref:System.Xml.Schema.XmlSchemaValidator>, ainsi que la séquence et l'occurrence des appels de méthode qui peuvent être effectués dans chaque état.

|State|Transition|
|-----------|----------------|
|Valider|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|
|Élément|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Contenu\*) ? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A><br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* &#124; de <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> contenu \* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|
|Contenu|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element|

> [!NOTE]
> Un objet <xref:System.InvalidOperationException> est levé par chacune des méthodes dans le tableau ci-dessus lorsque l'appel à la méthode est effectué dans l'ordre incorrect d'après l'état actuel d'un objet <xref:System.Xml.Schema.XmlSchemaValidator>.

Le tableau de transition d'état ci-dessus utilise des signes de ponctuation pour décrire les méthodes et d'autres états qui peuvent être appelés pour chaque état de la transition d'état de la classe <xref:System.Xml.Schema.XmlSchemaValidator>. Les symboles utilisés sont les mêmes que ceux qui se trouvent dans la référence Standards XML concernant la DTD (définition de type de document).

Le tableau suivant décrit la façon dont les signes de ponctuation trouvés dans le tableau de transition d'état ci-dessus affectent les méthodes et autres états qui peuvent être appelés pour chaque état de la transition d'état de la classe <xref:System.Xml.Schema.XmlSchemaValidator>.

|Symbole|Description|
|------------|-----------------|
|&#124;|La méthode ou l'état au choix (celui qui se trouve devant la barre ou après la barre) peut être appelé.|
|?|La méthode ou l'état qui précède le point d'interrogation est facultatif mais, s'il est appelé, il ne peut l'être qu'une fois.|
|*|La méthode ou l'état qui précède le signe * est facultatif et peut être appelé plusieurs fois.|

## <a name="validation-context"></a>Contexte de validation

Les méthodes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> permettant de valider des éléments, des attributs et du contenu dans un jeu d'informations XML modifient le contexte de validation d'un objet <xref:System.Xml.Schema.XmlSchemaValidator>. Par exemple, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> ignore la validation du contenu de l'élément actuel et prépare l'objet <xref:System.Xml.Schema.XmlSchemaValidator> à la validation du contenu dans le contexte de l'élément parent ; elle équivaut à ignorer la validation pour tous les enfants de l'élément actuel, puis à appeler la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.

Les résultats des méthodes <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> de la classe <xref:System.Xml.Schema.XmlSchemaValidator> dépendent du contexte actuel en cours de validation.

Le tableau suivant décrit les résultats de l'appel de ces méthodes après l'une des méthodes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> utilisée pour valider des éléments, des attributs et du contenu dans un jeu d'informations XML.

|Méthode|GetExpectedParticles|GetExpectedAttributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> par défaut est appelée, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau contenant tous les éléments globaux.<br /><br /> Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> surchargée, qui prend un objet <xref:System.Xml.Schema.XmlSchemaObject> comme paramètre, est appelée pour initialiser une validation partielle d'un élément, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> ne retourne que l'élément auquel l'objet <xref:System.Xml.Schema.XmlSchemaValidator> a été initialisé.|Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> par défaut est appelée, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.<br /><br /> Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> surchargée, qui prend un objet <xref:System.Xml.Schema.XmlSchemaObject> comme paramètre, est appelée pour initialiser une validation partielle d’un attribut, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> ne retourne que l’attribut auquel l’objet <xref:System.Xml.Schema.XmlSchemaValidator> a été initialisé.|Ajoute le schéma à l'objet <xref:System.Xml.Schema.XmlSchemaSet> de l'objet <xref:System.Xml.Schema.XmlSchemaValidator> s'il n'a pas d'erreurs de pré-traitement.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Si l'élément de contexte est valide, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus comme enfants de l'élément de contexte.<br /><br /> Si l'élément de contexte n'est pas valide, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.|Si l'élément de contexte est valide et si aucun appel à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> n'a été effectué précédemment, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne une liste de tous les attributs définis pour l'élément de contexte.<br /><br /> Si certains attributs ont déjà été validés, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne une liste des attributs restant à valider.<br /><br /> Si l'élément de contexte n'est pas valide, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.|Identique à ce qui précède.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Si l'attribut de contexte est un attribut de niveau supérieur, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.<br /><br /> Sinon, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus comme premier enfant de l'élément de contexte.|Si l'attribut de contexte est un attribut de niveau supérieur, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.<br /><br /> Sinon, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne la liste des attributs restant à valider.|Identique à ce qui précède.|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus comme premier enfant de l'élément de contexte.|La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne une liste des attributs obligatoires et facultatifs qui doivent encore être validés pour l'élément de contexte.|Identique à ce qui précède.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus comme premier enfant de l'élément de contexte.|La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.|Identique à ce qui précède.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Si le contentType de l'élément de contexte est Mixed, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus à la position suivante.<br /><br /> Si le contentType de l'élément de contexte est TextOnly ou Empty, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.<br /><br /> Si le contentType de l’élément de contexte est ElementOnly, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d’éléments attendus à la position suivante, mais une erreur de validation s’est déjà produite.|La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne la liste d'attributs non validés de l'élément de contexte.|Identique à ce qui précède.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Si l'espace blanc de contexte est un espace blanc de niveau supérieur, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.<br /><br /> Sinon, le comportement de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> est le même que dans <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Si l'espace blanc de contexte est un espace blanc de niveau supérieur, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.<br /><br /> Sinon, le comportement de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> est le même que dans <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Identique à ce qui précède.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus après l'élément de contexte (frères possibles).|La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne la liste d'attributs non validés de l'élément de contexte.<br /><br /> Si l'élément de contexte n'a pas de parent, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne une liste vide (l'élément de contexte est le parent de l'élément actuel pour lequel la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> a été appelée).|Identique à ce qui précède.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Identique à <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Identique à <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Identique à ce qui précède.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Retourne un tableau vide.|Retourne un tableau vide.|Identique à ce qui précède.|

> [!NOTE]
> Les valeurs retournées par les diverses propriétés de la classe <xref:System.Xml.Schema.XmlSchemaValidator> ne sont pas altérées par un appel à l'une des méthodes du tableau ci-dessus.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Schema.XmlSchemaValidator>
