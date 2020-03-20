---
title: Voir les mises à jour de sécurité et les hotfixes du cadre .NET installés
description: Découvrez comment déterminer les correctifs logiciels et mises à jour de sécurité .NET Framework installés sur un ordinateur.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181265"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="6e7bf-103">Comment déterminer quelles mises à jour de sécurité et hotfixes cadre .NET sont installés</span><span class="sxs-lookup"><span data-stu-id="6e7bf-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="6e7bf-104">Cet article montre comment rechercher les correctifs logiciels et mises à jour de sécurité .NET Framework installés sur un ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="6e7bf-105">Toutes les techniques présentées dans cet article nécessitent un compte avec des privilèges administratifs.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="6e7bf-106">Utiliser l’éditeur de registre</span><span class="sxs-lookup"><span data-stu-id="6e7bf-106">Use Registry Editor</span></span>

<span data-ttu-id="6e7bf-107">Les correctifs logiciels et mises à jour de sécurité installés pour chaque version du .NET Framework installée sur un ordinateur sont répertoriés dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="6e7bf-108">Vous pouvez utiliser le programme Éditeur du Registre (*regedit.exe*) pour afficher ces informations.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="6e7bf-109">Ouvrez le programme **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="6e7bf-110">Dans Windows 8 et les versions ultérieures, cliquez à droite **Démarrer** ![capture d’écran du logo de la clé Windows.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo (en)"), puis **sélectionnez Run**.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="6e7bf-111">Dans la zone **Ouvrir**, entrez **regedit** et sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="6e7bf-112">Dans l'Éditeur du Registre, ouvrez la sous-clé suivante :</span><span class="sxs-lookup"><span data-stu-id="6e7bf-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="6e7bf-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span><span class="sxs-lookup"><span data-stu-id="6e7bf-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="6e7bf-114">Les mises à jour installées sont répertoriées sous les sous-clés qui identifient la version du .NET Framework auquel elles s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="6e7bf-115">Chaque mise à jour est identifiée par un numéro de Base de connaissances (KB).</span><span class="sxs-lookup"><span data-stu-id="6e7bf-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="6e7bf-116">Dans l'Éditeur du Registre, les versions du .NET Framework et les mises à jour installées pour chaque version sont stockées dans des sous-clés distinctes.</span><span class="sxs-lookup"><span data-stu-id="6e7bf-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="6e7bf-117">Pour plus d’informations sur la détection des numéros des versions installées, consultez [Guide pratique pour déterminer les versions du .NET Framework installées](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="6e7bf-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="6e7bf-118">Requête du registre à l’aide du code</span><span class="sxs-lookup"><span data-stu-id="6e7bf-118">Query the registry using code</span></span>

<span data-ttu-id="6e7bf-119">L’exemple suivant détermine par programmation les correctifs logiciels et mises à jour de sécurité .NET Framework installés sur un ordinateur :</span><span class="sxs-lookup"><span data-stu-id="6e7bf-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="6e7bf-120">Cet exemple produit une sortie semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="6e7bf-120">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="6e7bf-121">Utilisez PowerShell pour interroger le registre</span><span class="sxs-lookup"><span data-stu-id="6e7bf-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="6e7bf-122">L’exemple suivant montre comment déterminer les correctifs logiciels et mises à jour de sécurité .NET Framework installés sur un ordinateur à l’aide de PowerShell :</span><span class="sxs-lookup"><span data-stu-id="6e7bf-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){

   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

<span data-ttu-id="6e7bf-123">Cet exemple produit une sortie semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="6e7bf-123">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a><span data-ttu-id="6e7bf-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e7bf-124">See also</span></span>

- [<span data-ttu-id="6e7bf-125">Comment : Déterminer quelles versions cadres .NET sont installées</span><span class="sxs-lookup"><span data-stu-id="6e7bf-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="6e7bf-126">Installer le .NET Framework pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="6e7bf-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="6e7bf-127">Versions et dépendances</span><span class="sxs-lookup"><span data-stu-id="6e7bf-127">Versions and dependencies</span></span>](versions-and-dependencies.md)
