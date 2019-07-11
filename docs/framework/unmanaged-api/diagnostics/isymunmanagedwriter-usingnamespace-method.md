---
title: ISymUnmanagedWriter::UsingNamespace, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0076b70c85c21f0c4b1fb140b15000f99dbff742
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755138"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="2e3c7-102">ISymUnmanagedWriter::UsingNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="2e3c7-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="2e3c7-103">Spécifie que le nom d’espace de noms complet donné est utilisé dans la portée lexicale actuellement ouverte.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="2e3c7-104">L’espace de noms sera utilisé dans toutes les portées qui héritent de la portée actuellement ouverte.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="2e3c7-105">Fermeture de la portée actuelle s’arrête également l’utilisation de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e3c7-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e3c7-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e3c7-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e3c7-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="2e3c7-108">[in] Pointeur vers le nom qualifié complet de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e3c7-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2e3c7-109">Return Value</span></span>  
 <span data-ttu-id="2e3c7-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2e3c7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e3c7-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e3c7-111">Requirements</span></span>  
 <span data-ttu-id="2e3c7-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2e3c7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3c7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e3c7-113">See also</span></span>

- [<span data-ttu-id="2e3c7-114">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="2e3c7-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
