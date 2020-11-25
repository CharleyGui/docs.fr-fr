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
ms.openlocfilehash: 352e1acd1fdd8297754e18b2e8c6448ea723a557
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717029"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="ed5f6-102">Énumération AssemblyOptions</span><span class="sxs-lookup"><span data-stu-id="ed5f6-102">AssemblyOptions Enumeration</span></span>

<span data-ttu-id="ed5f6-103">Énumère les options de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed5f6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ed5f6-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="ed5f6-105">Champs</span><span class="sxs-lookup"><span data-stu-id="ed5f6-105">Fields</span></span>  
  
|<span data-ttu-id="ed5f6-106">Champ</span><span class="sxs-lookup"><span data-stu-id="ed5f6-106">Field</span></span>|<span data-ttu-id="ed5f6-107">Description</span><span class="sxs-lookup"><span data-stu-id="ed5f6-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed5f6-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="ed5f6-108">optAssemTitle</span></span>|<span data-ttu-id="ed5f6-109">String : représente le titre de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="ed5f6-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="ed5f6-110">optAssemDescription</span></span>|<span data-ttu-id="ed5f6-111">Chaîne : contient la description de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="ed5f6-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="ed5f6-112">optAssemConfig</span></span>|<span data-ttu-id="ed5f6-113">Chaîne : contient la configuration de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="ed5f6-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="ed5f6-114">optAssemOS</span></span>|<span data-ttu-id="ed5f6-115">Encodée sous forme de chaîne comme : "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="ed5f6-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="ed5f6-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="ed5f6-116">optAssemProcessor</span></span>|<span data-ttu-id="ed5f6-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="ed5f6-117">ULONG</span></span>|  
|<span data-ttu-id="ed5f6-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="ed5f6-118">optAssemLocale</span></span>|<span data-ttu-id="ed5f6-119">Chaîne : contient les paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="ed5f6-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="ed5f6-120">optAssemVersion</span></span>|<span data-ttu-id="ed5f6-121">Encodée sous forme de chaîne comme : "major. minor. Build. Revision".</span><span class="sxs-lookup"><span data-stu-id="ed5f6-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="ed5f6-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="ed5f6-122">optAssemCompany</span></span>|<span data-ttu-id="ed5f6-123">Chaîne : contient la société.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="ed5f6-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="ed5f6-124">optAssemProduct</span></span>|<span data-ttu-id="ed5f6-125">Chaîne : contient le nom du produit.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="ed5f6-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="ed5f6-126">optAssemProductVersion</span></span>|<span data-ttu-id="ed5f6-127">Chaîne (également appelée InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="ed5f6-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="ed5f6-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="ed5f6-128">optAssemCopyright</span></span>|<span data-ttu-id="ed5f6-129">Chaîne : contient les informations de copyright.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="ed5f6-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="ed5f6-130">optAssemTrademark</span></span>|<span data-ttu-id="ed5f6-131">Chaîne : contient les informations relatives à la marque.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="ed5f6-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="ed5f6-132">optAssemKeyFile</span></span>|<span data-ttu-id="ed5f6-133">Chaîne (nom de fichier).</span><span class="sxs-lookup"><span data-stu-id="ed5f6-133">String (file name).</span></span>|  
|<span data-ttu-id="ed5f6-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="ed5f6-134">optAssemKeyName</span></span>|<span data-ttu-id="ed5f6-135">Chaîne (nom de la clé).</span><span class="sxs-lookup"><span data-stu-id="ed5f6-135">String (The key name).</span></span>|  
|<span data-ttu-id="ed5f6-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="ed5f6-136">optAssemAlgID</span></span>|<span data-ttu-id="ed5f6-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="ed5f6-137">ULONG</span></span>|  
|<span data-ttu-id="ed5f6-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="ed5f6-138">optAssemFlags</span></span>|<span data-ttu-id="ed5f6-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="ed5f6-139">ULONG</span></span>|  
|<span data-ttu-id="ed5f6-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="ed5f6-140">optAssemHalfSign</span></span>|<span data-ttu-id="ed5f6-141">Bool (également appelé DelaySign).</span><span class="sxs-lookup"><span data-stu-id="ed5f6-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="ed5f6-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="ed5f6-142">optAssemFileVersion</span></span>|<span data-ttu-id="ed5f6-143">Encodée sous forme de chaîne « major. minor. Build. Revision »--identique à ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="ed5f6-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="ed5f6-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="ed5f6-145">Encodée sous forme de chaîne « major. minor. Build. revision ».</span><span class="sxs-lookup"><span data-stu-id="ed5f6-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="ed5f6-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="ed5f6-146">optLastAssemOption</span></span>|<span data-ttu-id="ed5f6-147">Compteur du nombre d’éléments.</span><span class="sxs-lookup"><span data-stu-id="ed5f6-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed5f6-148">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ed5f6-148">Requirements</span></span>  

 <span data-ttu-id="ed5f6-149">**En-tête :** ALink. h</span><span class="sxs-lookup"><span data-stu-id="ed5f6-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="ed5f6-150">**Bibliothèque**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="ed5f6-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed5f6-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed5f6-151">See also</span></span>

- [<span data-ttu-id="ed5f6-152">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="ed5f6-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
