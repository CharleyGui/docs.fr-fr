---
title: CorFlags.exe (outil de conversion CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
ms.openlocfilehash: e1251b6660db45f3af4f6e57114b1b10da18bd0a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129863"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="b065b-102">CorFlags.exe (outil de conversion CorFlags)</span><span class="sxs-lookup"><span data-stu-id="b065b-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="b065b-103">L’outil de conversion CorFlags vous permet de configurer la section CorFlags de l’en-tête d’une image exécutable portable.</span><span class="sxs-lookup"><span data-stu-id="b065b-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="b065b-104">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b065b-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="b065b-105">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="b065b-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="b065b-106">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b065b-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="b065b-107">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="b065b-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b065b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b065b-108">Syntax</span></span>  
  
```console  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="b065b-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b065b-109">Parameters</span></span>  
  
|<span data-ttu-id="b065b-110">Paramètre requis</span><span class="sxs-lookup"><span data-stu-id="b065b-110">Required parameter</span></span>|<span data-ttu-id="b065b-111">Description</span><span class="sxs-lookup"><span data-stu-id="b065b-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="b065b-112">Nom de l'assembly pour lequel CorFlags doit être configuré.</span><span class="sxs-lookup"><span data-stu-id="b065b-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="b065b-113">Option</span><span class="sxs-lookup"><span data-stu-id="b065b-113">Option</span></span>|<span data-ttu-id="b065b-114">Description</span><span class="sxs-lookup"><span data-stu-id="b065b-114">Description</span></span>|  
|:------------|-----------------|  
|`-32BIT[REQ]+`|<span data-ttu-id="b065b-115">Définit l'indicateur 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="b065b-115">Sets the 32BITREQUIRED flag.</span></span>|  
|`-32BIT[REQ]-`|<span data-ttu-id="b065b-116">Efface l'indicateur 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="b065b-116">Clears the 32BITREQUIRED flag.</span></span>|  
|`-32BITPREF+`|<span data-ttu-id="b065b-117">Définit l'indicateur 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="b065b-117">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="b065b-118">L'application s'exécute comme un processus 32 bits même sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b065b-118">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="b065b-119">Affectez cet indicateur uniquement sur les fichiers EXE.</span><span class="sxs-lookup"><span data-stu-id="b065b-119">Set this flag only on EXE files.</span></span> <span data-ttu-id="b065b-120">Si l'indicateur est défini sur une DLL, la DLL ne charge pas dans les processus 64 bits, et une exception <xref:System.BadImageFormatException> est levée.</span><span class="sxs-lookup"><span data-stu-id="b065b-120">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="b065b-121">Un fichier EXE avec cet indicateur peut être chargé dans un processus 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b065b-121">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="b065b-122">Nouveautés de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b065b-122">New in the .NET Framework 4.5.</span></span>|  
|`-32BITPREF-`|<span data-ttu-id="b065b-123">Efface l'indicateur 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="b065b-123">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="b065b-124">Nouveautés de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="b065b-124">New in the .NET Framework 4.5.</span></span>|  
|`-?`|<span data-ttu-id="b065b-125">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="b065b-125">Displays command syntax and options for the tool.</span></span>|  
|`-Force`|<span data-ttu-id="b065b-126">Force une mise à jour même si l'assembly est associé à un nom fort.</span><span class="sxs-lookup"><span data-stu-id="b065b-126">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="b065b-127">**Important :** Si vous mettez à jour un assembly avec un nom fort, vous devez le resigner avant d’exécuter son code.</span><span class="sxs-lookup"><span data-stu-id="b065b-127">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|`-help`|<span data-ttu-id="b065b-128">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="b065b-128">Displays command syntax and options for the tool.</span></span>|  
|`-ILONLY+`|<span data-ttu-id="b065b-129">Définit l'indicateur ILONLY.</span><span class="sxs-lookup"><span data-stu-id="b065b-129">Sets the ILONLY flag.</span></span>|  
|`-ILONLY-`|<span data-ttu-id="b065b-130">Efface l'indicateur ILONLY.</span><span class="sxs-lookup"><span data-stu-id="b065b-130">Clears the ILONLY flag.</span></span>|  
|`-nologo`|<span data-ttu-id="b065b-131">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b065b-131">Suppresses the Microsoft startup banner display.</span></span>|  
|`-RevertCLRHeader`|<span data-ttu-id="b065b-132">Rétablit l'en-tête du CLR à la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="b065b-132">Reverts the CLR header version to 2.0.</span></span>|  
|`-UpgradeCLRHeader`|<span data-ttu-id="b065b-133">Met à niveau l'en-tête du CLR à la version 2.5.</span><span class="sxs-lookup"><span data-stu-id="b065b-133">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="b065b-134">**Remarque :** Les assemblys doivent avoir la version 2.5 ou ultérieure dans l’en-tête du CLR pour être exécutés en mode natif.</span><span class="sxs-lookup"><span data-stu-id="b065b-134">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b065b-135">Notes </span><span class="sxs-lookup"><span data-stu-id="b065b-135">Remarks</span></span>  
 <span data-ttu-id="b065b-136">Si aucune option n'est spécifiée, l'outil de conversion CorFlags affiche les indicateurs pour l'assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="b065b-136">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b065b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b065b-137">See also</span></span>

- [<span data-ttu-id="b065b-138">Outils</span><span class="sxs-lookup"><span data-stu-id="b065b-138">Tools</span></span>](index.md)
- [<span data-ttu-id="b065b-139">Applications 64 bits</span><span class="sxs-lookup"><span data-stu-id="b065b-139">64-bit Applications</span></span>](../64-bit-apps.md)
- [<span data-ttu-id="b065b-140">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="b065b-140">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
