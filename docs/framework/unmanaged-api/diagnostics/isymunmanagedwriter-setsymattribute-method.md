---
title: ISymUnmanagedWriter::SetSymAttribute, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4450c262b75a73114cb7de7de98567f053bbf564
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894462"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="3f91c-102">ISymUnmanagedWriter::SetSymAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="3f91c-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>
<span data-ttu-id="3f91c-103">Définit un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="3f91c-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="3f91c-104">Ces attributs sont conservés dans le magasin de symboles, contrairement aux attributs personnalisés des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="3f91c-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f91c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f91c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f91c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f91c-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="3f91c-107">dans Jeton de métadonnées pour lequel l’attribut est défini.</span><span class="sxs-lookup"><span data-stu-id="3f91c-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="3f91c-108">dans Pointeur vers un `WCHAR` qui contient le nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="3f91c-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="3f91c-109">dans Qui indique la taille `data` du tableau. `ULONG32`</span><span class="sxs-lookup"><span data-stu-id="3f91c-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="3f91c-110">dans Valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="3f91c-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f91c-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3f91c-111">Return Value</span></span>  
 <span data-ttu-id="3f91c-112">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3f91c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f91c-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3f91c-113">Requirements</span></span>  
 <span data-ttu-id="3f91c-114">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3f91c-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f91c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f91c-115">See also</span></span>

- [<span data-ttu-id="3f91c-116">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="3f91c-116">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
