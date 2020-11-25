---
title: ICLRMetaHost::ExitProcess, méthode
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
ms.openlocfilehash: 6d601ac3ece801353b630c74ed852c2657f25d7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730460"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="b4b22-102">ICLRMetaHost::ExitProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="b4b22-102">ICLRMetaHost::ExitProcess Method</span></span>

<span data-ttu-id="b4b22-103">Tente d’arrêter correctement tous les runtimes chargés, puis termine le processus.</span><span class="sxs-lookup"><span data-stu-id="b4b22-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="b4b22-104">Remplace la fonction [CorExitProcess,](corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b4b22-104">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b22-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4b22-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4b22-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4b22-106">Parameters</span></span>  

 `iExitCode`  
 <span data-ttu-id="b4b22-107">dans Code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="b4b22-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4b22-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b4b22-108">Return Value</span></span>  

 <span data-ttu-id="b4b22-109">Cette méthode ne retourne jamais, donc sa valeur de retour n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="b4b22-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4b22-110">Notes</span><span class="sxs-lookup"><span data-stu-id="b4b22-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4b22-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b4b22-111">Requirements</span></span>  

 <span data-ttu-id="b4b22-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4b22-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4b22-113">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="b4b22-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b4b22-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4b22-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4b22-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4b22-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b22-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4b22-116">See also</span></span>

- [<span data-ttu-id="b4b22-117">ICLRMetaHost, interface</span><span class="sxs-lookup"><span data-stu-id="b4b22-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="b4b22-118">Hébergement</span><span class="sxs-lookup"><span data-stu-id="b4b22-118">Hosting</span></span>](index.md)
