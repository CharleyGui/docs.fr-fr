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
ms.openlocfilehash: 674089f8a1076342a2479c64e253b7dda53ade87
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615200"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="be9ba-102">ISymUnmanagedWriter::DefineGlobalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="be9ba-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>
<span data-ttu-id="be9ba-103">Définit une variable globale unique.</span><span class="sxs-lookup"><span data-stu-id="be9ba-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be9ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be9ba-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="be9ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be9ba-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="be9ba-106">dans Pointeur vers un `WCHAR` qui définit le nom de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="be9ba-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="be9ba-107">dans Attributs de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="be9ba-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="be9ba-108">dans `ULONG32`Qui indique la taille, en caractères, de la `signature` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="be9ba-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="be9ba-109">dans Signature de la variable globale.</span><span class="sxs-lookup"><span data-stu-id="be9ba-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="be9ba-110">dans Type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="be9ba-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="be9ba-111">dans Première adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="be9ba-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="be9ba-112">dans Deuxième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="be9ba-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="be9ba-113">dans Troisième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="be9ba-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be9ba-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="be9ba-114">Return Value</span></span>  
 <span data-ttu-id="be9ba-115">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="be9ba-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be9ba-116">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="be9ba-116">Requirements</span></span>  
 <span data-ttu-id="be9ba-117">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="be9ba-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be9ba-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be9ba-118">See also</span></span>

- [<span data-ttu-id="be9ba-119">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="be9ba-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="be9ba-120">DefineLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="be9ba-120">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="be9ba-121">DefineGlobalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="be9ba-121">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
