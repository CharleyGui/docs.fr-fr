---
title: Fonction InitDbgTransportManager
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948e97064d12dc5b2044faf35aa374e5ba5f2592
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764786"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="4face-102">Fonction InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="4face-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="4face-103">Initialise le gestionnaire de transport pour se connecter à une cible distante pour l'énumération des processus et du runtime.</span><span class="sxs-lookup"><span data-stu-id="4face-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4face-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4face-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4face-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4face-105">Return Value</span></span>  
 <span data-ttu-id="4face-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="4face-106">S_OK</span></span>  
 <span data-ttu-id="4face-107">Opération réussie.</span><span class="sxs-lookup"><span data-stu-id="4face-107">Success.</span></span>  
  
 <span data-ttu-id="4face-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4face-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="4face-109">La fonction n'a pas pu allouer de mémoire pour un gestionnaire de transport.</span><span class="sxs-lookup"><span data-stu-id="4face-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="4face-110">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="4face-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4face-111">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="4face-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4face-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4face-112">Requirements</span></span>  
 <span data-ttu-id="4face-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4face-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4face-114">**En-tête :** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="4face-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="4face-115">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="4face-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="4face-116">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="4face-116">**.NET Framework Versions:** 3.5 SP1</span></span>
