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
ms.openlocfilehash: a5b4783eadb8045733b9ebd6d10c4e31f7829498
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716679"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="35b00-102">Fonction InitDbgTransportManager</span><span class="sxs-lookup"><span data-stu-id="35b00-102">InitDbgTransportManager Function</span></span>

<span data-ttu-id="35b00-103">Initialise le gestionnaire de transport pour se connecter à une cible distante pour l'énumération des processus et du runtime.</span><span class="sxs-lookup"><span data-stu-id="35b00-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35b00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35b00-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="35b00-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="35b00-105">Return Value</span></span>  

 <span data-ttu-id="35b00-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="35b00-106">S_OK</span></span>  
 <span data-ttu-id="35b00-107">Réussite.</span><span class="sxs-lookup"><span data-stu-id="35b00-107">Success.</span></span>  
  
 <span data-ttu-id="35b00-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="35b00-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="35b00-109">La fonction n'a pas pu allouer de mémoire pour un gestionnaire de transport.</span><span class="sxs-lookup"><span data-stu-id="35b00-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="35b00-110">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="35b00-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="35b00-111">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="35b00-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35b00-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="35b00-112">Requirements</span></span>  

 <span data-ttu-id="35b00-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35b00-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35b00-114">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="35b00-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="35b00-115">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="35b00-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="35b00-116">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="35b00-116">**.NET Framework Versions:** 3.5 SP1</span></span>
