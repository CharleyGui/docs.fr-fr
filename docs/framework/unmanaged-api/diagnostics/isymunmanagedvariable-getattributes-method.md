---
title: ISymUnmanagedVariable::GetAttributes, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7e71315b5ff99a550ae4a59f3b0d444093dac01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778276"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="ddcfc-102">ISymUnmanagedVariable::GetAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="ddcfc-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="ddcfc-103">Obtient les indicateurs d’attribut pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="ddcfc-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddcfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddcfc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddcfc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ddcfc-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ddcfc-106">[out] Un pointeur vers un `ULONG32` qui reçoit les attributs.</span><span class="sxs-lookup"><span data-stu-id="ddcfc-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="ddcfc-107">La valeur retournée sera une des valeurs définies dans le [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="ddcfc-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddcfc-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ddcfc-108">Return Value</span></span>  
 <span data-ttu-id="ddcfc-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ddcfc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddcfc-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ddcfc-110">Requirements</span></span>  
 <span data-ttu-id="ddcfc-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ddcfc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddcfc-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddcfc-112">See also</span></span>

- [<span data-ttu-id="ddcfc-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="ddcfc-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
