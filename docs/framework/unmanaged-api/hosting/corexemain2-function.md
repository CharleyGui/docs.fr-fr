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
ms.openlocfilehash: 8202fe4ec3ae6ef96440f203c5aea6db84744a72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616578"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="d1dc6-102">_CorExeMain2, fonction</span><span class="sxs-lookup"><span data-stu-id="d1dc6-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="d1dc6-103">Exécute le point d’entrée dans le code mappé en mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="d1dc6-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="d1dc6-104">Cette fonction est appelée par le chargeur du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="d1dc6-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1dc6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1dc6-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1dc6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d1dc6-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="d1dc6-107">dans Pointeur vers le code mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d1dc6-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="d1dc6-108">dans Le nombre d’éléments `pUnmappedPE` peut contenir.</span><span class="sxs-lookup"><span data-stu-id="d1dc6-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="d1dc6-109">dans Pointeur vers le nom de l’image exécutable.</span><span class="sxs-lookup"><span data-stu-id="d1dc6-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="d1dc6-110">dans Nom du fichier de chargeur.</span><span class="sxs-lookup"><span data-stu-id="d1dc6-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="d1dc6-111">dans Paramètres de ligne de commande, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="d1dc6-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1dc6-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d1dc6-112">Requirements</span></span>  
 <span data-ttu-id="d1dc6-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1dc6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1dc6-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d1dc6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1dc6-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d1dc6-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1dc6-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1dc6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1dc6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1dc6-117">See also</span></span>

- [<span data-ttu-id="d1dc6-118">Fonctions statiques globales des métadonnées</span><span class="sxs-lookup"><span data-stu-id="d1dc6-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
