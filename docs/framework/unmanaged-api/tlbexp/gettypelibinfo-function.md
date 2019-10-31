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
ms.openlocfilehash: e64a0512e05965b3da2e7486e986ee34ca8a20d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104304"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="dc729-102">Fonction GetTypeLibInfo</span><span class="sxs-lookup"><span data-stu-id="dc729-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="dc729-103">Retourne des informations sur la bibliothèque de types spécifiée en examinant sa structure [TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) .</span><span class="sxs-lookup"><span data-stu-id="dc729-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/windows/win32/api/oaidl/ns-oaidl-tlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc729-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc729-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dc729-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc729-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="dc729-106">dans Nom de fichier de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="dc729-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="dc729-107">à GUID de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="dc729-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="dc729-108">à ID de localisation de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="dc729-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="dc729-109">à Indicateur [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) qui identifie le système d’exploitation cible de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="dc729-109">[out] A [SYSKIND](https://docs.microsoft.com/windows/win32/api/oaidl/ne-oaidl-syskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="dc729-110">Les valeurs courantes sont SYS_WIN32 et SYS_WIN64.</span><span class="sxs-lookup"><span data-stu-id="dc729-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="dc729-111">à Numéro de version principale de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="dc729-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="dc729-112">Par exemple, pour la version *x. y*, le numéro de version principale est *x*.</span><span class="sxs-lookup"><span data-stu-id="dc729-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="dc729-113">à Numéro de version mineure de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="dc729-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="dc729-114">Par exemple, pour la version *x. y*, le numéro de version mineure est *y*.</span><span class="sxs-lookup"><span data-stu-id="dc729-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc729-115">Notes</span><span class="sxs-lookup"><span data-stu-id="dc729-115">Remarks</span></span>  
 <span data-ttu-id="dc729-116">La fonction `GetTypeLibInfo` est appelée par [Tlbexp. exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="dc729-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="dc729-117">Cet outil génère une bibliothèque de types qui décrit les types dans un assembly common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="dc729-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="dc729-118">Si un paramètre a la valeur null, la fonction retourne une `HRESULT` de `E_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="dc729-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="dc729-119">Sinon, il retourne `S_OK`.</span><span class="sxs-lookup"><span data-stu-id="dc729-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc729-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="dc729-120">Requirements</span></span>  
 <span data-ttu-id="dc729-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc729-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc729-122">**En-tête :** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="dc729-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="dc729-123">**Bibliothèque :** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="dc729-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="dc729-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc729-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc729-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc729-125">See also</span></span>

- [<span data-ttu-id="dc729-126">Fonctions d’assistance Tlbexp</span><span class="sxs-lookup"><span data-stu-id="dc729-126">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="dc729-127">LoadTypeLibEx fonction)</span><span class="sxs-lookup"><span data-stu-id="dc729-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
