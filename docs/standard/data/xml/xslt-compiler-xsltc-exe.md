---
title: XSLT Compiler (xsltc.exe)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8480e2d6817d0367e89542c0e6c89cd26183dd5e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774903"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="9ba50-102">XSLT Compiler (xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="9ba50-102">XSLT Compiler (xsltc.exe)</span></span>
<span data-ttu-id="9ba50-103">Le compilateur XSLT (xsltc.exe) compile des feuilles de style XSLT et génère un assembly.</span><span class="sxs-lookup"><span data-stu-id="9ba50-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="9ba50-104">La feuille de style compilée peut être passée directement dans la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ba50-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9ba50-105">Vous ne pouvez pas générer d'assemblys signés avec xsltc.exe.</span><span class="sxs-lookup"><span data-stu-id="9ba50-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="9ba50-106">L’outil xsltc.exe est inclus dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ba50-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="9ba50-107">Pour plus d’informations, consultez les [Téléchargements Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span><span class="sxs-lookup"><span data-stu-id="9ba50-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba50-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ba50-108">Syntax</span></span>  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="9ba50-109">Argument</span><span class="sxs-lookup"><span data-stu-id="9ba50-109">Argument</span></span>  
  
|<span data-ttu-id="9ba50-110">Argument</span><span class="sxs-lookup"><span data-stu-id="9ba50-110">Argument</span></span>|<span data-ttu-id="9ba50-111">Description</span><span class="sxs-lookup"><span data-stu-id="9ba50-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="9ba50-112">Spécifie le nom de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="9ba50-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="9ba50-113">La feuille de style doit être un fichier local ou se trouver sur l'intranet.</span><span class="sxs-lookup"><span data-stu-id="9ba50-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="9ba50-114">Options</span><span class="sxs-lookup"><span data-stu-id="9ba50-114">Options</span></span>  
  
|<span data-ttu-id="9ba50-115">Option</span><span class="sxs-lookup"><span data-stu-id="9ba50-115">Option</span></span>|<span data-ttu-id="9ba50-116">Description</span><span class="sxs-lookup"><span data-stu-id="9ba50-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9ba50-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="9ba50-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="9ba50-118">Définit le nom de la classe pour la feuille de style suivante.</span><span class="sxs-lookup"><span data-stu-id="9ba50-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="9ba50-119">Le nom de la classe peut être un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="9ba50-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="9ba50-120">Le nom de la classe est par défaut celui de la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="9ba50-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="9ba50-121">Par exemple, si la feuille de style customers.xsl est compilée, le nom de la classe par défaut est customers.</span><span class="sxs-lookup"><span data-stu-id="9ba50-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="9ba50-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="9ba50-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="9ba50-123">Spécifie s'il faut générer des informations de débogage.</span><span class="sxs-lookup"><span data-stu-id="9ba50-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="9ba50-124">Si vous spécifiez `+` ou `/debug`, le compilateur génère des informations de débogage et les place dans un fichier (PDB) de la base de données du programme.</span><span class="sxs-lookup"><span data-stu-id="9ba50-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="9ba50-125">Le nom du fichier PDB généré est `assemblyName`.pdb.</span><span class="sxs-lookup"><span data-stu-id="9ba50-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="9ba50-126">Si vous spécifiez `-`, qui est en vigueur si vous ne spécifiez pas `/debug`, aucune information de débogage n'est créée.</span><span class="sxs-lookup"><span data-stu-id="9ba50-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="9ba50-127">Un assembly retail est généré.</span><span class="sxs-lookup"><span data-stu-id="9ba50-127">A retail assembly is generated.</span></span> <span data-ttu-id="9ba50-128">**Remarque :**  La compilation en mode débogage peut affecter considérablement les performances de XSLT.</span><span class="sxs-lookup"><span data-stu-id="9ba50-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="9ba50-129">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="9ba50-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="9ba50-130">Supprime l'affichage du message de copyright du compilateur.</span><span class="sxs-lookup"><span data-stu-id="9ba50-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="9ba50-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="9ba50-131">`/platform:` `string`</span></span>|<span data-ttu-id="9ba50-132">Spécifie les plateformes sur lesquelles l'assembly peut s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="9ba50-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="9ba50-133">Les valeurs de plateforme valides sont décrites ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="9ba50-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="9ba50-134">`x86` compile votre assembly pour qu'il soit exécuté par le CLR 32 bits x86.</span><span class="sxs-lookup"><span data-stu-id="9ba50-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="9ba50-135">`x64` compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d'instructions AMD64 ou EM64T.</span><span class="sxs-lookup"><span data-stu-id="9ba50-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="9ba50-136">Itanium compile votre assembly pour que celui-ci soit exécuté par le CLR 64 bits sur un ordinateur doté d’un processeur Itanium.</span><span class="sxs-lookup"><span data-stu-id="9ba50-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="9ba50-137">`anycpu` compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme.</span><span class="sxs-lookup"><span data-stu-id="9ba50-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="9ba50-138">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9ba50-138">This is the default.</span></span>|  
|<span data-ttu-id="9ba50-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="9ba50-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="9ba50-140">Spécifie le nom de l'assembly qui est produit.</span><span class="sxs-lookup"><span data-stu-id="9ba50-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="9ba50-141">Le nom de l'assembly est par défaut celui de la feuille de style principale ou de la première feuille de style s'il y en a plusieurs.</span><span class="sxs-lookup"><span data-stu-id="9ba50-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="9ba50-142">Si la feuille de style contient des scripts, ceux-ci sont enregistrés dans un assembly séparé.</span><span class="sxs-lookup"><span data-stu-id="9ba50-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="9ba50-143">Les noms d'assemblys de script sont générés d'après le nom de l'assembly principal.</span><span class="sxs-lookup"><span data-stu-id="9ba50-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="9ba50-144">Par exemple, si vous avez spécifié CustOrders.dll comme nom d'assembly, le premier assembly de script est nommé CustOrders_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="9ba50-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="9ba50-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="9ba50-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="9ba50-146">Spécifie s'il faut autoriser des fonctions `document()`, un script XSLT ou une définition de type de document (DTD) dans la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="9ba50-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="9ba50-147">Le comportement par défaut désactive la prise en charge de la DTD, la fonction `document()` et les scripts.</span><span class="sxs-lookup"><span data-stu-id="9ba50-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="9ba50-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="9ba50-148">`@` `file`</span></span>|<span data-ttu-id="9ba50-149">Vous permet de spécifier un fichier qui contient les options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="9ba50-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="9ba50-150">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="9ba50-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ba50-151">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ba50-151">Remarks</span></span>  
 <span data-ttu-id="9ba50-152">Les solutions XSLT peuvent être constituées de plusieurs modules de feuilles de style.</span><span class="sxs-lookup"><span data-stu-id="9ba50-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="9ba50-153">L'outil xsltc.exe génère des assemblys à partir des feuilles de style.</span><span class="sxs-lookup"><span data-stu-id="9ba50-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="9ba50-154">Les assemblys peuvent ensuite être passés dans la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9ba50-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9ba50-155">Cela peut permettre de réduire le coût des performances dans certains scénarios de déploiement XSLT.</span><span class="sxs-lookup"><span data-stu-id="9ba50-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ba50-156">Vous devez également inclure l'assembly compilé comme référence dans votre application.</span><span class="sxs-lookup"><span data-stu-id="9ba50-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="9ba50-157">L’outil xsltc.exe ne valide pas les noms de classe (`/class:`*nom*) ou les noms d’assembly (`/out:`*nom_assembly*).</span><span class="sxs-lookup"><span data-stu-id="9ba50-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="9ba50-158">Si les noms ne sont pas valides, le Common Language Runtime lève des erreurs.</span><span class="sxs-lookup"><span data-stu-id="9ba50-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9ba50-159">Exemples</span><span class="sxs-lookup"><span data-stu-id="9ba50-159">Examples</span></span>  
 <span data-ttu-id="9ba50-160">La commande suivante compile la feuille de style et crée un assembly nommé booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="9ba50-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="9ba50-161">La commande suivante compile la feuille de style et crée un assembly et un fichier PDB nommés respectivement booksort.dll et booksort.pdb.</span><span class="sxs-lookup"><span data-stu-id="9ba50-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="9ba50-162">La commande suivante compile une feuille de style qui contient un élément msxsl:script et crée deux assemblys nommés calc.dll et calc_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="9ba50-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="9ba50-163">La commande suivante active le traitement DTD et la prise en charge de script et crée deux assemblys nommés myTest.dll et myTest_Script1.dll.</span><span class="sxs-lookup"><span data-stu-id="9ba50-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="9ba50-164">La commande suivante compile deux modules de feuilles de style et crée un assembly unique nommé booksort.dll.</span><span class="sxs-lookup"><span data-stu-id="9ba50-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ba50-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ba50-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="9ba50-166">Guide pratique pour effectuer une transformation XSLT à l’aide d’un assembly</span><span class="sxs-lookup"><span data-stu-id="9ba50-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="9ba50-167">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="9ba50-167">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
