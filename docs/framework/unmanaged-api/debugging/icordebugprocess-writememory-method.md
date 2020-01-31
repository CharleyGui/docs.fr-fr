---
title: ICorDebugProcess::WriteMemory, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: fb3e0ccb57cf3b056bd25e643706e49b8bc75531
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792539"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="26683-102">ICorDebugProcess::WriteMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="26683-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="26683-103">Écrit des données dans une zone de mémoire dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="26683-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26683-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26683-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26683-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="26683-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="26683-106">dans Valeur `CORDB_ADDRESS` qui est l’adresse de base de la zone mémoire dans laquelle les données sont écrites.</span><span class="sxs-lookup"><span data-stu-id="26683-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="26683-107">Avant le transfert de données, le système vérifie que la zone mémoire de la taille spécifiée, en commençant à l’adresse de base, est accessible en écriture.</span><span class="sxs-lookup"><span data-stu-id="26683-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="26683-108">S’il n’est pas accessible, la méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="26683-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="26683-109">dans Nombre d’octets à écrire dans la zone mémoire.</span><span class="sxs-lookup"><span data-stu-id="26683-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="26683-110">dans Mémoire tampon qui contient les données à écrire.</span><span class="sxs-lookup"><span data-stu-id="26683-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="26683-111">à Pointeur vers une variable qui reçoit le nombre d’octets écrits dans la zone mémoire de ce processus.</span><span class="sxs-lookup"><span data-stu-id="26683-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="26683-112">Si `written` a la valeur NULL, ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="26683-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26683-113">Notes</span><span class="sxs-lookup"><span data-stu-id="26683-113">Remarks</span></span>  
 <span data-ttu-id="26683-114">Les données sont écrites automatiquement derrière des points d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="26683-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="26683-115">Dans la version .NET Framework 2,0, les débogueurs natifs ne doivent pas utiliser cette méthode pour injecter des points d’arrêt dans le flux d’instructions.</span><span class="sxs-lookup"><span data-stu-id="26683-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="26683-116">Utilisez [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="26683-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="26683-117">La méthode `WriteMemory` doit être utilisée uniquement en dehors du code managé.</span><span class="sxs-lookup"><span data-stu-id="26683-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="26683-118">Cette méthode peut endommager le runtime si elle est utilisée de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="26683-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26683-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="26683-119">Requirements</span></span>  
 <span data-ttu-id="26683-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26683-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26683-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26683-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26683-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26683-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26683-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26683-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
