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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bc14c36563badb73ac9f9d955ea0c00f5330b4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777351"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="38d37-102">ISymUnmanagedWriter::DefineGlobalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="38d37-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="38d37-103">Définit une variable globale unique.</span><span class="sxs-lookup"><span data-stu-id="38d37-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38d37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38d37-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="38d37-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38d37-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="38d37-106">[in] Un pointeur vers un `WCHAR` qui définit le nom de variable global.</span><span class="sxs-lookup"><span data-stu-id="38d37-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="38d37-107">[in] Attributs de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="38d37-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="38d37-108">[in] Un `ULONG32` qui indique la taille, en caractères, de la `signature` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="38d37-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="38d37-109">[in] La signature de variable globale.</span><span class="sxs-lookup"><span data-stu-id="38d37-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="38d37-110">[in] Le type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="38d37-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="38d37-111">[in] La première adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="38d37-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="38d37-112">[in] La deuxième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="38d37-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="38d37-113">[in] Troisième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="38d37-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38d37-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="38d37-114">Return Value</span></span>  
 <span data-ttu-id="38d37-115">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="38d37-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38d37-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="38d37-116">Requirements</span></span>  
 <span data-ttu-id="38d37-117">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="38d37-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d37-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38d37-118">See also</span></span>

- [<span data-ttu-id="38d37-119">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="38d37-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="38d37-120">DefineLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="38d37-120">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="38d37-121">DefineGlobalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="38d37-121">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)
