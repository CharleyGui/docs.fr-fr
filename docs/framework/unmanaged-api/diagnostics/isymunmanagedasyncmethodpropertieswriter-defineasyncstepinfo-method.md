---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 59e3a95a4d2573263600da60b4f852caa361138e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129200"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="fabcd-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="fabcd-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="fabcd-103">Définissez un groupe d’opérations await Async dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="fabcd-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="fabcd-104">Chaque décalage de rendement correspond à l’instruction de retour d’une instruction await, identifiant un rendement potentiel.</span><span class="sxs-lookup"><span data-stu-id="fabcd-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="fabcd-105">Chaque `breakpointMethod`/paire de `breakpointOffset` indique où l’opération asynchrone reprend, qui peut se trouver dans une méthode différente.</span><span class="sxs-lookup"><span data-stu-id="fabcd-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fabcd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fabcd-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fabcd-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fabcd-107">Parameters</span></span>  
  
|<span data-ttu-id="fabcd-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="fabcd-108">Parameter</span></span>|<span data-ttu-id="fabcd-109">Description</span><span class="sxs-lookup"><span data-stu-id="fabcd-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="fabcd-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fabcd-110">Return Value</span></span>  
 <span data-ttu-id="fabcd-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="fabcd-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fabcd-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="fabcd-112">Requirements</span></span>  
 <span data-ttu-id="fabcd-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fabcd-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fabcd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fabcd-114">See also</span></span>

- [<span data-ttu-id="fabcd-115">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="fabcd-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
