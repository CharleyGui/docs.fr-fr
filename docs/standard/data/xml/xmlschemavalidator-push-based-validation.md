---
title: Validation XmlSchemaValidator de type push
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: d5b2fe4325000023acc98580a2a6d014f56fecbd
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419107"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="c2be5-102">Validation XmlSchemaValidator de type push</span><span class="sxs-lookup"><span data-stu-id="c2be5-102">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="c2be5-103">La classe <xref:System.Xml.Schema.XmlSchemaValidator> fournit un mécanisme efficace et performant de validation des données XML par rapport aux schémas XML selon le modèle push.</span><span class="sxs-lookup"><span data-stu-id="c2be5-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="c2be5-104">Par exemple, la classe <xref:System.Xml.Schema.XmlSchemaValidator> permet de valider un jeu d'informations XML sur place sans devoir le sérialiser dans un document XML et réanalyser ensuite le document à l'aide d'un lecteur XML de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="c2be5-105">La classe <xref:System.Xml.Schema.XmlSchemaValidator> peut être utilisée dans des scénarios avancés tels que la création de moteurs de validation pour des sources de données XML personnalisées ou la génération d’un writer XML de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="c2be5-106">L'exemple suivant illustre l'utilisation de la classe <xref:System.Xml.Schema.XmlSchemaValidator> pour valider le fichier `contosoBooks.xml` par rapport au schéma `contosoBooks.xsd`.</span><span class="sxs-lookup"><span data-stu-id="c2be5-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="c2be5-107">Cet exemple utilise la classe <xref:System.Xml.Serialization.XmlSerializer> pour désérialiser le fichier `contosoBooks.xml` et transmettre la valeur des nœuds aux méthodes de la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="c2be5-108">Cet exemple est utilisé dans toutes les sections de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c2be5-108">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="c2be5-109">L'exemple prend le fichier `contosoBooks.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="c2be5-109">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="c2be5-110">L'exemple prend également le fichier `contosoBooks.xsd` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="c2be5-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>

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

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="c2be5-111">Validation de données XML à l'aide de XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="c2be5-111">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="c2be5-112">Pour commencer à valider un jeu d'informations XML, vous devez d'abord initialiser une nouvelle instance de la classe <xref:System.Xml.Schema.XmlSchemaValidator> à l'aide du constructeur <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="c2be5-113">Le constructeur <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> prend comme paramètres des objets <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet> et <xref:System.Xml.XmlNamespaceManager> ainsi qu'une valeur <xref:System.Xml.Schema.XmlSchemaValidationFlags>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="c2be5-114">L'objet <xref:System.Xml.XmlNameTable> permet d'atomiser des chaînes d'espace de noms bien connues telles que l'espace de noms de schéma, l'espace de noms XML, etc., et est transmis à la méthode <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> lors de la validation d'un contenu simple.</span><span class="sxs-lookup"><span data-stu-id="c2be5-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="c2be5-115">L'objet <xref:System.Xml.Schema.XmlSchemaSet> contient les schémas XML permettant de valider le jeu d'informations XML.</span><span class="sxs-lookup"><span data-stu-id="c2be5-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="c2be5-116">L'objet <xref:System.Xml.XmlNamespaceManager> permet de résoudre les espaces de noms rencontrés pendant la validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="c2be5-117">La valeur <xref:System.Xml.Schema.XmlSchemaValidationFlags> permet de désactiver certaines fonctions de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="c2be5-118">Pour plus d'informations sur le constructeur <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="c2be5-119">Initialisation de la validation</span><span class="sxs-lookup"><span data-stu-id="c2be5-119">Initializing Validation</span></span>

<span data-ttu-id="c2be5-120">Une fois qu'un objet <xref:System.Xml.Schema.XmlSchemaValidator> a été construit, deux méthodes <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> surchargées permettent d'initialiser l'état de l'objet <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="c2be5-121">Voici les deux méthodes <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="c2be5-122">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> par défaut initialise un objet <xref:System.Xml.Schema.XmlSchemaValidator> à son état de départ, tandis que la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> surchargée, qui prend un objet <xref:System.Xml.Schema.XmlSchemaObject> comme paramètre, initialise un objet <xref:System.Xml.Schema.XmlSchemaValidator> à son état de départ pour une validation partielle.</span><span class="sxs-lookup"><span data-stu-id="c2be5-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="c2be5-123">Les deux méthodes <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> ne peuvent être appelées qu'immédiatement après la construction d'un objet <xref:System.Xml.Schema.XmlSchemaValidator> ou après un appel à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="c2be5-124">Pour un exemple de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, voir l'exemple donné dans l'introduction.</span><span class="sxs-lookup"><span data-stu-id="c2be5-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="c2be5-125">Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="c2be5-126">Validation partielle</span><span class="sxs-lookup"><span data-stu-id="c2be5-126">Partial Validation</span></span>

<span data-ttu-id="c2be5-127">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>, qui prend un objet <xref:System.Xml.Schema.XmlSchemaObject> comme paramètre, initialise un objet <xref:System.Xml.Schema.XmlSchemaValidator> à son état de départ pour une validation partielle.</span><span class="sxs-lookup"><span data-stu-id="c2be5-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="c2be5-128">Dans l'exemple suivant, un objet <xref:System.Xml.Schema.XmlSchemaObject> est initialisé en vue d'une validation partielle à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c2be5-129">L'élément de schéma `orderNumber` est transmis lorsque l'objet <xref:System.Xml.XmlQualifiedName> sélectionne l'élément de schéma dans la collection <xref:System.Xml.Schema.XmlSchemaObjectTable> retournée par la propriété <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="c2be5-130">L'objet <xref:System.Xml.Schema.XmlSchemaValidator> valide ensuite cet élément spécifique.</span><span class="sxs-lookup"><span data-stu-id="c2be5-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

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

<span data-ttu-id="c2be5-131">L'exemple prend le schéma XML suivant comme entrée.</span><span class="sxs-lookup"><span data-stu-id="c2be5-131">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="c2be5-132">Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="c2be5-133">Ajout de schémas supplémentaires</span><span class="sxs-lookup"><span data-stu-id="c2be5-133">Adding Additional Schemas</span></span>

<span data-ttu-id="c2be5-134">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> de la classe <xref:System.Xml.Schema.XmlSchemaValidator> permet d'ajouter un schéma XML à l'ensemble de schémas utilisés pendant la validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="c2be5-135">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> peut être utilisée pour simuler l'effet de la rencontre d'un schéma XML inline dans le jeu d'informations XML en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="c2be5-136">L'espace de noms cible du paramètre <xref:System.Xml.Schema.XmlSchema> ne peut pas correspondre à celui d'un élément ou attribut déjà rencontré par l'objet <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="c2be5-137">Si la valeur <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> n'a pas été transmise comme paramètre au constructeur <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> ne fait rien.</span><span class="sxs-lookup"><span data-stu-id="c2be5-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="c2be5-138">Le résultat de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> dépend du contexte de nœuds XML actuel en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="c2be5-139">Pour plus d’informations sur les contextes de validation, voir la section « Contexte de validation » de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c2be5-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="c2be5-140">Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="c2be5-141">Validation d'éléments, d'attributs et de contenu</span><span class="sxs-lookup"><span data-stu-id="c2be5-141">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="c2be5-142">La classe <xref:System.Xml.Schema.XmlSchemaValidator> fournit plusieurs méthodes permettant de valider des éléments, des attributs et du contenu se trouvant dans un jeu d'informations XML par rapport à des schémas XML.</span><span class="sxs-lookup"><span data-stu-id="c2be5-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="c2be5-143">Le tableau suivant décrit chacune de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="c2be5-143">The following table describes each of these methods.</span></span>

|<span data-ttu-id="c2be5-144">Méthode</span><span class="sxs-lookup"><span data-stu-id="c2be5-144">Method</span></span>|<span data-ttu-id="c2be5-145">Description</span><span class="sxs-lookup"><span data-stu-id="c2be5-145">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="c2be5-146">Valide le nom de l'élément dans le contexte actuel.</span><span class="sxs-lookup"><span data-stu-id="c2be5-146">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="c2be5-147">Valide l'attribut dans le contexte de l'élément actuel ou par rapport à l'objet <xref:System.Xml.Schema.XmlSchemaAttribute> transmis comme paramètre à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="c2be5-148">Vérifie si tous les attributs obligatoires dans le contexte de l'élément sont présents et prépare l'objet <xref:System.Xml.Schema.XmlSchemaValidator> à la validation du contenu enfant de l'élément.</span><span class="sxs-lookup"><span data-stu-id="c2be5-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="c2be5-149">Vérifie si du texte est autorisé dans le contexte de l’élément actuel et accumule le texte pour une validation si l’élément actuel a un contenu simple.</span><span class="sxs-lookup"><span data-stu-id="c2be5-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="c2be5-150">Vérifie si des espaces blancs sont autorisés dans le contexte de l’élément actuel et accumule les espaces blancs pour une validation si l’élément actuel a un contenu simple.</span><span class="sxs-lookup"><span data-stu-id="c2be5-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="c2be5-151">Pour les éléments ayant un contenu simple, vérifie si le contenu textuel de l'élément est valide par rapport à son type de données ; pour les éléments ayant un contenu complexe, vérifie si le contenu de l'élément actuel est complet.</span><span class="sxs-lookup"><span data-stu-id="c2be5-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="c2be5-152">Ignore la validation du contenu de l'élément actuel et prépare l'objet <xref:System.Xml.Schema.XmlSchemaValidator> à la validation du contenu dans le contexte de l'élément parent.</span><span class="sxs-lookup"><span data-stu-id="c2be5-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="c2be5-153">Termine la validation et vérifie les contraintes d’identité pour l’ensemble du document XML si l’option de validation <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> est activée.</span><span class="sxs-lookup"><span data-stu-id="c2be5-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="c2be5-154">La classe <xref:System.Xml.Schema.XmlSchemaValidator> a une transition d'état définie qui veille à la séquence et l'occurrence des appels effectués à chacune des méthodes décrites dans le tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c2be5-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="c2be5-155">La transition d'état spécifique de la classe <xref:System.Xml.Schema.XmlSchemaValidator> est décrite dans la section « Transition d'état de XmlSchemaValidator » de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c2be5-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="c2be5-156">Pour un exemple des méthodes utilisées pour valider des éléments, des attributs et du contenu dans un jeu d'informations XML, voir l'exemple de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="c2be5-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="c2be5-157">Pour plus d'informations sur ces méthodes, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="c2be5-158">Validation de contenu à l'aide un objet XmlValueGetter</span><span class="sxs-lookup"><span data-stu-id="c2be5-158">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="c2be5-159">L'objet <xref:System.Xml.Schema.XmlValueGetter>`delegate` permet de transmettre la valeur de nœuds d'attribut, de texte ou d'espace blanc comme un type CLR (Common Language Runtime) compatible avec le type XSD (XML Schema Definition) de ces nœuds.</span><span class="sxs-lookup"><span data-stu-id="c2be5-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="c2be5-160">Un objet <xref:System.Xml.Schema.XmlValueGetter>`delegate` s’avère utile si la valeur CLR d’un nœud d’attribut, de texte ou d’espace blanc est déjà disponible ; il évite de devoir la convertir en une `string` et la réanalyser pour la valider.</span><span class="sxs-lookup"><span data-stu-id="c2be5-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="c2be5-161">Les méthodes <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> sont surchargées et acceptent la valeur des nœuds d'attribut, de texte ou d'espace blanc comme `string` ou comme <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span><span class="sxs-lookup"><span data-stu-id="c2be5-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="c2be5-162">Les méthodes suivantes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> prennent un objet <xref:System.Xml.Schema.XmlValueGetter>`delegate` comme paramètre.</span><span class="sxs-lookup"><span data-stu-id="c2be5-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="c2be5-163">L'exemple de <xref:System.Xml.Schema.XmlValueGetter>`delegate` suivant est pris de l'exemple de classe <xref:System.Xml.Schema.XmlSchemaValidator> donné dans l'introduction.</span><span class="sxs-lookup"><span data-stu-id="c2be5-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="c2be5-164">L'objet <xref:System.Xml.Schema.XmlValueGetter>`delegate` retourne la valeur d'un attribut sous la forme d'un objet <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="c2be5-165">Pour valider cet objet <xref:System.DateTime> retourné par l'objet <xref:System.Xml.Schema.XmlValueGetter>, l'objet <xref:System.Xml.Schema.XmlSchemaValidator> commence par le convertir en un ValueType (ValueType est le mappage CLR par défaut pour le type XSD) correspondant au type de données de l'attribut, puis il vérifie les facettes de la valeur convertie.</span><span class="sxs-lookup"><span data-stu-id="c2be5-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

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

<span data-ttu-id="c2be5-166">Pour un exemple complet de l'objet <xref:System.Xml.Schema.XmlValueGetter>`delegate`, voir l'exemple donné dans l'introduction.</span><span class="sxs-lookup"><span data-stu-id="c2be5-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="c2be5-167">Pour plus d'informations sur l'objet <xref:System.Xml.Schema.XmlValueGetter>`delegate`, voir la documentation de référence sur les classes <xref:System.Xml.Schema.XmlValueGetter> et <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="c2be5-168">Informations de post-validation de schéma</span><span class="sxs-lookup"><span data-stu-id="c2be5-168">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="c2be5-169">La classe <xref:System.Xml.Schema.XmlSchemaInfo> représente certaines informations de post-validation de schéma d’un nœud XML validé par la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="c2be5-170">Diverses méthodes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> acceptent un objet <xref:System.Xml.Schema.XmlSchemaInfo> comme paramètre `null` (`out`) facultatif.</span><span class="sxs-lookup"><span data-stu-id="c2be5-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="c2be5-171">Si la validation réussit, des propriétés de l'objet <xref:System.Xml.Schema.XmlSchemaInfo> sont définies avec les résultats de la validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="c2be5-172">Par exemple, en cas de validation réussie d'un attribut à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, les propriétés <xref:System.Xml.Schema.XmlSchemaInfo>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A> et <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> (s'il est spécifié) sont définies à l'aide des résultats de la validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="c2be5-173">Les méthodes suivantes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> acceptent un objet <xref:System.Xml.Schema.XmlSchemaInfo> comme paramètre out.</span><span class="sxs-lookup"><span data-stu-id="c2be5-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="c2be5-174">Pour un exemple complet de la classe <xref:System.Xml.Schema.XmlSchemaInfo>, voir l'exemple donné dans l'introduction.</span><span class="sxs-lookup"><span data-stu-id="c2be5-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="c2be5-175">Pour plus d'informations sur la classe <xref:System.Xml.Schema.XmlSchemaInfo>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaInfo>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="c2be5-176">Extraction des particules attendues, attributs attendus et attributs par défaut non spécifiés</span><span class="sxs-lookup"><span data-stu-id="c2be5-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="c2be5-177">La classe <xref:System.Xml.Schema.XmlSchemaValidator> fournit les méthodes <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> pour extraire les particules, attributs et attributs par défaut non spécifiés attendus dans le contexte de validation actuel.</span><span class="sxs-lookup"><span data-stu-id="c2be5-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="c2be5-178">Extraction des particules attendues</span><span class="sxs-lookup"><span data-stu-id="c2be5-178">Retrieving Expected Particles</span></span>

<span data-ttu-id="c2be5-179">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau d'objets <xref:System.Xml.Schema.XmlSchemaParticle> contenant les particules attendues dans le contexte de l'élément actuel.</span><span class="sxs-lookup"><span data-stu-id="c2be5-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="c2be5-180">Les particules valides qui peuvent être retournées par la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sont des instances des classes <xref:System.Xml.Schema.XmlSchemaElement> et <xref:System.Xml.Schema.XmlSchemaAny>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="c2be5-181">Lorsque le constructeur du modèle de contenu est `xs:sequence`, seule la particule suivante dans la séquence est retournée.</span><span class="sxs-lookup"><span data-stu-id="c2be5-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="c2be5-182">Si le constructeur du modèle de contenu est `xs:all` ou `xs:choice`, toutes les particules valides pouvant suivre dans le contexte de l'élément actuel sont retournées.</span><span class="sxs-lookup"><span data-stu-id="c2be5-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="c2be5-183">Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> est appelée immédiatement après l'appel à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne tous les éléments globaux.</span><span class="sxs-lookup"><span data-stu-id="c2be5-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="c2be5-184">Par exemple, dans le schéma de langage XSD (XML Schema Definition) et le document XML qui suivent, après la validation de l'élément `book`, l'élément `book` est le contexte d'élément actuel.</span><span class="sxs-lookup"><span data-stu-id="c2be5-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="c2be5-185">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau contenant un seul objet <xref:System.Xml.Schema.XmlSchemaElement> représentant l'élément `title`.</span><span class="sxs-lookup"><span data-stu-id="c2be5-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="c2be5-186">Lorsque le contexte de validation est l'élément `title`, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="c2be5-187">Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> est appelée après que l'élément `title` a été validé mais avant que l'élément `description` soit validé, elle retourne un tableau contenant un seul objet <xref:System.Xml.Schema.XmlSchemaElement> représentant l'élément `description`.</span><span class="sxs-lookup"><span data-stu-id="c2be5-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="c2be5-188">Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> est appelée après que l'élément `description` a été validé, elle retourne un tableau contenant un seul objet <xref:System.Xml.Schema.XmlSchemaAny> représentant le caractère générique.</span><span class="sxs-lookup"><span data-stu-id="c2be5-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

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

 <span data-ttu-id="c2be5-189">L’exemple prend le code XML suivant comme entrée :</span><span class="sxs-lookup"><span data-stu-id="c2be5-189">The example takes the following XML as input:</span></span>

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

<span data-ttu-id="c2be5-190">L’exemple prend le schéma XSD suivant comme entrée :</span><span class="sxs-lookup"><span data-stu-id="c2be5-190">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="c2be5-191">Les résultats des méthodes <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> de la classe <xref:System.Xml.Schema.XmlSchemaValidator> dépendent du contexte actuel en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="c2be5-192">Pour plus d’informations, voir la section « Contexte de validation » de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c2be5-192">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="c2be5-193">Pour un exemple de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, voir l'exemple donné dans l'introduction.</span><span class="sxs-lookup"><span data-stu-id="c2be5-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="c2be5-194">Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="c2be5-195">Extraction des attributs attendus</span><span class="sxs-lookup"><span data-stu-id="c2be5-195">Retrieving Expected Attributes</span></span>

<span data-ttu-id="c2be5-196">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau d'objets <xref:System.Xml.Schema.XmlSchemaAttribute> contenant les attributs attendus dans le contexte de l'élément actuel.</span><span class="sxs-lookup"><span data-stu-id="c2be5-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="c2be5-197">Par exemple, dans l'exemple donné dans l'introduction, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> permet d'extraire tous les attributs de l'élément `book`.</span><span class="sxs-lookup"><span data-stu-id="c2be5-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="c2be5-198">Si vous appelez la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> immédiatement après la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>, elle retourne tous les attributs pouvant apparaître dans le document XML.</span><span class="sxs-lookup"><span data-stu-id="c2be5-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="c2be5-199">Toutefois, si vous appelez la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> après un ou plusieurs appels à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, elle retourne les attributs qui n'ont pas encore été validés pour l'élément actuel.</span><span class="sxs-lookup"><span data-stu-id="c2be5-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="c2be5-200">Les résultats des méthodes <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> de la classe <xref:System.Xml.Schema.XmlSchemaValidator> dépendent du contexte actuel en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="c2be5-201">Pour plus d’informations, voir la section « Contexte de validation » de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c2be5-201">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="c2be5-202">Pour un exemple de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, voir l'exemple donné dans l'introduction.</span><span class="sxs-lookup"><span data-stu-id="c2be5-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="c2be5-203">Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="c2be5-204">Extraction des attributs par défaut non spécifiés</span><span class="sxs-lookup"><span data-stu-id="c2be5-204">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="c2be5-205">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> remplit l'objet <xref:System.Collections.ArrayList> spécifié avec des objets <xref:System.Xml.Schema.XmlSchemaAttribute> pour tous les attributs ayant des valeurs par défaut qui n'ont pas encore été validés à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> dans le contexte de l'élément.</span><span class="sxs-lookup"><span data-stu-id="c2be5-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="c2be5-206">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> doit être appelée après la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> pour chaque attribut du contexte de l'élément.</span><span class="sxs-lookup"><span data-stu-id="c2be5-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="c2be5-207">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> doit être utilisée pour déterminer les attributs par défaut à insérer dans le document XML en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="c2be5-208">Pour plus d'informations sur la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>, voir la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="c2be5-209">Gestion des événements de validation de schéma</span><span class="sxs-lookup"><span data-stu-id="c2be5-209">Handling Schema Validation Events</span></span>

<span data-ttu-id="c2be5-210">Les avertissements et erreurs de validation de schéma rencontrés pendant la validation sont gérés par l’événement <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> de la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="c2be5-211">Les avertissements de validation de schéma ont une valeur <xref:System.Xml.Schema.XmlSeverityType> de <xref:System.Xml.Schema.XmlSeverityType.Warning> ; les erreurs de validation de schéma ont une valeur <xref:System.Xml.Schema.XmlSeverityType> de <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="c2be5-212">Si aucun événement <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> n’a été assigné, un objet <xref:System.Xml.Schema.XmlSchemaValidationException> est levé pour toutes les erreurs de validation de schéma ayant <xref:System.Xml.Schema.XmlSeverityType> comme valeur <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="c2be5-213">Toutefois, cet objet <xref:System.Xml.Schema.XmlSchemaValidationException> n’est pas levé pour les avertissements de validation de schéma dont l’objet <xref:System.Xml.Schema.XmlSeverityType> a pour valeur <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="c2be5-214">L'exemple suivant illustre un objet <xref:System.Xml.Schema.ValidationEventHandler> qui reçoit des avertissements et erreurs de validation de schéma pendant une validation de schéma, provenant de l'exemple donné dans l'introduction.</span><span class="sxs-lookup"><span data-stu-id="c2be5-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

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

<span data-ttu-id="c2be5-215">Pour un exemple complet de l'objet <xref:System.Xml.Schema.ValidationEventHandler>, voir l'exemple donné dans l'introduction.</span><span class="sxs-lookup"><span data-stu-id="c2be5-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="c2be5-216">Pour plus d’informations, consultez la documentation de référence sur la classe <xref:System.Xml.Schema.XmlSchemaInfo>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="c2be5-217">Transition d'état de XmlSchemaValidator</span><span class="sxs-lookup"><span data-stu-id="c2be5-217">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="c2be5-218">La classe <xref:System.Xml.Schema.XmlSchemaValidator> a une transition d'état définie qui veille à la séquence et l'occurrence des appels effectués à chacune des méthodes utilisées pour valider des éléments, des attributs et du contenu dans un jeu d'informations XML.</span><span class="sxs-lookup"><span data-stu-id="c2be5-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="c2be5-219">Le tableau suivant décrit la transition d'état de la classe <xref:System.Xml.Schema.XmlSchemaValidator>, ainsi que la séquence et l'occurrence des appels de méthode qui peuvent être effectués dans chaque état.</span><span class="sxs-lookup"><span data-stu-id="c2be5-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="c2be5-220">State</span><span class="sxs-lookup"><span data-stu-id="c2be5-220">State</span></span>|<span data-ttu-id="c2be5-221">Transition</span><span class="sxs-lookup"><span data-stu-id="c2be5-221">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="c2be5-222">Validate</span><span class="sxs-lookup"><span data-stu-id="c2be5-222">Validate</span></span>|<span data-ttu-id="c2be5-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="c2be5-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="c2be5-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="c2be5-224">TopLevel</span></span>|<span data-ttu-id="c2be5-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span><span class="sxs-lookup"><span data-stu-id="c2be5-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="c2be5-226">Élément</span><span class="sxs-lookup"><span data-stu-id="c2be5-226">Element</span></span>|<span data-ttu-id="c2be5-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* ( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Contenu \* ) ?</span><span class="sxs-lookup"><span data-stu-id="c2be5-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="c2be5-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="c2be5-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="c2be5-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="c2be5-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="c2be5-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> &#124; de contenu \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A></span><span class="sxs-lookup"><span data-stu-id="c2be5-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="c2be5-231">Content</span><span class="sxs-lookup"><span data-stu-id="c2be5-231">Content</span></span>|<span data-ttu-id="c2be5-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span><span class="sxs-lookup"><span data-stu-id="c2be5-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="c2be5-233">Un objet <xref:System.InvalidOperationException> est levé par chacune des méthodes dans le tableau ci-dessus lorsque l'appel à la méthode est effectué dans l'ordre incorrect d'après l'état actuel d'un objet <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="c2be5-234">Le tableau de transition d'état ci-dessus utilise des signes de ponctuation pour décrire les méthodes et d'autres états qui peuvent être appelés pour chaque état de la transition d'état de la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="c2be5-235">Les symboles utilisés sont les mêmes que ceux qui se trouvent dans la référence Standards XML concernant la DTD (définition de type de document).</span><span class="sxs-lookup"><span data-stu-id="c2be5-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="c2be5-236">Le tableau suivant décrit la façon dont les signes de ponctuation trouvés dans le tableau de transition d'état ci-dessus affectent les méthodes et autres états qui peuvent être appelés pour chaque état de la transition d'état de la classe <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="c2be5-237">Symbole</span><span class="sxs-lookup"><span data-stu-id="c2be5-237">Symbol</span></span>|<span data-ttu-id="c2be5-238">Description</span><span class="sxs-lookup"><span data-stu-id="c2be5-238">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="c2be5-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="c2be5-239">&#124;</span></span>|<span data-ttu-id="c2be5-240">La méthode ou l'état au choix (celui qui se trouve devant la barre ou après la barre) peut être appelé.</span><span class="sxs-lookup"><span data-stu-id="c2be5-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="c2be5-241">?</span><span class="sxs-lookup"><span data-stu-id="c2be5-241">?</span></span>|<span data-ttu-id="c2be5-242">La méthode ou l'état qui précède le point d'interrogation est facultatif mais, s'il est appelé, il ne peut l'être qu'une fois.</span><span class="sxs-lookup"><span data-stu-id="c2be5-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|\*|<span data-ttu-id="c2be5-243">La méthode ou l’État qui précède le \* symbole est facultatif et peut être appelé plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="c2be5-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="c2be5-244">Contexte de validation</span><span class="sxs-lookup"><span data-stu-id="c2be5-244">Validation Context</span></span>

<span data-ttu-id="c2be5-245">Les méthodes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> permettant de valider des éléments, des attributs et du contenu dans un jeu d'informations XML modifient le contexte de validation d'un objet <xref:System.Xml.Schema.XmlSchemaValidator>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="c2be5-246">Par exemple, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> ignore la validation du contenu de l'élément actuel et prépare l'objet <xref:System.Xml.Schema.XmlSchemaValidator> à la validation du contenu dans le contexte de l'élément parent ; elle équivaut à ignorer la validation pour tous les enfants de l'élément actuel, puis à appeler la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="c2be5-247">Les résultats des méthodes <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> et <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> de la classe <xref:System.Xml.Schema.XmlSchemaValidator> dépendent du contexte actuel en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="c2be5-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="c2be5-248">Le tableau suivant décrit les résultats de l'appel de ces méthodes après l'une des méthodes de la classe <xref:System.Xml.Schema.XmlSchemaValidator> utilisée pour valider des éléments, des attributs et du contenu dans un jeu d'informations XML.</span><span class="sxs-lookup"><span data-stu-id="c2be5-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="c2be5-249">Méthode</span><span class="sxs-lookup"><span data-stu-id="c2be5-249">Method</span></span>|<span data-ttu-id="c2be5-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="c2be5-250">GetExpectedParticles</span></span>|<span data-ttu-id="c2be5-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="c2be5-251">GetExpectedAttributes</span></span>|<span data-ttu-id="c2be5-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="c2be5-252">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="c2be5-253">Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> par défaut est appelée, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau contenant tous les éléments globaux.</span><span class="sxs-lookup"><span data-stu-id="c2be5-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="c2be5-254">Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> surchargée, qui prend un objet <xref:System.Xml.Schema.XmlSchemaObject> comme paramètre, est appelée pour initialiser une validation partielle d'un élément, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> ne retourne que l'élément auquel l'objet <xref:System.Xml.Schema.XmlSchemaValidator> a été initialisé.</span><span class="sxs-lookup"><span data-stu-id="c2be5-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="c2be5-255">Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> par défaut est appelée, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="c2be5-256">Si la méthode <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> surchargée, qui prend un objet <xref:System.Xml.Schema.XmlSchemaObject> comme paramètre, est appelée pour initialiser une validation partielle d’un attribut, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> ne retourne que l’attribut auquel l’objet <xref:System.Xml.Schema.XmlSchemaValidator> a été initialisé.</span><span class="sxs-lookup"><span data-stu-id="c2be5-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="c2be5-257">Ajoute le schéma à l'objet <xref:System.Xml.Schema.XmlSchemaSet> de l'objet <xref:System.Xml.Schema.XmlSchemaValidator> s'il n'a pas d'erreurs de pré-traitement.</span><span class="sxs-lookup"><span data-stu-id="c2be5-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="c2be5-258">Si l'élément de contexte est valide, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus comme enfants de l'élément de contexte.</span><span class="sxs-lookup"><span data-stu-id="c2be5-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="c2be5-259">Si l'élément de contexte n'est pas valide, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="c2be5-260">Si l'élément de contexte est valide et si aucun appel à la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> n'a été effectué précédemment, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne une liste de tous les attributs définis pour l'élément de contexte.</span><span class="sxs-lookup"><span data-stu-id="c2be5-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="c2be5-261">Si certains attributs ont déjà été validés, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne une liste des attributs restant à valider.</span><span class="sxs-lookup"><span data-stu-id="c2be5-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="c2be5-262">Si l'élément de contexte n'est pas valide, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="c2be5-263">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-263">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="c2be5-264">Si l'attribut de contexte est un attribut de niveau supérieur, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="c2be5-265">Sinon, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus comme premier enfant de l'élément de contexte.</span><span class="sxs-lookup"><span data-stu-id="c2be5-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="c2be5-266">Si l'attribut de contexte est un attribut de niveau supérieur, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="c2be5-267">Sinon, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne la liste des attributs restant à valider.</span><span class="sxs-lookup"><span data-stu-id="c2be5-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="c2be5-268">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-268">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="c2be5-269">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus comme premier enfant de l'élément de contexte.</span><span class="sxs-lookup"><span data-stu-id="c2be5-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="c2be5-270">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne une liste des attributs obligatoires et facultatifs qui doivent encore être validés pour l'élément de contexte.</span><span class="sxs-lookup"><span data-stu-id="c2be5-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="c2be5-271">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-271">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="c2be5-272">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus comme premier enfant de l'élément de contexte.</span><span class="sxs-lookup"><span data-stu-id="c2be5-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="c2be5-273">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="c2be5-274">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-274">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="c2be5-275">Si le contentType de l'élément de contexte est Mixed, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus à la position suivante.</span><span class="sxs-lookup"><span data-stu-id="c2be5-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="c2be5-276">Si le contentType de l'élément de contexte est TextOnly ou Empty, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="c2be5-277">Si le contentType de l’élément de contexte est ElementOnly, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d’éléments attendus à la position suivante, mais une erreur de validation s’est déjà produite.</span><span class="sxs-lookup"><span data-stu-id="c2be5-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="c2be5-278">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne la liste d'attributs non validés de l'élément de contexte.</span><span class="sxs-lookup"><span data-stu-id="c2be5-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="c2be5-279">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-279">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="c2be5-280">Si l'espace blanc de contexte est un espace blanc de niveau supérieur, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="c2be5-281">Sinon, le comportement de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> est le même que dans <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="c2be5-282">Si l'espace blanc de contexte est un espace blanc de niveau supérieur, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="c2be5-283">Sinon, le comportement de la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> est le même que dans <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="c2be5-284">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-284">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="c2be5-285">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> retourne la séquence d'éléments attendus après l'élément de contexte (frères possibles).</span><span class="sxs-lookup"><span data-stu-id="c2be5-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="c2be5-286">La méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne la liste d'attributs non validés de l'élément de contexte.</span><span class="sxs-lookup"><span data-stu-id="c2be5-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="c2be5-287">Si l'élément de contexte n'a pas de parent, la méthode <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> retourne une liste vide (l'élément de contexte est le parent de l'élément actuel pour lequel la méthode <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> a été appelée).</span><span class="sxs-lookup"><span data-stu-id="c2be5-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="c2be5-288">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-288">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="c2be5-289">Identique à <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="c2be5-290">Identique à <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="c2be5-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="c2be5-291">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-291">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="c2be5-292">Retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-292">Returns an empty array.</span></span>|<span data-ttu-id="c2be5-293">Retourne un tableau vide.</span><span class="sxs-lookup"><span data-stu-id="c2be5-293">Returns an empty array.</span></span>|<span data-ttu-id="c2be5-294">Identique à ce qui précède.</span><span class="sxs-lookup"><span data-stu-id="c2be5-294">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="c2be5-295">Les valeurs retournées par les diverses propriétés de la classe <xref:System.Xml.Schema.XmlSchemaValidator> ne sont pas altérées par un appel à l'une des méthodes du tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c2be5-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2be5-296">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2be5-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
