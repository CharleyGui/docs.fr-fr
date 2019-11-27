---
title: ISymUnmanagedReader2::GetSymAttributePreRemap, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 4009f8988c90ed090c0cc3d86164af347055722f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446423"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="7bebd-102">ISymUnmanagedReader2::GetSymAttributePreRemap, méthode</span><span class="sxs-lookup"><span data-stu-id="7bebd-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>
<span data-ttu-id="7bebd-103">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="7bebd-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="7bebd-104">Contrairement aux attributs personnalisés des métadonnées, ces attributs sont conservés dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="7bebd-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bebd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bebd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bebd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7bebd-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="7bebd-107">dans Jeton de métadonnées du parent.</span><span class="sxs-lookup"><span data-stu-id="7bebd-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="7bebd-108">dans Pointeur vers un `WCHAR` qui contient le nom.</span><span class="sxs-lookup"><span data-stu-id="7bebd-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="7bebd-109">dans `ULONG32` qui indique la taille du tableau de `buffer`.</span><span class="sxs-lookup"><span data-stu-id="7bebd-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="7bebd-110">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les octets d’attributs.</span><span class="sxs-lookup"><span data-stu-id="7bebd-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="7bebd-111">à Pointeur vers la mémoire tampon qui reçoit les octets d’attributs.</span><span class="sxs-lookup"><span data-stu-id="7bebd-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bebd-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7bebd-112">Return Value</span></span>  
 <span data-ttu-id="7bebd-113">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7bebd-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bebd-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7bebd-114">Requirements</span></span>  
 <span data-ttu-id="7bebd-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7bebd-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bebd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bebd-116">See also</span></span>

- [<span data-ttu-id="7bebd-117">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="7bebd-117">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
