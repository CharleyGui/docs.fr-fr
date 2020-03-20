---
title: Lc.exe (License Compiler)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 464514a241cc35fc821049ba0c29bec108d88253
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180396"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="1f058-102">Lc.exe (License Compiler)</span><span class="sxs-lookup"><span data-stu-id="1f058-102">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="1f058-103">L'outil License Compiler lit les fichiers texte comportant des informations sur les licences et génère un fichier binaire pouvant être incorporé dans un exécutable du Common Language Runtime en tant que ressource.</span><span class="sxs-lookup"><span data-stu-id="1f058-103">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="1f058-104">Un fichier .licx est automatiquement généré ou mis à jour par le concepteur Windows Forms lorsqu'un contrôle sous licence est ajouté au formulaire.</span><span class="sxs-lookup"><span data-stu-id="1f058-104">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="1f058-105">Dans le cadre de la compilation, le système de projet transforme le fichier texte .licx en ressource binaire .licenses qui assure la prise en charge des licences de contrôles .NET.</span><span class="sxs-lookup"><span data-stu-id="1f058-105">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="1f058-106">La ressource binaire est ensuite incorporée dans la sortie de projet.</span><span class="sxs-lookup"><span data-stu-id="1f058-106">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="1f058-107">La compilation croisée entre 32 bits et 64 bits n'est pas prise en charge lorsque vous utilisez l'outil License Compiler lors de la génération de votre projet.</span><span class="sxs-lookup"><span data-stu-id="1f058-107">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="1f058-108">Cela est dû au fait que l'outil License Compiler doit charger des assemblys et que le chargement d'assemblys 64 bits depuis une application 32 bits n'est pas autorisé, et vice versa.</span><span class="sxs-lookup"><span data-stu-id="1f058-108">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="1f058-109">Dans ce cas, utilisez l'outil License Compiler à partir de la ligne de commande pour compiler la licence manuellement et spécifiez l'architecture correspondante.</span><span class="sxs-lookup"><span data-stu-id="1f058-109">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="1f058-110">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1f058-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="1f058-111">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="1f058-111">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="1f058-112">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1f058-112">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="1f058-113">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="1f058-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f058-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f058-114">Syntax</span></span>  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="1f058-115">Option</span><span class="sxs-lookup"><span data-stu-id="1f058-115">Option</span></span>|<span data-ttu-id="1f058-116">Description</span><span class="sxs-lookup"><span data-stu-id="1f058-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1f058-117">**/complist:** *filename*</span><span class="sxs-lookup"><span data-stu-id="1f058-117">**/complist:** *filename*</span></span>|<span data-ttu-id="1f058-118">Spécifie le nom d'un fichier comportant la liste des composants sous licence à inclure dans le fichier .licenses.</span><span class="sxs-lookup"><span data-stu-id="1f058-118">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="1f058-119">Chaque composant est référencé avec son nom complet (un seul composant par ligne).</span><span class="sxs-lookup"><span data-stu-id="1f058-119">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="1f058-120">Les utilisateurs de ligne de commande peuvent spécifier un fichier distinct pour chaque formulaire du projet.</span><span class="sxs-lookup"><span data-stu-id="1f058-120">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="1f058-121">Lc.exe accepte plusieurs fichiers d'entrée et génère un seul fichier .licenses.</span><span class="sxs-lookup"><span data-stu-id="1f058-121">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="1f058-122">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="1f058-122">**/h**[**elp**]</span></span>|<span data-ttu-id="1f058-123">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="1f058-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="1f058-124">**/i:** *module*</span><span class="sxs-lookup"><span data-stu-id="1f058-124">**/i:** *module*</span></span>|<span data-ttu-id="1f058-125">Spécifie les modules contenant les composants répertoriés dans le fichier **/complist**.</span><span class="sxs-lookup"><span data-stu-id="1f058-125">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="1f058-126">Pour spécifier plusieurs modules, utilisez plusieurs indicateurs **/i**.</span><span class="sxs-lookup"><span data-stu-id="1f058-126">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="1f058-127">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="1f058-127">**/nologo**</span></span>|<span data-ttu-id="1f058-128">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1f058-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="1f058-129">**/outdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="1f058-129">**/outdir:** *path*</span></span>|<span data-ttu-id="1f058-130">Spécifie le répertoire dans lequel placer le fichier .licenses de sortie.</span><span class="sxs-lookup"><span data-stu-id="1f058-130">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="1f058-131">**/target:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="1f058-131">**/target:** *targetPE*</span></span>|<span data-ttu-id="1f058-132">Spécifie l'exécutable pour lequel le fichier .licenses est en cours de génération.</span><span class="sxs-lookup"><span data-stu-id="1f058-132">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="1f058-133">**/v**</span><span class="sxs-lookup"><span data-stu-id="1f058-133">**/v**</span></span>|<span data-ttu-id="1f058-134">Spécifie le mode détaillé ; affiche des informations sur la progression de la compilation.</span><span class="sxs-lookup"><span data-stu-id="1f058-134">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="1f058-135">\**@\*\*\*fichier*</span><span class="sxs-lookup"><span data-stu-id="1f058-135">**@** *file*</span></span>|<span data-ttu-id="1f058-136">Spécifie le fichier de réponse (.rsp).</span><span class="sxs-lookup"><span data-stu-id="1f058-136">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="1f058-137">**/?**</span><span class="sxs-lookup"><span data-stu-id="1f058-137">**/?**</span></span>|<span data-ttu-id="1f058-138">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="1f058-138">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f058-139"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1f058-139">Example</span></span>  
  
1. <span data-ttu-id="1f058-140">Si vous utilisez un contrôle sous licence `MyCompany.Samples.LicControl1` contenu dans `Samples.DLL`, dans une application appelée `HostApp.exe`\*, \*vous pouvez créer le fichier `HostAppLic.txt` contenant ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="1f058-140">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. <span data-ttu-id="1f058-141">Créez le fichier .licenses appelé `HostApp.exe.licenses` à l'aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="1f058-141">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. <span data-ttu-id="1f058-142">Générez `HostApp.exe` y compris le fichier .licenses en tant que ressource.</span><span class="sxs-lookup"><span data-stu-id="1f058-142">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="1f058-143">Si vous étiez en train de générer une application C#, vous utiliseriez alors la commande suivante pour générer votre application.</span><span class="sxs-lookup"><span data-stu-id="1f058-143">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="1f058-144">La commande suivante compile `myApp.licenses` à partir des listes de composants sous licence spécifiées par `hostapplic.txt`, `hostapplic2.txt` et `hostapplic3.txt`.</span><span class="sxs-lookup"><span data-stu-id="1f058-144">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="1f058-145">L'argument `modulesList` spécifie les modules qui comportent les composants sous licence.</span><span class="sxs-lookup"><span data-stu-id="1f058-145">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="1f058-146">Exemple de fichier de réponse</span><span class="sxs-lookup"><span data-stu-id="1f058-146">Response File Example</span></span>  
 <span data-ttu-id="1f058-147">La liste suivante montre un exemple de fichier réponse, `response.rsp`.</span><span class="sxs-lookup"><span data-stu-id="1f058-147">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="1f058-148">Pour plus d’informations sur les fichiers réponse, consultez [Fichiers réponse](/visualstudio/msbuild/msbuild-response-files).</span><span class="sxs-lookup"><span data-stu-id="1f058-148">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="1f058-149">La ligne de commande suivante utilise le fichier `response.rsp`.</span><span class="sxs-lookup"><span data-stu-id="1f058-149">The following command line uses the `response.rsp` file.</span></span>  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f058-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f058-150">See also</span></span>

- [<span data-ttu-id="1f058-151">Outils</span><span class="sxs-lookup"><span data-stu-id="1f058-151">Tools</span></span>](index.md)
- [<span data-ttu-id="1f058-152">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="1f058-152">Al.exe (Assembly Linker)</span></span>](al-exe-assembly-linker.md)
- [<span data-ttu-id="1f058-153">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="1f058-153">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
