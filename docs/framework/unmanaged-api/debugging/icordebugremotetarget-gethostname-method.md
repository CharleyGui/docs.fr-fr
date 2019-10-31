---
title: ICorDebugRemoteTarget::GetHostName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
ms.openlocfilehash: a9a6ca9ae3cdb1c6a7398d08c9f99e3cde125cf6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131896"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="3e7d1-102">ICorDebugRemoteTarget::GetHostName, méthode</span><span class="sxs-lookup"><span data-stu-id="3e7d1-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="3e7d1-103">Retourne le nom de domaine complet ou l’adresse IPv4 de l’ordinateur cible de débogage distant.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="3e7d1-104">IPV6 n’est pas pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e7d1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e7d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e7d1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e7d1-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="3e7d1-107">dans Taille, en caractères, de la mémoire tampon de `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="3e7d1-108">Si ce paramètre a la valeur 0 (zéro), `szHostName` doit avoir la valeur null.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="3e7d1-109">à Nombre de caractères, y compris la marque de fin null, dans le nom d’hôte ou l’adresse IP.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="3e7d1-110">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="3e7d1-111">à Mémoire tampon qui contient le nom d’hôte ou l’adresse IP.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e7d1-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3e7d1-112">Return Value</span></span>  
 <span data-ttu-id="3e7d1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e7d1-113">S_OK</span></span>  
 <span data-ttu-id="3e7d1-114">Le nom d’hôte ou l’adresse IP a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="3e7d1-115">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="3e7d1-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="3e7d1-116">Impossible de retourner le nom d’hôte ou l’adresse IP.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e7d1-117">Notes</span><span class="sxs-lookup"><span data-stu-id="3e7d1-117">Remarks</span></span>  
 <span data-ttu-id="3e7d1-118">Cette méthode est implémentée par l’enregistreur du débogueur.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="3e7d1-119">Il doit suivre le paradigme d’appel multiple : lors du premier appel, l’appelant passe la valeur null à `cchHostName` et `szHostName`, et `pcchHostName` retourne la taille de la mémoire tampon requise.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="3e7d1-120">Lors du deuxième appel, la taille précédemment retournée est passée dans `cchHostName`, et une mémoire tampon de taille appropriée est transmise `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="3e7d1-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e7d1-121">spécifications</span><span class="sxs-lookup"><span data-stu-id="3e7d1-121">Requirements</span></span>  
 <span data-ttu-id="3e7d1-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e7d1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e7d1-123">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="3e7d1-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="3e7d1-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e7d1-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e7d1-125">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="3e7d1-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e7d1-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e7d1-126">See also</span></span>

- [<span data-ttu-id="3e7d1-127">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="3e7d1-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="3e7d1-128">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="3e7d1-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
