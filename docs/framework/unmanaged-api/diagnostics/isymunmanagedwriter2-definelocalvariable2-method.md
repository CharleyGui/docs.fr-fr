---
title: ISymUnmanagedWriter2::DefineLocalVariable2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineLocalVariable2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2
helpviewer_keywords:
- ISymUnmanagedWriter2::DefineLocalVariable2 method [.NET Framework debugging]
- DefineLocalVariable2 method [.NET Framework debugging]
ms.assetid: e774eefe-858c-4362-8d2d-28ebf2ba1a24
topic_type:
- apiref
ms.openlocfilehash: 73f536b4ab98aa596c2395810cb8b616ffd309e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438291"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="41f73-102">ISymUnmanagedWriter2::DefineLocalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="41f73-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>
<span data-ttu-id="41f73-103">Définit une variable unique dans la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="41f73-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="41f73-104">Cette méthode peut être appelée plusieurs fois pour une variable du même nom qui a plusieurs maisons dans une étendue.</span><span class="sxs-lookup"><span data-stu-id="41f73-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="41f73-105">Dans ce cas, toutefois, les valeurs des paramètres `startOffset` et `endOffset` ne doivent pas se chevaucher.</span><span class="sxs-lookup"><span data-stu-id="41f73-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f73-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41f73-106">Syntax</span></span>  
  
```cpp  
HRESULT DefineLocalVariable2(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] mdSignature  sigToken,  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41f73-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="41f73-107">Parameters</span></span>  
 `name`  
 <span data-ttu-id="41f73-108">dans Nom de la variable locale.</span><span class="sxs-lookup"><span data-stu-id="41f73-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="41f73-109">dans Attributs de la variable locale.</span><span class="sxs-lookup"><span data-stu-id="41f73-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="41f73-110">dans Jeton de métadonnées de la signature.</span><span class="sxs-lookup"><span data-stu-id="41f73-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="41f73-111">dans Type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="41f73-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="41f73-112">dans Première adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="41f73-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="41f73-113">dans Deuxième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="41f73-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="41f73-114">dans Troisième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="41f73-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="41f73-115">dans Décalage de début de la variable.</span><span class="sxs-lookup"><span data-stu-id="41f73-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="41f73-116">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="41f73-116">This parameter is optional.</span></span> <span data-ttu-id="41f73-117">Si la valeur est égale à 0, ce paramètre est ignoré et la variable est définie dans l’ensemble de la portée.</span><span class="sxs-lookup"><span data-stu-id="41f73-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="41f73-118">S’il s’agit d’une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="41f73-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="41f73-119">dans Offset de fin de la variable.</span><span class="sxs-lookup"><span data-stu-id="41f73-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="41f73-120">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="41f73-120">This parameter is optional.</span></span> <span data-ttu-id="41f73-121">Si la valeur est égale à 0, ce paramètre est ignoré et la variable est définie dans l’ensemble de la portée.</span><span class="sxs-lookup"><span data-stu-id="41f73-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="41f73-122">S’il s’agit d’une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="41f73-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41f73-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="41f73-123">Return Value</span></span>  
 <span data-ttu-id="41f73-124">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="41f73-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41f73-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="41f73-125">Requirements</span></span>  
 <span data-ttu-id="41f73-126">**En-tête :** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="41f73-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f73-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41f73-127">See also</span></span>

- [<span data-ttu-id="41f73-128">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="41f73-128">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="41f73-129">DefineLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="41f73-129">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
