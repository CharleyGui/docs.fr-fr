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
ms.openlocfilehash: 6404252f2c1eb14f0cd723451beb82b4c65960fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683483"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="4288e-102">ISymUnmanagedWriter::UsingNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="4288e-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>

<span data-ttu-id="4288e-103">Spécifie que le nom d’espace de noms complet donné est utilisé dans la portée lexicale actuellement ouverte.</span><span class="sxs-lookup"><span data-stu-id="4288e-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="4288e-104">L’espace de noms sera utilisé dans toutes les portées qui héritent de l’étendue actuellement ouverte.</span><span class="sxs-lookup"><span data-stu-id="4288e-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="4288e-105">La fermeture de l’étendue actuelle arrêtera également l’utilisation de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4288e-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4288e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4288e-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4288e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4288e-107">Parameters</span></span>  

 `fullName`  
 <span data-ttu-id="4288e-108">dans Pointeur vers le nom qualifié complet de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4288e-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4288e-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="4288e-109">Return Value</span></span>  

 <span data-ttu-id="4288e-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4288e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4288e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4288e-111">Requirements</span></span>  

 <span data-ttu-id="4288e-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4288e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4288e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4288e-113">See also</span></span>

- [<span data-ttu-id="4288e-114">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="4288e-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
