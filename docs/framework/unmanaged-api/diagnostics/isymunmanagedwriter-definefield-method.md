---
title: ISymUnmanagedWriter::DefineField, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 5683c10938873821cbe998dbf13937a6a7d24d7c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675085"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="60f51-102">ISymUnmanagedWriter::DefineField, méthode</span><span class="sxs-lookup"><span data-stu-id="60f51-102">ISymUnmanagedWriter::DefineField Method</span></span>

<span data-ttu-id="60f51-103">Définit une variable unique qui ne se trouve pas dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="60f51-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="60f51-104">Cette méthode est utilisée pour certains champs dans les classes, les champs de bits, etc.</span><span class="sxs-lookup"><span data-stu-id="60f51-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f51-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60f51-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60f51-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60f51-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="60f51-107">dans Le type de métadonnées ou le jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="60f51-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="60f51-108">dans Nom du champ.</span><span class="sxs-lookup"><span data-stu-id="60f51-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="60f51-109">dans Attributs du champ.</span><span class="sxs-lookup"><span data-stu-id="60f51-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="60f51-110">dans `ULONG32` Qui est la taille, en caractères, de la mémoire tampon requise pour contenir la signature de champ.</span><span class="sxs-lookup"><span data-stu-id="60f51-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="60f51-111">dans Tableau de signatures de champs.</span><span class="sxs-lookup"><span data-stu-id="60f51-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="60f51-112">dans Type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="60f51-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="60f51-113">dans Première adresse de la spécification de champ.</span><span class="sxs-lookup"><span data-stu-id="60f51-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="60f51-114">dans Deuxième adresse de la spécification de champ.</span><span class="sxs-lookup"><span data-stu-id="60f51-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="60f51-115">dans Troisième adresse de la spécification de champ.</span><span class="sxs-lookup"><span data-stu-id="60f51-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60f51-116">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="60f51-116">Return Value</span></span>  

 <span data-ttu-id="60f51-117">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="60f51-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f51-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="60f51-118">Requirements</span></span>  

 <span data-ttu-id="60f51-119">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="60f51-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f51-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60f51-120">See also</span></span>

- [<span data-ttu-id="60f51-121">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="60f51-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
