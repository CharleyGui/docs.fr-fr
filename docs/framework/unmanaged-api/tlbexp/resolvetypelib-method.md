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
ms.openlocfilehash: 65bbae614c8872ab5d78b3855b56ceaf2aad50da
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558184"
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="b2c18-102">ResolveTypeLib, méthode</span><span class="sxs-lookup"><span data-stu-id="b2c18-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="b2c18-103">Résout le nom simple d’une bibliothèque de types en retournant son chemin d’accès qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="b2c18-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2c18-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b2c18-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2c18-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="b2c18-106">dans [BSTR](/previous-versions/windows/desktop/automat/bstr) qui contient le nom simple de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="b2c18-106">[in] A [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="b2c18-107">dans GUID affecté à la bibliothèque de types dans le registre.</span><span class="sxs-lookup"><span data-stu-id="b2c18-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="b2c18-108">dans ID de localisation de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="b2c18-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="b2c18-109">dans Numéro de version principale de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="b2c18-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="b2c18-110">Par exemple, pour la version *x. y*, le numéro de version principale est *x*.</span><span class="sxs-lookup"><span data-stu-id="b2c18-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="b2c18-111">dans Numéro de version mineure de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="b2c18-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="b2c18-112">Par exemple, pour la version *x. y*, le numéro de version mineure est *y*.</span><span class="sxs-lookup"><span data-stu-id="b2c18-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="b2c18-113">dans Indicateur [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) qui identifie l’environnement d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b2c18-113">[in] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the operating environment.</span></span> <span data-ttu-id="b2c18-114">Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="b2c18-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="b2c18-115">à Pointeur vers un [BSTR](/previous-versions/windows/desktop/automat/bstr) qui contient le chemin d’accès complet de la bibliothèque de types nommée dans le `bstrSimpleName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b2c18-115">[out] A pointer to a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2c18-116">Notes</span><span class="sxs-lookup"><span data-stu-id="b2c18-116">Remarks</span></span>  
 <span data-ttu-id="b2c18-117">La `ResolveTypeLib` méthode est appelée par la [fonction LoadTypeLibWithResolver,](loadtypelibwithresolver-function.md) pendant le traitement [ deTlbexp.exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md) .</span><span class="sxs-lookup"><span data-stu-id="b2c18-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="b2c18-118">Les implémentations personnalisées de cette interface doivent retourner un [BSTR](/previous-versions/windows/desktop/automat/bstr) qui contient le chemin d’accès complet de la bibliothèque de types nommée dans le `bstrSimpleName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b2c18-118">Custom implementations of this interface must return a [BSTR](/previous-versions/windows/desktop/automat/bstr) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c18-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b2c18-119">Requirements</span></span>  
 <span data-ttu-id="b2c18-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c18-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c18-121">**En-tête :** TlbRef. idl, TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="b2c18-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="b2c18-122">**Bibliothèque :** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="b2c18-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="b2c18-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c18-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c18-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2c18-124">See also</span></span>

- [<span data-ttu-id="b2c18-125">Fonctions d’assistance Tlbexp</span><span class="sxs-lookup"><span data-stu-id="b2c18-125">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="b2c18-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="b2c18-126">LoadTypeLibEx</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
