---
title: Ilasm.exe (Assembleur IL)
description: Prise en main de Ilasm.exe, l’assembleur IL. Cet outil génère un fichier exécutable portable (PE) à partir du langage intermédiaire (IL).
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: 1a85b3bf9509ffba6c2331d14196a6bef2bfa080
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166980"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="e0191-104">Ilasm.exe (Assembleur IL)</span><span class="sxs-lookup"><span data-stu-id="e0191-104">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="e0191-105">L'Assembleur IL génère un fichier PE (Portable Executable) en langage IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="e0191-105">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="e0191-106">(Pour plus d’informations sur IL, consultez [processus d’exécution managée](../../standard/managed-execution-process.md).) Vous pouvez exécuter le fichier exécutable obtenu, qui contient le langage IL et les métadonnées requises, pour déterminer si le langage IL fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="e0191-106">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="e0191-107">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0191-107">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="e0191-108">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="e0191-108">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="e0191-109">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e0191-109">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="e0191-110">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="e0191-110">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="e0191-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0191-111">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="e0191-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0191-112">Parameters</span></span>

| <span data-ttu-id="e0191-113">Argument</span><span class="sxs-lookup"><span data-stu-id="e0191-113">Argument</span></span> | <span data-ttu-id="e0191-114">Description</span><span class="sxs-lookup"><span data-stu-id="e0191-114">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="e0191-115">Nom du fichier source .il.</span><span class="sxs-lookup"><span data-stu-id="e0191-115">The name of the .il source file.</span></span> <span data-ttu-id="e0191-116">Ce fichier est composé de directives de déclaration de métadonnées et d'instructions IL symboliques.</span><span class="sxs-lookup"><span data-stu-id="e0191-116">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="e0191-117">Plusieurs arguments de fichier source peuvent être fournis pour générer un seul fichier PE avec *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="e0191-117">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="e0191-118">**Remarque :** Vérifiez que la dernière ligne de code du fichier source. il contient un espace blanc de fin ou un caractère de fin de ligne.</span><span class="sxs-lookup"><span data-stu-id="e0191-118">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="e0191-119">Option</span><span class="sxs-lookup"><span data-stu-id="e0191-119">Option</span></span> | <span data-ttu-id="e0191-120">Description</span><span class="sxs-lookup"><span data-stu-id="e0191-120">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="e0191-121">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="e0191-121">**/32bitpreferred**</span></span>|<span data-ttu-id="e0191-122">Crée une image 32 bits (PE32+).</span><span class="sxs-lookup"><span data-stu-id="e0191-122">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="e0191-123">**/alignment :**`integer`</span><span class="sxs-lookup"><span data-stu-id="e0191-123">**/alignment:** `integer`</span></span>|<span data-ttu-id="e0191-124">Assigne à FileAlignment la valeur spécifiée par `integer` dans l'en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="e0191-124">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="e0191-125">Lorsque la directive IL .alignment est spécifiée dans le fichier, cette option se substitue à elle.</span><span class="sxs-lookup"><span data-stu-id="e0191-125">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="e0191-126">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="e0191-126">**/appcontainer**</span></span>|<span data-ttu-id="e0191-127">Produit un fichier *. dll* ou *. exe* qui s’exécute dans le conteneur d’application Windows comme sortie.</span><span class="sxs-lookup"><span data-stu-id="e0191-127">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="e0191-128">**/arm**</span><span class="sxs-lookup"><span data-stu-id="e0191-128">**/arm**</span></span>|<span data-ttu-id="e0191-129">Spécifie l'ordinateur (ARM) Advanced RISC comme processeur cible.</span><span class="sxs-lookup"><span data-stu-id="e0191-129">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="e0191-130">Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="e0191-130">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="e0191-131">**/base :**`integer`</span><span class="sxs-lookup"><span data-stu-id="e0191-131">**/base:** `integer`</span></span>|<span data-ttu-id="e0191-132">Assigne à ImageBase la valeur spécifiée par `integer` dans l'en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="e0191-132">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="e0191-133">Lorsque la directive IL .imagebase est spécifiée dans le fichier, cette option se substitue à elle.</span><span class="sxs-lookup"><span data-stu-id="e0191-133">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="e0191-134">**/clock**</span><span class="sxs-lookup"><span data-stu-id="e0191-134">**/clock**</span></span>|<span data-ttu-id="e0191-135">Calcule et indique la durée des compilations suivantes, en millisecondes, pour le fichier source .il :</span><span class="sxs-lookup"><span data-stu-id="e0191-135">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="e0191-136">**Total Run**: Durée totale de l'exécution de toutes les opérations spécifiques qui suivent.</span><span class="sxs-lookup"><span data-stu-id="e0191-136">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="e0191-137">**Startup**: Chargement et ouverture du fichier.</span><span class="sxs-lookup"><span data-stu-id="e0191-137">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="e0191-138">**Emitting MD**: Émission de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e0191-138">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="e0191-139">**Ref to Def Resolution**: Résolution des références aux définitions dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="e0191-139">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="e0191-140">**CEE File Generation**: Génération de l'image du fichier en mémoire.</span><span class="sxs-lookup"><span data-stu-id="e0191-140">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="e0191-141">**PE File Writing**: Écriture de l'image dans un fichier PE.</span><span class="sxs-lookup"><span data-stu-id="e0191-141">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="e0191-142">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="e0191-142">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="e0191-143">Inclut des informations de débogage (noms des variables locales et des arguments et numéros de ligne).</span><span class="sxs-lookup"><span data-stu-id="e0191-143">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="e0191-144">Crée un fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="e0191-144">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="e0191-145">**/debug** sans valeur supplémentaire désactive l'optimisation JIT et utilise des points de séquence du fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="e0191-145">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="e0191-146">**IMPL** désactive l'optimisation JIT et utilise des points de séquence implicites.</span><span class="sxs-lookup"><span data-stu-id="e0191-146">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="e0191-147">**OPT** active l'optimisation JIT et utilise des points de séquence implicites.</span><span class="sxs-lookup"><span data-stu-id="e0191-147">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="e0191-148">**/dll**</span><span class="sxs-lookup"><span data-stu-id="e0191-148">**/dll**</span></span>|<span data-ttu-id="e0191-149">Produit un fichier *. dll* en tant que sortie.</span><span class="sxs-lookup"><span data-stu-id="e0191-149">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="e0191-150">**/enc :**`file`</span><span class="sxs-lookup"><span data-stu-id="e0191-150">**/enc:** `file`</span></span>|<span data-ttu-id="e0191-151">Crée des deltas Modifier && Continuer à partir du fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="e0191-151">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="e0191-152">Cet argument est utilisé uniquement à titre d'information et n'est pas pris en charge pour une utilisation commerciale.</span><span class="sxs-lookup"><span data-stu-id="e0191-152">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="e0191-153">**/exe**</span><span class="sxs-lookup"><span data-stu-id="e0191-153">**/exe**</span></span>|<span data-ttu-id="e0191-154">Génère un fichier exécutable en tant que sortie.</span><span class="sxs-lookup"><span data-stu-id="e0191-154">Produces an executable file as output.</span></span> <span data-ttu-id="e0191-155">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e0191-155">This is the default.</span></span>|
|<span data-ttu-id="e0191-156">**/Flags :**`integer`</span><span class="sxs-lookup"><span data-stu-id="e0191-156">**/flags:** `integer`</span></span>|<span data-ttu-id="e0191-157">Assigne à ImageFlags la valeur spécifiée par `integer` dans l'en-tête du Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="e0191-157">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="e0191-158">Lorsque la directive IL .corflags est spécifiée dans le fichier, cette option se substitue à elle.</span><span class="sxs-lookup"><span data-stu-id="e0191-158">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="e0191-159">Consultez CorHdr.h , COMIMAGE_FLAGS pour obtenir la liste des valeurs valides pour *integer*.</span><span class="sxs-lookup"><span data-stu-id="e0191-159">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="e0191-160">**/fold**</span><span class="sxs-lookup"><span data-stu-id="e0191-160">**/fold**</span></span>|<span data-ttu-id="e0191-161">Insère des corps de méthode identiques en un seul.</span><span class="sxs-lookup"><span data-stu-id="e0191-161">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="e0191-162">/**highentropyva**</span><span class="sxs-lookup"><span data-stu-id="e0191-162">/**highentropyva**</span></span>|<span data-ttu-id="e0191-163">Produit un fichier exécutable de sortie qui prend en charge l'Address Space Layout Randomization (ASLR) de forte entropie.</span><span class="sxs-lookup"><span data-stu-id="e0191-163">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="e0191-164">(Par défaut pour **/appcontainer**)</span><span class="sxs-lookup"><span data-stu-id="e0191-164">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="e0191-165">**/include :**`includePath`</span><span class="sxs-lookup"><span data-stu-id="e0191-165">**/include:** `includePath`</span></span>|<span data-ttu-id="e0191-166">Définit un chemin d'accès pour rechercher des fichiers fournis avec `#include`.</span><span class="sxs-lookup"><span data-stu-id="e0191-166">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="e0191-167">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="e0191-167">**/itanium**</span></span>|<span data-ttu-id="e0191-168">Spécifie Intel Itanium comme processeur cible.</span><span class="sxs-lookup"><span data-stu-id="e0191-168">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="e0191-169">Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="e0191-169">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="e0191-170">**/Key :**`keyFile`</span><span class="sxs-lookup"><span data-stu-id="e0191-170">**/key:** `keyFile`</span></span>|<span data-ttu-id="e0191-171">Compile `filename` avec une signature forte à l’aide de la clé privée figurant dans `keyFile`.</span><span class="sxs-lookup"><span data-stu-id="e0191-171">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="e0191-172">**/Key** @`keySource`</span><span class="sxs-lookup"><span data-stu-id="e0191-172">**/key:** @`keySource`</span></span>|<span data-ttu-id="e0191-173">Compile `filename` avec une signature forte à l’aide de la clé privée produite dans `keySource`.</span><span class="sxs-lookup"><span data-stu-id="e0191-173">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="e0191-174">**/Listing**</span><span class="sxs-lookup"><span data-stu-id="e0191-174">**/listing**</span></span>|<span data-ttu-id="e0191-175">Génère un fichier listing lors de la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="e0191-175">Produces a listing file on the standard output.</span></span> <span data-ttu-id="e0191-176">Si vous omettez cette option, aucun fichier listing n'est alors généré.</span><span class="sxs-lookup"><span data-stu-id="e0191-176">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="e0191-177">Ce paramètre n'est pas pris en charge dans les versions 2.0 et ultérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e0191-177">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="e0191-178">**/MDV :**`versionString`</span><span class="sxs-lookup"><span data-stu-id="e0191-178">**/mdv:** `versionString`</span></span>|<span data-ttu-id="e0191-179">Définit la chaîne de version de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e0191-179">Sets the metadata version string.</span></span>|
|<span data-ttu-id="e0191-180">**/mSv :** `major` .`minor`</span><span class="sxs-lookup"><span data-stu-id="e0191-180">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="e0191-181">Définit la version de flux de métadonnées, dans laquelle `major` et `minor` sont des entiers.</span><span class="sxs-lookup"><span data-stu-id="e0191-181">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="e0191-182">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="e0191-182">**/noautoinherit**</span></span>|<span data-ttu-id="e0191-183">Désactive l'héritage par défaut de <xref:System.Object> lorsque aucune classe de base n'est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e0191-183">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="e0191-184">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="e0191-184">**/nocorstub**</span></span>|<span data-ttu-id="e0191-185">Supprime la génération du stub CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="e0191-185">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="e0191-186">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="e0191-186">**/nologo**</span></span>|<span data-ttu-id="e0191-187">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e0191-187">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="e0191-188">**/Output :**`file.ext`</span><span class="sxs-lookup"><span data-stu-id="e0191-188">**/output:** `file.ext`</span></span>|<span data-ttu-id="e0191-189">Spécifie le nom du fichier de sortie et son extension.</span><span class="sxs-lookup"><span data-stu-id="e0191-189">Specifies the output file name and extension.</span></span> <span data-ttu-id="e0191-190">Le nom du fichier de sortie est, par défaut, le même que le nom du premier fichier source.</span><span class="sxs-lookup"><span data-stu-id="e0191-190">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="e0191-191">L’extension par défaut est *. exe*.</span><span class="sxs-lookup"><span data-stu-id="e0191-191">The default extension is *.exe*.</span></span> <span data-ttu-id="e0191-192">Si vous spécifiez l’option **/dll** , l’extension par défaut est *. dll*.</span><span class="sxs-lookup"><span data-stu-id="e0191-192">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="e0191-193">**Remarque :** La spécification de **/output**:myfile.dll ne définit pas l’option **/dll** .</span><span class="sxs-lookup"><span data-stu-id="e0191-193">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="e0191-194">Si vous ne spécifiez pas **/dll**, le résultat sera un fichier exécutable nommé *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="e0191-194">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="e0191-195">**/Optimize**</span><span class="sxs-lookup"><span data-stu-id="e0191-195">**/optimize**</span></span>|<span data-ttu-id="e0191-196">Optimise les instructions allongées en instructions abrégées.</span><span class="sxs-lookup"><span data-stu-id="e0191-196">Optimizes long instructions to short.</span></span> <span data-ttu-id="e0191-197">Par exemple, `br` en `br.s`.</span><span class="sxs-lookup"><span data-stu-id="e0191-197">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="e0191-198">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="e0191-198">**/pe64**</span></span>|<span data-ttu-id="e0191-199">Crée une image 64 bits (PE32+).</span><span class="sxs-lookup"><span data-stu-id="e0191-199">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="e0191-200">Si aucun processeur cible n'est spécifié, la valeur par défaut est `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="e0191-200">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="e0191-201">**/PDB**</span><span class="sxs-lookup"><span data-stu-id="e0191-201">**/pdb**</span></span>|<span data-ttu-id="e0191-202">Crée un fichier PDB sans activer le suivi des informations de débogage.</span><span class="sxs-lookup"><span data-stu-id="e0191-202">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="e0191-203">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="e0191-203">**/quiet**</span></span>|<span data-ttu-id="e0191-204">Spécifie le mode silencieux ; ne fait pas état de la progression de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="e0191-204">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="e0191-205">**/Resource :**`file.res`</span><span class="sxs-lookup"><span data-stu-id="e0191-205">**/resource:** `file.res`</span></span>|<span data-ttu-id="e0191-206">Contient le fichier de ressources spécifié au \* format. res dans le fichier *. exe* ou *. dll* qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="e0191-206">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="e0191-207">Un seul fichier .res peut être spécifié avec l'option **/resource** .</span><span class="sxs-lookup"><span data-stu-id="e0191-207">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="e0191-208">**/ssver :** `int` .`int`</span><span class="sxs-lookup"><span data-stu-id="e0191-208">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="e0191-209">Définit le numéro de version du sous-système dans l'en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="e0191-209">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="e0191-210">Pour **/appcontainer** et **/arm** le numéro de version minimale est 6.02.</span><span class="sxs-lookup"><span data-stu-id="e0191-210">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="e0191-211">**/Stack :**`stackSize`</span><span class="sxs-lookup"><span data-stu-id="e0191-211">**/stack:** `stackSize`</span></span>|<span data-ttu-id="e0191-212">Affecte `stackSize`à la valeur SizeOfStackReserve dans l'en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="e0191-212">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="e0191-213">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="e0191-213">**/stripreloc**</span></span>|<span data-ttu-id="e0191-214">Spécifie qu'aucun réadressage de base n'est requis.</span><span class="sxs-lookup"><span data-stu-id="e0191-214">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="e0191-215">**/SUBSYSTEM :**`integer`</span><span class="sxs-lookup"><span data-stu-id="e0191-215">**/subsystem:** `integer`</span></span>|<span data-ttu-id="e0191-216">Assigne à subsystem la valeur spécifiée par `integer` dans l’en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="e0191-216">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="e0191-217">Lorsque la directive IL .subsystem est spécifiée dans le fichier, cette option se substitue à elle.</span><span class="sxs-lookup"><span data-stu-id="e0191-217">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="e0191-218">Consultez winnt.h, IMAGE_SUBSYSTEM pour obtenir la liste des valeurs valides pour `integer`.</span><span class="sxs-lookup"><span data-stu-id="e0191-218">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="e0191-219">**/x64**</span><span class="sxs-lookup"><span data-stu-id="e0191-219">**/x64**</span></span>|<span data-ttu-id="e0191-220">Spécifie un processeur AMD 64 bits comme processeur cible.</span><span class="sxs-lookup"><span data-stu-id="e0191-220">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="e0191-221">Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="e0191-221">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="e0191-222">**/?**</span><span class="sxs-lookup"><span data-stu-id="e0191-222">**/?**</span></span>|<span data-ttu-id="e0191-223">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="e0191-223">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="e0191-224">Toutes les options de *Ilasm.exe* ne respectent pas la casse et sont reconnues par les trois premières lettres.</span><span class="sxs-lookup"><span data-stu-id="e0191-224">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="e0191-225">Par exemple, **/lis** est équivalent à **/Listing** et **/res**: myresfile. res équivaut à **/Resource**: myresfile. res. Les options qui spécifient des arguments acceptent un signe deux-points ( :) ou un signe égal (=) comme séparateur entre l’option et l’argument.</span><span class="sxs-lookup"><span data-stu-id="e0191-225">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="e0191-226">Par exemple, **/Output**:*file. ext* équivaut à **/Output** = *file. ext*.</span><span class="sxs-lookup"><span data-stu-id="e0191-226">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0191-227">Notes</span><span class="sxs-lookup"><span data-stu-id="e0191-227">Remarks</span></span>

<span data-ttu-id="e0191-228">L'Assembleur IL permet aux fournisseurs d'outils de concevoir et d'implémenter des générateurs IL.</span><span class="sxs-lookup"><span data-stu-id="e0191-228">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="e0191-229">À l’aide de *Ilasm.exe*, les développeurs d’outils et de compilateurs peuvent se concentrer sur la génération de langage intermédiaire et de métadonnées sans se préoccuper de l’émission du langage intermédiaire dans le format de fichier PE.</span><span class="sxs-lookup"><span data-stu-id="e0191-229">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="e0191-230">Semblable à d’autres compilateurs ciblant le runtime, tels que C# et Visual Basic, *Ilasm.exe* ne génère pas de fichiers objets intermédiaires et ne requiert pas d’étape de liaison pour former un fichier PE.</span><span class="sxs-lookup"><span data-stu-id="e0191-230">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="e0191-231">L'Assembleur IL peut exprimer toutes les fonctionnalités métadonnées et IL existantes des langages de programmation ayant pour cible le runtime.</span><span class="sxs-lookup"><span data-stu-id="e0191-231">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="e0191-232">Cela permet au code managé écrit dans l’un de ces langages de programmation d’être correctement exprimé dans l’assembleur IL et compilé avec *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="e0191-232">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="e0191-233">La compilation peut échouer si la dernière ligne de code du fichier source .il ne comporte pas d'espace blanc de fin ou de caractère de fin de ligne.</span><span class="sxs-lookup"><span data-stu-id="e0191-233">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="e0191-234">Vous pouvez utiliser *Ilasm.exe* conjointement avec son outil d’accompagnement, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="e0191-234">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="e0191-235">*Ildasm.exe* prend un fichier PE qui contient le code il et crée un fichier texte pouvant servir d’entrée pour *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="e0191-235">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="e0191-236">Cet outil s'avère, par exemple, utile lors de la compilation d'un code dans un langage de programmation ne prenant pas en charge tous les attributs de métadonnées du runtime.</span><span class="sxs-lookup"><span data-stu-id="e0191-236">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="e0191-237">Après la compilation du code et l’exécution de la sortie via *Ildasm.exe*, le fichier texte il obtenu peut être modifié manuellement pour ajouter les attributs manquants.</span><span class="sxs-lookup"><span data-stu-id="e0191-237">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="e0191-238">Vous pouvez ensuite exécuter ce fichier texte via le *Ilasm.exe* pour générer un fichier exécutable final.</span><span class="sxs-lookup"><span data-stu-id="e0191-238">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="e0191-239">Vous pouvez également utiliser cette technique pour générer un seul fichier exécutable portable à partir de plusieurs fichiers exécutables portables provenant de différents compilateurs.</span><span class="sxs-lookup"><span data-stu-id="e0191-239">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="e0191-240">Actuellement, vous ne pouvez pas utiliser cette technique avec des fichiers exécutables portables qui contiennent du code natif incorporé (par exemple, des fichiers exécutables portables générés par Visual C++).</span><span class="sxs-lookup"><span data-stu-id="e0191-240">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="e0191-241">Pour que cette utilisation combinée de *Ildasm.exe* et *Ilasm.exe* aussi précis que possible, l’assembleur ne substitue pas par défaut les encodages courts à des encodages longs que vous avez pu écrire dans vos sources il (ou qui peuvent être émises par un autre compilateur).</span><span class="sxs-lookup"><span data-stu-id="e0191-241">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="e0191-242">Utilisez l'option **/optimize** pour remplacer les encodages abrégés dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="e0191-242">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="e0191-243">*Ildasm.exe* ne s’applique qu’aux fichiers sur disque.</span><span class="sxs-lookup"><span data-stu-id="e0191-243">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="e0191-244">Il ne fonctionne pas avec des fichiers installés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="e0191-244">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="e0191-245">Pour plus d’informations sur la grammaire du langage IL, consultez le fichier asmparse.grammar dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="e0191-245">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="e0191-246">Informations sur la version</span><span class="sxs-lookup"><span data-stu-id="e0191-246">Version Information</span></span>

<span data-ttu-id="e0191-247">À compter de .NET Framework 4.5, joignez un attribut personnalisé à une implémentation d’interface à l’aide d’un code semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="e0191-247">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

<span data-ttu-id="e0191-248">À compter de .NET Framework 4.5, spécifiez un objet blob (Binary Large Object) marshal arbitraire à l’aide de sa représentation binaire brute, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e0191-248">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="e0191-249">Pour plus d’informations sur la grammaire du langage IL, consultez le fichier asmparse.grammar dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="e0191-249">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="e0191-250">Exemples</span><span class="sxs-lookup"><span data-stu-id="e0191-250">Examples</span></span>

<span data-ttu-id="e0191-251">La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier exécutable *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="e0191-251">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="e0191-252">La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier *.dll*, *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="e0191-252">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="e0191-253">La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier *.dll*, *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="e0191-253">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="e0191-254">L’exemple de code suivant illustre une application extrêmement simple qui affiche « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="e0191-254">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="e0191-255">dans la console.</span><span class="sxs-lookup"><span data-stu-id="e0191-255">to the console.</span></span> <span data-ttu-id="e0191-256">Vous pouvez compiler ce code, puis utiliser l’outil [*Ildasm.exe*](ildasm-exe-il-disassembler.md) pour générer un fichier il.</span><span class="sxs-lookup"><span data-stu-id="e0191-256">You can compile this code and then use the [*Ildasm.exe*](ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

<span data-ttu-id="e0191-257">L'exemple de code IL suivant correspond à l'exemple de code C# précédent.</span><span class="sxs-lookup"><span data-stu-id="e0191-257">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="e0191-258">Vous pouvez compiler ce code dans un assembly à l’aide de l’Assembleur IL.</span><span class="sxs-lookup"><span data-stu-id="e0191-258">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="e0191-259">Les exemples de code IL et C# affichent « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="e0191-259">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="e0191-260">dans la console.</span><span class="sxs-lookup"><span data-stu-id="e0191-260">to the console.</span></span>

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a><span data-ttu-id="e0191-261">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0191-261">See also</span></span>

- [<span data-ttu-id="e0191-262">outils</span><span class="sxs-lookup"><span data-stu-id="e0191-262">Tools</span></span>](index.md)
- [<span data-ttu-id="e0191-263">*Ildasm.exe* (Désassembleur il)</span><span class="sxs-lookup"><span data-stu-id="e0191-263">*Ildasm.exe* (IL Disassembler)</span></span>](ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="e0191-264">Processus d’exécution managée</span><span class="sxs-lookup"><span data-stu-id="e0191-264">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="e0191-265">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="e0191-265">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
