---
title: Options interactives
description: En savoir plus sur les options de ligne de commande prises en charge par F# Interactive, fsi.exe.
ms.date: 08/15/2020
ms.openlocfilehash: da2251c1d2e57090ed926e501cebf3c53ac58052
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558606"
---
# <a name="f-interactive-options"></a><span data-ttu-id="4bcf9-103">Options de F# Interactive</span><span class="sxs-lookup"><span data-stu-id="4bcf9-103">F# Interactive options</span></span>

<span data-ttu-id="4bcf9-104">Cet article décrit les options de ligne de commande prises en charge par F# Interactive, `fsi.exe` .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-104">This article describes the command-line options supported by F# Interactive, `fsi.exe`.</span></span> <span data-ttu-id="4bcf9-105">F# Interactive accepte un grand nombre des mêmes options de ligne de commande que le compilateur F #, mais il accepte également quelques options supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-105">F# Interactive accepts many of the same command-line options as the F# compiler, but also accepts some additional options.</span></span>

## <a name="use-f-interactive-for-scripting"></a><span data-ttu-id="4bcf9-106">Utiliser F# Interactive pour l’écriture de scripts</span><span class="sxs-lookup"><span data-stu-id="4bcf9-106">Use F# Interactive for scripting</span></span>

<span data-ttu-id="4bcf9-107">F# Interactive, `dotnet fsi` , peut être lancé de manière interactive ou peut être lancé à partir de la ligne de commande pour exécuter un script.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-107">F# Interactive, `dotnet fsi`, can be launched interactively, or it can be launched from the command line to run a script.</span></span> <span data-ttu-id="4bcf9-108">La syntaxe de la ligne de commande est</span><span class="sxs-lookup"><span data-stu-id="4bcf9-108">The command-line syntax is</span></span>

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

<span data-ttu-id="4bcf9-109">L’extension de fichier pour les fichiers de script F # est `.fsx` .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-109">The file extension for F# script files is `.fsx`.</span></span>

## <a name="table-of-f-interactive-options"></a><span data-ttu-id="4bcf9-110">Tableau des options de F# Interactive</span><span class="sxs-lookup"><span data-stu-id="4bcf9-110">Table of F# Interactive Options</span></span>

<span data-ttu-id="4bcf9-111">Le tableau suivant récapitule les options prises en charge par F# Interactive.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-111">The following table summarizes the options supported by F# Interactive.</span></span> <span data-ttu-id="4bcf9-112">Vous pouvez définir ces options sur la ligne de commande ou à l’aide de l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-112">You can set these options on the command line or through the Visual Studio IDE.</span></span> <span data-ttu-id="4bcf9-113">Pour définir ces options dans l’IDE de Visual Studio, ouvrez le menu **Outils** , sélectionnez **options**, développez le nœud **Outils F #** , puis sélectionnez **F# Interactive**.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-113">To set these options in the Visual Studio IDE, open the **Tools** menu, select **Options**, expand the **F# Tools** node, and then select **F# Interactive**.</span></span>

<span data-ttu-id="4bcf9-114">Quand des listes apparaissent dans F# Interactive arguments de l’option, les éléments de liste sont séparés par des points-virgules ( `;` ).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-114">Where lists appear in F# Interactive option arguments, list elements are separated by semicolons (`;`).</span></span>

|<span data-ttu-id="4bcf9-115">Option</span><span class="sxs-lookup"><span data-stu-id="4bcf9-115">Option</span></span>|<span data-ttu-id="4bcf9-116">Description</span><span class="sxs-lookup"><span data-stu-id="4bcf9-116">Description</span></span>|
|------|-----------|
|**--**|<span data-ttu-id="4bcf9-117">Permet d’indiquer à F# Interactive de traiter les arguments restants comme des arguments de ligne de commande pour le programme ou le script F #, auquel vous pouvez accéder dans le code à l’aide de la liste **FSI. CommandLineArgs**.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-117">Used to instruct F# Interactive to treat remaining arguments as command-line arguments to the F# program or script, which you can access in code by using the list **fsi.CommandLineArgs**.</span></span>|
|<span data-ttu-id="4bcf9-118">**--activé**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-118">**--checked**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-119">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-119">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-120">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-120">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-121">**--CodePage : &lt; int&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-121">**--codepage:&lt;int&gt;**</span></span>|<span data-ttu-id="4bcf9-122">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-122">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-123">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-123">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-124">**--consolecolors**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-124">**--consolecolors**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-125">Génère des messages d’avertissement et d’erreur en couleur.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-125">Outputs warning and error messages in color.</span></span>|
|<span data-ttu-id="4bcf9-126">**--crossoptimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-126">**--crossoptimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-127">Activez ou désactivez les optimisations entre modules.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-127">Enable or disable cross-module optimizations.</span></span>|
|<span data-ttu-id="4bcf9-128">**--Déboguer**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-128">**--debug**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="4bcf9-129">**--Debug :**[**full**&#124;**pdbonly**&#124;**portable**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-129">**--debug:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span><br /><br /><span data-ttu-id="4bcf9-130">**-g**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-130">**-g**[**+**&#124;**-**]</span></span><br /><br /><span data-ttu-id="4bcf9-131">**-g :**[**full**&#124;**pdbonly**&#124;**portable**&#124;**Embedded**]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-131">**-g:**[**full**&#124;**pdbonly**&#124;**portable**&#124;**embedded**]</span></span>|<span data-ttu-id="4bcf9-132">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-132">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-133">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-133">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-134">**--define : &lt; chaîne&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-134">**--define:&lt;string&gt;**</span></span>|<span data-ttu-id="4bcf9-135">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-135">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-136">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-136">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-137">**--déterministe**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-137">**--deterministic**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-138">Produit un assembly déterministe (y compris le GUID de la version du module et l’horodateur).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-138">Produces a deterministic assembly (including module version GUID and timestamp).</span></span>|
|<span data-ttu-id="4bcf9-139">**--exec**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-139">**--exec**</span></span>|<span data-ttu-id="4bcf9-140">Ordonne à F # interactive de se fermer après le chargement des fichiers ou l’exécution du fichier de script spécifié sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-140">Instructs F# interactive to exit after loading the files or running the script file given on the command line.</span></span>|
|<span data-ttu-id="4bcf9-141">**--fullpaths**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-141">**--fullpaths**</span></span>|<span data-ttu-id="4bcf9-142">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-142">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-143">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-143">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-144">**--GUI**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-144">**--gui**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-145">Active ou désactive la boucle d’événements Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-145">Enables or disables the Windows Forms event loop.</span></span> <span data-ttu-id="4bcf9-146">Il est activé par défaut.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-146">The default is enabled.</span></span>|
|<span data-ttu-id="4bcf9-147">**--aide**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-147">**--help**</span></span><br /><br /><span data-ttu-id="4bcf9-148">**-?**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-148">**-?**</span></span>|<span data-ttu-id="4bcf9-149">Utilisé pour afficher la syntaxe de la ligne de commande et une brève description de chaque option.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-149">Used to display the command-line syntax and a brief description of each option.</span></span>|
|<span data-ttu-id="4bcf9-150">**--lib : &lt; Folder-List&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-150">**--lib:&lt;folder-list&gt;**</span></span><br /><br /><span data-ttu-id="4bcf9-151">**-I : &lt; dossier-liste&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-151">**-I:&lt;folder-list&gt;**</span></span>|<span data-ttu-id="4bcf9-152">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-152">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-153">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-153">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-154">**--Load : &lt; nom de fichier&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-154">**--load:&lt;filename&gt;**</span></span>|<span data-ttu-id="4bcf9-155">Compile le code source donné au démarrage et charge les constructions F # compilées dans la session.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-155">Compiles the given source code at startup and loads the compiled F# constructs into the session.</span></span>|
|<span data-ttu-id="4bcf9-156">**--mlcompatibility**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-156">**--mlcompatibility**</span></span>|<span data-ttu-id="4bcf9-157">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-157">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-158">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-158">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-159">**--noframework**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-159">**--noframework**</span></span>|<span data-ttu-id="4bcf9-160">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-160">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-161">Pour plus d’informations, consultez [Options du compilateur](compiler-options.md)</span><span class="sxs-lookup"><span data-stu-id="4bcf9-161">For more information, see [Compiler Options](compiler-options.md)</span></span>|
|<span data-ttu-id="4bcf9-162">**--nologo**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-162">**--nologo**</span></span>|<span data-ttu-id="4bcf9-163">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-163">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-164">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-164">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-165">**--nowarn : &lt; Avertissement-liste&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-165">**--nowarn:&lt;warning-list&gt;**</span></span>|<span data-ttu-id="4bcf9-166">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-166">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-167">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-167">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-168">**--optimize**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-168">**--optimize**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-169">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-169">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-170">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-170">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-171">**--preferreduilang : &lt; lang&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-171">**--preferreduilang:&lt;lang&gt;**</span></span>| <span data-ttu-id="4bcf9-172">Spécifie le nom de culture de la langue de sortie par défaut (par exemple, es-ES, ja-JP).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-172">Specifies the preferred output language culture name (for example, es-ES, ja-JP).</span></span> |
|<span data-ttu-id="4bcf9-173">**--quiet**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-173">**--quiet**</span></span>|<span data-ttu-id="4bcf9-174">Supprime la sortie de F# Interactive dans le flux **stdout** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-174">Suppress F# Interactive's output to the **stdout** stream.</span></span>|
|<span data-ttu-id="4bcf9-175">**--Quotations-débogage**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-175">**--quotations-debug**</span></span>|<span data-ttu-id="4bcf9-176">Spécifie que des informations de débogage supplémentaires doivent être émises pour les expressions dérivées des littéraux de quotation F # et des définitions réfléchies.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-176">Specifies that extra debugging information should be emitted for expressions that are derived from F# quotation literals and reflected definitions.</span></span> <span data-ttu-id="4bcf9-177">Les informations de débogage sont ajoutées aux attributs personnalisés d’un nœud d’arborescence d’expression F #.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-177">The debug information is added to the custom attributes of an F# expression tree node.</span></span> <span data-ttu-id="4bcf9-178">Consultez [Quotations de code](code-quotations.md) et [expr. CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-178">See [Code Quotations](code-quotations.md) and [Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).</span></span>|
|<span data-ttu-id="4bcf9-179">**--ReadLine**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-179">**--readline**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-180">Activez ou désactivez la saisie semi-automatique par tabulation en mode interactif.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-180">Enable or disable tab completion in interactive mode.</span></span>|
|<span data-ttu-id="4bcf9-181">**--Référence : &lt; nom de fichier&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-181">**--reference:&lt;filename&gt;**</span></span><br /><br /><span data-ttu-id="4bcf9-182">**-r : &lt; nom_fichier&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-182">**-r:&lt;filename&gt;**</span></span>|<span data-ttu-id="4bcf9-183">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-183">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-184">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-184">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-185">**--tailcalls**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-185">**--tailcalls**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-186">Activez ou désactivez l’utilisation de l’instruction IL tail, qui entraîne la réutilisation du frame de pile pour les fonctions récursives tail.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-186">Enable or disable the use of the tail IL instruction, which causes the stack frame to be reused for tail recursive functions.</span></span> <span data-ttu-id="4bcf9-187">Cette option est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-187">This option is enabled by default.</span></span>|
|<span data-ttu-id="4bcf9-188">**--TargetProfile : &lt; chaîne&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-188">**--targetprofile:&lt;string&gt;**</span></span>|<span data-ttu-id="4bcf9-189">Spécifie le profil du Framework cible de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-189">Specifies target framework profile of this assembly.</span></span> <span data-ttu-id="4bcf9-190">Les valeurs valides sont `mscorlib`, `netcore` ou `netstandard`.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-190">Valid values are `mscorlib`, `netcore`, or `netstandard`.</span></span> <span data-ttu-id="4bcf9-191">La valeur par défaut est `mscorlib`.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-191">The default is `mscorlib`.</span></span>|
|<span data-ttu-id="4bcf9-192">**--Use : &lt; nom_fichier&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-192">**--use:&lt;filename&gt;**</span></span>|<span data-ttu-id="4bcf9-193">Indique à l’interpréteur d’utiliser le fichier donné au démarrage comme entrée initiale.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-193">Tells the interpreter to use the given file on startup as initial input.</span></span>|
|<span data-ttu-id="4bcf9-194">**--utf8output**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-194">**--utf8output**</span></span>|<span data-ttu-id="4bcf9-195">Identique à l’option du compilateur fsc.exe.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-195">Same as the fsc.exe compiler option.</span></span> <span data-ttu-id="4bcf9-196">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-196">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-197">**--Warn : &lt; Warning-niveau&gt;**</span><span class="sxs-lookup"><span data-stu-id="4bcf9-197">**--warn:&lt;warning-level&gt;**</span></span>|<span data-ttu-id="4bcf9-198">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-198">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-199">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-199">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-200">**--warnaserror**[ **+**&#124;**-** ]</span><span class="sxs-lookup"><span data-stu-id="4bcf9-200">**--warnaserror**[**+**&#124;**-**]</span></span>|<span data-ttu-id="4bcf9-201">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-201">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-202">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-202">For more information, see [Compiler Options](compiler-options.md).</span></span>|
|<span data-ttu-id="4bcf9-203">**--warnaserror**[ **+**&#124;**-** ] :\*\* &lt; int-List &gt; \*\*</span><span class="sxs-lookup"><span data-stu-id="4bcf9-203">**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**</span></span>|<span data-ttu-id="4bcf9-204">Identique à l’option du compilateur **fsc.exe** .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-204">Same as the **fsc.exe** compiler option.</span></span> <span data-ttu-id="4bcf9-205">Pour plus d’informations, consultez l’article [Options du compilateur](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf9-205">For more information, see [Compiler Options](compiler-options.md).</span></span>|

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="4bcf9-206">F# Interactive l’impression structurée</span><span class="sxs-lookup"><span data-stu-id="4bcf9-206">F# Interactive structured printing</span></span>

<span data-ttu-id="4bcf9-207">F# Interactive ( `dotnet fsi` ) utilise une version étendue de la [mise en forme de texte brut structurée](plaintext-formatting.md) pour les valeurs de rapport.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-207">F# Interactive (`dotnet fsi`) uses an extended version of [structured plain text formatting](plaintext-formatting.md) to report values.</span></span>

1. <span data-ttu-id="4bcf9-208">Toutes les fonctionnalités de `%A` mise en forme de texte brut sont prises en charge, et d’autres sont personnalisables.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-208">All features of `%A` plain text formatting are supported, and some are additionally customizable.</span></span>

2. <span data-ttu-id="4bcf9-209">L’impression est colorée si les couleurs sont prises en charge par la console de sortie.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-209">Printing is colorized if colors are supported by the output console.</span></span>

3. <span data-ttu-id="4bcf9-210">Une limite est placée sur la longueur des chaînes affichées, sauf si vous évaluez explicitement cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-210">A limit is placed on the length of strings shown, unless you explicitly evaluate that string.</span></span>

4. <span data-ttu-id="4bcf9-211">Un ensemble de paramètres définissables par l’utilisateur est disponible via l' `fsi` objet.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-211">A set of user-definable settings is available via the `fsi` object.</span></span>

<span data-ttu-id="4bcf9-212">Les paramètres disponibles pour personnaliser l’impression en texte brut pour les valeurs signalées sont :</span><span class="sxs-lookup"><span data-stu-id="4bcf9-212">The available settings to customize plain text printing for reported values are:</span></span>

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a><span data-ttu-id="4bcf9-213">Personnaliser avec `AddPrinter` et `AddPrintTransformer`</span><span class="sxs-lookup"><span data-stu-id="4bcf9-213">Customize with `AddPrinter` and `AddPrintTransformer`</span></span>

<span data-ttu-id="4bcf9-214">L’impression dans F# Interactive sorties peut être personnalisée à l’aide `fsi.AddPrinter` de et de `fsi.AddPrintTransformer` .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-214">Printing in F# Interactive outputs can be customized by using `fsi.AddPrinter` and `fsi.AddPrintTransformer`.</span></span>
<span data-ttu-id="4bcf9-215">La première fonction donne du texte pour remplacer l’impression d’un objet.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-215">The first function gives text to replace the printing of an object.</span></span> <span data-ttu-id="4bcf9-216">La deuxième fonction retourne un objet de substitution à afficher à la place.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-216">The second function returns a surrogate object to display instead.</span></span> <span data-ttu-id="4bcf9-217">Par exemple, considérez le code F # suivant :</span><span class="sxs-lookup"><span data-stu-id="4bcf9-217">For example, consider the following F# code:</span></span>

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

<span data-ttu-id="4bcf9-218">Si vous exécutez l’exemple dans F# Interactive, il est en sortie en fonction de l’option de mise en forme définie.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-218">If you execute the example in F# Interactive, it outputs based on the formatting option set.</span></span> <span data-ttu-id="4bcf9-219">Dans ce cas, il affecte la mise en forme de la date et de l’heure :</span><span class="sxs-lookup"><span data-stu-id="4bcf9-219">In this case, it affects the formatting of date and time:</span></span>

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

<span data-ttu-id="4bcf9-220">`fsi.AddPrintTransformer` peut être utilisé pour fournir un objet de substitution pour l’impression :</span><span class="sxs-lookup"><span data-stu-id="4bcf9-220">`fsi.AddPrintTransformer` can be used to give a surrogate object for printing:</span></span>

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

<span data-ttu-id="4bcf9-221">Voici les résultats :</span><span class="sxs-lookup"><span data-stu-id="4bcf9-221">This outputs:</span></span>

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

<span data-ttu-id="4bcf9-222">Si la fonction de transformateur est passée à `fsi.AddPrintTransformer` returns `null` , le transformateur d’impression est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-222">If the transformer function passed to `fsi.AddPrintTransformer` returns `null`, then the print transformer is ignored.</span></span>
<span data-ttu-id="4bcf9-223">Cela peut être utilisé pour filtrer toute valeur d’entrée en commençant par le type `obj` .</span><span class="sxs-lookup"><span data-stu-id="4bcf9-223">This can be used to filter any input value by starting with type `obj`.</span></span>  <span data-ttu-id="4bcf9-224">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="4bcf9-224">For example:</span></span>

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

<span data-ttu-id="4bcf9-225">Voici les résultats :</span><span class="sxs-lookup"><span data-stu-id="4bcf9-225">This outputs:</span></span>

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a><span data-ttu-id="4bcf9-226">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="4bcf9-226">Related topics</span></span>

|<span data-ttu-id="4bcf9-227">Intitulé</span><span class="sxs-lookup"><span data-stu-id="4bcf9-227">Title</span></span>|<span data-ttu-id="4bcf9-228">Description</span><span class="sxs-lookup"><span data-stu-id="4bcf9-228">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="4bcf9-229">Options du compilateur</span><span class="sxs-lookup"><span data-stu-id="4bcf9-229">Compiler Options</span></span>](compiler-options.md)|<span data-ttu-id="4bcf9-230">Décrit les options de ligne de commande disponibles pour le compilateur F #, **fsc.exe**.</span><span class="sxs-lookup"><span data-stu-id="4bcf9-230">Describes command-line options available for the F# compiler, **fsc.exe**.</span></span>|
