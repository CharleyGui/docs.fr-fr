---
title: ICLRDataTarget::GetPointerSize, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
ms.openlocfilehash: e6c4d5f8cc911198add176cab9c4b9b89128068e
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860623"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="0df74-102">ICLRDataTarget::GetPointerSize, méthode</span><span class="sxs-lookup"><span data-stu-id="0df74-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="0df74-103">Obtient la taille, en octets, du type pointeur utilisé par le processus cible.</span><span class="sxs-lookup"><span data-stu-id="0df74-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="0df74-104">Cette méthode est appelée par les services d’accès aux données common language runtime.</span><span class="sxs-lookup"><span data-stu-id="0df74-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df74-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0df74-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0df74-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0df74-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="0df74-107">à Pointeur vers une valeur entière qui spécifie la taille, en octets, d’un pointeur sur le processus cible.</span><span class="sxs-lookup"><span data-stu-id="0df74-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0df74-108">Notes </span><span class="sxs-lookup"><span data-stu-id="0df74-108">Remarks</span></span>  
 <span data-ttu-id="0df74-109">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="0df74-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0df74-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0df74-110">Requirements</span></span>  
 <span data-ttu-id="0df74-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0df74-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0df74-112">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="0df74-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0df74-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0df74-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0df74-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df74-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0df74-115">See also</span></span>

- [<span data-ttu-id="0df74-116">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="0df74-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
