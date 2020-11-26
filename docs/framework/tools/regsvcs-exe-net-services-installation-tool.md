---
title: Regsvcs.exe (outil .NET Services Installation)
description: Utilisez Regsvcs.exe, l’outil d’installation de .NET services. Chargez et inscrivez un assembly, configurez les services que vous avez ajoutés par programmation à une classe, et bien plus encore.
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 58a20084457cb217f3af73f4b4ff9ea251647782
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238546"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="dc471-104">Regsvcs.exe (outil .NET Services Installation)</span><span class="sxs-lookup"><span data-stu-id="dc471-104">Regsvcs.exe (.NET Services Installation Tool)</span></span>

<span data-ttu-id="dc471-105">L'outil .NET Services Installation (Installation des services .NET) effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dc471-105">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="dc471-106">Il charge et inscrit un assembly ;</span><span class="sxs-lookup"><span data-stu-id="dc471-106">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="dc471-107">Il génère, inscrit et installe une bibliothèque de types dans l'application COM+ spécifiée ;</span><span class="sxs-lookup"><span data-stu-id="dc471-107">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="dc471-108">Il configure les services que vous avez ajoutés à votre classe par programmation.</span><span class="sxs-lookup"><span data-stu-id="dc471-108">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="dc471-109">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="dc471-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="dc471-110">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="dc471-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="dc471-111">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="dc471-111">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc471-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc471-112">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="dc471-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc471-113">Parameters</span></span>  
  
|<span data-ttu-id="dc471-114">Argument</span><span class="sxs-lookup"><span data-stu-id="dc471-114">Argument</span></span>|<span data-ttu-id="dc471-115">Description</span><span class="sxs-lookup"><span data-stu-id="dc471-115">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="dc471-116">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="dc471-116">*assemblyFile.dll*</span></span>|<span data-ttu-id="dc471-117">Fichier d'assembly source.</span><span class="sxs-lookup"><span data-stu-id="dc471-117">The source assembly file.</span></span> <span data-ttu-id="dc471-118">L'assembly doit être signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="dc471-118">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="dc471-119">Pour plus d’informations, consultez [Signature d’un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="dc471-119">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="dc471-120">Option</span><span class="sxs-lookup"><span data-stu-id="dc471-120">Option</span></span>|<span data-ttu-id="dc471-121">Description</span><span class="sxs-lookup"><span data-stu-id="dc471-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="dc471-122">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="dc471-122">**/appdir:** *path*</span></span>|<span data-ttu-id="dc471-123">Spécifie le répertoire racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="dc471-123">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="dc471-124">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="dc471-124">**/appname:** *applicationName*</span></span>|<span data-ttu-id="dc471-125">Spécifie le nom de l'application COM+ à rechercher ou à créer.</span><span class="sxs-lookup"><span data-stu-id="dc471-125">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="dc471-126">**commutateur**</span><span class="sxs-lookup"><span data-stu-id="dc471-126">**/c**</span></span>|<span data-ttu-id="dc471-127">Crée l'application cible.</span><span class="sxs-lookup"><span data-stu-id="dc471-127">Creates the target application.</span></span>|  
|<span data-ttu-id="dc471-128">**/componly**</span><span class="sxs-lookup"><span data-stu-id="dc471-128">**/componly**</span></span>|<span data-ttu-id="dc471-129">Configure uniquement les composants ; ignore les méthodes et les interfaces.</span><span class="sxs-lookup"><span data-stu-id="dc471-129">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="dc471-130">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="dc471-130">**/exapp**</span></span>|<span data-ttu-id="dc471-131">Spécifie à l'outil qu'il doit attendre une application existante.</span><span class="sxs-lookup"><span data-stu-id="dc471-131">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="dc471-132">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="dc471-132">**/extlb**</span></span>|<span data-ttu-id="dc471-133">Utilise une bibliothèque de types existante.</span><span class="sxs-lookup"><span data-stu-id="dc471-133">Uses an existing type library.</span></span>|  
|<span data-ttu-id="dc471-134">**/FC**</span><span class="sxs-lookup"><span data-stu-id="dc471-134">**/fc**</span></span>|<span data-ttu-id="dc471-135">Recherche ou crée l'application cible.</span><span class="sxs-lookup"><span data-stu-id="dc471-135">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="dc471-136">**/Help**</span><span class="sxs-lookup"><span data-stu-id="dc471-136">**/help**</span></span>|<span data-ttu-id="dc471-137">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="dc471-137">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="dc471-138">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="dc471-138">**/noreconfig**</span></span>|<span data-ttu-id="dc471-139">Ne reconfigure pas une application cible existante.</span><span class="sxs-lookup"><span data-stu-id="dc471-139">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="dc471-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="dc471-140">**/nologo**</span></span>|<span data-ttu-id="dc471-141">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dc471-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="dc471-142">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="dc471-142">**/parname:** *name*</span></span>|<span data-ttu-id="dc471-143">Spécifie le nom ou l'identificateur de l'application COM+ à rechercher ou à créer.</span><span class="sxs-lookup"><span data-stu-id="dc471-143">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="dc471-144">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="dc471-144">**/reconfig**</span></span>|<span data-ttu-id="dc471-145">Reconfigure une application cible existante.</span><span class="sxs-lookup"><span data-stu-id="dc471-145">Reconfigures an existing target application.</span></span> <span data-ttu-id="dc471-146">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="dc471-146">This is the default.</span></span>|  
|<span data-ttu-id="dc471-147">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="dc471-147">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="dc471-148">Spécifie le fichier bibliothèque de types à installer.</span><span class="sxs-lookup"><span data-stu-id="dc471-148">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="dc471-149">**/u.**</span><span class="sxs-lookup"><span data-stu-id="dc471-149">**/u**</span></span>|<span data-ttu-id="dc471-150">Désinstalle l'application cible.</span><span class="sxs-lookup"><span data-stu-id="dc471-150">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="dc471-151">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="dc471-151">**/quiet**</span></span>|<span data-ttu-id="dc471-152">Spécifie le mode silencieux ; supprime le logo et l'affichage des messages de réussite.</span><span class="sxs-lookup"><span data-stu-id="dc471-152">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="dc471-153">**/?**</span><span class="sxs-lookup"><span data-stu-id="dc471-153">**/?**</span></span>|<span data-ttu-id="dc471-154">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="dc471-154">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc471-155">Notes</span><span class="sxs-lookup"><span data-stu-id="dc471-155">Remarks</span></span>  

 <span data-ttu-id="dc471-156">Regsvcs.exe nécessite un fichier d’assembly source spécifié par *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="dc471-156">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="dc471-157">Cet assembly doit être signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="dc471-157">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="dc471-158">Pour plus d’informations sur la signature avec un nom fort, consultez [Signature d’un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="dc471-158">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="dc471-159">Le nom de l'application cible et le nom du fichier bibliothèque de types sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="dc471-159">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="dc471-160">L’argument *applicationName* peut être généré à partir du fichier d’assembly source et sera créé par Regsvcs.exe, s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="dc471-160">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="dc471-161">L’argument *typelibraryfile* peut spécifier un nom de bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="dc471-161">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="dc471-162">Si vous ne spécifiez pas de nom de bibliothèque de types, Regsvcs.exe utilise alors par défaut le nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="dc471-162">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="dc471-163">Quand Regsvcs.exe inscrit les méthodes d’un composant, il est soumis aux [demandes](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) et aux [demandes de liaison](../misc/link-demands.md) sur ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="dc471-163">When Regsvcs.exe registers a component's methods, it is subject to the [demands](/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="dc471-164">Étant donné que l'outil s'exécute dans un environnement de niveau de confiance total, la plupart des demandes d'autorisation aboutissent.</span><span class="sxs-lookup"><span data-stu-id="dc471-164">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="dc471-165">Toutefois, Regsvcs.exe ne peut pas inscrire de composants avec des méthodes protégées par une demande ou une demande de liaison pour les autorisations <xref:System.Security.Permissions.StrongNameIdentityPermission> ou <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="dc471-165">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="dc471-166">Vous devez détenir des privilèges d'administrateur sur l'ordinateur local pour utiliser Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="dc471-166">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="dc471-167">Si Regsvcs.exe échoue tandis qu'il effectue l'une de ces actions, il affiche les messages d'erreur correspondants.</span><span class="sxs-lookup"><span data-stu-id="dc471-167">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dc471-168">Exemples</span><span class="sxs-lookup"><span data-stu-id="dc471-168">Examples</span></span>  

 <span data-ttu-id="dc471-169">La commande suivante ajoute toutes les classes publiques figurant dans `myTest.dll` à `myTargetApp` (une application COM+ existante) et génère la bibliothèque de types `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="dc471-169">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="dc471-170">La commande suivante ajoute toutes les classes publiques figurant dans `myTest.dll` à `myTargetApp` (une application COM+ existante) et génère la bibliothèque de types `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="dc471-170">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc471-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc471-171">See also</span></span>

- [<span data-ttu-id="dc471-172">outils</span><span class="sxs-lookup"><span data-stu-id="dc471-172">Tools</span></span>](index.md)
- [<span data-ttu-id="dc471-173">Comment : signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="dc471-173">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="dc471-174">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="dc471-174">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
