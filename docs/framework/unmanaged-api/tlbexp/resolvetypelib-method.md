---
title: ResolveTypeLib, méthode
ms.date: 03/30/2017
api_name:
- ResolveTypeLib
api_location:
- tlbref.dll
f1_keywords:
- ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b6db8925fb966f4a8b2a213b0d6e340d0edf107
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756426"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="db4de-102">ResolveTypeLib, méthode</span><span class="sxs-lookup"><span data-stu-id="db4de-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="db4de-103">Résout le nom simple d’une bibliothèque de types en retournant son chemin d’accès qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="db4de-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db4de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db4de-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db4de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db4de-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="db4de-106">[in] Un [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) qui contient le nom simple de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="db4de-106">[in] A [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="db4de-107">[in] Le GUID affecté à la bibliothèque de types dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="db4de-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="db4de-108">[in] ID de localisation de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="db4de-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="db4de-109">[in] Numéro de version principale de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="db4de-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="db4de-110">Par exemple, pour la version *x.y*, le numéro de version majeure est *x*.</span><span class="sxs-lookup"><span data-stu-id="db4de-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="db4de-111">[in] Numéro de version secondaire de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="db4de-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="db4de-112">Par exemple, pour la version *x.y*, le numéro de version mineure est *y*.</span><span class="sxs-lookup"><span data-stu-id="db4de-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="db4de-113">[in] Un [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) indicateur qui identifie l’environnement d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="db4de-113">[in] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="db4de-114">Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="db4de-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="db4de-115">[out] Un pointeur vers un [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) qui contient le chemin d’accès complet de la bibliothèque de types nommée dans le `bstrSimpleName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="db4de-115">[out] A pointer to a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db4de-116">Notes</span><span class="sxs-lookup"><span data-stu-id="db4de-116">Remarks</span></span>  
 <span data-ttu-id="db4de-117">Le `ResolveTypeLib` méthode est appelée par le [LoadTypeLibWithResolver, fonction](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) pendant [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) de traitement.</span><span class="sxs-lookup"><span data-stu-id="db4de-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="db4de-118">Les implémentations personnalisées de cette interface doivent retourner un [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) qui contient le chemin d’accès complet de la bibliothèque de types nommée dans le `bstrSimpleName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="db4de-118">Custom implementations of this interface must return a [BSTR](https://docs.microsoft.com/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db4de-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="db4de-119">Requirements</span></span>  
 <span data-ttu-id="db4de-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db4de-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db4de-121">**En-tête :** TlbRef.idl, TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="db4de-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="db4de-122">**Bibliothèque :** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="db4de-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="db4de-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db4de-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db4de-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db4de-124">See also</span></span>

- [<span data-ttu-id="db4de-125">Fonctions d’assistance Tlbexp</span><span class="sxs-lookup"><span data-stu-id="db4de-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [<span data-ttu-id="db4de-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="db4de-126">LoadTypeLibEx</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
