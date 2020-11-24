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
ms.openlocfilehash: cdbb09d25f51e479a8a8ddfc23348305ba7c0a71
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683418"
---
# <a name="isymunmanagedwriter2definelocalvariable2-method"></a><span data-ttu-id="ff398-102">ISymUnmanagedWriter2::DefineLocalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="ff398-102">ISymUnmanagedWriter2::DefineLocalVariable2 Method</span></span>

<span data-ttu-id="ff398-103">Définit une variable unique dans la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="ff398-103">Defines a single variable in the current lexical scope.</span></span> <span data-ttu-id="ff398-104">Cette méthode peut être appelée plusieurs fois pour une variable du même nom qui a plusieurs maisons dans une étendue.</span><span class="sxs-lookup"><span data-stu-id="ff398-104">This method can be called multiple times for a variable of the same name that has multiple homes throughout a scope.</span></span> <span data-ttu-id="ff398-105">Dans ce cas, toutefois, les valeurs des `startOffset` paramètres et `endOffset` ne doivent pas se chevaucher.</span><span class="sxs-lookup"><span data-stu-id="ff398-105">In this case, however, the values of the `startOffset` and `endOffset` parameters must not overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff398-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff398-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ff398-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ff398-107">Parameters</span></span>  

 `name`  
 <span data-ttu-id="ff398-108">dans Nom de la variable locale.</span><span class="sxs-lookup"><span data-stu-id="ff398-108">[in] The local variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="ff398-109">dans Attributs de la variable locale.</span><span class="sxs-lookup"><span data-stu-id="ff398-109">[in] The local variable attributes.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="ff398-110">dans Jeton de métadonnées de la signature.</span><span class="sxs-lookup"><span data-stu-id="ff398-110">[in] The metadata token of the signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="ff398-111">dans Type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="ff398-111">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="ff398-112">dans Première adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="ff398-112">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="ff398-113">dans Deuxième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="ff398-113">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="ff398-114">dans Troisième adresse de la spécification de paramètre.</span><span class="sxs-lookup"><span data-stu-id="ff398-114">[in] The third address for the parameter specification.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="ff398-115">dans Décalage de début de la variable.</span><span class="sxs-lookup"><span data-stu-id="ff398-115">[in] The start offset for the variable.</span></span> <span data-ttu-id="ff398-116">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff398-116">This parameter is optional.</span></span> <span data-ttu-id="ff398-117">Si la valeur est égale à 0, ce paramètre est ignoré et la variable est définie dans l’ensemble de la portée.</span><span class="sxs-lookup"><span data-stu-id="ff398-117">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="ff398-118">S’il s’agit d’une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ff398-118">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="ff398-119">dans Offset de fin de la variable.</span><span class="sxs-lookup"><span data-stu-id="ff398-119">[in] The end offset for the variable.</span></span> <span data-ttu-id="ff398-120">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="ff398-120">This parameter is optional.</span></span> <span data-ttu-id="ff398-121">Si la valeur est égale à 0, ce paramètre est ignoré et la variable est définie dans l’ensemble de la portée.</span><span class="sxs-lookup"><span data-stu-id="ff398-121">If it is 0, this parameter is ignored and the variable is defined throughout the entire scope.</span></span> <span data-ttu-id="ff398-122">S’il s’agit d’une valeur différente de zéro, la variable est comprise entre les offsets de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ff398-122">If it is a nonzero value, the variable falls within the offsets of the current scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff398-123">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ff398-123">Return Value</span></span>  

 <span data-ttu-id="ff398-124">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ff398-124">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff398-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ff398-125">Requirements</span></span>  

 <span data-ttu-id="ff398-126">**En-tête :** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="ff398-126">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff398-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff398-127">See also</span></span>

- [<span data-ttu-id="ff398-128">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="ff398-128">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="ff398-129">DefineLocalVariable, méthode</span><span class="sxs-lookup"><span data-stu-id="ff398-129">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
