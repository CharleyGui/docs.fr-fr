---
title: ISymUnmanagedVariable::GetName, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8298e7240052bdd859dbe414281d8e78984342e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778253"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="8dcf9-102">ISymUnmanagedVariable::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="8dcf9-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="8dcf9-103">Obtient le nom de cette variable.</span><span class="sxs-lookup"><span data-stu-id="8dcf9-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dcf9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8dcf9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dcf9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8dcf9-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8dcf9-106">[in] La longueur de la mémoire tampon qui le `pcchName` paramètre pointe vers.</span><span class="sxs-lookup"><span data-stu-id="8dcf9-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8dcf9-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom, y compris le caractère null de fin.</span><span class="sxs-lookup"><span data-stu-id="8dcf9-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="8dcf9-108">[out] La mémoire tampon qui stocke le nom.</span><span class="sxs-lookup"><span data-stu-id="8dcf9-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8dcf9-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8dcf9-109">Return Value</span></span>  
 <span data-ttu-id="8dcf9-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8dcf9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dcf9-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8dcf9-111">Requirements</span></span>  
 <span data-ttu-id="8dcf9-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8dcf9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dcf9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dcf9-113">See also</span></span>

- [<span data-ttu-id="8dcf9-114">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="8dcf9-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
