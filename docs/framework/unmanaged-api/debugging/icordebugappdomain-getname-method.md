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
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179087"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="ac52f-102">ICorDebugAppDomain::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="ac52f-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="ac52f-103">Obtient le nom du domaine de l’application.</span><span class="sxs-lookup"><span data-stu-id="ac52f-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac52f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac52f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac52f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac52f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ac52f-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="ac52f-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="ac52f-107">Définissez cette valeur à zéro pour mettre cette méthode en mode requête.</span><span class="sxs-lookup"><span data-stu-id="ac52f-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ac52f-108">[out] Un pointeur sur la taille du nom ou `szName`le nombre de caractères effectivement retournés dans .</span><span class="sxs-lookup"><span data-stu-id="ac52f-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="ac52f-109">En mode requête, cette valeur permet à l’appelant de savoir dans quelle mesure un tampon à allouer pour le nom.</span><span class="sxs-lookup"><span data-stu-id="ac52f-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ac52f-110">[out] Un tableau qui stocke le nom du domaine de l’application.</span><span class="sxs-lookup"><span data-stu-id="ac52f-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac52f-111">Notes </span><span class="sxs-lookup"><span data-stu-id="ac52f-111">Remarks</span></span>  
 <span data-ttu-id="ac52f-112">Un débbuggeur `GetName` appelle la méthode une fois pour obtenir la taille d’un tampon nécessaire pour le nom.</span><span class="sxs-lookup"><span data-stu-id="ac52f-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="ac52f-113">Le débbuggeur alloue le tampon, puis appelle la méthode une deuxième fois pour remplir le tampon.</span><span class="sxs-lookup"><span data-stu-id="ac52f-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="ac52f-114">Le premier appel, pour obtenir la taille du nom, est appelé *mode requête*.</span><span class="sxs-lookup"><span data-stu-id="ac52f-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac52f-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ac52f-115">Requirements</span></span>  
 <span data-ttu-id="ac52f-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac52f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac52f-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ac52f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac52f-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac52f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac52f-119">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac52f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
