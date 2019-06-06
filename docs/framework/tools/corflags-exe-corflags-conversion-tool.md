---
title: CorFlags.exe (outil de conversion CorFlags)
ms.date: 03/30/2017
helpviewer_keywords:
- CorFlags conversion tool
- CorFlags.exe
- portable executable files, CorFlags section
ms.assetid: ef900f8f-71ca-4dde-9b8c-95ddb0d7d89c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ef10ba566842db26ed8c29643535c41aaca9806
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378661"
---
# <a name="corflagsexe-corflags-conversion-tool"></a><span data-ttu-id="761e2-102">CorFlags.exe (outil de conversion CorFlags)</span><span class="sxs-lookup"><span data-stu-id="761e2-102">CorFlags.exe (CorFlags Conversion Tool)</span></span>
<span data-ttu-id="761e2-103">L’outil de conversion CorFlags vous permet de configurer la section CorFlags de l’en-tête d’une image exécutable portable.</span><span class="sxs-lookup"><span data-stu-id="761e2-103">The CorFlags Conversion tool allows you to configure the CorFlags section of the header of a portable executable image.</span></span>  
  
 <span data-ttu-id="761e2-104">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="761e2-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="761e2-105">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="761e2-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="761e2-106">Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="761e2-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="761e2-107">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="761e2-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="761e2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="761e2-108">Syntax</span></span>  
  
```  
CorFlags.exe assembly [options]  
```  
  
## <a name="parameters"></a><span data-ttu-id="761e2-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="761e2-109">Parameters</span></span>  
  
|<span data-ttu-id="761e2-110">Paramètre requis</span><span class="sxs-lookup"><span data-stu-id="761e2-110">Required parameter</span></span>|<span data-ttu-id="761e2-111">Description</span><span class="sxs-lookup"><span data-stu-id="761e2-111">Description</span></span>|  
|------------------------|-----------------|  
|`assembly`|<span data-ttu-id="761e2-112">Nom de l'assembly pour lequel CorFlags doit être configuré.</span><span class="sxs-lookup"><span data-stu-id="761e2-112">The name of the assembly for which to configure the CorFlags.</span></span>|  
  
|<span data-ttu-id="761e2-113">Option</span><span class="sxs-lookup"><span data-stu-id="761e2-113">Option</span></span>|<span data-ttu-id="761e2-114">Description</span><span class="sxs-lookup"><span data-stu-id="761e2-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="761e2-115">**/32BIT[REQ]+**</span><span class="sxs-lookup"><span data-stu-id="761e2-115">**/32BIT[REQ]+**</span></span>|<span data-ttu-id="761e2-116">Définit l'indicateur 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="761e2-116">Sets the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="761e2-117">**/32BIT[REQ]-**</span><span class="sxs-lookup"><span data-stu-id="761e2-117">**/32BIT[REQ]-**</span></span>|<span data-ttu-id="761e2-118">Efface l'indicateur 32BITREQUIRED.</span><span class="sxs-lookup"><span data-stu-id="761e2-118">Clears the 32BITREQUIRED flag.</span></span>|  
|<span data-ttu-id="761e2-119">**/32BITPREF+**</span><span class="sxs-lookup"><span data-stu-id="761e2-119">**/32BITPREF+**</span></span>|<span data-ttu-id="761e2-120">Définit l'indicateur 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="761e2-120">Sets the 32BITPREFERRED flag.</span></span> <span data-ttu-id="761e2-121">L'application s'exécute comme un processus 32 bits même sur les plateformes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="761e2-121">The app runs as a 32-bit process even on 64-bit platforms.</span></span> <span data-ttu-id="761e2-122">Affectez cet indicateur uniquement sur les fichiers EXE.</span><span class="sxs-lookup"><span data-stu-id="761e2-122">Set this flag only on EXE files.</span></span> <span data-ttu-id="761e2-123">Si l'indicateur est défini sur une DLL, la DLL ne charge pas dans les processus 64 bits, et une exception <xref:System.BadImageFormatException> est levée.</span><span class="sxs-lookup"><span data-stu-id="761e2-123">If the flag is set on a DLL, the DLL fails to load in 64-bit processes, and a <xref:System.BadImageFormatException> exception is thrown.</span></span> <span data-ttu-id="761e2-124">Un fichier EXE avec cet indicateur peut être chargé dans un processus 64 bits.</span><span class="sxs-lookup"><span data-stu-id="761e2-124">An EXE file with this flag can be loaded into a 64-bit process.</span></span><br /><br /> <span data-ttu-id="761e2-125">Nouveautés de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="761e2-125">New in the .NET Framework 4.5.</span></span>|  
|<span data-ttu-id="761e2-126">**/32BITPREF-**</span><span class="sxs-lookup"><span data-stu-id="761e2-126">**/32BITPREF-**</span></span>|<span data-ttu-id="761e2-127">Efface l'indicateur 32BITPREFERRED.</span><span class="sxs-lookup"><span data-stu-id="761e2-127">Clears the 32BITPREFERRED flag.</span></span><br /><br /> <span data-ttu-id="761e2-128">Nouveautés de .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="761e2-128">New in the .NET Framework 4.5.</span></span>|  
|<span data-ttu-id="761e2-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="761e2-129">**/?**</span></span>|<span data-ttu-id="761e2-130">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="761e2-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="761e2-131">**/Force**</span><span class="sxs-lookup"><span data-stu-id="761e2-131">**/Force**</span></span>|<span data-ttu-id="761e2-132">Force une mise à jour même si l'assembly est associé à un nom fort.</span><span class="sxs-lookup"><span data-stu-id="761e2-132">Forces an update even if the assembly is strong-named.</span></span> <span data-ttu-id="761e2-133">**Important :**  si vous mettez à jour un assembly à nom fort, vous devez le signer à nouveau avant d’exécuter son code.</span><span class="sxs-lookup"><span data-stu-id="761e2-133">**Important:**  If you update a strong-named assembly, you must sign it again before executing its code.</span></span>|  
|<span data-ttu-id="761e2-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="761e2-134">**/help**</span></span>|<span data-ttu-id="761e2-135">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="761e2-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="761e2-136">**/ILONLY+**</span><span class="sxs-lookup"><span data-stu-id="761e2-136">**/ILONLY+**</span></span>|<span data-ttu-id="761e2-137">Définit l'indicateur ILONLY.</span><span class="sxs-lookup"><span data-stu-id="761e2-137">Sets the ILONLY flag.</span></span>|  
|<span data-ttu-id="761e2-138">**/ILONLY-**</span><span class="sxs-lookup"><span data-stu-id="761e2-138">**/ILONLY-**</span></span>|<span data-ttu-id="761e2-139">Efface l'indicateur ILONLY.</span><span class="sxs-lookup"><span data-stu-id="761e2-139">Clears the ILONLY flag.</span></span>|  
|<span data-ttu-id="761e2-140">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="761e2-140">**/nologo**</span></span>|<span data-ttu-id="761e2-141">Supprime l'affichage de la bannière de démarrage Microsoft.</span><span class="sxs-lookup"><span data-stu-id="761e2-141">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="761e2-142">**/RevertCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="761e2-142">**/RevertCLRHeader**</span></span>|<span data-ttu-id="761e2-143">Rétablit l'en-tête du CLR à la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="761e2-143">Reverts the CLR header version to 2.0.</span></span>|  
|<span data-ttu-id="761e2-144">**/UpgradeCLRHeader**</span><span class="sxs-lookup"><span data-stu-id="761e2-144">**/UpgradeCLRHeader**</span></span>|<span data-ttu-id="761e2-145">Met à niveau l'en-tête du CLR à la version 2.5.</span><span class="sxs-lookup"><span data-stu-id="761e2-145">Upgrades the CLR header version to 2.5.</span></span> <span data-ttu-id="761e2-146">**Remarque :**  les assemblys doivent avoir la version 2.5 ou une version ultérieure de l’en-tête du CLR pour s’exécuter en mode natif.</span><span class="sxs-lookup"><span data-stu-id="761e2-146">**Note:**  Assemblies must have a CLR header version of 2.5 or greater to run natively.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="761e2-147">Remarques</span><span class="sxs-lookup"><span data-stu-id="761e2-147">Remarks</span></span>  
 <span data-ttu-id="761e2-148">Si aucune option n'est spécifiée, l'outil de conversion CorFlags affiche les indicateurs pour l'assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="761e2-148">If no options are specified, the CorFlags Conversion tool displays the flags for the specified assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761e2-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="761e2-149">See also</span></span>

- [<span data-ttu-id="761e2-150">Outils</span><span class="sxs-lookup"><span data-stu-id="761e2-150">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="761e2-151">Applications 64 bits</span><span class="sxs-lookup"><span data-stu-id="761e2-151">64-bit Applications</span></span>](../../../docs/framework/64-bit-apps.md)
- [<span data-ttu-id="761e2-152">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="761e2-152">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
