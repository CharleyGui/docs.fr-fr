---
title: Accès à des données XML fortement typées à l'aide de XPathNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: fcf46a0716d79fd27cb06924bf74c119b8435147
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822826"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="0683d-102">Accès à des données XML fortement typées à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0683d-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>
<span data-ttu-id="0683d-103">En tant qu’instance du modèle de données XPath 2,0, la <xref:System.Xml.XPath.XPathNavigator> classe peut contenir des données fortement typées qui sont mappées à des types Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0683d-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="0683d-104">Selon le modèle de données XPath 2,0, seuls les éléments et les attributs peuvent contenir des données fortement typées.</span><span class="sxs-lookup"><span data-stu-id="0683d-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly typed data.</span></span> <span data-ttu-id="0683d-105">La <xref:System.Xml.XPath.XPathNavigator> classe fournit des mécanismes pour accéder aux données dans <xref:System.Xml.XPath.XPathDocument> un <xref:System.Xml.XmlDocument> objet ou en tant que données fortement typées, ainsi que des mécanismes de conversion d’un type de données en un autre.</span><span class="sxs-lookup"><span data-stu-id="0683d-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="0683d-106">Informations sur le type exposées par XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0683d-106">Type Information Exposed by XPathNavigator</span></span>  
 <span data-ttu-id="0683d-107">D'un point de vue technique, les données XML 1.0 ne présentent pas de type, sauf si elles sont traitées avec une DTD, un schéma de langage XSD (XML schema definition) ou un autre mécanisme.</span><span class="sxs-lookup"><span data-stu-id="0683d-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="0683d-108">Un certain nombre de catégories d'informations sur le type peuvent être associées à un attribut ou un élément XML.</span><span class="sxs-lookup"><span data-stu-id="0683d-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="0683d-109">Types CLR simples : aucun des langages de schéma XML ne prend directement en charge les types CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="0683d-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="0683d-110">Puisqu'il est utile de pouvoir afficher du contenu d'attribut ou d'élément simple en tant que type CLR le plus approprié, tout contenu simple peut être typé <xref:System.String> en l'absence d'informations de schéma avec des informations complémentaires sur le schéma qui redéfinissent potentiellement ce contenu en type plus approprié.</span><span class="sxs-lookup"><span data-stu-id="0683d-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="0683d-111">La propriété <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> permet de trouver le type CLR le plus adapté à un contenu d'attribut ou d'élément simple.</span><span class="sxs-lookup"><span data-stu-id="0683d-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="0683d-112">Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0683d-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="0683d-113">Listes de types (CLR) simples : un élément ou un attribut avec du contenu simple peut contenir une liste de valeurs séparées par des espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="0683d-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="0683d-114">Les valeurs sont spécifiées par un schéma XML comme « type de liste ».</span><span class="sxs-lookup"><span data-stu-id="0683d-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="0683d-115">En l'absence d'un schéma XML, un tel contenu simple est traité comme un nœud de texte simple.</span><span class="sxs-lookup"><span data-stu-id="0683d-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="0683d-116">Si un schéma XML est disponible, ce contenu simple peut être exposé comme une série de valeurs atomiques ayant chacune un type simple qui correspond à un ensemble d'objets CLR.</span><span class="sxs-lookup"><span data-stu-id="0683d-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="0683d-117">Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0683d-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="0683d-118">Valeur typée : élément ou attribut validé par rapport à un schéma avec un type simple qui présente une valeur typée.</span><span class="sxs-lookup"><span data-stu-id="0683d-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="0683d-119">Cette valeur est un type primitif tel qu'un type numérique, de chaîne ou de date.</span><span class="sxs-lookup"><span data-stu-id="0683d-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="0683d-120">Tous les types intégrés simples de XSD peuvent être mappés à des types CLR fournissant un accès à la valeur d'un nœud en tant que type le plus approprié, au lieu d'un simple objet <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0683d-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="0683d-121">Un élément avec des attributs ou des éléments enfants est considéré comme un type complexe.</span><span class="sxs-lookup"><span data-stu-id="0683d-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="0683d-122">La valeur typée d'un type complexe avec un contenu simple (uniquement des nœuds de texte comme enfants) est identique à celui du type simple de son contenu.</span><span class="sxs-lookup"><span data-stu-id="0683d-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="0683d-123">La valeur typée d'un type complexe avec un contenu complexe (un ou plusieurs éléments enfants) est la valeur de chaîne de la concaténation de tous ses nœuds de texte enfant retournée sous la forme d'un objet <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0683d-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="0683d-124">Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0683d-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="0683d-125">Nom du type spécifique au langage du schéma : dans la plupart des cas, les types CLR, définis comme l'effet secondaire de l'application d'un schéma externe, permettent de fournir un accès à la valeur d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="0683d-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="0683d-126">Toutefois, dans certaines situations, il se peut que vous souhaitiez examiner le type associé à un schéma particulier appliqué à un document XML.</span><span class="sxs-lookup"><span data-stu-id="0683d-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="0683d-127">Par exemple, il se peut que vous souhaitiez effectuer une recherche dans un document XML et extraire tous les éléments identifiés comme ayant un contenu de type « OrdreAchat » conformément à un schéma associé.</span><span class="sxs-lookup"><span data-stu-id="0683d-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="0683d-128">Ces informations sur le type ne peuvent être définies que suite à une validation de schéma et sont accessibles via les propriétés <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> et <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0683d-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="0683d-129">Pour plus d'informations, consultez la section ci-dessous sur le jeu d'informations de post-validation de schéma (PSVI).</span><span class="sxs-lookup"><span data-stu-id="0683d-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="0683d-130">Réflexion du type spécifique au langage du schéma : dans d'autres cas, il se peut que vous souhaitiez obtenir d'autres détails sur le type spécifique au schéma appliqué à un document XML.</span><span class="sxs-lookup"><span data-stu-id="0683d-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="0683d-131">Par exemple, lors de la lecture d'un fichier XML; il se peut que vous souhaitiez extraire l'attribut `maxOccurs` pour chaque nœud valide du document XML pour effectuer certains calculs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="0683d-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="0683d-132">Étant donné que ces informations ne sont définies que via la validation de schéma, elles sont accessibles par le biais de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0683d-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="0683d-133">Pour plus d'informations, consultez la section ci-dessous sur le jeu d'informations de post-validation de schéma (PSVI).</span><span class="sxs-lookup"><span data-stu-id="0683d-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="0683d-134">Accesseurs typés XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0683d-134">XPathNavigator Typed Accessors</span></span>  
 <span data-ttu-id="0683d-135">Le tableau suivant illustre les différentes propriétés et méthodes de la classe <xref:System.Xml.XPath.XPathNavigator> pouvant être utilisées pour accéder aux informations sur le type à propos d'un nœud.</span><span class="sxs-lookup"><span data-stu-id="0683d-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="0683d-136">Propriété</span><span class="sxs-lookup"><span data-stu-id="0683d-136">Property</span></span>|<span data-ttu-id="0683d-137">Description</span><span class="sxs-lookup"><span data-stu-id="0683d-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="0683d-138">Contient les informations sur le type de schéma XML pour le nœud s'il est valide.</span><span class="sxs-lookup"><span data-stu-id="0683d-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="0683d-139">Contient le jeu d’informations de post-validation de schéma du nœud ajouté après validation,</span><span class="sxs-lookup"><span data-stu-id="0683d-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="0683d-140">notamment les informations sur le type de schéma XML et sur la validité.</span><span class="sxs-lookup"><span data-stu-id="0683d-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="0683d-141">Type CLR de la valeur typée du nœud.</span><span class="sxs-lookup"><span data-stu-id="0683d-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="0683d-142">Contenu du nœud si au moins une valeur CLR du type correspondant le plus au type de schéma XML du nœud.</span><span class="sxs-lookup"><span data-stu-id="0683d-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="0683d-143">Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.Boolean> conformément aux règles de conversion de XPath 2.0 pour `xs:boolean`.</span><span class="sxs-lookup"><span data-stu-id="0683d-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="0683d-144">Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.DateTime> conformément aux règles de conversion de XPath 2.0 pour `xs:datetime`.</span><span class="sxs-lookup"><span data-stu-id="0683d-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="0683d-145">Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.Double> conformément aux règles de conversion de XPath 2.0 pour `xsd:double`.</span><span class="sxs-lookup"><span data-stu-id="0683d-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="0683d-146">Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.Int32> conformément aux règles de conversion de XPath 2.0 pour `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="0683d-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="0683d-147">Valeur <xref:System.String> du nœud actuel cast en valeur <xref:System.Int64> conformément aux règles de conversion de XPath 2.0 pour `xs:integer`.</span><span class="sxs-lookup"><span data-stu-id="0683d-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="0683d-148">Contenu du nœud cast en type cible conformément aux règles de conversion de XPath 2.0.</span><span class="sxs-lookup"><span data-stu-id="0683d-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="0683d-149">Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0683d-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="0683d-150">Jeu d'informations de post-validation de schéma (PSVI)</span><span class="sxs-lookup"><span data-stu-id="0683d-150">The Post Schema Validation Infoset (PSVI)</span></span>  
 <span data-ttu-id="0683d-151">Un processeur de schéma XML accepte un jeu d'informations XML et le convertit en jeu d'informations de post-validation de schéma (PSVI).</span><span class="sxs-lookup"><span data-stu-id="0683d-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="0683d-152">Un PSVI est le jeu d'informations XML d'entrée original auquel sont ajoutés les nouveaux éléments d'informations et les nouvelles propriétés, elles-mêmes ajoutées aux éléments d'informations existants.</span><span class="sxs-lookup"><span data-stu-id="0683d-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="0683d-153">Trois grandes classes d'informations sont ajoutées au jeu d'informations XML du PSVI exposé par l'objet <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0683d-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="0683d-154">Résultats de validation : informations indiquant si un élément ou un attribut a été correctement validé ou non.</span><span class="sxs-lookup"><span data-stu-id="0683d-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="0683d-155">Ces informations sont exposées par la propriété <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0683d-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="0683d-156">Informations par défaut : indiquent si la valeur de l'élément ou de l'attribut a été obtenue via des valeurs par défaut spécifiées dans le schéma ou non.</span><span class="sxs-lookup"><span data-stu-id="0683d-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="0683d-157">Ces informations sont exposées par la propriété <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0683d-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="0683d-158">Annotations de type : références aux composants de schéma pouvant être des définitions de types ou des déclarations d'élément et d'attribut.</span><span class="sxs-lookup"><span data-stu-id="0683d-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="0683d-159">La propriété <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> de l'objet <xref:System.Xml.XPath.XPathNavigator> contient les informations spécifiques sur le type du nœud s'il est valide.</span><span class="sxs-lookup"><span data-stu-id="0683d-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="0683d-160">Si la validité d'un nœud est inconnue, par exemple s'il a été validé, puis modifié,</span><span class="sxs-lookup"><span data-stu-id="0683d-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="0683d-161">la propriété <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> est définie sur `null`, mais les informations sur le type sont toujours disponibles à partir des différentes propriétés de la propriété <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0683d-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="0683d-162">L’exemple suivant illustre l’utilisation des informations dans le jeu d’informations de post-validation de schéma exposé par l’objet <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0683d-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="0683d-163">L'exemple prend le fichier `books.xml` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="0683d-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="0683d-164">L'exemple prend également le schéma `books.xsd` comme entrée.</span><span class="sxs-lookup"><span data-stu-id="0683d-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="0683d-165">Obtention de valeurs typées à l'aide des propriétés ValueAs</span><span class="sxs-lookup"><span data-stu-id="0683d-165">Obtain Typed Values Using ValueAs Properties</span></span>  
 <span data-ttu-id="0683d-166">Vous pouvez récupérer la valeur typée d'un nœud en accédant à la propriété <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> de l'objet <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="0683d-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="0683d-167">Dans certains cas, il se peut que vous souhaitiez convertir la valeur typée d'un nœud en un type différent.</span><span class="sxs-lookup"><span data-stu-id="0683d-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="0683d-168">Un exemple courant consiste à obtenir une valeur numérique à partir d'un nœud XML.</span><span class="sxs-lookup"><span data-stu-id="0683d-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="0683d-169">Considérez par exemple le document XML non typé et non validé suivant.</span><span class="sxs-lookup"><span data-stu-id="0683d-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="0683d-170">Si l'objet <xref:System.Xml.XPath.XPathNavigator> est positionné sur l'élément `price`, la propriété <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> serait `null`, la propriété <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> serait l'objet <xref:System.String> et la propriété <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> serait la chaîne `10.00`.</span><span class="sxs-lookup"><span data-stu-id="0683d-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="0683d-171">Toutefois, il est toujours possible d'extraire la valeur sous la forme d'une valeur numérique à l'aide des propriétés et de la méthode <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A> ou <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>.</span><span class="sxs-lookup"><span data-stu-id="0683d-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="0683d-172">L'exemple suivant illustre l'exécution de ce type de conversion à l'aide de la méthode <xref:System.Xml.XPath.XPathItem.ValueAs%2A>.</span><span class="sxs-lookup"><span data-stu-id="0683d-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="0683d-173">Pour plus d'informations sur le mappage de types de schéma intégrés à des types CLR, consultez [Prise en charge du type dans les classes System.Xml](type-support-in-the-system-xml-classes.md).</span><span class="sxs-lookup"><span data-stu-id="0683d-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0683d-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0683d-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="0683d-175">Prise en charge du type dans les classes System.Xml</span><span class="sxs-lookup"><span data-stu-id="0683d-175">Type Support in the System.Xml Classes</span></span>](type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="0683d-176">Traitement des données XML à l'aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="0683d-176">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="0683d-177">Navigation dans la collection de nœuds à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0683d-177">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="0683d-178">Navigation entre les nœuds d'attribut et d'espace de noms à l'aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0683d-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="0683d-179">Extraction de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0683d-179">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)
