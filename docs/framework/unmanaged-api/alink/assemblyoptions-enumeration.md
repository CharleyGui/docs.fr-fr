---
title: Énumération AssemblyOptions
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49e7b73559e8def890f8df8f596fbe8ad5bb5d3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777478"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="ce167-102">Énumération AssemblyOptions</span><span class="sxs-lookup"><span data-stu-id="ce167-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="ce167-103">Énumère les options de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ce167-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce167-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce167-104">Syntax</span></span>  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="ce167-105">Champs</span><span class="sxs-lookup"><span data-stu-id="ce167-105">Fields</span></span>  
  
|<span data-ttu-id="ce167-106">Champ</span><span class="sxs-lookup"><span data-stu-id="ce167-106">Field</span></span>|<span data-ttu-id="ce167-107">Description</span><span class="sxs-lookup"><span data-stu-id="ce167-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ce167-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="ce167-108">optAssemTitle</span></span>|<span data-ttu-id="ce167-109">String : représente le titre de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ce167-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="ce167-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="ce167-110">optAssemDescription</span></span>|<span data-ttu-id="ce167-111">Chaîne : contient la description de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ce167-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="ce167-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="ce167-112">optAssemConfig</span></span>|<span data-ttu-id="ce167-113">Chaîne : contient la configuration de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ce167-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="ce167-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="ce167-114">optAssemOS</span></span>|<span data-ttu-id="ce167-115">Encodée sous forme de chaîne comme : "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="ce167-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="ce167-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="ce167-116">optAssemProcessor</span></span>|<span data-ttu-id="ce167-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="ce167-117">ULONG</span></span>|  
|<span data-ttu-id="ce167-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="ce167-118">optAssemLocale</span></span>|<span data-ttu-id="ce167-119">Chaîne : contient les paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ce167-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="ce167-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="ce167-120">optAssemVersion</span></span>|<span data-ttu-id="ce167-121">Codé sous forme de chaîne en tant que : « Major. mineure. Build. revision ».</span><span class="sxs-lookup"><span data-stu-id="ce167-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="ce167-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="ce167-122">optAssemCompany</span></span>|<span data-ttu-id="ce167-123">Chaîne : contient la société.</span><span class="sxs-lookup"><span data-stu-id="ce167-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="ce167-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="ce167-124">optAssemProduct</span></span>|<span data-ttu-id="ce167-125">Chaîne : contient le nom du produit.</span><span class="sxs-lookup"><span data-stu-id="ce167-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="ce167-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="ce167-126">optAssemProductVersion</span></span>|<span data-ttu-id="ce167-127">Chaîne (également appelée InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="ce167-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="ce167-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="ce167-128">optAssemCopyright</span></span>|<span data-ttu-id="ce167-129">Chaîne : contient les informations de copyright.</span><span class="sxs-lookup"><span data-stu-id="ce167-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="ce167-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="ce167-130">optAssemTrademark</span></span>|<span data-ttu-id="ce167-131">Chaîne : contient les informations relatives à la marque.</span><span class="sxs-lookup"><span data-stu-id="ce167-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="ce167-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="ce167-132">optAssemKeyFile</span></span>|<span data-ttu-id="ce167-133">Chaîne (nom de fichier).</span><span class="sxs-lookup"><span data-stu-id="ce167-133">String (file name).</span></span>|  
|<span data-ttu-id="ce167-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="ce167-134">optAssemKeyName</span></span>|<span data-ttu-id="ce167-135">Chaîne (nom de la clé).</span><span class="sxs-lookup"><span data-stu-id="ce167-135">String (The key name).</span></span>|  
|<span data-ttu-id="ce167-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="ce167-136">optAssemAlgID</span></span>|<span data-ttu-id="ce167-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="ce167-137">ULONG</span></span>|  
|<span data-ttu-id="ce167-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="ce167-138">optAssemFlags</span></span>|<span data-ttu-id="ce167-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="ce167-139">ULONG</span></span>|  
|<span data-ttu-id="ce167-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="ce167-140">optAssemHalfSign</span></span>|<span data-ttu-id="ce167-141">Bool (également appelé DelaySign).</span><span class="sxs-lookup"><span data-stu-id="ce167-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="ce167-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="ce167-142">optAssemFileVersion</span></span>|<span data-ttu-id="ce167-143">Encodée sous forme de chaîne « major. minor. Build. Revision »--identique à ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="ce167-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="ce167-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="ce167-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="ce167-145">Encodée sous forme de chaîne « major. minor. Build. revision ».</span><span class="sxs-lookup"><span data-stu-id="ce167-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="ce167-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="ce167-146">optLastAssemOption</span></span>|<span data-ttu-id="ce167-147">Compteur du nombre d’éléments.</span><span class="sxs-lookup"><span data-stu-id="ce167-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce167-148">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ce167-148">Requirements</span></span>  
 <span data-ttu-id="ce167-149">**En-tête :** ALink. h</span><span class="sxs-lookup"><span data-stu-id="ce167-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="ce167-150">**Bibliothèque**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="ce167-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce167-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce167-151">See also</span></span>

- [<span data-ttu-id="ce167-152">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="ce167-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
