---
title: ISymUnmanagedWriter::SetUserEntryPoint, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
ms.openlocfilehash: 951fc10a4560e0b4e256312017cdcd9a389f17f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427819"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="401fb-102">ISymUnmanagedWriter::SetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="401fb-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="401fb-103">Specifies the user-defined method that is the entry point for this module.</span><span class="sxs-lookup"><span data-stu-id="401fb-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="401fb-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span><span class="sxs-lookup"><span data-stu-id="401fb-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="401fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="401fb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="401fb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="401fb-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="401fb-107">[in] The metadata token for the method that is the user entry point.</span><span class="sxs-lookup"><span data-stu-id="401fb-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="401fb-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="401fb-108">Return Value</span></span>  
 <span data-ttu-id="401fb-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="401fb-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="401fb-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="401fb-110">Requirements</span></span>  
 <span data-ttu-id="401fb-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="401fb-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401fb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="401fb-112">See also</span></span>

- [<span data-ttu-id="401fb-113">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="401fb-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
