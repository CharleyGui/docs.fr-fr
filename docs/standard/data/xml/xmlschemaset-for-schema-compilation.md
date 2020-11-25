---
title: XmlSchemaSet pour la compilation de schémas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 4501f3dde8d402bd318332dfe9b2209b3febea71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723361"
---
# <a name="xmlschemaset-for-schema-compilation"></a><span data-ttu-id="fd77e-102">XmlSchemaSet pour la compilation de schémas</span><span class="sxs-lookup"><span data-stu-id="fd77e-102">XmlSchemaSet for Schema Compilation</span></span>

<span data-ttu-id="fd77e-103">Décrit l'objet <xref:System.Xml.Schema.XmlSchemaSet>, un cache où les schémas de langage XSD (XML Schema Definition) peuvent être stockés et validés.</span><span class="sxs-lookup"><span data-stu-id="fd77e-103">Describes the <xref:System.Xml.Schema.XmlSchemaSet>, a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
## <a name="the-xmlschemaset-class"></a><span data-ttu-id="fd77e-104">Classe XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="fd77e-104">The XmlSchemaSet Class</span></span>  

 <span data-ttu-id="fd77e-105">L'objet <xref:System.Xml.Schema.XmlSchemaSet> est un cache où les schémas de langage XSD (XML Schema Definition) peuvent être stockés et validés.</span><span class="sxs-lookup"><span data-stu-id="fd77e-105">The <xref:System.Xml.Schema.XmlSchemaSet> is a cache where XML Schema definition language (XSD) schemas can be stored and validated.</span></span>  
  
 <span data-ttu-id="fd77e-106">Dans <xref:System.Xml?displayProperty=nameWithType> version 1.0, les schémas XML ont été chargés dans une classe <xref:System.Xml.Schema.XmlSchemaCollection> sous la forme d'une bibliothèque de schémas.</span><span class="sxs-lookup"><span data-stu-id="fd77e-106">In <xref:System.Xml?displayProperty=nameWithType> version 1.0, XML schemas were loaded into an <xref:System.Xml.Schema.XmlSchemaCollection> class as a library of schemas.</span></span> <span data-ttu-id="fd77e-107">Dans <xref:System.Xml?displayProperty=nameWithType> version 2.0, les classes <xref:System.Xml.XmlValidatingReader> et <xref:System.Xml.Schema.XmlSchemaCollection> sont obsolètes et ont été respectivement remplacées par les méthodes <xref:System.Xml.XmlReader.Create%2A> et la classe <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-107">In <xref:System.Xml?displayProperty=nameWithType> version 2.0, the <xref:System.Xml.XmlValidatingReader> and the <xref:System.Xml.Schema.XmlSchemaCollection> classes are obsolete, and have been replaced by the <xref:System.Xml.XmlReader.Create%2A> methods, and the <xref:System.Xml.Schema.XmlSchemaSet> class respectively.</span></span>  
  
 <span data-ttu-id="fd77e-108"><xref:System.Xml.Schema.XmlSchemaSet> a été introduit pour résoudre un certain nombre de problèmes, notamment la compatibilité aux normes, les performances et le format de schéma XDR (XML-Data Reduced) obsolète de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fd77e-108">The <xref:System.Xml.Schema.XmlSchemaSet> has been introduced to fix a number of issues including standards compatibility, performance, and the obsolete Microsoft XML-Data Reduced (XDR) schema format.</span></span>  
  
 <span data-ttu-id="fd77e-109">Voici une comparaison entre la classe <xref:System.Xml.Schema.XmlSchemaCollection> et la classe <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-109">The following is a comparison between the <xref:System.Xml.Schema.XmlSchemaCollection> class and the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span>  
  
|<span data-ttu-id="fd77e-110">XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="fd77e-110">XmlSchemaCollection</span></span>|<span data-ttu-id="fd77e-111">XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="fd77e-111">XmlSchemaSet</span></span>|  
|-------------------------|------------------|  
|<span data-ttu-id="fd77e-112">Prend en charge les schémas XML du W3C et XDR de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fd77e-112">Supports Microsoft XDR and W3C XML schemas.</span></span>|<span data-ttu-id="fd77e-113">Ne prend en charge que les schémas XML du W3C.</span><span class="sxs-lookup"><span data-stu-id="fd77e-113">Only supports W3C XML schemas.</span></span>|  
|<span data-ttu-id="fd77e-114">Les schémas sont compilés lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-114">Schemas are compiled when the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method is called.</span></span>|<span data-ttu-id="fd77e-115">Les schémas ne sont pas compilés lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-115">Schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span> <span data-ttu-id="fd77e-116">Les performances sont ainsi améliorées lors de la création de la bibliothèque de schémas.</span><span class="sxs-lookup"><span data-stu-id="fd77e-116">This provides a performance improvement during creation of the schema library.</span></span>|  
|<span data-ttu-id="fd77e-117">Chaque schéma génère une version compilée individuelle pouvant se traduire par des « îlots de schémas ».</span><span class="sxs-lookup"><span data-stu-id="fd77e-117">Each schema generates an individual compiled version that can result in "schema islands."</span></span> <span data-ttu-id="fd77e-118">Par conséquent, toutes les inclusions et importations se trouvent dans la portée de ce schéma uniquement.</span><span class="sxs-lookup"><span data-stu-id="fd77e-118">As a result, all includes and imports are scoped only within that schema.</span></span>|<span data-ttu-id="fd77e-119">Les schémas compilés génèrent un seul schéma logique, un « ensemble » de schémas.</span><span class="sxs-lookup"><span data-stu-id="fd77e-119">Compiled schemas generate a single logical schema, a "set" of schemas.</span></span> <span data-ttu-id="fd77e-120">Tous les schémas importés dans un schéma qui est ajouté à l'ensemble sont également directement ajoutés à l'ensemble.</span><span class="sxs-lookup"><span data-stu-id="fd77e-120">Any imported schemas within a schema that are added to the set are directly added to the set themselves.</span></span> <span data-ttu-id="fd77e-121">Tous les types sont donc disponibles pour tous les schémas.</span><span class="sxs-lookup"><span data-stu-id="fd77e-121">This means that all types are available to all schemas.</span></span>|  
|<span data-ttu-id="fd77e-122">Un seul schéma peut exister dans la collection pour un espace de noms cible particulier.</span><span class="sxs-lookup"><span data-stu-id="fd77e-122">Only one schema for a particular target namespace can exist in the collection.</span></span>|<span data-ttu-id="fd77e-123">Plusieurs schémas peuvent être ajoutés pour le même espace de noms cible tant qu'aucun conflit de type ne survient.</span><span class="sxs-lookup"><span data-stu-id="fd77e-123">Multiple schemas for the same target namespace can be added as long as there are no type conflicts.</span></span>|  
  
## <a name="migrating-to-the-xmlschemaset"></a><span data-ttu-id="fd77e-124">Migration vers XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="fd77e-124">Migrating to the XmlSchemaSet</span></span>  

 <span data-ttu-id="fd77e-125">L'exemple de code suivant fournit un guide pour la migration vers la nouvelle classe <xref:System.Xml.Schema.XmlSchemaSet> à partir de la classe <xref:System.Xml.Schema.XmlSchemaCollection> obsolète.</span><span class="sxs-lookup"><span data-stu-id="fd77e-125">The following code example provides a guide to migrating to the new <xref:System.Xml.Schema.XmlSchemaSet> class from the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class.</span></span> <span data-ttu-id="fd77e-126">L'exemple de code illustre les principales différences suivantes entre les deux classes.</span><span class="sxs-lookup"><span data-stu-id="fd77e-126">The code example illustrates the following major differences between the two classes.</span></span>  
  
- <span data-ttu-id="fd77e-127">Contrairement à la méthode <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> de la classe <xref:System.Xml.Schema.XmlSchemaCollection>, les schémas ne sont pas compilés lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-127">Unlike the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when calling the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-128">La méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> est explicitement appelée dans l'exemple de code.</span><span class="sxs-lookup"><span data-stu-id="fd77e-128">The <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is explicitly called in the example code.</span></span>  
  
- <span data-ttu-id="fd77e-129">Pour itérer sur un objet <xref:System.Xml.Schema.XmlSchemaSet>, vous devez utiliser la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-129">To iterate over an <xref:System.Xml.Schema.XmlSchemaSet>, you must use the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="fd77e-130">Voici un exemple de code <xref:System.Xml.Schema.XmlSchemaCollection> obsolète.</span><span class="sxs-lookup"><span data-stu-id="fd77e-130">The following is the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> code example.</span></span>  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 <span data-ttu-id="fd77e-131">Voici un exemple de code <xref:System.Xml.Schema.XmlSchemaSet> équivalent.</span><span class="sxs-lookup"><span data-stu-id="fd77e-131">The following is the equivalent <xref:System.Xml.Schema.XmlSchemaSet> code example.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a><span data-ttu-id="fd77e-132">Ajout et récupération de schémas</span><span class="sxs-lookup"><span data-stu-id="fd77e-132">Adding and Retrieving Schemas</span></span>  

 <span data-ttu-id="fd77e-133">Les schémas sont ajoutés à un objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-133">Schemas are added to an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-134">Lorsqu'un schéma est ajouté à un objet <xref:System.Xml.Schema.XmlSchemaSet>, il est associé à un URI d'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="fd77e-134">When a schema is added to an <xref:System.Xml.Schema.XmlSchemaSet>, it is associated with a target namespace URI.</span></span> <span data-ttu-id="fd77e-135">L'URI d'espace de noms cible peut être spécifié sous la forme d'un paramètre pour la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> ou si aucun espace de noms cible n'est spécifié, l'objet <xref:System.Xml.Schema.XmlSchemaSet> utilise l'espace de noms cible défini dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="fd77e-135">The target namespace URI can either be specified as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method or if no target namespace is specified, the <xref:System.Xml.Schema.XmlSchemaSet> uses the target namespace defined in the schema.</span></span>  
  
 <span data-ttu-id="fd77e-136">Les schémas sont récupérés à partir d'un objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide de la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-136">Schemas are retrieved from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-137">La propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> permet d'itérer sur les objets <xref:System.Xml.Schema.XmlSchema> contenus dans l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-137">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> allows you to iterate over the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-138">La propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> retourne tous les objets <xref:System.Xml.Schema.XmlSchema> contenus dans l'objet <xref:System.Xml.Schema.XmlSchemaSet> ou, en cas de fourniture d'un paramètre d'espace de noms cible, tous les objets <xref:System.Xml.Schema.XmlSchema> qui appartiennent à l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="fd77e-138">The <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property either returns all the <xref:System.Xml.Schema.XmlSchema> objects contained in the <xref:System.Xml.Schema.XmlSchemaSet>, or, given a target namespace parameter, returns all the <xref:System.Xml.Schema.XmlSchema> objects that belong to the target namespace.</span></span> <span data-ttu-id="fd77e-139">Si `null` est spécifié comme paramètre d'espace de noms cible, la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> retourne tous les schémas sans espace de noms.</span><span class="sxs-lookup"><span data-stu-id="fd77e-139">If `null` is specified as the target namespace parameter, the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property returns all schemas without a namespace.</span></span>  
  
 <span data-ttu-id="fd77e-140">L'exemple suivant ajoute le schéma `books.xsd` de l'espace de noms `http://www.contoso.com/books` à un objet <xref:System.Xml.Schema.XmlSchemaSet>, récupère tous les schémas qui appartiennent à l'espace de noms `http://www.contoso.com/books` à partir de l'objet <xref:System.Xml.Schema.XmlSchemaSet>, puis écrit ces schémas dans l'objet <xref:System.Console></span><span class="sxs-lookup"><span data-stu-id="fd77e-140">The following example adds the `books.xsd` schema in the `http://www.contoso.com/books` namespace to an <xref:System.Xml.Schema.XmlSchemaSet>, retrieves all schemas that belong to the `http://www.contoso.com/books` namespace from the <xref:System.Xml.Schema.XmlSchemaSet>, and then writes those schemas to the <xref:System.Console>.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 <span data-ttu-id="fd77e-141">Pour plus d'informations sur l'ajout et la récupération de schémas à partir d'un objet <xref:System.Xml.Schema.XmlSchemaSet>, voir la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> et la documentation de référence sur la propriété <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-141">For more information about adding and retrieving schemas from an <xref:System.Xml.Schema.XmlSchemaSet> object, see the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method and the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property reference documentation.</span></span>  
  
## <a name="compiling-schemas"></a><span data-ttu-id="fd77e-142">Compilation de schémas</span><span class="sxs-lookup"><span data-stu-id="fd77e-142">Compiling Schemas</span></span>  

 <span data-ttu-id="fd77e-143">Les schémas d'un objet <xref:System.Xml.Schema.XmlSchemaSet> sont compilés en un seul schéma logique par la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-143">Schemas in an <xref:System.Xml.Schema.XmlSchemaSet> are compiled into one logical schema by the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd77e-144">Contrairement à la classe <xref:System.Xml.Schema.XmlSchemaCollection> obsolète, les schémas ne sont pas compilés lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-144">Unlike the obsolete <xref:System.Xml.Schema.XmlSchemaCollection> class, schemas are not compiled when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method is called.</span></span>  
  
 <span data-ttu-id="fd77e-145">Si la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> s'exécute correctement, la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> est définie sur `true`.</span><span class="sxs-lookup"><span data-stu-id="fd77e-145">If the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method executes successfully, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd77e-146">La propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> n'est pas affectée si les schémas sont modifiés dans l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-146">The <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is not affected if schemas are edited while in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-147">Le suivi des mises à jour des schémas individuels dans l'objet <xref:System.Xml.Schema.XmlSchemaSet> n'est pas assuré.</span><span class="sxs-lookup"><span data-stu-id="fd77e-147">Updates of the individual schemas in the <xref:System.Xml.Schema.XmlSchemaSet> are not tracked.</span></span> <span data-ttu-id="fd77e-148">Par conséquent, la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> peut être `true`, même si l'un des schémas contenus dans l'objet <xref:System.Xml.Schema.XmlSchemaSet> a été modifié, pour autant qu'aucun schéma n'a été ajouté ou supprimé de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-148">As a result, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property can be `true` even though one of the schemas contained in the <xref:System.Xml.Schema.XmlSchemaSet> has been altered, as long as no schemas were added or removed from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="fd77e-149">L'exemple suivant ajoute le fichier `books.xsd` à l'objet <xref:System.Xml.Schema.XmlSchemaSet>, puis appelle la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-149">The following example adds the `books.xsd` file to the <xref:System.Xml.Schema.XmlSchemaSet> and then calls the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 <span data-ttu-id="fd77e-150">Pour plus d'informations sur la compilation de schémas dans un objet <xref:System.Xml.Schema.XmlSchemaSet>, voir la documentation de référence sur la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-150">For more information about compiling schemas in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method reference documentation.</span></span>  
  
## <a name="reprocessing-schemas"></a><span data-ttu-id="fd77e-151">Nouveau traitement des schémas</span><span class="sxs-lookup"><span data-stu-id="fd77e-151">Reprocessing Schemas</span></span>  

 <span data-ttu-id="fd77e-152">Un nouveau traitement d'un schéma dans un objet <xref:System.Xml.Schema.XmlSchemaSet> effectue toutes les étapes de prétraitement sur un schéma lors d'un appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-152">Reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet> performs all the preprocessing steps performed on a schema when the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span> <span data-ttu-id="fd77e-153">Si l'appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> réussit, la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> est définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="fd77e-153">If the call to the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method is successful, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> is set to `false`.</span></span>  
  
 <span data-ttu-id="fd77e-154">La méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> doit être utilisée lorsqu'un schéma de l'objet <xref:System.Xml.Schema.XmlSchemaSet> a été modifié après l'exécution de la compilation par l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-154">The <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method should be used when a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified after the <xref:System.Xml.Schema.XmlSchemaSet> has performed compilation.</span></span>  
  
 <span data-ttu-id="fd77e-155">L'exemple suivant illustre le nouveau traitement d'un schéma ajouté à l'objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-155">The following example illustrates reprocessing a schema added to the <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method.</span></span> <span data-ttu-id="fd77e-156">Après la compilation de l'objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide de la méthode <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> et la modification du schéma ajouté à l'objet <xref:System.Xml.Schema.XmlSchemaSet>, la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> est définie sur `true`, même si un schéma de l'objet <xref:System.Xml.Schema.XmlSchemaSet> a été modifié.</span><span class="sxs-lookup"><span data-stu-id="fd77e-156">After the <xref:System.Xml.Schema.XmlSchemaSet> is compiled using the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method, and the schema added to the <xref:System.Xml.Schema.XmlSchemaSet> is modified, the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property is set to `true` even though a schema in the <xref:System.Xml.Schema.XmlSchemaSet> has been modified.</span></span> <span data-ttu-id="fd77e-157">L'appel à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> exécute l'ensemble du prétraitement effectué par la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> et définit la propriété <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> sur `false`.</span><span class="sxs-lookup"><span data-stu-id="fd77e-157">Calling the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method performs all the preprocessing performed by the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method, and sets the <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> property to `false`.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 <span data-ttu-id="fd77e-158">Pour plus d'informations sur un nouveau traitement de schémas dans un objet <xref:System.Xml.Schema.XmlSchemaSet>, voir la documentation de référence sur la méthode <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-158">For more information about reprocessing a schema in an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> method reference documentation.</span></span>  
  
## <a name="checking-for-a-schema"></a><span data-ttu-id="fd77e-159">Recherche d'un schéma</span><span class="sxs-lookup"><span data-stu-id="fd77e-159">Checking for a Schema</span></span>  

 <span data-ttu-id="fd77e-160">La méthode <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet> peut permettre de vérifier la présence d'un schéma dans un objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-160">You can use the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> to check if a schema is contained within an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-161">La méthode <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> prend un espace de noms cible ou un objet <xref:System.Xml.Schema.XmlSchema> à rechercher.</span><span class="sxs-lookup"><span data-stu-id="fd77e-161">The <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method takes either a target namespace or an <xref:System.Xml.Schema.XmlSchema> object to check for.</span></span> <span data-ttu-id="fd77e-162">Dans les deux cas, la méthode <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> retourne `true` si le schéma est contenu dans l'objet <xref:System.Xml.Schema.XmlSchemaSet> ; sinon, elle retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="fd77e-162">In either case, the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method returns `true` if the schema is contained within the <xref:System.Xml.Schema.XmlSchemaSet>; otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="fd77e-163">Pour plus d'informations sur la recherche d'un schéma, voir la documentation de référence sur la méthode <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-163">For more information about checking for a schema, see the <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> method reference documentation.</span></span>  
  
## <a name="removing-schemas"></a><span data-ttu-id="fd77e-164">Suppression de schémas</span><span class="sxs-lookup"><span data-stu-id="fd77e-164">Removing Schemas</span></span>  

 <span data-ttu-id="fd77e-165">Les schémas sont supprimés d'un objet <xref:System.Xml.Schema.XmlSchemaSet> à l'aide des méthodes <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> et <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-165">Schemas are removed from an <xref:System.Xml.Schema.XmlSchemaSet> using the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-166">La méthode <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> supprime le schéma spécifié de l'objet <xref:System.Xml.Schema.XmlSchemaSet>, tandis que la méthode <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> supprime le schéma spécifié et tous les schémas importés à partir de l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-166">The <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> method removes the specified schema from the <xref:System.Xml.Schema.XmlSchemaSet>, while the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method removes the specified schema and all the schemas it imports from the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="fd77e-167">L'exemple suivant illustre l'ajout de plusieurs schémas à un objet <xref:System.Xml.Schema.XmlSchemaSet>, puis l'utilisation de la méthode <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> pour supprimer l'un des schémas et tous les schémas importés.</span><span class="sxs-lookup"><span data-stu-id="fd77e-167">The following example illustrates adding multiple schemas to an <xref:System.Xml.Schema.XmlSchemaSet>, then using the <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> method to remove one of the schemas and all the schemas it imports.</span></span>  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 <span data-ttu-id="fd77e-168">Pour plus d'informations sur la suppression de schémas d'un objet <xref:System.Xml.Schema.XmlSchemaSet>, voir la documentation de référence sur les méthodes <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> et <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-168">For more information about removing schemas from an <xref:System.Xml.Schema.XmlSchemaSet>, see the <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> and <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> methods reference documentation.</span></span>  
  
## <a name="schema-resolution-and-xsimport"></a><span data-ttu-id="fd77e-169">Résolution de schémas et xs:import</span><span class="sxs-lookup"><span data-stu-id="fd77e-169">Schema Resolution and xs:import</span></span>  

 <span data-ttu-id="fd77e-170">Les exemples suivants décrivent le comportement <xref:System.Xml.Schema.XmlSchemaSet> pour l'importation de schémas lorsque plusieurs schémas existent dans un objet <xref:System.Xml.Schema.XmlSchemaSet> pour un espace de noms donné.</span><span class="sxs-lookup"><span data-stu-id="fd77e-170">The following examples describe the <xref:System.Xml.Schema.XmlSchemaSet> behavior for importing schemas when multiple schemas for a given namespace exist in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
 <span data-ttu-id="fd77e-171">Supposez par exemple qu'un objet <xref:System.Xml.Schema.XmlSchemaSet> contienne plusieurs schémas pour l'espace de noms `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="fd77e-171">For example, consider an <xref:System.Xml.Schema.XmlSchemaSet> that contains multiple schemas for the `http://www.contoso.com` namespace.</span></span> <span data-ttu-id="fd77e-172">Un schéma présentant la directive `xs:import` est ajouté à l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-172">A schema with the following `xs:import` directive is added to the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <span data-ttu-id="fd77e-173">L'objet <xref:System.Xml.Schema.XmlSchemaSet> tente d'importer un schéma pour l'espace de noms `http://www.contoso.com` en le chargeant à partir de l'URL `http://www.contoso.com/schema.xsd`.</span><span class="sxs-lookup"><span data-stu-id="fd77e-173">The <xref:System.Xml.Schema.XmlSchemaSet> attempts to import a schema for the `http://www.contoso.com` namespace by loading it from the `http://www.contoso.com/schema.xsd` URL.</span></span> <span data-ttu-id="fd77e-174">Seuls la déclaration de schéma et les types déclarés dans le document de schéma sont disponibles dans le schéma d'importation, même si d'autres documents de schéma existent pour l'espace de noms `http://www.contoso.com` dans l'objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-174">Only the schema declaration and types declared in the schema document are available in the importing schema, even though there are other schema documents for the `http://www.contoso.com` namespace in the <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-175">Si le fichier `schema.xsd` est introuvable à l'URL `http://www.contoso.com/schema.xsd`, aucun schéma n'est importé dans le schéma d'importation pour l'espace de noms `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="fd77e-175">If the `schema.xsd` file cannot be located at the `http://www.contoso.com/schema.xsd` URL, no schema for the `http://www.contoso.com` namespace is imported into the importing schema.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="fd77e-176">Validation de documents XML</span><span class="sxs-lookup"><span data-stu-id="fd77e-176">Validating XML Documents</span></span>  

 <span data-ttu-id="fd77e-177">Les document XML peuvent être validés par rapport à des schémas dans un objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-177">XML documents can be validated against schemas in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="fd77e-178">Pour valider un document XML, ajoutez un schéma à la propriété <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> d'un objet <xref:System.Xml.XmlReaderSettings>, ou ajoutez un objet <xref:System.Xml.Schema.XmlSchemaSet> à la propriété <xref:System.Xml.XmlReaderSettings.Schemas%2A> d'un objet <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="fd77e-178">You validate an XML document by adding a schema to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object, or by adding an <xref:System.Xml.Schema.XmlSchemaSet> to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of an <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="fd77e-179">L'objet <xref:System.Xml.XmlReaderSettings> est ensuite utilisé par la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader> pour créer un objet <xref:System.Xml.XmlReader> et valider le document XML.</span><span class="sxs-lookup"><span data-stu-id="fd77e-179">The <xref:System.Xml.XmlReaderSettings> object is then used by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to create an <xref:System.Xml.XmlReader> object and validate the XML document.</span></span>  
  
 <span data-ttu-id="fd77e-180">Pour plus d’informations sur la validation de documents XML à l’aide d’un <xref:System.Xml.Schema.XmlSchemaSet>, consultez [Validation de schéma XML (XSD) avec XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md).</span><span class="sxs-lookup"><span data-stu-id="fd77e-180">For more information about validating XML documents using an <xref:System.Xml.Schema.XmlSchemaSet>, see [XML Schema (XSD) Validation with XmlSchemaSet](xml-schema-xsd-validation-with-xmlschemaset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd77e-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd77e-181">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [<span data-ttu-id="fd77e-182">XmlSchemaSet en tant que cache de schéma</span><span class="sxs-lookup"><span data-stu-id="fd77e-182">XmlSchemaSet as a Schema Cache</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="fd77e-183">Validation de schéma XML (XSD) avec XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="fd77e-183">XML Schema (XSD) Validation with XmlSchemaSet</span></span>](xml-schema-xsd-validation-with-xmlschemaset.md)
