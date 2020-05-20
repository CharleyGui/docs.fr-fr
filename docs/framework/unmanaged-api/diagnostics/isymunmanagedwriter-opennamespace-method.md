---
title: ISymUnmanagedWriter::OpenNamespace, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::OpenNamespace method [.NET Framework debugging]
- OpenNamespace method [.NET Framework debugging]
ms.assetid: 426f4e4f-e60d-4ad1-b546-a10e3c55c283
topic_type:
- apiref
ms.openlocfilehash: ab248c6a624fbed1a6783383566be093c449ff97
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609883"
---
# <a name="isymunmanagedwriteropennamespace-method"></a><span data-ttu-id="d84df-102">ISymUnmanagedWriter::OpenNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="d84df-102">ISymUnmanagedWriter::OpenNamespace Method</span></span>
<span data-ttu-id="d84df-103">Ouvre un nouvel espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d84df-103">Opens a new namespace.</span></span> <span data-ttu-id="d84df-104">Appelez cette méthode avant de définir des méthodes ou des variables qui occupent un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d84df-104">Call this method before defining methods or variables that occupy a namespace.</span></span> <span data-ttu-id="d84df-105">Les espaces de noms peuvent être imbriqués.</span><span class="sxs-lookup"><span data-stu-id="d84df-105">Namespaces can be nested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84df-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d84df-106">Syntax</span></span>  
  
```cpp  
HRESULT OpenNamespace(  
    [in] const WCHAR *name);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d84df-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d84df-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d84df-108">dans Pointeur vers le nom du nouvel espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d84df-108">[in] A pointer to the name of the new namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d84df-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d84df-109">Return Value</span></span>  
 <span data-ttu-id="d84df-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d84df-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d84df-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d84df-111">Requirements</span></span>  
 <span data-ttu-id="d84df-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d84df-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84df-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d84df-113">See also</span></span>

- [<span data-ttu-id="d84df-114">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="d84df-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d84df-115">CloseNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="d84df-115">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)
