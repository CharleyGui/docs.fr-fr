---
title: Gestion d'espaces de noms dans un document XML
description: Découvrez comment gérer les espaces de noms dans un document XML. Les espaces de noms XML associent les noms d'éléments et d'attributs dans un document XML à des URI prédéfinis et personnalisés.
ms.date: 03/30/2017
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 120493de430c2372f3f71d1d1498ba880feda3d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720150"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="42efe-104">Gestion d'espaces de noms dans un document XML</span><span class="sxs-lookup"><span data-stu-id="42efe-104">Managing Namespaces in an XML Document</span></span>

<span data-ttu-id="42efe-105">Les espaces de noms XML associent les noms d'éléments et d'attributs dans un document XML à des URI prédéfinis et personnalisés.</span><span class="sxs-lookup"><span data-stu-id="42efe-105">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="42efe-106">Pour créer ces associations, définissez des préfixes pour des URI d'espace de noms et utilisez ces préfixes pour qualifier des noms d'élément et d'attribut dans des données XML.</span><span class="sxs-lookup"><span data-stu-id="42efe-106">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="42efe-107">Les espaces de noms empêchent les conflits entre les noms d'élément et d'attribut et permettent aux éléments et attributs de même nom d'être gérés différemment et validés différemment.</span><span class="sxs-lookup"><span data-stu-id="42efe-107">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>

## <a name="declaring-namespaces"></a><span data-ttu-id="42efe-108">Déclaration d'espaces de noms</span><span class="sxs-lookup"><span data-stu-id="42efe-108">Declaring namespaces</span></span>  

 <span data-ttu-id="42efe-109">Pour déclarer un espace de noms sur un élément, utilisez l'attribut `xmlns:` :</span><span class="sxs-lookup"><span data-stu-id="42efe-109">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="42efe-110">où `<name>` est le préfixe de l'espace de noms et `<"uri">` fait référence à l'URI qui identifie l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="42efe-110">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="42efe-111">Une fois que vous avez déclaré le préfixe, vous pouvez l'utiliser pour qualifier des éléments et des attributs dans un document XML et les associer à un URI d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="42efe-111">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="42efe-112">Le préfixe de l'espace de noms étant utilisé dans la totalité d'un document, il doit être court de préférence.</span><span class="sxs-lookup"><span data-stu-id="42efe-112">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="42efe-113">Cet exemple définit deux éléments `BOOK`.</span><span class="sxs-lookup"><span data-stu-id="42efe-113">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="42efe-114">Le premier élément est qualifié par le préfixe `mybook`, tandis que le deuxième élément est qualifié par le préfixe `bb`.</span><span class="sxs-lookup"><span data-stu-id="42efe-114">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="42efe-115">Chaque préfixe est associé à un URI d'espace de noms différent :</span><span class="sxs-lookup"><span data-stu-id="42efe-115">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="42efe-116">Pour indiquer qu'un élément fait partie d'un espace de noms particulier, ajoutez-lui le préfixe de l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="42efe-116">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="42efe-117">Par exemple, si un élément `Author` appartient à l'espace de noms `mybook`, il est déclaré comme suit : `<mybook:Author>`.</span><span class="sxs-lookup"><span data-stu-id="42efe-117">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>

## <a name="declaration-scope"></a><span data-ttu-id="42efe-118">Portée de la déclaration</span><span class="sxs-lookup"><span data-stu-id="42efe-118">Declaration scope</span></span>  

 <span data-ttu-id="42efe-119">Un espace de noms est effectif à partir de son point de déclaration jusqu'à la fin de l'élément dans lequel il a été déclaré.</span><span class="sxs-lookup"><span data-stu-id="42efe-119">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="42efe-120">Dans cet exemple, l'espace de noms défini dans l'élément `BOOK` ne s'applique pas aux éléments situés en dehors de l'élément `BOOK`, tels que l'élément `Publisher` :</span><span class="sxs-lookup"><span data-stu-id="42efe-120">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="42efe-121">Un espace de noms doit être déclaré avant de pouvoir être utilisé, mais cela ne signifie pas qu'il doit apparaître tout en haut du document XML.</span><span class="sxs-lookup"><span data-stu-id="42efe-121">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="42efe-122">Lorsque vous utilisez plusieurs espaces de noms dans un document XML, vous pouvez définir un espace de noms comme l'espace de noms par défaut afin de créer un document plus clair.</span><span class="sxs-lookup"><span data-stu-id="42efe-122">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="42efe-123">L'espace de noms par défaut est déclaré dans l'élément racine et s'applique à tous les éléments non qualifiés dans le document.</span><span class="sxs-lookup"><span data-stu-id="42efe-123">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="42efe-124">Les espaces de noms par défaut s'appliquent uniquement aux éléments, pas aux attributs.</span><span class="sxs-lookup"><span data-stu-id="42efe-124">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="42efe-125">Pour utiliser l'espace de noms par défaut, omettez le préfixe et le signe deux-points de la déclaration sur l'élément :</span><span class="sxs-lookup"><span data-stu-id="42efe-125">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="42efe-126">Gestion des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="42efe-126">Managing namespaces</span></span>  

 <span data-ttu-id="42efe-127">La classe <xref:System.Xml.XmlNamespaceManager> stocke une collection d’URI d’espace de noms et leurs préfixes, et vous permet de rechercher, d’ajouter et de supprimer des espaces de noms dans cette collection.</span><span class="sxs-lookup"><span data-stu-id="42efe-127">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="42efe-128">Dans certains contextes, cette classe est indispensable pour améliorer les performances de traitement XML.</span><span class="sxs-lookup"><span data-stu-id="42efe-128">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="42efe-129">Par exemple, la classe <xref:System.Xml.Xsl.XsltContext> utilise <xref:System.Xml.XmlNamespaceManager> pour la prise en charge de XPath.</span><span class="sxs-lookup"><span data-stu-id="42efe-129">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="42efe-130">Le gestionnaire d'espaces de noms n'effectue aucune validation sur les espaces de noms, mais part du principe que les préfixes et les espaces de noms ont déjà été vérifiés et qu’ils sont conformes à la spécification du [W3C sur les espaces de noms](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="42efe-130">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42efe-131">LINQ to XML en [C#](../../linq/linq-xml-overview.md) et [Visual Basic](../../linq/linq-xml-overview.md) n’utilisent pas <xref:System.Xml.XmlNamespaceManager> pour gérer les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="42efe-131">LINQ TO XML in [C#](../../linq/linq-xml-overview.md) and [Visual Basic](../../linq/linq-xml-overview.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="42efe-132">Pour des informations sur la gestion des espaces de noms en cas d’utilisation de LINQ to XML, consultez [Utilisation des espaces de noms XML (C#)](../../linq/namespaces-overview.md) et [Utilisation des espaces de noms XML (Visual Basic)](../../linq/namespaces-overview.md) dans la documentation LINQ.</span><span class="sxs-lookup"><span data-stu-id="42efe-132">See [Working with XML Namespaces (C#)](../../linq/namespaces-overview.md) and [Working with XML Namespaces (Visual Basic)](../../linq/namespaces-overview.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="42efe-133">Voici quelques tâches de recherche et de gestion que vous pouvez effectuer avec la classe <xref:System.Xml.XmlNamespaceManager>.</span><span class="sxs-lookup"><span data-stu-id="42efe-133">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="42efe-134">Pour obtenir plus d'informations et des exemples, suivez les liens à la page de référence de chaque méthode ou propriété.</span><span class="sxs-lookup"><span data-stu-id="42efe-134">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="42efe-135">À</span><span class="sxs-lookup"><span data-stu-id="42efe-135">To</span></span>|<span data-ttu-id="42efe-136">Utiliser</span><span class="sxs-lookup"><span data-stu-id="42efe-136">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="42efe-137">Ajouter un espace de noms</span><span class="sxs-lookup"><span data-stu-id="42efe-137">Add a namespace</span></span>|<span data-ttu-id="42efe-138">Méthode <xref:System.Xml.XmlNamespaceManager.AddNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="42efe-139">Supprimer un espace de noms</span><span class="sxs-lookup"><span data-stu-id="42efe-139">Remove a namespace</span></span>|<span data-ttu-id="42efe-140">Méthode <xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="42efe-141">Rechercher l'URI de l'espace de noms par défaut</span><span class="sxs-lookup"><span data-stu-id="42efe-141">Find the URI for the default namespace</span></span>|<span data-ttu-id="42efe-142">Propriété<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="42efe-143">Rechercher l'URI du préfixe d'un espace de noms</span><span class="sxs-lookup"><span data-stu-id="42efe-143">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="42efe-144">Méthode <xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="42efe-145">Rechercher le préfixe de l'URI d'un espace de noms</span><span class="sxs-lookup"><span data-stu-id="42efe-145">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="42efe-146">Méthode <xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="42efe-147">Obtenir une liste des espaces de noms dans le nœud actuel</span><span class="sxs-lookup"><span data-stu-id="42efe-147">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="42efe-148">Méthode <xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="42efe-149">Définir la portée d'un espace de noms</span><span class="sxs-lookup"><span data-stu-id="42efe-149">Scope a namespace</span></span>|<span data-ttu-id="42efe-150">Méthodes <xref:System.Xml.XmlNamespaceManager.PushScope%2A> et <xref:System.Xml.XmlNamespaceManager.PopScope%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="42efe-151">Vérifier si un préfixe est défini dans la portée actuelle</span><span class="sxs-lookup"><span data-stu-id="42efe-151">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="42efe-152">Méthode <xref:System.Xml.XmlNamespaceManager.HasNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="42efe-153">Obtenir la table de noms utilisée pour rechercher les préfixes et les URI</span><span class="sxs-lookup"><span data-stu-id="42efe-153">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="42efe-154">Propriété<xref:System.Xml.XmlNamespaceManager.NameTable%2A></span><span class="sxs-lookup"><span data-stu-id="42efe-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42efe-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42efe-155">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="42efe-156">Documents et données XML</span><span class="sxs-lookup"><span data-stu-id="42efe-156">XML Documents and Data</span></span>](index.md)
