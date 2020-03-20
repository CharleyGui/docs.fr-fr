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
ms.openlocfilehash: aecd2f6894558b45898c7f22dd333617d9e2e327
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180362"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="f60b1-102">Regsvcs.exe (outil .NET Services Installation)</span><span class="sxs-lookup"><span data-stu-id="f60b1-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="f60b1-103">L'outil .NET Services Installation (Installation des services .NET) effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f60b1-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="f60b1-104">Il charge et inscrit un assembly ;</span><span class="sxs-lookup"><span data-stu-id="f60b1-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="f60b1-105">Il génère, inscrit et installe une bibliothèque de types dans l'application COM+ spécifiée ;</span><span class="sxs-lookup"><span data-stu-id="f60b1-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="f60b1-106">Il configure les services que vous avez ajoutés à votre classe par programmation.</span><span class="sxs-lookup"><span data-stu-id="f60b1-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="f60b1-107">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="f60b1-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="f60b1-108">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f60b1-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="f60b1-109">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="f60b1-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f60b1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f60b1-110">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll
```  
  
## <a name="parameters"></a><span data-ttu-id="f60b1-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f60b1-111">Parameters</span></span>  
  
|<span data-ttu-id="f60b1-112">Argument</span><span class="sxs-lookup"><span data-stu-id="f60b1-112">Argument</span></span>|<span data-ttu-id="f60b1-113">Description</span><span class="sxs-lookup"><span data-stu-id="f60b1-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f60b1-114">*assemblyFile.dll*</span><span class="sxs-lookup"><span data-stu-id="f60b1-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="f60b1-115">Fichier d'assembly source.</span><span class="sxs-lookup"><span data-stu-id="f60b1-115">The source assembly file.</span></span> <span data-ttu-id="f60b1-116">L'assembly doit être signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="f60b1-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="f60b1-117">Pour plus d’informations, consultez [Signature d’un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="f60b1-117">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="f60b1-118">Option</span><span class="sxs-lookup"><span data-stu-id="f60b1-118">Option</span></span>|<span data-ttu-id="f60b1-119">Description</span><span class="sxs-lookup"><span data-stu-id="f60b1-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f60b1-120">**/appdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="f60b1-120">**/appdir:** *path*</span></span>|<span data-ttu-id="f60b1-121">Spécifie le répertoire racine de l'application.</span><span class="sxs-lookup"><span data-stu-id="f60b1-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="f60b1-122">**/appname:** *applicationName*</span><span class="sxs-lookup"><span data-stu-id="f60b1-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="f60b1-123">Spécifie le nom de l'application COM+ à rechercher ou à créer.</span><span class="sxs-lookup"><span data-stu-id="f60b1-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="f60b1-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="f60b1-124">**/c**</span></span>|<span data-ttu-id="f60b1-125">Crée l'application cible.</span><span class="sxs-lookup"><span data-stu-id="f60b1-125">Creates the target application.</span></span>|  
|<span data-ttu-id="f60b1-126">**/componly**</span><span class="sxs-lookup"><span data-stu-id="f60b1-126">**/componly**</span></span>|<span data-ttu-id="f60b1-127">Configure uniquement les composants ; ignore les méthodes et les interfaces.</span><span class="sxs-lookup"><span data-stu-id="f60b1-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="f60b1-128">**/exapp**</span><span class="sxs-lookup"><span data-stu-id="f60b1-128">**/exapp**</span></span>|<span data-ttu-id="f60b1-129">Spécifie à l'outil qu'il doit attendre une application existante.</span><span class="sxs-lookup"><span data-stu-id="f60b1-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="f60b1-130">**/extlb**</span><span class="sxs-lookup"><span data-stu-id="f60b1-130">**/extlb**</span></span>|<span data-ttu-id="f60b1-131">Utilise une bibliothèque de types existante.</span><span class="sxs-lookup"><span data-stu-id="f60b1-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="f60b1-132">**/fc**</span><span class="sxs-lookup"><span data-stu-id="f60b1-132">**/fc**</span></span>|<span data-ttu-id="f60b1-133">Recherche ou crée l'application cible.</span><span class="sxs-lookup"><span data-stu-id="f60b1-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="f60b1-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="f60b1-134">**/help**</span></span>|<span data-ttu-id="f60b1-135">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="f60b1-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="f60b1-136">**/noreconfig**</span><span class="sxs-lookup"><span data-stu-id="f60b1-136">**/noreconfig**</span></span>|<span data-ttu-id="f60b1-137">Ne reconfigure pas une application cible existante.</span><span class="sxs-lookup"><span data-stu-id="f60b1-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="f60b1-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="f60b1-138">**/nologo**</span></span>|<span data-ttu-id="f60b1-139">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f60b1-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="f60b1-140">**/parname:** *name*</span><span class="sxs-lookup"><span data-stu-id="f60b1-140">**/parname:** *name*</span></span>|<span data-ttu-id="f60b1-141">Spécifie le nom ou l'identificateur de l'application COM+ à rechercher ou à créer.</span><span class="sxs-lookup"><span data-stu-id="f60b1-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="f60b1-142">**/reconfig**</span><span class="sxs-lookup"><span data-stu-id="f60b1-142">**/reconfig**</span></span>|<span data-ttu-id="f60b1-143">Reconfigure une application cible existante.</span><span class="sxs-lookup"><span data-stu-id="f60b1-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="f60b1-144">Il s’agit de la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f60b1-144">This is the default.</span></span>|  
|<span data-ttu-id="f60b1-145">**/tlb:** *typelibraryfile*</span><span class="sxs-lookup"><span data-stu-id="f60b1-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="f60b1-146">Spécifie le fichier bibliothèque de types à installer.</span><span class="sxs-lookup"><span data-stu-id="f60b1-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="f60b1-147">**/u**</span><span class="sxs-lookup"><span data-stu-id="f60b1-147">**/u**</span></span>|<span data-ttu-id="f60b1-148">Désinstalle l'application cible.</span><span class="sxs-lookup"><span data-stu-id="f60b1-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="f60b1-149">**/calme**</span><span class="sxs-lookup"><span data-stu-id="f60b1-149">**/quiet**</span></span>|<span data-ttu-id="f60b1-150">Spécifie le mode silencieux ; supprime le logo et l'affichage des messages de réussite.</span><span class="sxs-lookup"><span data-stu-id="f60b1-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="f60b1-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="f60b1-151">**/?**</span></span>|<span data-ttu-id="f60b1-152">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="f60b1-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f60b1-153">Notes </span><span class="sxs-lookup"><span data-stu-id="f60b1-153">Remarks</span></span>  
 <span data-ttu-id="f60b1-154">Regsvcs.exe nécessite un fichier d’assembly source spécifié par *assemblyFile.dll*.</span><span class="sxs-lookup"><span data-stu-id="f60b1-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="f60b1-155">Cet assembly doit être signé avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="f60b1-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="f60b1-156">Pour plus d’informations sur la signature avec un nom fort, consultez [Signature d’un assembly avec un nom fort](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="f60b1-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="f60b1-157">Le nom de l'application cible et le nom du fichier bibliothèque de types sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="f60b1-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="f60b1-158">L’argument *applicationName* peut être généré à partir du fichier d’assembly source et sera créé par Regsvcs.exe, s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="f60b1-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="f60b1-159">L’argument *typelibraryfile* peut spécifier un nom de bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="f60b1-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="f60b1-160">Si vous ne spécifiez pas de nom de bibliothèque de types, Regsvcs.exe utilise alors par défaut le nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="f60b1-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="f60b1-161">Quand Regsvcs.exe inscrit les méthodes d’un composant, il est soumis aux [demandes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) et aux [demandes de liaison](../misc/link-demands.md) sur ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="f60b1-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="f60b1-162">Étant donné que l'outil s'exécute dans un environnement de niveau de confiance total, la plupart des demandes d'autorisation aboutissent.</span><span class="sxs-lookup"><span data-stu-id="f60b1-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="f60b1-163">Toutefois, Regsvcs.exe ne peut pas inscrire de composants avec des méthodes protégées par une demande ou une demande de liaison pour les autorisations <xref:System.Security.Permissions.StrongNameIdentityPermission> ou <xref:System.Security.Permissions.PublisherIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="f60b1-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="f60b1-164">Vous devez détenir des privilèges d'administrateur sur l'ordinateur local pour utiliser Regsvcs.exe.</span><span class="sxs-lookup"><span data-stu-id="f60b1-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="f60b1-165">Si Regsvcs.exe échoue tandis qu'il effectue l'une de ces actions, il affiche les messages d'erreur correspondants.</span><span class="sxs-lookup"><span data-stu-id="f60b1-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f60b1-166">Exemples</span><span class="sxs-lookup"><span data-stu-id="f60b1-166">Examples</span></span>  
 <span data-ttu-id="f60b1-167">La commande suivante ajoute toutes les classes publiques figurant dans `myTest.dll` à `myTargetApp` (une application COM+ existante) et génère la bibliothèque de types `myTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="f60b1-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="f60b1-168">La commande suivante ajoute toutes les classes publiques figurant dans `myTest.dll` à `myTargetApp` (une application COM+ existante) et génère la bibliothèque de types `newTest.tlb`.</span><span class="sxs-lookup"><span data-stu-id="f60b1-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="f60b1-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f60b1-169">See also</span></span>

- [<span data-ttu-id="f60b1-170">Outils</span><span class="sxs-lookup"><span data-stu-id="f60b1-170">Tools</span></span>](index.md)
- [<span data-ttu-id="f60b1-171">Comment : signer un assembly avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="f60b1-171">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="f60b1-172">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="f60b1-172">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
