---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 5a501cca16f06e7ccd5da9f65a213c6b24c1092c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441784"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="51c2b-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="51c2b-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="51c2b-103">Définissez un groupe d’opérations await Async dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="51c2b-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="51c2b-104">Chaque décalage de rendement correspond à l’instruction de retour d’une instruction await, identifiant un rendement potentiel.</span><span class="sxs-lookup"><span data-stu-id="51c2b-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="51c2b-105">Chaque `breakpointMethod` / `breakpointOffset` paire nous indique où l’opération asynchrone reprend, qui peut se trouver dans une méthode différente.</span><span class="sxs-lookup"><span data-stu-id="51c2b-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51c2b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51c2b-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51c2b-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51c2b-107">Parameters</span></span>  
  
|<span data-ttu-id="51c2b-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="51c2b-108">Parameter</span></span>|<span data-ttu-id="51c2b-109">Description</span><span class="sxs-lookup"><span data-stu-id="51c2b-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="51c2b-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="51c2b-110">Return Value</span></span>  
 <span data-ttu-id="51c2b-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="51c2b-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51c2b-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="51c2b-112">Requirements</span></span>  
 <span data-ttu-id="51c2b-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="51c2b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c2b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51c2b-114">See also</span></span>

- [<span data-ttu-id="51c2b-115">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="51c2b-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
