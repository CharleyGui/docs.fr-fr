---
title: Écriture de feuilles de style XSLT avec msxsl:script>
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: aef2471a375469f7cd4dff27084b305ef9394d5e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291966"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="01e86-102">Écriture de scripts de feuille de style XSLT à l’aide de\<msxsl:script></span><span class="sxs-lookup"><span data-stu-id="01e86-102">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>
<span data-ttu-id="01e86-103">La classe <xref:System.Xml.Xsl.XslTransform> prend en charge les scripts incorporés en utilisant l'élément `script`.</span><span class="sxs-lookup"><span data-stu-id="01e86-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01e86-104">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="01e86-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="01e86-105">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="01e86-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="01e86-106">Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="01e86-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="01e86-107">La classe <xref:System.Xml.Xsl.XslTransform> prend en charge les scripts incorporés en utilisant l'élément `script`.</span><span class="sxs-lookup"><span data-stu-id="01e86-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="01e86-108">Lorsque la feuille de style est chargée, toute fonction définie est compilée en langage MSIL (Microsoft Intermediate Language) par son enveloppement dans une définition de classe et n'engendre aucune perte des performances.</span><span class="sxs-lookup"><span data-stu-id="01e86-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="01e86-109">L'élément `<msxsl:script>` est défini ci-après :</span><span class="sxs-lookup"><span data-stu-id="01e86-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="01e86-110">où `msxsl` est un préfixe lié à l'espace de noms `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="01e86-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="01e86-111">L' `language` attribut n’est pas obligatoire, mais s’il est spécifié, sa valeur doit être l’une des suivantes : `C#` , `VB` , `JScript` ,, `JavaScript` `VisualBasic` ou `CSharp` .</span><span class="sxs-lookup"><span data-stu-id="01e86-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="01e86-112">Lorsqu'il n'est pas spécifié, le langage par défaut est JScript.</span><span class="sxs-lookup"><span data-stu-id="01e86-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="01e86-113">Le `language-name` ne respecte pas la casse : les termes « JavaScript » et « javascript » sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="01e86-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="01e86-114">L'attribut `implements-prefix` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="01e86-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="01e86-115">Cet attribut est utilisé pour déclarer un espace de noms et l'associer au bloc de script.</span><span class="sxs-lookup"><span data-stu-id="01e86-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="01e86-116">La valeur de cet attribut est le préfixe qui représente l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="01e86-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="01e86-117">Cet espace de noms peut être défini à un endroit d'une feuille de style.</span><span class="sxs-lookup"><span data-stu-id="01e86-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="01e86-118">Dans la mesure où l'élément `msxsl:script` appartient à l'espace de noms `urn:schemas-microsoft-com:xslt`, la feuille de style doit inclure la déclaration d'espaces de noms `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="01e86-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="01e86-119">Si l'appelant du script ne possède pas l'autorisation d'accès <xref:System.Security.Permissions.SecurityPermissionFlag>, le script présent dans une feuille de style ne se compilera jamais et l'appel à <xref:System.Xml.Xsl.XslTransform.Load%2A> échouera.</span><span class="sxs-lookup"><span data-stu-id="01e86-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="01e86-120">Si l'appelant possède une autorisation `UnmanagedCode`, le script se compile, mais les opérations autorisées sont dépendantes des preuves fournies au moment du chargement.</span><span class="sxs-lookup"><span data-stu-id="01e86-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="01e86-121">Si vous utilisez l'une des méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> qui prennent un objet <xref:System.Xml.XmlReader> ou un objet <xref:System.Xml.XPath.XPathNavigator> pour charger la feuille de style, vous devez utiliser la surcharge <xref:System.Xml.Xsl.XslTransform.Load%2A> qui prend un paramètre <xref:System.Security.Policy.Evidence>.</span><span class="sxs-lookup"><span data-stu-id="01e86-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="01e86-122">Pour fournir des preuves, l'appelant doit avoir l'autorisation <xref:System.Security.Permissions.SecurityPermissionFlag> pour fournir `Evidence` à l'assembly du script.</span><span class="sxs-lookup"><span data-stu-id="01e86-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="01e86-123">Si l'appelant n'a pas cette autorisation, il peut attribuer la valeur `Evidence` au paramètre `null`.</span><span class="sxs-lookup"><span data-stu-id="01e86-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="01e86-124">Cela entraîne l'échec de la fonction <xref:System.Xml.Xsl.XslTransform.Load%2A> si le script n'est pas trouvé.</span><span class="sxs-lookup"><span data-stu-id="01e86-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="01e86-125">L'autorisation `ControlEvidence` est considérée comme une autorisation très puissante qui ne doit être accordée qu'au code d'un niveau de confiance élevé.</span><span class="sxs-lookup"><span data-stu-id="01e86-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="01e86-126">Pour obtenir la preuve de votre assembly, utilisez `this.GetType().Assembly.Evidence`.</span><span class="sxs-lookup"><span data-stu-id="01e86-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="01e86-127">Pour obtenir la preuve d'un URI (Uniform Resource Identifier), utilisez `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span><span class="sxs-lookup"><span data-stu-id="01e86-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="01e86-128">Si vous utilisez les méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> qui prennent un objet <xref:System.Xml.XmlResolver> mais aucun `Evidence`, la zone de sécurité pour l'assembly prend la valeur Confiance totale par défaut.</span><span class="sxs-lookup"><span data-stu-id="01e86-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="01e86-129">Pour plus d'informations, consultez les pages <xref:System.Security.SecurityZone> et [Ensemble d'autorisations nommés](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="01e86-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="01e86-130">Les fonctions peuvent être déclarées dans l'élément `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="01e86-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="01e86-131">Le tableau suivant montre les espaces de noms qui sont pris en charge par défaut.</span><span class="sxs-lookup"><span data-stu-id="01e86-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="01e86-132">Vous pouvez utiliser des classes en dehors des espaces de noms répertoriés.</span><span class="sxs-lookup"><span data-stu-id="01e86-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="01e86-133">Toutefois, ces classes doivent être qualifiées complètes.</span><span class="sxs-lookup"><span data-stu-id="01e86-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="01e86-134">Espaces de noms par défaut</span><span class="sxs-lookup"><span data-stu-id="01e86-134">Default Namespaces</span></span>|<span data-ttu-id="01e86-135">Description</span><span class="sxs-lookup"><span data-stu-id="01e86-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="01e86-136">System</span><span class="sxs-lookup"><span data-stu-id="01e86-136">System</span></span>|<span data-ttu-id="01e86-137">Classe système.</span><span class="sxs-lookup"><span data-stu-id="01e86-137">System class.</span></span>|  
|<span data-ttu-id="01e86-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="01e86-138">System.Collection</span></span>|<span data-ttu-id="01e86-139">Classes de collection.</span><span class="sxs-lookup"><span data-stu-id="01e86-139">Collection classes.</span></span>|  
|<span data-ttu-id="01e86-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="01e86-140">System.Text</span></span>|<span data-ttu-id="01e86-141">Classes de texte.</span><span class="sxs-lookup"><span data-stu-id="01e86-141">Text classes.</span></span>|  
|<span data-ttu-id="01e86-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="01e86-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="01e86-143">Classes d'expressions régulières.</span><span class="sxs-lookup"><span data-stu-id="01e86-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="01e86-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="01e86-144">System.Xml</span></span>|<span data-ttu-id="01e86-145">Classes XML principales.</span><span class="sxs-lookup"><span data-stu-id="01e86-145">Core XML classes.</span></span>|  
|<span data-ttu-id="01e86-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="01e86-146">System.Xml.Xsl</span></span>|<span data-ttu-id="01e86-147">Classes XSLT.</span><span class="sxs-lookup"><span data-stu-id="01e86-147">XSLT classes.</span></span>|  
|<span data-ttu-id="01e86-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="01e86-148">System.Xml.XPath</span></span>|<span data-ttu-id="01e86-149">Classes XML Path Language (XPath).</span><span class="sxs-lookup"><span data-stu-id="01e86-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="01e86-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="01e86-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="01e86-151">Classes pour les scripts Microsoft Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01e86-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="01e86-152">Lorsqu'une fonction est déclarée, elle est contenue dans un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="01e86-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="01e86-153">Les feuilles de style peuvent contenir plusieurs blocs de scripts, chacun fonctionnant indépendamment des autres.</span><span class="sxs-lookup"><span data-stu-id="01e86-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="01e86-154">Ainsi, si vous êtes en cours d'exécution dans un bloc de script, vous ne pouvez pas appeler une fonction que vous avez définie dans un autre bloc de script, sauf si elle est déclarée comme possédant le même espace de noms et le même langage de script.</span><span class="sxs-lookup"><span data-stu-id="01e86-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="01e86-155">Puisque chaque bloc de script peut être écrit dans son propre langage et que le bloc est analysé en fonction des règles grammaticales de cet analyseur de langage, vous devez utiliser la syntaxe correcte pour la langue utilisée.</span><span class="sxs-lookup"><span data-stu-id="01e86-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="01e86-156">Par exemple, il n'est pas correct d'utiliser un nœud de commentaire XML `<!-- an XML comment -->` dans un bloc de script C#.</span><span class="sxs-lookup"><span data-stu-id="01e86-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="01e86-157">Les arguments fournis et les valeurs de retour définies par les fonctions du script doivent être l'un des types définis par le World Wide Web Consortium (W3C), XPath ou XSLT.</span><span class="sxs-lookup"><span data-stu-id="01e86-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="01e86-158">Le tableau suivant illustre les types W3C correspondants, les classes .NET Framework équivalentes (Type), et précise si le type W3C est un XPath ou XSLT.</span><span class="sxs-lookup"><span data-stu-id="01e86-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="01e86-159">Type</span><span class="sxs-lookup"><span data-stu-id="01e86-159">Type</span></span>|<span data-ttu-id="01e86-160">Classe .NET Framework équivalente (Type)</span><span class="sxs-lookup"><span data-stu-id="01e86-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="01e86-161">Type XPath ou type XSLT</span><span class="sxs-lookup"><span data-stu-id="01e86-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="01e86-162">String</span><span class="sxs-lookup"><span data-stu-id="01e86-162">String</span></span>|<span data-ttu-id="01e86-163">System.String</span><span class="sxs-lookup"><span data-stu-id="01e86-163">System.String</span></span>|<span data-ttu-id="01e86-164">XPath</span><span class="sxs-lookup"><span data-stu-id="01e86-164">XPath</span></span>|  
|<span data-ttu-id="01e86-165">Boolean</span><span class="sxs-lookup"><span data-stu-id="01e86-165">Boolean</span></span>|<span data-ttu-id="01e86-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="01e86-166">System.Boolean</span></span>|<span data-ttu-id="01e86-167">XPath</span><span class="sxs-lookup"><span data-stu-id="01e86-167">XPath</span></span>|  
|<span data-ttu-id="01e86-168">Number</span><span class="sxs-lookup"><span data-stu-id="01e86-168">Number</span></span>|<span data-ttu-id="01e86-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="01e86-169">System.Double</span></span>|<span data-ttu-id="01e86-170">XPath</span><span class="sxs-lookup"><span data-stu-id="01e86-170">XPath</span></span>|  
|<span data-ttu-id="01e86-171">Fragment d’arborescence résultat</span><span class="sxs-lookup"><span data-stu-id="01e86-171">Result Tree Fragment</span></span>|<span data-ttu-id="01e86-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="01e86-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="01e86-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="01e86-173">XSLT</span></span>|  
|<span data-ttu-id="01e86-174">Collection de nœuds</span><span class="sxs-lookup"><span data-stu-id="01e86-174">Node Set</span></span>|<span data-ttu-id="01e86-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="01e86-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="01e86-176">XPath</span><span class="sxs-lookup"><span data-stu-id="01e86-176">XPath</span></span>|  
  
 <span data-ttu-id="01e86-177">Si la fonction de script utilise l’un des types numériques suivants : Int16, UInt16, Int32, UInt32, Int64, UInt64, Single ou Decimal, ils deviennent Double, ce qui effectue un mappage sur le nombre de type XPath W3C.</span><span class="sxs-lookup"><span data-stu-id="01e86-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="01e86-178">Tous les autres types deviennent une chaîne à l'aide de la méthode `ToString`.</span><span class="sxs-lookup"><span data-stu-id="01e86-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="01e86-179">Si la fonction de script utilise un type différent de ceux mentionnés ci-avant ou si la fonction ne se compile pas lorsque la feuille de style est chargée dans l'objet <xref:System.Xml.Xsl.XslTransform>, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="01e86-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="01e86-180">Si l'élément `msxsl:script` est utilisé, il est vivement recommandé de placer le script (quel que soit son langage) dans une section CDATA.</span><span class="sxs-lookup"><span data-stu-id="01e86-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="01e86-181">Par exemple, le langage XML suivant illustre le modèle de la section CDATA dans laquelle est placé votre code.</span><span class="sxs-lookup"><span data-stu-id="01e86-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="01e86-182">Il est vivement recommandé de placer tout le contenu du script dans une section CDATA car les opérateurs, les identificateurs ou les délimiteurs d'un langage donné peuvent être mal interprétés en tant que XML.</span><span class="sxs-lookup"><span data-stu-id="01e86-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="01e86-183">L'exemple suivant illustre l'utilisation de l'opérateur AND logique dans le script.</span><span class="sxs-lookup"><span data-stu-id="01e86-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="01e86-184">Cela lève une exception car les signes &amp; ne font pas l'objet d'un échappement.</span><span class="sxs-lookup"><span data-stu-id="01e86-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="01e86-185">Le document est chargé en tant que XML et aucun traitement spécial n’est appliqué au texte qui se trouve entre les étiquettes d’élément `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="01e86-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01e86-186">Exemple</span><span class="sxs-lookup"><span data-stu-id="01e86-186">Example</span></span>  
 <span data-ttu-id="01e86-187">L'exemple suivant utilise un script incorporé pour calculer la circonférence d'un cercle en fonction de son rayon.</span><span class="sxs-lookup"><span data-stu-id="01e86-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="01e86-188">Entrée</span><span class="sxs-lookup"><span data-stu-id="01e86-188">Input</span></span>  
 <span data-ttu-id="01e86-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="01e86-189">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="01e86-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="01e86-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="01e86-191">Output</span><span class="sxs-lookup"><span data-stu-id="01e86-191">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>
```  
  
## <a name="see-also"></a><span data-ttu-id="01e86-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01e86-192">See also</span></span>

- [<span data-ttu-id="01e86-193">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="01e86-193">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
