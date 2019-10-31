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
ms.openlocfilehash: 2d67bee3ea0e57080179b3fbb7e0b4193860c44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103287"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="05399-102">Fonction InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="05399-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="05399-103">Initialise le gestionnaire de transport pour se connecter à une cible distante pour l'énumération des processus et du runtime.</span><span class="sxs-lookup"><span data-stu-id="05399-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05399-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05399-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="05399-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="05399-105">Return Value</span></span>  
 <span data-ttu-id="05399-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="05399-106">S_OK</span></span>  
 <span data-ttu-id="05399-107">Opération réussie.</span><span class="sxs-lookup"><span data-stu-id="05399-107">Success.</span></span>  
  
 <span data-ttu-id="05399-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="05399-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="05399-109">La fonction n'a pas pu allouer de mémoire pour un gestionnaire de transport.</span><span class="sxs-lookup"><span data-stu-id="05399-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="05399-110">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="05399-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="05399-111">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="05399-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05399-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="05399-112">Requirements</span></span>  
 <span data-ttu-id="05399-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05399-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05399-114">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="05399-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="05399-115">**Bibliothèque :** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="05399-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="05399-116">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="05399-116">**.NET Framework Versions:** 3.5 SP1</span></span>
