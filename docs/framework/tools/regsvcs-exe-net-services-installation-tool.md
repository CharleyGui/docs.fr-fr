---
title: Regsvcs.exe (outil .NET Services Installation)
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 032f43aa16dbca0f4ab0477d586e7568230b7381
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044265"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="68094-102">Regsvcs.exe (outil .NET Services Installation)</span><span class="sxs-lookup"><span data-stu-id="68094-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="68094-103">L'outil .NET Services Installation (Installation des services .NET) effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="68094-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="68094-104">Il charge et inscrit un assembly ;</span><span class="sxs-lookup"><span data-stu-id="68094-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="68094-105">Il génère, inscrit et installe une bibliothèque de types dans l'application COM+ spécifiée ;</span><span class="sxs-lookup"><span data-stu-id="68094-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="68094-106">Il configure les services que vous avez ajoutés à votre classe par programmation.</span><span class="sxs-lookup"><span data-stu-id="68094-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="68094-107">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="68094-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="68094-108">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="68094-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="68094-109">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="68094-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68094-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68094-110">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a><span data-ttu-id="68094-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68094-111">Parameters</span></span>  
  
|<span data-ttu-id="68094-112">Argument</span><span class="sxs-lookup"><span data-stu-id="68094-112">Argument</span></span>|<span data-ttu-id="68094-113">Description</span><span class="sxs-lookup"><span data-stu-id="68094-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="68094-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="68094-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="68094-115">Fichier d'assembly source.</span><span class="sxs-lookup"><span data-stu-id="68094-115">The source assembly file.</span></span> <span data-ttu-id="68094-116">L'assembly doit être signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="68094-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="68094-117">Pour plus d’informations, consultez [Signature d’un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="68094-117">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="68094-118">Option</span><span class="sxs-lookup"><span data-stu-id="68094-118">Option</span></span>|<span data-ttu-id="68094-119">Description</span><span class="sxs-lookup"><span data-stu-id="68094-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="68094-120">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="68094-120">**/appdir:** *path*</span></span>|<span data-ttu-id="68094-121">Spécifie le répertoire racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="68094-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="68094-122">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="68094-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="68094-123">Spécifie le nom de l'application COM+ à rechercher ou à créer.</span><span class="sxs-lookup"><span data-stu-id="68094-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="68094-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="68094-124">**/c**</span></span>|<span data-ttu-id="68094-125">Crée l'application cible.</span><span class="sxs-lookup"><span data-stu-id="68094-125">Creates the target application.</span></span>|  
|<span data-ttu-id="68094-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="68094-126">**/componly**</span></span>|<span data-ttu-id="68094-127">Configure uniquement les composants ; ignore les méthodes et les interfaces.</span><span class="sxs-lookup"><span data-stu-id="68094-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="68094-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="68094-128">**/exapp**</span></span>|<span data-ttu-id="68094-129">Spécifie à l'outil qu'il doit attendre une application existante.</span><span class="sxs-lookup"><span data-stu-id="68094-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="68094-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="68094-130">**/extlb**</span></span>|<span data-ttu-id="68094-131">Utilise une bibliothèque de types existante.</span><span class="sxs-lookup"><span data-stu-id="68094-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="68094-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="68094-132">**/fc**</span></span>|<span data-ttu-id="68094-133">Recherche ou crée l'application cible.</span><span class="sxs-lookup"><span data-stu-id="68094-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="68094-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="68094-134">**/help**</span></span>|<span data-ttu-id="68094-135">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="68094-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="68094-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="68094-136">**/noreconfig**</span></span>|<span data-ttu-id="68094-137">Ne reconfigure pas une application cible existante.</span><span class="sxs-lookup"><span data-stu-id="68094-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="68094-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="68094-138">**/nologo**</span></span>|<span data-ttu-id="68094-139">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="68094-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="68094-140">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="68094-140">**/parname:** *name*</span></span>|<span data-ttu-id="68094-141">Spécifie le nom ou l'identificateur de l'application COM+ à rechercher ou à créer.</span><span class="sxs-lookup"><span data-stu-id="68094-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="68094-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="68094-142">**/reconfig**</span></span>|<span data-ttu-id="68094-143">Reconfigure une application cible existante.</span><span class="sxs-lookup"><span data-stu-id="68094-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="68094-144">Il s'agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="68094-144">This is the default.</span></span>|  
|<span data-ttu-id="68094-145">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="68094-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="68094-146">Spécifie le fichier bibliothèque de types à installer.</span><span class="sxs-lookup"><span data-stu-id="68094-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="68094-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="68094-147">**/u**</span></span>|<span data-ttu-id="68094-148">Désinstalle l'application cible.</span><span class="sxs-lookup"><span data-stu-id="68094-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="68094-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="68094-149">**/quiet**</span></span>|<span data-ttu-id="68094-150">Spécifie le mode silencieux ; supprime le logo et l'affichage des messages de réussite.</span><span class="sxs-lookup"><span data-stu-id="68094-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="68094-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="68094-151">**/?**</span></span>|<span data-ttu-id="68094-152">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="68094-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68094-153">Notes</span><span class="sxs-lookup"><span data-stu-id="68094-153">Remarks</span></span>  
 <span data-ttu-id="68094-154">Regsvcs.exe nécessite un fichier d’assembly source spécifié par *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="68094-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="68094-155">Cet assembly doit être signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="68094-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="68094-156">Pour plus d’informations sur la signature avec un nom fort, consultez [Signature d’un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="68094-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="68094-157">Le nom de l'application cible et le nom du fichier bibliothèque de types sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="68094-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="68094-158">L’argument *applicationName* peut être généré à partir du fichier d’assembly source et sera créé par Regsvcs.exe, s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="68094-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="68094-159">L’argument *typelibraryfile* peut spécifier un nom de bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="68094-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="68094-160">Si vous ne spécifiez pas de nom de bibliothèque de types, Regsvcs.exe utilise alors par défaut le nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="68094-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="68094-161">Quand Regsvcs.exe inscrit les méthodes d’un composant, il est soumis aux [demandes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) et aux [demandes de liaison](../misc/link-demands.md) sur ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="68094-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="68094-162">Étant donné que l'outil s'exécute dans un environnement de niveau de confiance total, la plupart des demandes d'autorisation aboutissent.</span><span class="sxs-lookup"><span data-stu-id="68094-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="68094-163">Toutefois, Regsvcs.exe ne peut pas inscrire de composants avec des méthodes protégées par une demande ou une demande de liaison pour les autorisations <xref:System.Security.Permissions.StrongNameIdentityPermission> ou <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="68094-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="68094-164">Vous devez détenir des privilèges d'administrateur sur l'ordinateur local pour utiliser Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="68094-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="68094-165">Si Regsvcs.exe échoue tandis qu'il effectue l'une de ces actions, il affiche les messages d'erreur correspondants.</span><span class="sxs-lookup"><span data-stu-id="68094-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="68094-166">Exemples</span><span class="sxs-lookup"><span data-stu-id="68094-166">Examples</span></span>  
 <span data-ttu-id="68094-167">La commande suivante ajoute toutes les classes publiques figurant dans `myTest.dll` à `myTargetApp` (une application COM+ existante) et génère la bibliothèque de types `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="68094-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="68094-168">La commande suivante ajoute toutes les classes publiques figurant dans `myTest.dll` à `myTargetApp` (une application COM+ existante) et génère la bibliothèque de types `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="68094-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="68094-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68094-169">See also</span></span>

- [<span data-ttu-id="68094-170">Outils</span><span class="sxs-lookup"><span data-stu-id="68094-170">Tools</span></span>](index.md)
- [<span data-ttu-id="68094-171">Guide pratique pour signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="68094-171">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="68094-172">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="68094-172">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
