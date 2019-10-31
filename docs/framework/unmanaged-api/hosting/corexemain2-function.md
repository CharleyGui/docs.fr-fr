---
title: _CorExeMain2, fonction
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: cc5324683daa9a02a6a89b2a3fb57ee9fd5dbe72
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136961"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="8224b-102">_CorExeMain2, fonction</span><span class="sxs-lookup"><span data-stu-id="8224b-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="8224b-103">Exécute le point d’entrée dans le code mappé en mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="8224b-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="8224b-104">Cette fonction est appelée par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="8224b-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8224b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8224b-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8224b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8224b-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="8224b-107">dans Pointeur vers le code mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="8224b-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="8224b-108">dans Nombre d’éléments que `pUnmappedPE` peut contenir.</span><span class="sxs-lookup"><span data-stu-id="8224b-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="8224b-109">dans Pointeur vers le nom de l’image exécutable.</span><span class="sxs-lookup"><span data-stu-id="8224b-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="8224b-110">dans Nom du fichier de chargeur.</span><span class="sxs-lookup"><span data-stu-id="8224b-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="8224b-111">dans Paramètres de ligne de commande, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="8224b-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8224b-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="8224b-112">Requirements</span></span>  
 <span data-ttu-id="8224b-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8224b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8224b-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8224b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8224b-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8224b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8224b-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8224b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8224b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8224b-117">See also</span></span>

- [<span data-ttu-id="8224b-118">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="8224b-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
