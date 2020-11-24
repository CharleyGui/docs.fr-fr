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
ms.openlocfilehash: 484affb2ca87ca50a805d1bb46b7749d294d09f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683509"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="8876f-102">ISymUnmanagedWriter::SetSymAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="8876f-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>

<span data-ttu-id="8876f-103">Définit un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="8876f-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="8876f-104">Ces attributs sont conservés dans le magasin de symboles, contrairement aux attributs personnalisés des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8876f-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8876f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8876f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8876f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8876f-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="8876f-107">dans Jeton de métadonnées pour lequel l’attribut est défini.</span><span class="sxs-lookup"><span data-stu-id="8876f-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="8876f-108">dans Pointeur vers un `WCHAR` qui contient le nom de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="8876f-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="8876f-109">dans `ULONG32` Qui indique la taille du `data` tableau.</span><span class="sxs-lookup"><span data-stu-id="8876f-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="8876f-110">dans Valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="8876f-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8876f-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8876f-111">Return Value</span></span>  

 <span data-ttu-id="8876f-112">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8876f-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8876f-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8876f-113">Requirements</span></span>  

 <span data-ttu-id="8876f-114">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8876f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8876f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8876f-115">See also</span></span>

- [<span data-ttu-id="8876f-116">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="8876f-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
