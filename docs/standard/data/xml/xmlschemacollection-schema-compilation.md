---
title: Compilation de schéma XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
ms.openlocfilehash: af6df3729f1bd926e9a47cc5b9d9bf460c8e1225
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159284"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="cdfa8-102">Compilation de schéma XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="cdfa8-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="cdfa8-103">La classe **XmlSchemaCollection** est un cache ou une bibliothèque où des schémas XDR (XML-Data Reduced) et des schémas de langage XSD (XML Schema Definition) peuvent être stockés et validés.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="cdfa8-104">**XmlSchemaCollection** améliore les performances en mettant les schémas en cache au lieu d'y accéder à partir d'un fichier ou d'une URL.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdfa8-105">Bien que la classe **XmlSchemaCollection** contienne à la fois des schémas XDR et des schémas XML, toute méthode ou propriété qui prend ou retourne un objet **XmlSchema** ne prend en charge que les schémas XML.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cdfa8-106">La classe <xref:System.Xml.Schema.XmlSchemaCollection> est désormais obsolète et a été remplacée par la classe <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="cdfa8-107">Pour plus d’informations sur la classe <xref:System.Xml.Schema.XmlSchemaSet>, consultez [XmlSchemaSet pour la compilation de schémas](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="cdfa8-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="cdfa8-108">Ajout de schémas à la collection</span><span class="sxs-lookup"><span data-stu-id="cdfa8-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="cdfa8-109">Les schémas sont chargés dans la collection à l’aide de la méthode **Add** de la collection **XmlSchemaCollection**. C’est à ce moment-là que le schéma est associé à un URI d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="cdfa8-110">Pour les schémas XML, l'URI d'espace de noms correspond généralement à l'espace de noms cible du schéma.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="cdfa8-111">Pour les schémas XDR, l'URI d'espace de noms correspond à l'espace de noms spécifié lors de l'ajout du schéma à la collection.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="cdfa8-112">Recherche d'un schéma dans la collection</span><span class="sxs-lookup"><span data-stu-id="cdfa8-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="cdfa8-113">Vous pouvez vérifier si un schéma se trouve dans la collection à l’aide de la méthode **Contains**.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="cdfa8-114">La méthode **Contains** prend soit un objet **XmlSchema** (schémas XML uniquement), soit une chaîne qui représente l'URI d'espace de noms associé au schéma (schémas XDR et schémas XML).</span><span class="sxs-lookup"><span data-stu-id="cdfa8-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="cdfa8-115">Extraction d'un schéma à partir de la collection</span><span class="sxs-lookup"><span data-stu-id="cdfa8-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="cdfa8-116">Vous pouvez extraire un schéma à partir de la collection à l’aide de la propriété **Item**.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="cdfa8-117">La propriété **Item** prend une chaîne qui représente l'URI d'espace de noms associé au schéma, généralement son espace de noms cible, et retourne un objet **XmlSchema**.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="cdfa8-118">La propriété **Item** s'applique uniquement aux schémas XML.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="cdfa8-119">La valeur de retour est toujours une référence null pour les schémas XDR car ils n'ont pas de modèle objet disponible.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="cdfa8-120">Validation des documents XML à l'aide de XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="cdfa8-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="cdfa8-121">Vous pouvez valider un document d’instance XML à l’aide de **XmlSchemaCollection** en créant l’objet **XmlSchemaCollection**, en ajoutant vos schémas à la collection et en définissant la propriété **Schemas** sur **XmlValidatingReader** pour assigner **XmlSchemaCollection** créé à **XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="cdfa8-122">Performances améliorées</span><span class="sxs-lookup"><span data-stu-id="cdfa8-122">Improved Performance</span></span>  
 <span data-ttu-id="cdfa8-123">Si vous procédez à la validation de plusieurs documents par rapport au même schéma, il est recommandé d'utiliser **XmlSchemaCollection** car elle offre de meilleures performances grâce à la mise en cache des schémas.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="cdfa8-124">L’exemple de code suivant crée l’objet **XmlSchemaCollection**, ajoute des schémas à la collection et définit la propriété **Schemas**.</span><span class="sxs-lookup"><span data-stu-id="cdfa8-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdfa8-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdfa8-125">See also</span></span>

- [<span data-ttu-id="cdfa8-126">Validation XDR avec XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="cdfa8-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)
- [<span data-ttu-id="cdfa8-127">Validation de schéma XML (XSD) avec XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="cdfa8-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
