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
ms.openlocfilehash: e18ceb25b9c58a9710ef967cb071e3ef55beea8c
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421044"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="fc556-102">Fonction InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="fc556-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="fc556-103">Initialise le gestionnaire de transport pour se connecter à une cible distante pour l'énumération des processus et du runtime.</span><span class="sxs-lookup"><span data-stu-id="fc556-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc556-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc556-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fc556-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fc556-105">Return Value</span></span>  
 <span data-ttu-id="fc556-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc556-106">S_OK</span></span>  
 <span data-ttu-id="fc556-107">Opération réussie.</span><span class="sxs-lookup"><span data-stu-id="fc556-107">Success.</span></span>  
  
 <span data-ttu-id="fc556-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fc556-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="fc556-109">La fonction n'a pas pu allouer de mémoire pour un gestionnaire de transport.</span><span class="sxs-lookup"><span data-stu-id="fc556-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="fc556-110">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="fc556-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="fc556-111">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="fc556-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc556-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="fc556-112">Requirements</span></span>  
 <span data-ttu-id="fc556-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc556-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc556-114">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="fc556-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="fc556-115">**Bibliothèque :** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="fc556-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="fc556-116">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="fc556-116">**.NET Framework Versions:** 3.5 SP1</span></span>
