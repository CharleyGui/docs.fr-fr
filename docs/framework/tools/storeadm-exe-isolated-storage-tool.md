---
title: Storeadm.exe (outil Isolated Storage)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b947ea2bfabe1c3fa9afb43cb5ecc41ab92be89
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929904"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="f245d-102">Storeadm.exe (outil Isolated Storage)</span><span class="sxs-lookup"><span data-stu-id="f245d-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="f245d-103">L'outil Isolated Storage (Stockage isolé) répertorie ou supprime tous les magasins existants de l'utilisateur en cours.</span><span class="sxs-lookup"><span data-stu-id="f245d-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="f245d-104">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f245d-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="f245d-105">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="f245d-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="f245d-106">Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="f245d-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="f245d-107">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="f245d-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f245d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f245d-108">Syntax</span></span>  
  
```  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="f245d-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f245d-109">Parameters</span></span>  
  
|<span data-ttu-id="f245d-110">Option</span><span class="sxs-lookup"><span data-stu-id="f245d-110">Option</span></span>|<span data-ttu-id="f245d-111">Description</span><span class="sxs-lookup"><span data-stu-id="f245d-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f245d-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="f245d-112">**/h**[**elp**]</span></span>|<span data-ttu-id="f245d-113">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="f245d-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="f245d-114">**/list**</span><span class="sxs-lookup"><span data-stu-id="f245d-114">**/list**</span></span>|<span data-ttu-id="f245d-115">Affiche tous les magasins existants de l'utilisateur en cours.</span><span class="sxs-lookup"><span data-stu-id="f245d-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="f245d-116">Sont inclus les magasins de toutes les applications ou de tous les assemblys exécutés par cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f245d-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="f245d-117">**/machine**</span><span class="sxs-lookup"><span data-stu-id="f245d-117">**/machine**</span></span>|<span data-ttu-id="f245d-118">Sélectionne le magasin de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f245d-118">Selects the machine store.</span></span> <span data-ttu-id="f245d-119">Utilisez cette option avec l’option **/list** ou **/remove** pour spécifier que l’action doit s’appliquer au magasin de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f245d-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="f245d-120">Nouveau dans le .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="f245d-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="f245d-121">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="f245d-121">**/quiet**</span></span>|<span data-ttu-id="f245d-122">Spécifie le mode silencieux ; supprime la sortie d'informations pour n'afficher que les messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="f245d-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="f245d-123">**/remove**</span><span class="sxs-lookup"><span data-stu-id="f245d-123">**/remove**</span></span>|<span data-ttu-id="f245d-124">Supprime définitivement tous les magasins existants de l'utilisateur en cours.</span><span class="sxs-lookup"><span data-stu-id="f245d-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="f245d-125">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="f245d-125">**/roaming**</span></span>|<span data-ttu-id="f245d-126">Sélectionne le magasin itinérant.</span><span class="sxs-lookup"><span data-stu-id="f245d-126">Selects the roaming store.</span></span> <span data-ttu-id="f245d-127">Utilisez cette option avec l’option **/list** ou **/remove** pour spécifier que cette action doit s’appliquer au magasin itinérant.</span><span class="sxs-lookup"><span data-stu-id="f245d-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="f245d-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="f245d-128">**/?**</span></span>|<span data-ttu-id="f245d-129">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="f245d-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f245d-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="f245d-130">Remarks</span></span>  
 <span data-ttu-id="f245d-131">Lorsque vous exécutez Storeadm.exe à partir de la ligne de commande sans spécifier d'options, la syntaxe et les options de l'outil s'affichent.</span><span class="sxs-lookup"><span data-stu-id="f245d-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="f245d-132">Les options **/list** et **/remove** sont généralement utilisées l’une après l’autre ; si deux options ou plus sont spécifiées, elles sont alors exécutées dans leur ordre d’apparition sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f245d-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="f245d-133">Les applications peuvent enregistrer soit dans l'un des deux magasins d'un utilisateur, soit dans le magasin de l'ordinateur :</span><span class="sxs-lookup"><span data-stu-id="f245d-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="f245d-134">Le magasin local est situé à un emplacement assuré de ne pas être itinérant (sur Windows 2000 et ultérieur), même si le profil d’utilisateur itinérant est activé pour cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f245d-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="f245d-135">Le magasin itinérant est situé à un emplacement pouvant être itinérant, mais uniquement quand l’itinérance est activée pour l’utilisateur par le biais de l’administration de Windows NT.</span><span class="sxs-lookup"><span data-stu-id="f245d-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="f245d-136">Le magasin de l'ordinateur est commun à tous les utilisateurs sur un ordinateur et est stocké sous un répertoire commun de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f245d-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="f245d-137">Le magasin d'ordinateur est une nouveauté du .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="f245d-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="f245d-138">Que l'itinérance soit ou non réellement activée pour l'utilisateur n'affecte pas l'administration de Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="f245d-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="f245d-139">L'exécution de l'outil sans option applique toutes les actions au magasin local.</span><span class="sxs-lookup"><span data-stu-id="f245d-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="f245d-140">L’exécution de l’outil avec l’option **/roaming** affecte toutes les actions au magasin qui est capable d’effectuer l’itinérance.</span><span class="sxs-lookup"><span data-stu-id="f245d-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="f245d-141">L’exécution de l’outil avec l’option **/machine** affecte toutes les actions au magasin de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f245d-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f245d-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f245d-142">See also</span></span>

- [<span data-ttu-id="f245d-143">Outils</span><span class="sxs-lookup"><span data-stu-id="f245d-143">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="f245d-144">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="f245d-144">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="f245d-145">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="f245d-145">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
