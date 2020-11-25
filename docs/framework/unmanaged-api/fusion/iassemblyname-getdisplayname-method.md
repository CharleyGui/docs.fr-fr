---
title: IAssemblyName::GetDisplayName, méthode
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 13d71a9da2539c45076e5eb92e153e37c1df4b47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727911"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="c4607-102">IAssemblyName::GetDisplayName, méthode</span><span class="sxs-lookup"><span data-stu-id="c4607-102">IAssemblyName::GetDisplayName Method</span></span>

<span data-ttu-id="c4607-103">Obtient le nom explicite de l’assembly référencé par cet objet [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c4607-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4607-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4607-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4607-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4607-105">Parameters</span></span>  

 `szDisplayName`  
 <span data-ttu-id="c4607-106">à Mémoire tampon de chaîne qui contient le nom de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="c4607-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="c4607-107">[in, out] Taille de `szDisplayName` en caractères larges, y compris un caractère de fin null.</span><span class="sxs-lookup"><span data-stu-id="c4607-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="c4607-108">dans Combinaison d’opérations de bits de valeurs [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) qui influencent les fonctionnalités de `szDisplayName` .</span><span class="sxs-lookup"><span data-stu-id="c4607-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4607-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c4607-109">Requirements</span></span>  

 <span data-ttu-id="c4607-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4607-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4607-111">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c4607-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c4607-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4607-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4607-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4607-113">See also</span></span>

- [<span data-ttu-id="c4607-114">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="c4607-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="c4607-115">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="c4607-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
