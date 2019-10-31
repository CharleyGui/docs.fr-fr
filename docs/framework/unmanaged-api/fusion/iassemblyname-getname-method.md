---
title: IAssemblyName::GetName, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetName
helpviewer_keywords:
- GetName method, IAssemblyName interface [.NET Framework debugging]
- IAssemblyName::GetName method [.NET Framework fusion]
ms.assetid: 1dee9781-1cf3-48a9-a376-d18ea1f73280
topic_type:
- apiref
ms.openlocfilehash: 5f758d76d779cff7db119e69dc1cf3342071f1c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134350"
---
# <a name="iassemblynamegetname-method"></a><span data-ttu-id="7c5d8-102">IAssemblyName::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="7c5d8-102">IAssemblyName::GetName Method</span></span>
<span data-ttu-id="7c5d8-103">Obtient le nom simple et non chiffré de l’assembly référencé par cet objet [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7c5d8-103">Gets the simple, unencrypted name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c5d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c5d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in, out] LPDWORD lpcwBuffer,  
    [out]     WCHAR *pwzName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c5d8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7c5d8-105">Parameters</span></span>  
 `lpcwBuffer`  
 <span data-ttu-id="7c5d8-106">[in, out] Taille de `pwzName` en caractères larges, y compris le caractère de marque de fin null.</span><span class="sxs-lookup"><span data-stu-id="7c5d8-106">[in, out] The size of `pwzName` in wide characters, including the null terminator character.</span></span>  
  
 `pwzName`  
 <span data-ttu-id="7c5d8-107">à Mémoire tampon destinée à contenir le nom de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7c5d8-107">[out] A buffer to hold the name of the referenced assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c5d8-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="7c5d8-108">Requirements</span></span>  
 <span data-ttu-id="7c5d8-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c5d8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c5d8-110">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="7c5d8-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7c5d8-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c5d8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c5d8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c5d8-112">See also</span></span>

- [<span data-ttu-id="7c5d8-113">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="7c5d8-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
