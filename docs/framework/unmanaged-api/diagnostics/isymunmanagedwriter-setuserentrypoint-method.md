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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11dc050e2fe16a64db4ac95bb1386e2d90535e81
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895026"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="a502e-102">ISymUnmanagedWriter::SetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="a502e-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="a502e-103">Spécifie la méthode définie par l’utilisateur qui est le point d’entrée de ce module.</span><span class="sxs-lookup"><span data-stu-id="a502e-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="a502e-104">Par exemple, ce point d’entrée peut être la méthode main de l’utilisateur au lieu des stubs générés par le compilateur avant main.</span><span class="sxs-lookup"><span data-stu-id="a502e-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a502e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a502e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a502e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a502e-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="a502e-107">dans Jeton de métadonnées pour la méthode qui est le point d’entrée de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a502e-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a502e-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a502e-108">Return Value</span></span>  
 <span data-ttu-id="a502e-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a502e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a502e-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a502e-110">Requirements</span></span>  
 <span data-ttu-id="a502e-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a502e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a502e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a502e-112">See also</span></span>

- [<span data-ttu-id="a502e-113">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="a502e-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
