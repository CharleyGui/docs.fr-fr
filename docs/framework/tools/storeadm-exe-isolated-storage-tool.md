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
ms.openlocfilehash: 46e846eaf92835fb2a9130b85ed20749934ca5a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715713"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="55de3-102">Storeadm.exe (outil Isolated Storage)</span><span class="sxs-lookup"><span data-stu-id="55de3-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="55de3-103">L'outil Isolated Storage (Stockage isolé) répertorie ou supprime tous les magasins existants de l'utilisateur en cours.</span><span class="sxs-lookup"><span data-stu-id="55de3-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="55de3-104">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55de3-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="55de3-105">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="55de3-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="55de3-106">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="55de3-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="55de3-107">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="55de3-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55de3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55de3-108">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="55de3-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="55de3-109">Parameters</span></span>  
  
|<span data-ttu-id="55de3-110">Option</span><span class="sxs-lookup"><span data-stu-id="55de3-110">Option</span></span>|<span data-ttu-id="55de3-111">Description</span><span class="sxs-lookup"><span data-stu-id="55de3-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="55de3-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="55de3-112">**/h**[**elp**]</span></span>|<span data-ttu-id="55de3-113">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="55de3-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="55de3-114">**/liste**</span><span class="sxs-lookup"><span data-stu-id="55de3-114">**/list**</span></span>|<span data-ttu-id="55de3-115">Affiche tous les magasins existants de l'utilisateur en cours.</span><span class="sxs-lookup"><span data-stu-id="55de3-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="55de3-116">Sont inclus les magasins de toutes les applications ou de tous les assemblys exécutés par cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="55de3-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="55de3-117">**/machine**</span><span class="sxs-lookup"><span data-stu-id="55de3-117">**/machine**</span></span>|<span data-ttu-id="55de3-118">Sélectionne le magasin de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55de3-118">Selects the machine store.</span></span> <span data-ttu-id="55de3-119">Utilisez cette option avec l’option **/list** ou **/remove** pour spécifier que l’action doit s’appliquer au magasin de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55de3-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="55de3-120">Nouveau dans le .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="55de3-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="55de3-121">**/calme**</span><span class="sxs-lookup"><span data-stu-id="55de3-121">**/quiet**</span></span>|<span data-ttu-id="55de3-122">Spécifie le mode silencieux ; supprime la sortie d'informations pour n'afficher que les messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="55de3-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="55de3-123">**/supprimer**</span><span class="sxs-lookup"><span data-stu-id="55de3-123">**/remove**</span></span>|<span data-ttu-id="55de3-124">Supprime définitivement tous les magasins existants de l'utilisateur en cours.</span><span class="sxs-lookup"><span data-stu-id="55de3-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="55de3-125">**/roaming**</span><span class="sxs-lookup"><span data-stu-id="55de3-125">**/roaming**</span></span>|<span data-ttu-id="55de3-126">Sélectionne le magasin itinérant.</span><span class="sxs-lookup"><span data-stu-id="55de3-126">Selects the roaming store.</span></span> <span data-ttu-id="55de3-127">Utilisez cette option avec l’option **/list** ou **/remove** pour spécifier que cette action doit s’appliquer au magasin itinérant.</span><span class="sxs-lookup"><span data-stu-id="55de3-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="55de3-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="55de3-128">**/?**</span></span>|<span data-ttu-id="55de3-129">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="55de3-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55de3-130">Notes </span><span class="sxs-lookup"><span data-stu-id="55de3-130">Remarks</span></span>  
 <span data-ttu-id="55de3-131">Lorsque vous exécutez Storeadm.exe à partir de la ligne de commande sans spécifier d'options, la syntaxe et les options de l'outil s'affichent.</span><span class="sxs-lookup"><span data-stu-id="55de3-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="55de3-132">Les options **/list** et **/remove** sont généralement utilisées l’une après l’autre ; si deux options ou plus sont spécifiées, elles sont alors exécutées dans leur ordre d’apparition sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="55de3-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="55de3-133">Les applications peuvent enregistrer soit dans l'un des deux magasins d'un utilisateur, soit dans le magasin de l'ordinateur :</span><span class="sxs-lookup"><span data-stu-id="55de3-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="55de3-134">Le magasin local est situé à un emplacement assuré de ne pas être itinérant (sur Windows 2000 et ultérieur), même si le profil d’utilisateur itinérant est activé pour cet utilisateur.</span><span class="sxs-lookup"><span data-stu-id="55de3-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="55de3-135">Le magasin itinérant est situé à un emplacement pouvant être itinérant, mais uniquement quand l’itinérance est activée pour l’utilisateur par le biais de l’administration de Windows NT.</span><span class="sxs-lookup"><span data-stu-id="55de3-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="55de3-136">Le magasin de l'ordinateur est commun à tous les utilisateurs sur un ordinateur et est stocké sous un répertoire commun de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55de3-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="55de3-137">Le magasin d'ordinateur est une nouveauté du .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="55de3-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="55de3-138">Que l'itinérance soit ou non réellement activée pour l'utilisateur n'affecte pas l'administration de Storeadm.exe.</span><span class="sxs-lookup"><span data-stu-id="55de3-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="55de3-139">L'exécution de l'outil sans option applique toutes les actions au magasin local.</span><span class="sxs-lookup"><span data-stu-id="55de3-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="55de3-140">L’exécution de l’outil avec l’option **/roaming** affecte toutes les actions au magasin qui est capable d’effectuer l’itinérance.</span><span class="sxs-lookup"><span data-stu-id="55de3-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="55de3-141">L’exécution de l’outil avec l’option **/machine** affecte toutes les actions au magasin de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="55de3-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55de3-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55de3-142">See also</span></span>

- [<span data-ttu-id="55de3-143">Outils</span><span class="sxs-lookup"><span data-stu-id="55de3-143">Tools</span></span>](index.md)
- [<span data-ttu-id="55de3-144">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="55de3-144">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="55de3-145">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="55de3-145">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
