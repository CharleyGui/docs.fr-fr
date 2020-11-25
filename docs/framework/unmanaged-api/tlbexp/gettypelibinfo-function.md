---
title: Fonction GetTypeLibInfo
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
ms.openlocfilehash: e9f6ae9a0fcd6651395c54c2e44973e53668c1ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708320"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="c5c10-102">Fonction GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="c5c10-102">GetTypeLibInfo Function</span></span>

<span data-ttu-id="c5c10-103">Retourne des informations sur la bibliothèque de types spécifiée en examinant sa structure [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) .</span><span class="sxs-lookup"><span data-stu-id="c5c10-103">Returns information about the specified type library by examining its [TLIBATTR](/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5c10-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5c10-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5c10-105">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="c5c10-106">dans Nom de fichier de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="c5c10-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="c5c10-107">à GUID de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="c5c10-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="c5c10-108">à ID de localisation de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="c5c10-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="c5c10-109">à Indicateur [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) qui identifie le système d’exploitation cible de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="c5c10-109">[out] A [SYSKIND](/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="c5c10-110">Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="c5c10-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="c5c10-111">à Numéro de version principale de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="c5c10-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="c5c10-112">Par exemple, pour la version *x. y*, le numéro de version principale est *x*.</span><span class="sxs-lookup"><span data-stu-id="c5c10-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="c5c10-113">à Numéro de version mineure de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="c5c10-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="c5c10-114">Par exemple, pour la version *x. y*, le numéro de version mineure est *y*.</span><span class="sxs-lookup"><span data-stu-id="c5c10-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5c10-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5c10-115">Remarks</span></span>  

 <span data-ttu-id="c5c10-116">La `GetTypeLibInfo` fonction est appelée par le [Tlbexp.exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="c5c10-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="c5c10-117">Cet outil génère une bibliothèque de types qui décrit les types dans un assembly common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c5c10-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="c5c10-118">Si un paramètre a la valeur null, la fonction retourne un `HRESULT` de `E_POINTER` .</span><span class="sxs-lookup"><span data-stu-id="c5c10-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="c5c10-119">Sinon, `S_OK`est retourné.</span><span class="sxs-lookup"><span data-stu-id="c5c10-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c10-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c5c10-120">Requirements</span></span>  

 <span data-ttu-id="c5c10-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5c10-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c10-122">**En-tête :** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="c5c10-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="c5c10-123">**Bibliothèque :** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="c5c10-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="c5c10-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c10-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c10-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5c10-125">See also</span></span>

- [<span data-ttu-id="c5c10-126">Fonctions d’assistance Tlbexp</span><span class="sxs-lookup"><span data-stu-id="c5c10-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="c5c10-127">LoadTypeLibEx fonction)</span><span class="sxs-lookup"><span data-stu-id="c5c10-127">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
