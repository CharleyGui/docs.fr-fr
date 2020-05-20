---
title: IDebugAutoAttach::AutoAttach, méthode
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442122"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="21f12-102">IDebugAutoAttach::AutoAttach, méthode</span><span class="sxs-lookup"><span data-stu-id="21f12-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="21f12-103">Exécute l’attachement automatique du débogueur appelé par le serveur.</span><span class="sxs-lookup"><span data-stu-id="21f12-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21f12-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21f12-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21f12-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21f12-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="21f12-106">dans Toujours défini sur `GUID_NULL` .</span><span class="sxs-lookup"><span data-stu-id="21f12-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="21f12-107">dans ID de processus, normalement récupéré avec la `GetCurrentProcessId` fonction.</span><span class="sxs-lookup"><span data-stu-id="21f12-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="21f12-108">dans Type de programme : `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` ou `AUTOATTACH_PROGRAM_UNKNOWN` .</span><span class="sxs-lookup"><span data-stu-id="21f12-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="21f12-109">dans ID de programme.</span><span class="sxs-lookup"><span data-stu-id="21f12-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="21f12-110">dans Chaîne passée par le verbe Debug.</span><span class="sxs-lookup"><span data-stu-id="21f12-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21f12-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="21f12-111">Return Value</span></span>  
 <span data-ttu-id="21f12-112">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="21f12-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f12-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="21f12-113">Requirements</span></span>  
 <span data-ttu-id="21f12-114">**En-tête :** DbgAutoAttach. h</span><span class="sxs-lookup"><span data-stu-id="21f12-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f12-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21f12-115">See also</span></span>

- [<span data-ttu-id="21f12-116">IDebugAutoAttach, interface</span><span class="sxs-lookup"><span data-stu-id="21f12-116">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
