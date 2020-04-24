---
title: Blocs de scripts utilisant msxsl:script
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
ms.openlocfilehash: a63452df16e452a90eff3977ac8726cc0a5ac439
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710191"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="63a8a-102">Blocs de scripts utilisant msxsl:script</span><span class="sxs-lookup"><span data-stu-id="63a8a-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="63a8a-103">La classe <xref:System.Xml.Xsl.XslCompiledTransform> prend en charge les scripts incorporés en utilisant l'élément `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="63a8a-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="63a8a-104">Lorsque la feuille de style est chargée, toute fonction définie est compilée en langage MSIL (Microsoft Intermediate Language) par le CodeDOM (Code Document Object Model) et exécutée au cours de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="63a8a-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="63a8a-105">L' assembly généré à partir du bloc de script incorporé est distinct de l'assembly généré pour la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="63a8a-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="63a8a-106">Activer les scripts XSLT</span><span class="sxs-lookup"><span data-stu-id="63a8a-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="63a8a-107">La prise en charge des scripts incorporés est un réglage XSLT facultatif de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="63a8a-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="63a8a-108">La prise en charge des scripts est désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="63a8a-108">Script support is disabled by default.</span></span> <span data-ttu-id="63a8a-109">Pour l'activer, créez un objet <xref:System.Xml.Xsl.XsltSettings> avec la propriété <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> définie sur `true` et transmettez l'objet à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="63a8a-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63a8a-110">Le script XSLT ne doit être activé que si la prise en charge des scripts est nécessaire et si vous travaillez dans un environnement totalement fiable.</span><span class="sxs-lookup"><span data-stu-id="63a8a-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="63a8a-111">Définition de l'élément msxsl:script</span><span class="sxs-lookup"><span data-stu-id="63a8a-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="63a8a-112">L’élément `msxsl:script` est une extension Microsoft de la recommandation XSLT 1.0. Il se définit comme suit :</span><span class="sxs-lookup"><span data-stu-id="63a8a-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="63a8a-113">Le préfixe `msxsl` est lié à l'URI d'espace de noms `urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="63a8a-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="63a8a-114">La feuille de style doit inclure la déclaration d'espace de noms `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span><span class="sxs-lookup"><span data-stu-id="63a8a-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="63a8a-115">L'attribut `language` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="63a8a-115">The `language` attribute is optional.</span></span> <span data-ttu-id="63a8a-116">Sa valeur est le langage du bloc de code incorporé.</span><span class="sxs-lookup"><span data-stu-id="63a8a-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="63a8a-117">Ce langage est mappé au compilateur CodeDOM approprié à l’aide de la méthode <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63a8a-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="63a8a-118">La classe <xref:System.Xml.Xsl.XslCompiledTransform> peut prendre en charge tout langage Microsoft .NET, à condition que le fournisseur approprié soit installé sur l'ordinateur et enregistré dans la section system.codedom du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="63a8a-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="63a8a-119">Si aucun attribut `language` n'est spécifié, le langage par défaut est JScript.</span><span class="sxs-lookup"><span data-stu-id="63a8a-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="63a8a-120">Le nom du langage ne respecte pas la casse : les termes « JavaScript » et « javascript » sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="63a8a-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="63a8a-121">L'attribut `implements-prefix` est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="63a8a-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="63a8a-122">Cet attribut est utilisé pour déclarer un espace de noms et l'associer au bloc de script.</span><span class="sxs-lookup"><span data-stu-id="63a8a-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="63a8a-123">La valeur de cet attribut est le préfixe qui représente l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="63a8a-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="63a8a-124">Ce préfixe peut être défini à un endroit d'une feuille de style.</span><span class="sxs-lookup"><span data-stu-id="63a8a-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63a8a-125">Lors de l'utilisation de l'élément `msxsl:script`, il est vivement recommandé de placer le script (quel que soit son langage) dans une section CDATA.</span><span class="sxs-lookup"><span data-stu-id="63a8a-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="63a8a-126">Étant donné que le script peut contenir des opérateurs, identificateurs ou délimiteurs pour un langage donné, s'il n'est pas contenu dans une section CDATA, il risque d'être interprété à tort comme du XML.</span><span class="sxs-lookup"><span data-stu-id="63a8a-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="63a8a-127">Le XML suivant illustre un modèle de la section CDATA où peut être placé le code.</span><span class="sxs-lookup"><span data-stu-id="63a8a-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="63a8a-128">Fonctions de script</span><span class="sxs-lookup"><span data-stu-id="63a8a-128">Script Functions</span></span>  
 <span data-ttu-id="63a8a-129">Les fonctions peuvent être déclarées dans l'élément `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="63a8a-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="63a8a-130">Lorsqu'une fonction est déclarée, elle est contenue dans un bloc de script.</span><span class="sxs-lookup"><span data-stu-id="63a8a-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="63a8a-131">Les feuilles de style peuvent contenir plusieurs blocs de scripts, chacun fonctionnant indépendamment des autres.</span><span class="sxs-lookup"><span data-stu-id="63a8a-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="63a8a-132">Ainsi, si vous êtes en cours d'exécution dans un bloc de script, vous ne pouvez pas appeler une fonction que vous avez définie dans un autre bloc de script, sauf si elle est déclarée comme possédant le même espace de noms et le même langage de script.</span><span class="sxs-lookup"><span data-stu-id="63a8a-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="63a8a-133">Puisque chaque bloc de script peut être écrit dans son propre langage et que le bloc est analysé en fonction des règles grammaticales de cet analyseur de langage, il est recommandé d'utiliser la syntaxe correcte pour le langage utilisé.</span><span class="sxs-lookup"><span data-stu-id="63a8a-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="63a8a-134">Par exemple, si vous êtes dans un bloc de script Microsoft C#, utilisez la syntaxe de commentaires C#.</span><span class="sxs-lookup"><span data-stu-id="63a8a-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="63a8a-135">Les arguments fournis et les valeurs retournées par la fonction peuvent être de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="63a8a-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="63a8a-136">Les types XPath W3C étant un sous-ensemble des types CLR (common language runtime), une conversion de type est appliquée aux types qui ne sont pas considérés comme des types XPath.</span><span class="sxs-lookup"><span data-stu-id="63a8a-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="63a8a-137">Le tableau suivant indique les correspondances entre les types W3C et les types CLR.</span><span class="sxs-lookup"><span data-stu-id="63a8a-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="63a8a-138">Type W3C</span><span class="sxs-lookup"><span data-stu-id="63a8a-138">W3C type</span></span>|<span data-ttu-id="63a8a-139">Type CLR</span><span class="sxs-lookup"><span data-stu-id="63a8a-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="63a8a-140">Les types CLR numériques sont convertis en objet <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="63a8a-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="63a8a-141">Le type <xref:System.DateTime> est converti en <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="63a8a-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="63a8a-142">Les types <xref:System.Xml.XPath.IXPathNavigable> sont convertis en <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="63a8a-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="63a8a-143">**XPathNavigator[]** est converti en objet <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="63a8a-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="63a8a-144">Tous les autres types provoquent une erreur.</span><span class="sxs-lookup"><span data-stu-id="63a8a-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="63a8a-145">Importation d'espaces de noms et d'assemblys</span><span class="sxs-lookup"><span data-stu-id="63a8a-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="63a8a-146">La classe <xref:System.Xml.Xsl.XslCompiledTransform> prédéfinit un ensemble d'assemblys et d'espaces de noms qui sont pris en charge par défaut par l'élément `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="63a8a-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="63a8a-147">Cependant, vous pouvez utiliser des classes et des membres appartenant à un espace de noms qui ne figure pas sur la liste prédéfinie en important l'assembly et l'espace de noms dans un bloc `msxsl:script`.</span><span class="sxs-lookup"><span data-stu-id="63a8a-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="63a8a-148">Assemblys</span><span class="sxs-lookup"><span data-stu-id="63a8a-148">Assemblies</span></span>  
 <span data-ttu-id="63a8a-149">Les deux assemblys suivants sont référencés par défaut :</span><span class="sxs-lookup"><span data-stu-id="63a8a-149">The following two assemblies are referenced by default:</span></span>  
  
- <span data-ttu-id="63a8a-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="63a8a-150">System.dll</span></span>  
  
- <span data-ttu-id="63a8a-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="63a8a-151">System.Xml.dll</span></span>  
  
- <span data-ttu-id="63a8a-152">Microsoft.VisualBasic.dll (lorsque le langage de script est VB)</span><span class="sxs-lookup"><span data-stu-id="63a8a-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="63a8a-153">Vous pouvez importer les assemblys supplémentaires en utilisant l'élément `msxsl:assembly`.</span><span class="sxs-lookup"><span data-stu-id="63a8a-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="63a8a-154">Cela comprend l'assembly lorsque la feuille de style est compilée.</span><span class="sxs-lookup"><span data-stu-id="63a8a-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="63a8a-155">L'élément `msxsl:assembly` a la définition suivante :</span><span class="sxs-lookup"><span data-stu-id="63a8a-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="63a8a-156">L'attribut `name` contient le nom de l'assembly et l'attribut `href` contient le chemin de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="63a8a-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="63a8a-157">Le nom de l'assembly peut être un nom complet, comme « System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089 », ou un nom court, comme « System.Web ».</span><span class="sxs-lookup"><span data-stu-id="63a8a-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="63a8a-158">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="63a8a-158">Namespaces</span></span>  
 <span data-ttu-id="63a8a-159">Les espaces de noms suivants sont inclus par défaut :</span><span class="sxs-lookup"><span data-stu-id="63a8a-159">The following namespaces are included by default:</span></span>  
  
- <span data-ttu-id="63a8a-160">Système</span><span class="sxs-lookup"><span data-stu-id="63a8a-160">System</span></span>  
  
- <span data-ttu-id="63a8a-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="63a8a-161">System.Collection</span></span>  
  
- <span data-ttu-id="63a8a-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="63a8a-162">System.Text</span></span>  
  
- <span data-ttu-id="63a8a-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="63a8a-163">System.Text.RegularExpressions</span></span>  
  
- <span data-ttu-id="63a8a-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="63a8a-164">System.Xml</span></span>  
  
- <span data-ttu-id="63a8a-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="63a8a-165">System.Xml.Xsl</span></span>  
  
- <span data-ttu-id="63a8a-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="63a8a-166">System.Xml.XPath</span></span>  
  
- <span data-ttu-id="63a8a-167">Microsoft.VisualBasic (lorsque le langage de script est VB)</span><span class="sxs-lookup"><span data-stu-id="63a8a-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="63a8a-168">Vous pouvez ajouter la prise en charge d'autres espaces de noms à l'aide de l'attribut `namespace`.</span><span class="sxs-lookup"><span data-stu-id="63a8a-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="63a8a-169">La valeur de l'attribut est le nom de l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="63a8a-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="63a8a-170">Exemple</span><span class="sxs-lookup"><span data-stu-id="63a8a-170">Example</span></span>  
 <span data-ttu-id="63a8a-171">L'exemple suivant utilise un script incorporé pour calculer la circonférence d'un cercle en fonction de son rayon.</span><span class="sxs-lookup"><span data-stu-id="63a8a-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="63a8a-172">number.xml</span><span class="sxs-lookup"><span data-stu-id="63a8a-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="63a8a-173">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="63a8a-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="63a8a-174">Output</span><span class="sxs-lookup"><span data-stu-id="63a8a-174">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63a8a-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63a8a-175">See also</span></span>

- [<span data-ttu-id="63a8a-176">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="63a8a-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
- [<span data-ttu-id="63a8a-177">Génération et compilation de code source dynamique</span><span class="sxs-lookup"><span data-stu-id="63a8a-177">Dynamic Source Code Generation and Compilation</span></span>](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
