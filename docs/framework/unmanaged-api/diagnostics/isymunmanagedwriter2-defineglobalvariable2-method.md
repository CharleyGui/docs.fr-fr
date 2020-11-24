---
title: ISymUnmanagedWriter2::DefineGlobalVariable2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineGlobalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineGlobalVariable2 method [.NET Framework debugging]
- DefineGlobalVariable2 method [.NET Framework debugging]
ms.assetid: 04d569d6-a151-4957-9872-f3f694c3e4a9
topic_type:
- apiref
ms.openlocfilehash: e417854f5f82ba2e0f16848f53b2b605dccf9eb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683457"
---
# <a name="isymunmanagedwriter2defineglobalvariable2-method"></a><span data-ttu-id="88d51-102">ISymUnmanagedWriter2::DefineGlobalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="88d51-102">ISymUnmanagedWriter2::DefineGlobalVariable2 Method</span></span>

<span data-ttu-id="88d51-103">Définit une variable globale unique.</span><span class="sxs-lookup"><span data-stu-id="88d51-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88d51-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88d51-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="88d51-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="88d51-106">dans Nom de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="88d51-106">[in] The global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="88d51-107">dans Attributs de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="88d51-107">[in] The global variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="88d51-108">dans Jeton de métadonnées de la signature.</span><span class="sxs-lookup"><span data-stu-id="88d51-108">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="88d51-109">dans Type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="88d51-109">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="88d51-110">dans Première adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="88d51-110">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="88d51-111">dans Deuxième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="88d51-111">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="88d51-112">dans Troisième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="88d51-112">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88d51-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="88d51-113">Return Value</span></span>  

 <span data-ttu-id="88d51-114">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="88d51-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88d51-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="88d51-115">Requirements</span></span>  

 <span data-ttu-id="88d51-116">**En-tête :** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="88d51-116">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88d51-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88d51-117">See also</span></span>

- [<span data-ttu-id="88d51-118">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="88d51-118">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="88d51-119">DefineGlobalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="88d51-119">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)
