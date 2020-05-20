---
title: ISymUnmanagedWriter::SetUserEntryPoint, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
ms.openlocfilehash: 8b51a9dc3a968c6bd2f5f9b149f13f88dc6a1e05
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614745"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="8bbc0-102">ISymUnmanagedWriter::SetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="8bbc0-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="8bbc0-103">Spécifie la méthode définie par l’utilisateur qui est le point d’entrée de ce module.</span><span class="sxs-lookup"><span data-stu-id="8bbc0-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="8bbc0-104">Par exemple, ce point d’entrée peut être la méthode main de l’utilisateur au lieu des stubs générés par le compilateur avant main.</span><span class="sxs-lookup"><span data-stu-id="8bbc0-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bbc0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bbc0-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bbc0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8bbc0-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="8bbc0-107">dans Jeton de métadonnées pour la méthode qui est le point d’entrée de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8bbc0-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bbc0-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8bbc0-108">Return Value</span></span>  
 <span data-ttu-id="8bbc0-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8bbc0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bbc0-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="8bbc0-110">Requirements</span></span>  
 <span data-ttu-id="8bbc0-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8bbc0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bbc0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bbc0-112">See also</span></span>

- [<span data-ttu-id="8bbc0-113">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="8bbc0-113">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
