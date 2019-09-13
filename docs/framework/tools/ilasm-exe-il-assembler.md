---
title: Ilasm.exe (Assembleur IL)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcc9ba5e379897247f50175603b1002d5688d215
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894688"
---
# <a name="ilasmexe-il-assembler"></a><span data-ttu-id="79f8d-102">Ilasm.exe (Assembleur IL)</span><span class="sxs-lookup"><span data-stu-id="79f8d-102">Ilasm.exe (IL Assembler)</span></span>

<span data-ttu-id="79f8d-103">L'Assembleur IL génère un fichier PE (Portable Executable) en langage IL (Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="79f8d-103">The IL Assembler generates a portable executable (PE) file from intermediate language (IL).</span></span> <span data-ttu-id="79f8d-104">(Pour plus d’informations sur le langage IL, consultez [Processus d’exécution managée](../../standard/managed-execution-process.md).) Vous pouvez exécuter le fichier exécutable obtenu, qui comporte le langage IL et les métadonnées nécessaires, pour déterminer si le langage IL fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="79f8d-104">(For more information on IL, see [Managed Execution Process](../../standard/managed-execution-process.md).) You can run the resulting executable, which contains IL and the required metadata, to determine whether the IL performs as expected.</span></span>

<span data-ttu-id="79f8d-105">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79f8d-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="79f8d-106">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="79f8d-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="79f8d-107">Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="79f8d-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="79f8d-108">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="79f8d-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="79f8d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79f8d-109">Syntax</span></span>

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a><span data-ttu-id="79f8d-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79f8d-110">Parameters</span></span>

| <span data-ttu-id="79f8d-111">Argument</span><span class="sxs-lookup"><span data-stu-id="79f8d-111">Argument</span></span> | <span data-ttu-id="79f8d-112">Description</span><span class="sxs-lookup"><span data-stu-id="79f8d-112">Description</span></span> |
| -------- | ----------- |
|`filename`|<span data-ttu-id="79f8d-113">Nom du fichier source .il.</span><span class="sxs-lookup"><span data-stu-id="79f8d-113">The name of the .il source file.</span></span> <span data-ttu-id="79f8d-114">Ce fichier est composé de directives de déclaration de métadonnées et d'instructions IL symboliques.</span><span class="sxs-lookup"><span data-stu-id="79f8d-114">This file consists of metadata declaration directives and symbolic IL instructions.</span></span> <span data-ttu-id="79f8d-115">Plusieurs arguments du fichier source peuvent être fournis pour générer un seul fichier exécutable portable avec *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-115">Multiple source file arguments can be supplied to produce a single PE file with *Ilasm.exe*.</span></span> <span data-ttu-id="79f8d-116">**Remarque :** vérifiez que la dernière ligne de code du fichier source .il comporte un espace blanc de fin ou un caractère de fin de ligne.</span><span class="sxs-lookup"><span data-stu-id="79f8d-116">**Note:** Ensure that the last line of code in the .il source file has either trailing white space or an end-of-line character.</span></span>|

| <span data-ttu-id="79f8d-117">Option</span><span class="sxs-lookup"><span data-stu-id="79f8d-117">Option</span></span> | <span data-ttu-id="79f8d-118">Description</span><span class="sxs-lookup"><span data-stu-id="79f8d-118">Description</span></span> |
| ------ | ----------- |
|<span data-ttu-id="79f8d-119">**/32bitpreferred**</span><span class="sxs-lookup"><span data-stu-id="79f8d-119">**/32bitpreferred**</span></span>|<span data-ttu-id="79f8d-120">Crée une image 32 bits (PE32+).</span><span class="sxs-lookup"><span data-stu-id="79f8d-120">Creates a 32-bit-preferred image (PE32).</span></span>|
|<span data-ttu-id="79f8d-121">**/alignment:** `integer`</span><span class="sxs-lookup"><span data-stu-id="79f8d-121">**/alignment:** `integer`</span></span>|<span data-ttu-id="79f8d-122">Assigne à FileAlignment la valeur spécifiée par `integer` dans l'en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="79f8d-122">Sets FileAlignment to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="79f8d-123">Lorsque la directive IL .alignment est spécifiée dans le fichier, cette option se substitue à elle.</span><span class="sxs-lookup"><span data-stu-id="79f8d-123">If the .alignment IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="79f8d-124">**/appcontainer**</span><span class="sxs-lookup"><span data-stu-id="79f8d-124">**/appcontainer**</span></span>|<span data-ttu-id="79f8d-125">Produit un fichier *.dll* ou *.exe* qui s'exécute dans le conteneur d’application Windows comme sortie.</span><span class="sxs-lookup"><span data-stu-id="79f8d-125">Produces a *.dll* or *.exe* file that runs in the Windows app container, as output.</span></span>|
|<span data-ttu-id="79f8d-126">**/arm**</span><span class="sxs-lookup"><span data-stu-id="79f8d-126">**/arm**</span></span>|<span data-ttu-id="79f8d-127">Spécifie l'ordinateur (ARM) Advanced RISC comme processeur cible.</span><span class="sxs-lookup"><span data-stu-id="79f8d-127">Specifies the Advanced RISC Machine (ARM) as the target processor.</span></span><br /><br /> <span data-ttu-id="79f8d-128">Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/32bitpreferred**.</span><span class="sxs-lookup"><span data-stu-id="79f8d-128">If no image bitness is specified, the default is **/32bitpreferred**.</span></span>|
|<span data-ttu-id="79f8d-129">**/base:** `integer`</span><span class="sxs-lookup"><span data-stu-id="79f8d-129">**/base:** `integer`</span></span>|<span data-ttu-id="79f8d-130">Assigne à ImageBase la valeur spécifiée par `integer` dans l'en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="79f8d-130">Sets ImageBase to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="79f8d-131">Lorsque la directive IL .imagebase est spécifiée dans le fichier, cette option se substitue à elle.</span><span class="sxs-lookup"><span data-stu-id="79f8d-131">If the .imagebase IL directive is specified in the file, this option overrides it.</span></span>|
|<span data-ttu-id="79f8d-132">**/clock**</span><span class="sxs-lookup"><span data-stu-id="79f8d-132">**/clock**</span></span>|<span data-ttu-id="79f8d-133">Calcule et indique la durée des compilations suivantes, en millisecondes, pour le fichier source .il :</span><span class="sxs-lookup"><span data-stu-id="79f8d-133">Measures and reports the following compilation times in milliseconds for the specified .il source file:</span></span><br /><br /> <span data-ttu-id="79f8d-134">**Total Run** : Durée totale d’exécution de toutes les opérations spécifiques qui suivent.</span><span class="sxs-lookup"><span data-stu-id="79f8d-134">**Total Run**: The total time spent performing all the specific operations that follow.</span></span><br /><br /> <span data-ttu-id="79f8d-135">**Startup** : Chargement et ouverture du fichier.</span><span class="sxs-lookup"><span data-stu-id="79f8d-135">**Startup**: Loading and opening the file.</span></span><br /><br /> <span data-ttu-id="79f8d-136">**Emitting MD** : Envoi des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="79f8d-136">**Emitting MD**: Emitting metadata.</span></span><br /><br /> <span data-ttu-id="79f8d-137">**Ref to Def Resolution** : Résolution des références aux définitions dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="79f8d-137">**Ref to Def Resolution**: Resolving references to definitions in the file.</span></span><br /><br /> <span data-ttu-id="79f8d-138">**CEE File Generation** : Génération de l’image du fichier en mémoire.</span><span class="sxs-lookup"><span data-stu-id="79f8d-138">**CEE File Generation**: Generating the file image in memory.</span></span><br /><br /> <span data-ttu-id="79f8d-139">**Écriture du fichier PE** : Écriture de l’image dans un fichier PE.</span><span class="sxs-lookup"><span data-stu-id="79f8d-139">**PE File Writing**: Writing the image to a PE file.</span></span>|
|<span data-ttu-id="79f8d-140">**/debug**[:**IMPL**&#124;**OPT**]</span><span class="sxs-lookup"><span data-stu-id="79f8d-140">**/debug**[:**IMPL**&#124;**OPT**]</span></span>|<span data-ttu-id="79f8d-141">Inclut des informations de débogage (noms des variables locales et des arguments et numéros de ligne).</span><span class="sxs-lookup"><span data-stu-id="79f8d-141">Includes debug information (local variable and argument names, and line numbers).</span></span> <span data-ttu-id="79f8d-142">Crée un fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="79f8d-142">Creates a PDB file.</span></span><br /><br /> <span data-ttu-id="79f8d-143">**/debug** sans valeur supplémentaire désactive l'optimisation JIT et utilise des points de séquence du fichier PDB.</span><span class="sxs-lookup"><span data-stu-id="79f8d-143">**/debug** with no additional value disables JIT optimization and uses sequence points from the PDB file.</span></span><br /><br /> <span data-ttu-id="79f8d-144">**IMPL** désactive l'optimisation JIT et utilise des points de séquence implicites.</span><span class="sxs-lookup"><span data-stu-id="79f8d-144">**IMPL** disables JIT optimization and uses implicit sequence points.</span></span><br /><br /> <span data-ttu-id="79f8d-145">**OPT** active l'optimisation JIT et utilise des points de séquence implicites.</span><span class="sxs-lookup"><span data-stu-id="79f8d-145">**OPT** enables JIT optimization and uses implicit sequence points.</span></span>|
|<span data-ttu-id="79f8d-146">**/dll**</span><span class="sxs-lookup"><span data-stu-id="79f8d-146">**/dll**</span></span>|<span data-ttu-id="79f8d-147">Génère un fichier *.dll* en tant que sortie.</span><span class="sxs-lookup"><span data-stu-id="79f8d-147">Produces a *.dll* file as output.</span></span>|
|<span data-ttu-id="79f8d-148">**/enc:** `file`</span><span class="sxs-lookup"><span data-stu-id="79f8d-148">**/enc:** `file`</span></span>|<span data-ttu-id="79f8d-149">Crée des deltas Modifier && Continuer à partir du fichier source spécifié.</span><span class="sxs-lookup"><span data-stu-id="79f8d-149">Creates Edit-and-Continue deltas from the specified source file.</span></span><br /><br /> <span data-ttu-id="79f8d-150">Cet argument est utilisé uniquement à titre d'information et n'est pas pris en charge pour une utilisation commerciale.</span><span class="sxs-lookup"><span data-stu-id="79f8d-150">This argument is for academic use only and is not supported for commercial use.</span></span>|
|<span data-ttu-id="79f8d-151">**/exe**</span><span class="sxs-lookup"><span data-stu-id="79f8d-151">**/exe**</span></span>|<span data-ttu-id="79f8d-152">Génère un fichier exécutable en tant que sortie.</span><span class="sxs-lookup"><span data-stu-id="79f8d-152">Produces an executable file as output.</span></span> <span data-ttu-id="79f8d-153">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="79f8d-153">This is the default.</span></span>|
|<span data-ttu-id="79f8d-154">**/flags:** `integer`</span><span class="sxs-lookup"><span data-stu-id="79f8d-154">**/flags:** `integer`</span></span>|<span data-ttu-id="79f8d-155">Assigne à ImageFlags la valeur spécifiée par `integer` dans l'en-tête du Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="79f8d-155">Sets ImageFlags to the value specified by `integer` in the common language runtime header.</span></span> <span data-ttu-id="79f8d-156">Lorsque la directive IL .corflags est spécifiée dans le fichier, cette option se substitue à elle.</span><span class="sxs-lookup"><span data-stu-id="79f8d-156">If the .corflags IL directive is specified in the file, this option overrides it.</span></span> <span data-ttu-id="79f8d-157">Consultez CorHdr.h , COMIMAGE_FLAGS pour obtenir la liste des valeurs valides pour *integer*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-157">See CorHdr.h, COMIMAGE_FLAGS for a list of valid values for *integer*.</span></span>|
|<span data-ttu-id="79f8d-158">**/fold**</span><span class="sxs-lookup"><span data-stu-id="79f8d-158">**/fold**</span></span>|<span data-ttu-id="79f8d-159">Insère des corps de méthode identiques en un seul.</span><span class="sxs-lookup"><span data-stu-id="79f8d-159">Folds identical method bodies into one.</span></span>|
|<span data-ttu-id="79f8d-160">/ **/highentropyva**</span><span class="sxs-lookup"><span data-stu-id="79f8d-160">/**highentropyva**</span></span>|<span data-ttu-id="79f8d-161">Produit un fichier exécutable de sortie qui prend en charge l'Address Space Layout Randomization (ASLR) de forte entropie.</span><span class="sxs-lookup"><span data-stu-id="79f8d-161">Produces an output executable that supports high-entropy address space layout randomization (ASLR).</span></span> <span data-ttu-id="79f8d-162">(Par défaut pour **/appcontainer**)</span><span class="sxs-lookup"><span data-stu-id="79f8d-162">(Default for **/appcontainer**.)</span></span>|
|<span data-ttu-id="79f8d-163">**/include:** `includePath`</span><span class="sxs-lookup"><span data-stu-id="79f8d-163">**/include:** `includePath`</span></span>|<span data-ttu-id="79f8d-164">Définit un chemin d'accès pour rechercher des fichiers fournis avec `#include`.</span><span class="sxs-lookup"><span data-stu-id="79f8d-164">Sets a path to search for files included with `#include`.</span></span>|
|<span data-ttu-id="79f8d-165">**/itanium**</span><span class="sxs-lookup"><span data-stu-id="79f8d-165">**/itanium**</span></span>|<span data-ttu-id="79f8d-166">Spécifie Intel Itanium comme processeur cible.</span><span class="sxs-lookup"><span data-stu-id="79f8d-166">Specifies Intel Itanium as the target processor.</span></span><br /><br /> <span data-ttu-id="79f8d-167">Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="79f8d-167">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="79f8d-168">**/key:** `keyFile`</span><span class="sxs-lookup"><span data-stu-id="79f8d-168">**/key:** `keyFile`</span></span>|<span data-ttu-id="79f8d-169">Compile `filename` avec une signature forte à l’aide de la clé privée figurant dans `keyFile`.</span><span class="sxs-lookup"><span data-stu-id="79f8d-169">Compiles `filename` with a strong signature using the private key contained in `keyFile`.</span></span>|
|<span data-ttu-id="79f8d-170">**/key:**  @`keySource`</span><span class="sxs-lookup"><span data-stu-id="79f8d-170">**/key:** @`keySource`</span></span>|<span data-ttu-id="79f8d-171">Compile `filename` avec une signature forte à l’aide de la clé privée produite dans `keySource`.</span><span class="sxs-lookup"><span data-stu-id="79f8d-171">Compiles `filename` with a strong signature using the private key produced at `keySource`.</span></span>|
|<span data-ttu-id="79f8d-172">**/listing**</span><span class="sxs-lookup"><span data-stu-id="79f8d-172">**/listing**</span></span>|<span data-ttu-id="79f8d-173">Génère un fichier listing lors de la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="79f8d-173">Produces a listing file on the standard output.</span></span> <span data-ttu-id="79f8d-174">Si vous omettez cette option, aucun fichier listing n'est alors généré.</span><span class="sxs-lookup"><span data-stu-id="79f8d-174">If you omit this option, no listing file is produced.</span></span><br /><br /> <span data-ttu-id="79f8d-175">Ce paramètre n'est pas pris en charge dans les versions 2.0 et ultérieures du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79f8d-175">This parameter is not supported in the .NET Framework 2.0 or later.</span></span>|
|<span data-ttu-id="79f8d-176">**/mdv:** `versionString`</span><span class="sxs-lookup"><span data-stu-id="79f8d-176">**/mdv:** `versionString`</span></span>|<span data-ttu-id="79f8d-177">Définit la chaîne de version de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="79f8d-177">Sets the metadata version string.</span></span>|
|<span data-ttu-id="79f8d-178">**/msv:** `major`.`minor`</span><span class="sxs-lookup"><span data-stu-id="79f8d-178">**/msv:** `major`.`minor`</span></span>|<span data-ttu-id="79f8d-179">Définit la version de flux de métadonnées, dans laquelle `major` et `minor` sont des entiers.</span><span class="sxs-lookup"><span data-stu-id="79f8d-179">Sets the metadata stream version, where `major` and `minor` are integers.</span></span>|
|<span data-ttu-id="79f8d-180">**/noautoinherit**</span><span class="sxs-lookup"><span data-stu-id="79f8d-180">**/noautoinherit**</span></span>|<span data-ttu-id="79f8d-181">Désactive l'héritage par défaut de <xref:System.Object> lorsque aucune classe de base n'est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="79f8d-181">Disables default inheritance from <xref:System.Object> when no base class is specified.</span></span>|
|<span data-ttu-id="79f8d-182">**/nocorstub**</span><span class="sxs-lookup"><span data-stu-id="79f8d-182">**/nocorstub**</span></span>|<span data-ttu-id="79f8d-183">Supprime la génération du stub CORExeMain.</span><span class="sxs-lookup"><span data-stu-id="79f8d-183">Suppresses generation of the CORExeMain stub.</span></span>|
|<span data-ttu-id="79f8d-184">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="79f8d-184">**/nologo**</span></span>|<span data-ttu-id="79f8d-185">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="79f8d-185">Suppresses the Microsoft startup banner display.</span></span>|
|<span data-ttu-id="79f8d-186">**/output:** `file.ext`</span><span class="sxs-lookup"><span data-stu-id="79f8d-186">**/output:** `file.ext`</span></span>|<span data-ttu-id="79f8d-187">Spécifie le nom du fichier de sortie et son extension.</span><span class="sxs-lookup"><span data-stu-id="79f8d-187">Specifies the output file name and extension.</span></span> <span data-ttu-id="79f8d-188">Le nom du fichier de sortie est, par défaut, le même que le nom du premier fichier source.</span><span class="sxs-lookup"><span data-stu-id="79f8d-188">By default, the output file name is the same as the name of the first source file.</span></span> <span data-ttu-id="79f8d-189">L’extension par défaut est *.exe*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-189">The default extension is *.exe*.</span></span> <span data-ttu-id="79f8d-190">Si vous spécifiez l'option **/dll**, l'extension par défaut est *.dll*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-190">If you specify the **/dll** option, the default extension is *.dll*.</span></span> <span data-ttu-id="79f8d-191">**Remarque :** La spécification de **/output**:myfile.dll ne définit pas l’option **/dll**.</span><span class="sxs-lookup"><span data-stu-id="79f8d-191">**Note:** Specifying **/output**:myfile.dll does not set the **/dll** option.</span></span> <span data-ttu-id="79f8d-192">Si vous ne spécifiez pas l’option **/dll**, il en résultera un fichier exécutable nommé *myfile.dll*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-192">If you do not specify **/dll**, the result will be an executable file named *myfile.dll*.</span></span>|
|<span data-ttu-id="79f8d-193">**/optimize**</span><span class="sxs-lookup"><span data-stu-id="79f8d-193">**/optimize**</span></span>|<span data-ttu-id="79f8d-194">Optimise les instructions allongées en instructions abrégées.</span><span class="sxs-lookup"><span data-stu-id="79f8d-194">Optimizes long instructions to short.</span></span> <span data-ttu-id="79f8d-195">Par exemple, `br` en `br.s`.</span><span class="sxs-lookup"><span data-stu-id="79f8d-195">For example, `br` to `br.s`.</span></span>|
|<span data-ttu-id="79f8d-196">**/pe64**</span><span class="sxs-lookup"><span data-stu-id="79f8d-196">**/pe64**</span></span>|<span data-ttu-id="79f8d-197">Crée une image 64 bits (PE32+).</span><span class="sxs-lookup"><span data-stu-id="79f8d-197">Creates a 64-bit image (PE32+).</span></span><br /><br /> <span data-ttu-id="79f8d-198">Si aucun processeur cible n'est spécifié, la valeur par défaut est `/itanium`.</span><span class="sxs-lookup"><span data-stu-id="79f8d-198">If no target processor is specified, the default is `/itanium`.</span></span>|
|<span data-ttu-id="79f8d-199">**/pdb**</span><span class="sxs-lookup"><span data-stu-id="79f8d-199">**/pdb**</span></span>|<span data-ttu-id="79f8d-200">Crée un fichier PDB sans activer le suivi des informations de débogage.</span><span class="sxs-lookup"><span data-stu-id="79f8d-200">Creates a PDB file without enabling debug information tracking.</span></span>|
|<span data-ttu-id="79f8d-201">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="79f8d-201">**/quiet**</span></span>|<span data-ttu-id="79f8d-202">Spécifie le mode silencieux ; ne fait pas état de la progression de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="79f8d-202">Specifies quiet mode; does not report assembly progress.</span></span>|
|<span data-ttu-id="79f8d-203">**/resource:** `file.res`</span><span class="sxs-lookup"><span data-stu-id="79f8d-203">**/resource:** `file.res`</span></span>|<span data-ttu-id="79f8d-204">Inclut le fichier de ressources spécifié au format \*.res dans le fichier *.exe* ou *.dll* obtenu.</span><span class="sxs-lookup"><span data-stu-id="79f8d-204">Includes the specified resource file in \*.res format in the resulting *.exe* or *.dll* file.</span></span> <span data-ttu-id="79f8d-205">Un seul fichier .res peut être spécifié avec l'option **/resource** .</span><span class="sxs-lookup"><span data-stu-id="79f8d-205">Only one .res file can be specified with the **/resource** option.</span></span>|
|<span data-ttu-id="79f8d-206">**/ssver:** `int`.`int`</span><span class="sxs-lookup"><span data-stu-id="79f8d-206">**/ssver:** `int`.`int`</span></span>|<span data-ttu-id="79f8d-207">Définit le numéro de version du sous-système dans l'en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="79f8d-207">Sets the subsystem version number in the NT optional header.</span></span> <span data-ttu-id="79f8d-208">Pour **/appcontainer** et **/arm** le numéro de version minimale est 6.02.</span><span class="sxs-lookup"><span data-stu-id="79f8d-208">For **/appcontainer** and **/arm** the minimum version number is 6.02.</span></span>|
|<span data-ttu-id="79f8d-209">**/stack:** `stackSize`</span><span class="sxs-lookup"><span data-stu-id="79f8d-209">**/stack:** `stackSize`</span></span>|<span data-ttu-id="79f8d-210">Affecte `stackSize`à la valeur SizeOfStackReserve dans l'en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="79f8d-210">Sets the SizeOfStackReserve value in the NT Optional header to `stackSize`.</span></span>|
|<span data-ttu-id="79f8d-211">**/stripreloc**</span><span class="sxs-lookup"><span data-stu-id="79f8d-211">**/stripreloc**</span></span>|<span data-ttu-id="79f8d-212">Spécifie qu'aucun réadressage de base n'est requis.</span><span class="sxs-lookup"><span data-stu-id="79f8d-212">Specifies that no base relocations are needed.</span></span>|
|<span data-ttu-id="79f8d-213">**/subsystem:** `integer`</span><span class="sxs-lookup"><span data-stu-id="79f8d-213">**/subsystem:** `integer`</span></span>|<span data-ttu-id="79f8d-214">Assigne à subsystem la valeur spécifiée par `integer` dans l’en-tête Optional NT.</span><span class="sxs-lookup"><span data-stu-id="79f8d-214">Sets subsystem to the value specified by `integer` in the NT Optional header.</span></span> <span data-ttu-id="79f8d-215">Lorsque la directive IL .subsystem est spécifiée dans le fichier, cette option se substitue à elle.</span><span class="sxs-lookup"><span data-stu-id="79f8d-215">If the .subsystem IL directive is specified in the file, this command overrides it.</span></span> <span data-ttu-id="79f8d-216">Consultez winnt.h, IMAGE_SUBSYSTEM pour obtenir la liste des valeurs valides pour `integer`.</span><span class="sxs-lookup"><span data-stu-id="79f8d-216">See winnt.h, IMAGE_SUBSYSTEM for a list of valid values for `integer`.</span></span>|
|<span data-ttu-id="79f8d-217">**/x64**</span><span class="sxs-lookup"><span data-stu-id="79f8d-217">**/x64**</span></span>|<span data-ttu-id="79f8d-218">Spécifie un processeur AMD 64 bits comme processeur cible.</span><span class="sxs-lookup"><span data-stu-id="79f8d-218">Specifies a 64-bit AMD processor as the target processor.</span></span><br /><br /> <span data-ttu-id="79f8d-219">Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/pe64**.</span><span class="sxs-lookup"><span data-stu-id="79f8d-219">If no image bitness is specified, the default is **/pe64**.</span></span>|
|<span data-ttu-id="79f8d-220">**/?**</span><span class="sxs-lookup"><span data-stu-id="79f8d-220">**/?**</span></span>|<span data-ttu-id="79f8d-221">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="79f8d-221">Displays command syntax and options for the tool.</span></span>|

> [!NOTE]
> <span data-ttu-id="79f8d-222">Aucune option d’*Ilasm.exe* ne respecte la casse et toutes se reconnaissent à leurs trois premières lettres.</span><span class="sxs-lookup"><span data-stu-id="79f8d-222">All options for *Ilasm.exe* are case-insensitive and recognized by the first three letters.</span></span> <span data-ttu-id="79f8d-223">Par exemple, **/lis** équivaut à **/listing** et **/res:** myresfile.res équivaut à **/resource:** myresfile.res. Les options spécifiant des arguments prennent en charge les deux-points (:) ou le signe égal (=) en tant que séparateur entre l'option et l'argument.</span><span class="sxs-lookup"><span data-stu-id="79f8d-223">For example, **/lis** is equivalent to **/listing** and **/res**:myresfile.res is equivalent to **/resource**:myresfile.res. Options that specify arguments accept either a colon (:) or an equal sign (=) as the separator between the option and the argument.</span></span> <span data-ttu-id="79f8d-224">Par exemple, **/output**:*file.ext* équivaut à **/output**=*file.ext*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-224">For example, **/output**:*file.ext* is equivalent to **/output**=*file.ext*.</span></span>

## <a name="remarks"></a><span data-ttu-id="79f8d-225">Notes</span><span class="sxs-lookup"><span data-stu-id="79f8d-225">Remarks</span></span>

<span data-ttu-id="79f8d-226">L'Assembleur IL permet aux fournisseurs d'outils de concevoir et d'implémenter des générateurs IL.</span><span class="sxs-lookup"><span data-stu-id="79f8d-226">The IL Assembler helps tool vendors design and implement IL generators.</span></span> <span data-ttu-id="79f8d-227">Avec *Ilasm.exe*, les développeurs d’outils et de compilateurs peuvent se concentrer sur le langage IL et la génération de métadonnées sans se préoccuper de l’émission du langage IL au format de fichier exécutable portable.</span><span class="sxs-lookup"><span data-stu-id="79f8d-227">Using *Ilasm.exe*, tool and compiler developers can concentrate on IL and metadata generation without being concerned with emitting IL in the PE file format.</span></span>

<span data-ttu-id="79f8d-228">Comparable à d'autres compilateurs ayant pour cible le runtime, tels que C# et Visual Basic, *Ilasm.exe* ne génère pas de fichiers objets intermédiaires et ne nécessite pas d’étape de liaison pour constituer un fichier exécutable portable.</span><span class="sxs-lookup"><span data-stu-id="79f8d-228">Similar to other compilers that target the runtime, such as C# and Visual Basic, *Ilasm.exe* does not produce intermediate object files and does not require a linking stage to form a PE file.</span></span>

<span data-ttu-id="79f8d-229">L'Assembleur IL peut exprimer toutes les fonctionnalités métadonnées et IL existantes des langages de programmation ayant pour cible le runtime.</span><span class="sxs-lookup"><span data-stu-id="79f8d-229">The IL Assembler can express all the existing metadata and IL features of the programming languages that target the runtime.</span></span> <span data-ttu-id="79f8d-230">Du code managé écrit dans l’un de ces langages de programmation peut ainsi être correctement exprimé dans l’Assembleur IL et compilé avec *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-230">This allows managed code written in any of these programming languages to be adequately expressed in IL Assembler and compiled with *Ilasm.exe*.</span></span>

> [!NOTE]
> <span data-ttu-id="79f8d-231">La compilation peut échouer si la dernière ligne de code du fichier source .il ne comporte pas d'espace blanc de fin ou de caractère de fin de ligne.</span><span class="sxs-lookup"><span data-stu-id="79f8d-231">Compilation might fail if the last line of code in the .il source file does not have either trailing white space or an end-of-line character.</span></span>

<span data-ttu-id="79f8d-232">Vous pouvez utiliser *Ilasm.exe* avec l’outil qui lui est associé, [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span><span class="sxs-lookup"><span data-stu-id="79f8d-232">You can use *Ilasm.exe* in conjunction with its companion tool, [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).</span></span> <span data-ttu-id="79f8d-233">*Ildasm.exe* utilise un fichier PE qui contient le code IL et crée un fichier texte qu’il peut utiliser en entrée dans *Ilasm.exe*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-233">*Ildasm.exe* takes a PE file that contains IL code and creates a text file suitable as input to *Ilasm.exe*.</span></span> <span data-ttu-id="79f8d-234">Cet outil s'avère, par exemple, utile lors de la compilation d'un code dans un langage de programmation ne prenant pas en charge tous les attributs de métadonnées du runtime.</span><span class="sxs-lookup"><span data-stu-id="79f8d-234">This is useful, for example, when compiling code in a programming language that does not support all the runtime metadata attributes.</span></span> <span data-ttu-id="79f8d-235">Une fois le code compilé et la sortie exécutée via *Ildasm.exe*, le fichier texte IL obtenu peut être modifié manuellement pour y ajouter les attributs manquants.</span><span class="sxs-lookup"><span data-stu-id="79f8d-235">After compiling the code and running the output through *Ildasm.exe*, the resulting IL text file can be hand-edited to add the missing attributes.</span></span> <span data-ttu-id="79f8d-236">Vous pouvez ensuite exécuter ce fichier texte via *Ilasm.exe* pour générer un fichier exécutable final.</span><span class="sxs-lookup"><span data-stu-id="79f8d-236">You can then run this text file through the *Ilasm.exe* to produce a final executable file.</span></span>

<span data-ttu-id="79f8d-237">Vous pouvez également utiliser cette technique pour générer un seul fichier exécutable portable à partir de plusieurs fichiers exécutables portables provenant de différents compilateurs.</span><span class="sxs-lookup"><span data-stu-id="79f8d-237">You can also use this technique to produce a single PE file from several PE files originally generated by different compilers.</span></span>

> [!NOTE]
> <span data-ttu-id="79f8d-238">Actuellement, vous ne pouvez pas utiliser cette technique avec des fichiers exécutables portables qui contiennent du code natif incorporé (par exemple, des fichiers exécutables portables générés par Visual C++).</span><span class="sxs-lookup"><span data-stu-id="79f8d-238">Currently, you cannot use this technique with PE files that contain embedded native code (for example, PE files produced by Visual C++).</span></span>

<span data-ttu-id="79f8d-239">Pour que cette utilisation conjointe d’*Ildasm.exe* et d’*Ilasm.exe* soit la plus exacte possible, l’assembleur ne substitue pas par défaut les encodages abrégés par un codage allongé que vous avez pu écrire dans vos sources IL (ou qu’un autre compilateur a pu émettre).</span><span class="sxs-lookup"><span data-stu-id="79f8d-239">To make this combined use of *Ildasm.exe* and *Ilasm.exe* as accurate as possible, by default the assembler does not substitute short encodings for long ones you might have written in your IL sources (or that might be emitted by another compiler).</span></span> <span data-ttu-id="79f8d-240">Utilisez l'option **/optimize** pour remplacer les encodages abrégés dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="79f8d-240">Use the **/optimize** option to substitute short encodings wherever possible.</span></span>

> [!NOTE]
> <span data-ttu-id="79f8d-241">*Ildasm.exe* ne fonctionne qu’avec des fichiers stockés sur le disque.</span><span class="sxs-lookup"><span data-stu-id="79f8d-241">*Ildasm.exe* only operates on files on disk.</span></span> <span data-ttu-id="79f8d-242">Il ne fonctionne pas avec des fichiers installés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="79f8d-242">It does not operate on files installed in the global assembly cache.</span></span>

<span data-ttu-id="79f8d-243">Pour plus d’informations sur la grammaire du langage IL, consultez le fichier asmparse.grammar dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="79f8d-243">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="version-information"></a><span data-ttu-id="79f8d-244">Informations sur la version</span><span class="sxs-lookup"><span data-stu-id="79f8d-244">Version Information</span></span>

<span data-ttu-id="79f8d-245">À compter de .NET Framework 4.5, joignez un attribut personnalisé à une implémentation d’interface à l’aide d’un code semblable au suivant :</span><span class="sxs-lookup"><span data-stu-id="79f8d-245">Starting with the .NET Framework 4.5, you can attach a custom attribute to an interface implementation by using code similar to the following:</span></span>

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

<span data-ttu-id="79f8d-246">À compter de .NET Framework 4.5, spécifiez un objet blob (Binary Large Object) marshal arbitraire à l’aide de sa représentation binaire brute, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="79f8d-246">Starting with the .NET Framework 4.5, you can specify an arbitrary marshal BLOB (binary large object) by using its raw binary representation, as shown in the following code:</span></span>

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

<span data-ttu-id="79f8d-247">Pour plus d’informations sur la grammaire du langage IL, consultez le fichier asmparse.grammar dans le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="79f8d-247">For more information about the grammar of IL, see the asmparse.grammar file in the Windows SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="79f8d-248">Exemples</span><span class="sxs-lookup"><span data-stu-id="79f8d-248">Examples</span></span>

<span data-ttu-id="79f8d-249">La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier exécutable *myTestFile.exe*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-249">The following command assembles the IL file *myTestFile.il* and produces the executable *myTestFile.exe*.</span></span>

```console
ilasm myTestFile
```

<span data-ttu-id="79f8d-250">La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier *.dll*, *myTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-250">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll
```

<span data-ttu-id="79f8d-251">La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier *.dll*, *myNewTestFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="79f8d-251">The following command assembles the IL file *myTestFile.il* and produces the *.dll* file *myNewTestFile.dll*.</span></span>

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

<span data-ttu-id="79f8d-252">L’exemple de code suivant illustre une application extrêmement simple qui affiche « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="79f8d-252">The following code example shows an extremely simple application that displays "Hello World!"</span></span> <span data-ttu-id="79f8d-253">dans la console.</span><span class="sxs-lookup"><span data-stu-id="79f8d-253">to the console.</span></span> <span data-ttu-id="79f8d-254">Vous pouvez compiler ce code, puis utiliser l’outil [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour générer un fichier IL.</span><span class="sxs-lookup"><span data-stu-id="79f8d-254">You can compile this code and then use the [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tool to generate an IL file.</span></span>

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

<span data-ttu-id="79f8d-255">L'exemple de code IL suivant correspond à l'exemple de code C# précédent.</span><span class="sxs-lookup"><span data-stu-id="79f8d-255">The following IL code example corresponds to the previous C# code example.</span></span> <span data-ttu-id="79f8d-256">Vous pouvez compiler ce code dans un assembly à l’aide de l’Assembleur IL.</span><span class="sxs-lookup"><span data-stu-id="79f8d-256">You can compile this code into an assembly using the IL Assembler tool.</span></span> <span data-ttu-id="79f8d-257">Les exemples de code IL et C# affichent « Hello World! »</span><span class="sxs-lookup"><span data-stu-id="79f8d-257">Both IL and C# code examples display "Hello World!"</span></span> <span data-ttu-id="79f8d-258">dans la console.</span><span class="sxs-lookup"><span data-stu-id="79f8d-258">to the console.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="79f8d-259">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79f8d-259">See also</span></span>

- [<span data-ttu-id="79f8d-260">Outils</span><span class="sxs-lookup"><span data-stu-id="79f8d-260">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="79f8d-261">*Ildasm.exe* (Désassembleur IL)</span><span class="sxs-lookup"><span data-stu-id="79f8d-261">*Ildasm.exe* (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="79f8d-262">Processus d'exécution managée</span><span class="sxs-lookup"><span data-stu-id="79f8d-262">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="79f8d-263">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="79f8d-263">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
