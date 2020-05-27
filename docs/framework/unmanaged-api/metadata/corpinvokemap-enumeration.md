---
title: CorPinvokeMap, énumération
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 199a649b0481c2a740926636345eefbda6831ef2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007544"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="e0a2b-102">CorPinvokeMap, énumération</span><span class="sxs-lookup"><span data-stu-id="e0a2b-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="e0a2b-103">Spécifie les options d’un appel PInvoke.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0a2b-104">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="e0a2b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e0a2b-105">Members</span></span>  
  
|<span data-ttu-id="e0a2b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e0a2b-106">Member</span></span>|<span data-ttu-id="e0a2b-107">Description</span><span class="sxs-lookup"><span data-stu-id="e0a2b-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="e0a2b-108">Utilisez chaque nom de membre comme spécifié.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="e0a2b-109">Réservé.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="e0a2b-110">Réservé.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="e0a2b-111">Les chaînes sont marshalées sous forme de chaînes de caractères à plusieurs octets.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="e0a2b-112">Les chaînes sont marshalées sous forme de caractères Unicode de 2 octets.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="e0a2b-113">Les chaînes sont automatiquement marshalées, comme requis par le système d'exploitation cible.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="e0a2b-114">La valeur par défaut est Unicode sur Windows NT, Windows 2000, Windows XP et la famille Windows Server 2003. la valeur par défaut est ANSI sur Windows 98 et Windows Me.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="e0a2b-115">Réservé.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="e0a2b-116">Effectuez le mappage le mieux adapté des caractères Unicode qui n’ont pas de correspondance exacte dans le jeu de caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="e0a2b-117">N’effectuez pas le mappage le mieux adapté des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="e0a2b-118">Dans ce cas, tous les caractères non mappables seront remplacés par un «  ? ».</span><span class="sxs-lookup"><span data-stu-id="e0a2b-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="e0a2b-119">Réservé.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="e0a2b-120">Réservé.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="e0a2b-121">Levez une exception lorsque le marshaleur d’interopérabilité rencontre un caractère non mappable.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="e0a2b-122">Ne levez pas d’exception lorsque le marshaleur d’interopérabilité rencontre un caractère non mappable.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="e0a2b-123">Réservé</span><span class="sxs-lookup"><span data-stu-id="e0a2b-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="e0a2b-124">Autorisez l’appelé à appeler la `SetLastError` fonction Win32 avant de retourner la méthode avec attributs.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="e0a2b-125">Réservé</span><span class="sxs-lookup"><span data-stu-id="e0a2b-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="e0a2b-126">Utilisez la Convention d’appel de la plateforme par défaut.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-126">Use the default platform calling convention.</span></span> <span data-ttu-id="e0a2b-127">Par exemple, sur Windows, la valeur par défaut est `StdCall` et sur Windows CE .net il s’agit de `Cdecl` .</span><span class="sxs-lookup"><span data-stu-id="e0a2b-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="e0a2b-128">Utilisez la `Cdecl` Convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="e0a2b-129">Dans ce cas, l’appelant nettoie la pile.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="e0a2b-130">Cela permet d’appeler des fonctions avec les `varargs` fonctions (autrement dit, les fonctions qui acceptent un nombre variable de paramètres).</span><span class="sxs-lookup"><span data-stu-id="e0a2b-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="e0a2b-131">Utilisez la `StdCall` Convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="e0a2b-132">Dans ce cas, l’appelé nettoie la pile.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="e0a2b-133">Il s'agit de la convention par défaut pour appeler les fonctions non managées avec appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="e0a2b-134">Utilisez la `ThisCall` Convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="e0a2b-135">Dans ce cas, le premier paramètre est le `this` pointeur et est stocké dans le registre ECX.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="e0a2b-136">D'autres paramètres font l'objet d'un push sur la pile.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="e0a2b-137">La `ThisCall` Convention d’appel est utilisée pour appeler des méthodes sur des classes exportées à partir d’une DLL non managée.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="e0a2b-138">Réservé.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="e0a2b-139">Réservé.</span><span class="sxs-lookup"><span data-stu-id="e0a2b-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0a2b-140">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e0a2b-140">Requirements</span></span>  
 <span data-ttu-id="e0a2b-141">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0a2b-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a2b-142">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="e0a2b-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e0a2b-143">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0a2b-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a2b-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0a2b-144">See also</span></span>

- [<span data-ttu-id="e0a2b-145">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="e0a2b-145">Metadata Enumerations</span></span>](metadata-enumerations.md)
