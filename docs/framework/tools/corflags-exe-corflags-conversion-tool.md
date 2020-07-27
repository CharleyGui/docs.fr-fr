---
title: CorFlags.exe (outil de conversion CorFlags)
description: Comprenez CorFlags.exe, l’outil de conversion CorFlags. Cet outil vous permet de configurer la section CorFlags de l’en-tête d’une image exécutable portable.
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: da5efadd63cc03f6f6e4eecf3115865ca3643b39
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167230"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="58fc3-104">CorFlags.exe (outil de conversion CorFlags)</span><span class="sxs-lookup"><span data-stu-id="58fc3-104">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="58fc3-105">L’outil de conversion CorFlags vous permet de configurer la section CorFlags de l’en-tête d’une image exécutable portable.</span><span class="sxs-lookup"><span data-stu-id="58fc3-105">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="58fc3-106">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58fc3-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="58fc3-107">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="58fc3-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="58fc3-108">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="58fc3-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="58fc3-109">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="58fc3-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58fc3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58fc3-110">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="58fc3-111">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58fc3-111">Parameters</span></span>  
  
|<span data-ttu-id="58fc3-112">Paramètre requis</span><span class="sxs-lookup"><span data-stu-id="58fc3-112">Required parameter</span></span>|<span data-ttu-id="58fc3-113">Description</span><span class="sxs-lookup"><span data-stu-id="58fc3-113">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="58fc3-114">Nom de l'assembly pour lequel CorFlags doit être configuré.</span><span class="sxs-lookup"><span data-stu-id="58fc3-114">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="58fc3-115">Option</span><span class="sxs-lookup"><span data-stu-id="58fc3-115">Option</span></span>|<span data-ttu-id="58fc3-116">Description</span><span class="sxs-lookup"><span data-stu-id="58fc3-116">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="58fc3-117">Définit l'indicateur 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="58fc3-117">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="58fc3-118">Efface l'indicateur 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="58fc3-118">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="58fc3-119">Définit l'indicateur 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="58fc3-119">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="58fc3-120">L'application s'exécute comme un processus 32 bits même sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="58fc3-120">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="58fc3-121">Affectez cet indicateur uniquement sur les fichiers EXE.</span><span class="sxs-lookup"><span data-stu-id="58fc3-121">Set this flag only on EXE files.</span></span> <span data-ttu-id="58fc3-122">Si l'indicateur est défini sur une DLL, la DLL ne charge pas dans les processus 64 bits, et une exception <xref:System.BadImageFormatException> est levée.</span><span class="sxs-lookup"><span data-stu-id="58fc3-122">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="58fc3-123">Un fichier EXE avec cet indicateur peut être chargé dans un processus 64 bits.</span><span class="sxs-lookup"><span data-stu-id="58fc3-123">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="58fc3-124">Nouveautés de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="58fc3-124">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="58fc3-125">Efface l'indicateur 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="58fc3-125">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="58fc3-126">Nouveautés de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="58fc3-126">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="58fc3-127">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="58fc3-127">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="58fc3-128">Force une mise à jour même si l'assembly est associé à un nom fort.</span><span class="sxs-lookup"><span data-stu-id="58fc3-128">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="58fc3-129">**Important :** Si vous mettez à jour un assembly avec un nom fort, vous devez le resigner avant d’exécuter son code.</span><span class="sxs-lookup"><span data-stu-id="58fc3-129">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="58fc3-130">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="58fc3-130">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="58fc3-131">Définit l'indicateur ILONLY.</span><span class="sxs-lookup"><span data-stu-id="58fc3-131">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="58fc3-132">Efface l'indicateur ILONLY.</span><span class="sxs-lookup"><span data-stu-id="58fc3-132">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="58fc3-133">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="58fc3-133">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="58fc3-134">Rétablit l'en-tête du CLR à la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="58fc3-134">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="58fc3-135">Met à niveau l'en-tête du CLR à la version 2.5.</span><span class="sxs-lookup"><span data-stu-id="58fc3-135">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="58fc3-136">**Remarque :** Les assemblys doivent avoir la version 2.5 ou ultérieure dans l’en-tête du CLR pour être exécutés en mode natif.</span><span class="sxs-lookup"><span data-stu-id="58fc3-136">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58fc3-137">Notes</span><span class="sxs-lookup"><span data-stu-id="58fc3-137">Remarks</span></span>  
 <span data-ttu-id="58fc3-138">Si aucune option n'est spécifiée, l'outil de conversion CorFlags affiche les indicateurs pour l'assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="58fc3-138">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58fc3-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58fc3-139">See also</span></span>

- [<span data-ttu-id="58fc3-140">outils</span><span class="sxs-lookup"><span data-stu-id="58fc3-140">Tools</span></span>](index.md)
- [<span data-ttu-id="58fc3-141">Applications 64 bits</span><span class="sxs-lookup"><span data-stu-id="58fc3-141">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="58fc3-142">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="58fc3-142">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
