---
title: ISymUnmanagedWriter::DefineGlobalVariable, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: 94d1aa5bba87e8ca11b58bdf89a697e1ccf500b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428023"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="5f2e8-102">ISymUnmanagedWriter::DefineGlobalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="5f2e8-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="5f2e8-103">Définit une variable globale unique.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f2e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f2e8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f2e8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5f2e8-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5f2e8-106">dans Pointeur vers un `WCHAR` qui définit le nom de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="5f2e8-107">dans Attributs de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="5f2e8-108">dans `ULONG32` qui indique la taille, en caractères, de la mémoire tampon de `signature`.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="5f2e8-109">dans Signature de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="5f2e8-110">dans Type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="5f2e8-111">dans Première adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="5f2e8-112">dans Deuxième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="5f2e8-113">dans Troisième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f2e8-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5f2e8-114">Return Value</span></span>  
 <span data-ttu-id="5f2e8-115">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5f2e8-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f2e8-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5f2e8-116">Requirements</span></span>  
 <span data-ttu-id="5f2e8-117">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5f2e8-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f2e8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f2e8-118">See also</span></span>

- [<span data-ttu-id="5f2e8-119">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="5f2e8-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="5f2e8-120">DefineLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="5f2e8-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="5f2e8-121">DefineGlobalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="5f2e8-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
