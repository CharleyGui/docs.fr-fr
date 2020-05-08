---
title: ICorDebugAppDomain::GetName, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
ms.openlocfilehash: 3db37576f5da7b26e7bd9d3343f8bb8b97f2ba82
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895242"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="ef1d0-102">ICorDebugAppDomain::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="ef1d0-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="ef1d0-103">Obtient le nom du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef1d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef1d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef1d0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef1d0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ef1d0-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="ef1d0-107">Définissez cette valeur sur zéro pour mettre cette méthode en mode requête.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ef1d0-108">à Pointeur vers la taille du nom ou le nombre de caractères réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="ef1d0-109">En mode requête, cette valeur permet à l’appelant de connaître la taille d’une mémoire tampon à allouer au nom.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ef1d0-110">à Tableau qui stocke le nom du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef1d0-111">Notes </span><span class="sxs-lookup"><span data-stu-id="ef1d0-111">Remarks</span></span>  
 <span data-ttu-id="ef1d0-112">Un débogueur appelle la `GetName` méthode une fois pour obtenir la taille d’une mémoire tampon nécessaire pour le nom.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="ef1d0-113">Le débogueur alloue la mémoire tampon, puis appelle la méthode une deuxième fois pour remplir la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="ef1d0-114">Le premier appel, pour obtenir la taille du nom, est appelé *mode de requête*.</span><span class="sxs-lookup"><span data-stu-id="ef1d0-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef1d0-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ef1d0-115">Requirements</span></span>  
 <span data-ttu-id="ef1d0-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef1d0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef1d0-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef1d0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef1d0-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef1d0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef1d0-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef1d0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
