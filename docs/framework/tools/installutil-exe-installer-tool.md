---
title: Installutil.exe (outil Installer Tool)
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ad0497bd5303dc4113dbb7b8078c70cb044cc95
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044540"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="8d56a-102">Installutil.exe (outil Installer Tool)</span><span class="sxs-lookup"><span data-stu-id="8d56a-102">Installutil.exe (Installer Tool)</span></span>

<span data-ttu-id="8d56a-103">L'outil Installer est un utilitaire en ligne de commande qui vous permet d'installer et de désinstaller les ressources serveur en exécutant les composants du programme d'installation dans des assemblys spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8d56a-103">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="8d56a-104">Cet outil fonctionne conjointement avec les classes de l'espace de noms <xref:System.Configuration.Install>.</span><span class="sxs-lookup"><span data-stu-id="8d56a-104">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>

<span data-ttu-id="8d56a-105">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8d56a-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="8d56a-106">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="8d56a-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="8d56a-107">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8d56a-107">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="8d56a-108">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="8d56a-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="8d56a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d56a-109">Syntax</span></span>

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a><span data-ttu-id="8d56a-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d56a-110">Parameters</span></span>

|<span data-ttu-id="8d56a-111">Argument</span><span class="sxs-lookup"><span data-stu-id="8d56a-111">Argument</span></span>|<span data-ttu-id="8d56a-112">Description</span><span class="sxs-lookup"><span data-stu-id="8d56a-112">Description</span></span>|
|--------------|-----------------|
|`assembly`|<span data-ttu-id="8d56a-113">Nom de fichier de l'assembly dans lequel exécuter les composants du programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="8d56a-113">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="8d56a-114">Omettez ce paramètre si vous souhaitez spécifier le nom fort de l'assembly à l'aide de l'option `/AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="8d56a-114">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|

<a name="options"></a>

## <a name="options"></a><span data-ttu-id="8d56a-115">Options</span><span class="sxs-lookup"><span data-stu-id="8d56a-115">Options</span></span>

|<span data-ttu-id="8d56a-116">Option</span><span class="sxs-lookup"><span data-stu-id="8d56a-116">Option</span></span>|<span data-ttu-id="8d56a-117">Description</span><span class="sxs-lookup"><span data-stu-id="8d56a-117">Description</span></span>|
|------------|-----------------|
|`/h[elp]`<br /><br /> <span data-ttu-id="8d56a-118">ou</span><span class="sxs-lookup"><span data-stu-id="8d56a-118">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="8d56a-119">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="8d56a-119">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="8d56a-120">`/help` *assembly*</span><span class="sxs-lookup"><span data-stu-id="8d56a-120">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="8d56a-121">ou</span><span class="sxs-lookup"><span data-stu-id="8d56a-121">-or-</span></span><br /><br /> <span data-ttu-id="8d56a-122">`/?` *assembly*</span><span class="sxs-lookup"><span data-stu-id="8d56a-122">`/?` *assembly*</span></span>|<span data-ttu-id="8d56a-123">Affiche les options supplémentaires reconnues par des programmes d'installation individuels dans l'assembly spécifié, avec la syntaxe et les options de commande d'InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="8d56a-123">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="8d56a-124">Cette option ajoute le texte retourné par la propriété <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> de chaque composant de programme d'installation au texte d'aide d'InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="8d56a-124">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|
|<span data-ttu-id="8d56a-125">`/AssemblyName` "*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="8d56a-125">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="8d56a-126">,Version=*major.minor.build.revision*</span><span class="sxs-lookup"><span data-stu-id="8d56a-126">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="8d56a-127">,Culture=*locale*</span><span class="sxs-lookup"><span data-stu-id="8d56a-127">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="8d56a-128">,PublicKeyToken=*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="8d56a-128">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="8d56a-129">Spécifie le nom fort d'un assembly, qui doit être enregistré dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="8d56a-129">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="8d56a-130">Le nom de l'assembly doit être qualifié complet avec la version, la culture et le jeton de clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8d56a-130">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="8d56a-131">Le nom qualifié complet doit être placé entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="8d56a-131">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="8d56a-132">Par exemple, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" est un nom d'assembly qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="8d56a-132">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|
|<span data-ttu-id="8d56a-133">`/InstallStateDir=[` *directoryName* `]`</span><span class="sxs-lookup"><span data-stu-id="8d56a-133">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="8d56a-134">Spécifie le répertoire du fichier .InstallState contenant les données utilisées pour désinstaller l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8d56a-134">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="8d56a-135">La valeur par défaut est le répertoire qui contient l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8d56a-135">The default is the directory that contains the assembly.</span></span>|
|<span data-ttu-id="8d56a-136">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="8d56a-136">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="8d56a-137">Spécifie le nom du fichier journal dans lequel la progression de l'installation est enregistrée.</span><span class="sxs-lookup"><span data-stu-id="8d56a-137">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="8d56a-138">Par défaut, si l'option `/LogFile` est omise, un fichier journal nommé *assemblyname*.InstallLog est créé.</span><span class="sxs-lookup"><span data-stu-id="8d56a-138">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="8d56a-139">Si *filename* est omis, aucun fichier journal n'est généré.</span><span class="sxs-lookup"><span data-stu-id="8d56a-139">If *filename* is omitted, no log file is generated.</span></span>|
|<span data-ttu-id="8d56a-140">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="8d56a-140">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="8d56a-141">Si la valeur est `true`, affiche la sortie dans la console.</span><span class="sxs-lookup"><span data-stu-id="8d56a-141">If `true`, displays output to the console.</span></span> <span data-ttu-id="8d56a-142">Si la valeur est `false`, supprime la sortie dans la console.</span><span class="sxs-lookup"><span data-stu-id="8d56a-142">If `false` (the default), suppresses output to the console.</span></span>|
|`/ShowCallStack`|<span data-ttu-id="8d56a-143">Sort la pile des appels dans le journal si une exception se produit à tout moment de l'installation.</span><span class="sxs-lookup"><span data-stu-id="8d56a-143">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|
|<span data-ttu-id="8d56a-144">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="8d56a-144">`/u`[`ninstall`]</span></span>|<span data-ttu-id="8d56a-145">Désinstalle les assemblys spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8d56a-145">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="8d56a-146">À la différence des autres options, `/u` s'applique à tous les assemblys, quel que soit l'endroit où l'option apparaît sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8d56a-146">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a><span data-ttu-id="8d56a-147">Options supplémentaires du programme d'installation</span><span class="sxs-lookup"><span data-stu-id="8d56a-147">Additional Installer Options</span></span>

<span data-ttu-id="8d56a-148">Les programmes d'installation utilisés avec un assembly peuvent reconnaître les options en plus de celles répertoriées dans la section [Options](#options).</span><span class="sxs-lookup"><span data-stu-id="8d56a-148">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="8d56a-149">Pour plus d'informations sur ces options, exécutez InstallUtil.exe avec les chemins d'accès des assemblys sur la ligne de commande avec l'option `/?` ou `/help`.</span><span class="sxs-lookup"><span data-stu-id="8d56a-149">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="8d56a-150">Pour spécifier ces options, ajoutez-les sur la ligne de commande avec les options identifiées par InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="8d56a-150">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="8d56a-151">Le texte d'aide sur les options prises en charge par les différents composants du programme d'installation est retourné par la propriété <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d56a-151">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8d56a-152">Les différentes options qui ont été entrées dans la ligne de commande sont accessibles par programmation depuis la propriété <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8d56a-152">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="8d56a-153">Tous les paramètres de ligne de commande et options sont écrits dans le fichier journal de l'installation.</span><span class="sxs-lookup"><span data-stu-id="8d56a-153">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="8d56a-154">Toutefois, si vous utilisez le paramètre `/Password` reconnu par certains composants du programme d'installation, les informations de mot de passe seront remplacées par huit astérisques (\*) et n'apparaîtront pas dans le fichier journal.</span><span class="sxs-lookup"><span data-stu-id="8d56a-154">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8d56a-155">Dans certains cas, les paramètres passés au programme d'installation peuvent comprendre des informations sensibles ou personnellement identifiables qui, par défaut, sont écrites dans un fichier journal de texte brut.</span><span class="sxs-lookup"><span data-stu-id="8d56a-155">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="8d56a-156">Pour empêcher ce comportement, vous pouvez supprimer le fichier journal en spécifiant `/LogFile=` (sans l'argument *filename*) après Installutil.exe sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8d56a-156">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d56a-157">Notes</span><span class="sxs-lookup"><span data-stu-id="8d56a-157">Remarks</span></span>

<span data-ttu-id="8d56a-158">Les applications .NET Framework comportent des fichiers programme traditionnels et des ressources associées, comme les files d'attente de messages, les journaux des événements et les compteurs de performance qui doivent être créés lors du déploiement de l'application.</span><span class="sxs-lookup"><span data-stu-id="8d56a-158">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="8d56a-159">Vous pouvez utiliser les composants du programme d'installation d'un assembly pour créer ces ressources lors de l'installation de l'application et les supprimer lors de la désinstallation de l'application.</span><span class="sxs-lookup"><span data-stu-id="8d56a-159">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="8d56a-160">Installutil.exe détecte et exécute les composants de ce programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="8d56a-160">Installutil.exe detects and executes these installer components.</span></span>

<span data-ttu-id="8d56a-161">Vous pouvez spécifier plusieurs assemblys sur la même ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="8d56a-161">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="8d56a-162">Toute option précédant le nom d'un assembly s'applique à l'installation de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="8d56a-162">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="8d56a-163">À l'exception de `/u` et `/AssemblyName`, les options sont cumulatives mais remplaçables.</span><span class="sxs-lookup"><span data-stu-id="8d56a-163">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="8d56a-164">Autrement dit, les options spécifiées pour un assembly s'appliquent à tous les assemblys suivants, à moins que l'option ne soit spécifiée avec une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="8d56a-164">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>

<span data-ttu-id="8d56a-165">Si vous exécutez Installutil.exe par rapport à un assembly sans spécifier d'options, les trois fichiers suivants seront alors placés dans le répertoire de cet assembly :</span><span class="sxs-lookup"><span data-stu-id="8d56a-165">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>

- <span data-ttu-id="8d56a-166">InstallUtil.InstallLog : contient une description générale de la progression de l'installation.</span><span class="sxs-lookup"><span data-stu-id="8d56a-166">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>

- <span data-ttu-id="8d56a-167">*assemblyname*.InstallLog : Contient des informations propres à la phase de validation du processus d'installation.</span><span class="sxs-lookup"><span data-stu-id="8d56a-167">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="8d56a-168">Pour plus d'informations sur la phase de validation, consultez la méthode <xref:System.Configuration.Install.Installer.Commit%2A>.</span><span class="sxs-lookup"><span data-stu-id="8d56a-168">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>

- <span data-ttu-id="8d56a-169">*assemblyname*.InstallState : Contient les données utilisées pour désinstaller l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8d56a-169">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>

<span data-ttu-id="8d56a-170">Installutil.exe utilise la réflexion pour inspecter les assemblys spécifiés et récupérer tous les types <xref:System.Configuration.Install.Installer> dont l'attribut <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> est défini sur `true`.</span><span class="sxs-lookup"><span data-stu-id="8d56a-170">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="8d56a-171">L'outil exécute alors soit la méthode <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType>, soit la méthode <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> sur chaque instance du type <xref:System.Configuration.Install.Installer>.</span><span class="sxs-lookup"><span data-stu-id="8d56a-171">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="8d56a-172">Installutil.exe exécute l'installation sous une forme transactionnelle. En cas d'échec de l'installation de l'un des assemblys, l'installation de tous les autres assemblys est restaurée.</span><span class="sxs-lookup"><span data-stu-id="8d56a-172">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="8d56a-173">La désinstallation ne fonctionne pas de manière transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="8d56a-173">Uninstall is not transactional.</span></span>

<span data-ttu-id="8d56a-174">Installutil.exe ne peut pas installer ou désinstaller les assemblys dont la signature est différée, mais il peut installer ou désinstaller des assemblys à nom fort.</span><span class="sxs-lookup"><span data-stu-id="8d56a-174">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>

<span data-ttu-id="8d56a-175">Depuis le .NET Framework version 2.0, la version 32 bits du Common Language Runtime (CLR) est fournie uniquement avec la version 32 bits de l'outil Installer, mais la version 64 bits du CLR est fournie avec les versions 32 bits et 64 bits de l'outil Installer.</span><span class="sxs-lookup"><span data-stu-id="8d56a-175">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="8d56a-176">Lorsque vous utilisez la version 64 bits du CLR, utilisez l'outil Installer 32 bits pour installer des assemblys 32 bits et l'outil Installer 64 bits pour les assemblys 64 bits et Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="8d56a-176">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="8d56a-177">Les deux versions de l'outil Installer ont le même comportement.</span><span class="sxs-lookup"><span data-stu-id="8d56a-177">Both versions of the Installer tool behave the same.</span></span>

<span data-ttu-id="8d56a-178">Vous ne pouvez pas utiliser Installutil.exe pour déployer un service Windows qui a été créé à l'aide de C++, car Installutil.exe ne peut pas identifier du code natif incorporé généré par le compilateur C++.</span><span class="sxs-lookup"><span data-stu-id="8d56a-178">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="8d56a-179">Si vous tentez de déployer un service Windows créé à l'aide de C++ avec Installutil.exe, une exception telle que <xref:System.BadImageFormatException> est levée.</span><span class="sxs-lookup"><span data-stu-id="8d56a-179">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="8d56a-180">Pour utiliser ce scénario, déplacez le code de service dans un module C++, puis écrivez l'objet de programme d'installation en C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8d56a-180">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>

## <a name="examples"></a><span data-ttu-id="8d56a-181">Exemples</span><span class="sxs-lookup"><span data-stu-id="8d56a-181">Examples</span></span>

<span data-ttu-id="8d56a-182">La commande suivante affiche une description de la syntaxe de la commande et des options de InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="8d56a-182">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>

```console
installutil /?
```

<span data-ttu-id="8d56a-183">La commande suivante affiche une description de la syntaxe de la commande et des options de InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="8d56a-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="8d56a-184">Elle affiche également une description et une liste d’options prises en charge par les composants du programme d’installation dans `myAssembly.exe` si le texte d’aide a été assigné à la propriété <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> du programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="8d56a-184">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>

```console
installutil /? myAssembly.exe
```

<span data-ttu-id="8d56a-185">La commande suivante exécute les composants du programme d'installation dans l'assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="8d56a-185">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>

```console
installutil myAssembly.exe
```

<span data-ttu-id="8d56a-186">La commande suivante exécute les composants du programme d'installation dans un assembly à l'aide du commutateur `/AssemblyName` et un nom qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="8d56a-186">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="8d56a-187">La commande suivante exécute les composants du programme d'installation dans un assembly spécifié par le nom de fichier et dans un assembly spécifié par le nom fort.</span><span class="sxs-lookup"><span data-stu-id="8d56a-187">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="8d56a-188">Notez que tous les assemblys spécifiés par le nom de fichier doivent précéder les assemblys spécifiés par le nom fort sur la ligne de commande, car l'option `/AssemblyName` ne peut pas être remplacée.</span><span class="sxs-lookup"><span data-stu-id="8d56a-188">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="8d56a-189">La commande suivante exécute les composants du programme de désinstallation dans l'assembly `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="8d56a-189">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>

```console
installutil /u myAssembly.exe
```

<span data-ttu-id="8d56a-190">La commande suivante exécute les composants du programme de désinstallation dans les assemblys `myAssembly1.exe` et `myAssembly2.exe`.</span><span class="sxs-lookup"><span data-stu-id="8d56a-190">The following command executes the uninstaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

<span data-ttu-id="8d56a-191">Étant donné que la position de l'option `/u` sur la ligne de commande n'est pas importante, cela est équivalent à la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="8d56a-191">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

<span data-ttu-id="8d56a-192">La commande suivante exécute les programmes d'installation dans l'assembly `myAssembly.exe` et spécifie l'écriture des informations sur la progression dans `myLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="8d56a-192">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

<span data-ttu-id="8d56a-193">La commande suivante exécute les programmes d'installation dans l'assembly `myAssembly.exe`, spécifie que les informations de progression doivent être écrites dans `myLog.InstallLog` et utilise l'option `/reg` personnalisée des programmes d'installation pour spécifier que les mises à jour doivent être effectuées dans le Registre système.</span><span class="sxs-lookup"><span data-stu-id="8d56a-193">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

<span data-ttu-id="8d56a-194">La commande suivante exécute les programmes d'installation dans l'assembly `myAssembly.exe`, utilise l'option `/email` personnalisée du programme d'installation pour spécifier l'adresse de messagerie de l'utilisateur et supprime la sortie du fichier journal.</span><span class="sxs-lookup"><span data-stu-id="8d56a-194">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

<span data-ttu-id="8d56a-195">La commande suivante écrit la progression de l'installation de `myAssembly.exe` dans `myLog.InstallLog` et celle de `myTestAssembly.exe` dans `myTestLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="8d56a-195">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a><span data-ttu-id="8d56a-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d56a-196">See also</span></span>

- <xref:System.Configuration.Install>
- [<span data-ttu-id="8d56a-197">Outils</span><span class="sxs-lookup"><span data-stu-id="8d56a-197">Tools</span></span>](index.md)
- [<span data-ttu-id="8d56a-198">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="8d56a-198">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
