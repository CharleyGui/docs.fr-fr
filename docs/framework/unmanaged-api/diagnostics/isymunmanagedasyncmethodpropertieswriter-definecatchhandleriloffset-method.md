---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: b108c8c87d3afdbfacb569ab501274e5c45c2e2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129189"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="31955-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="31955-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="31955-103">Définit l’offset IL pour le gestionnaire catch généré par le compilateur qui encapsule une méthode Async.</span><span class="sxs-lookup"><span data-stu-id="31955-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="31955-104">Le décalage IL de l’interception générée est utilisé par le débogueur pour gérer le catch comme s’il s’agissait de code non-utilisateur, même s’il peut se produire dans une méthode de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="31955-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="31955-105">En particulier, elle est utilisée en réponse à un événement d’exception **CatchHandlerFound** .</span><span class="sxs-lookup"><span data-stu-id="31955-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31955-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31955-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31955-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31955-107">Parameters</span></span>  
  
|<span data-ttu-id="31955-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="31955-108">Parameter</span></span>|<span data-ttu-id="31955-109">Description</span><span class="sxs-lookup"><span data-stu-id="31955-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="31955-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="31955-110">Return Value</span></span>  
 <span data-ttu-id="31955-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="31955-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31955-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="31955-112">Requirements</span></span>  
 <span data-ttu-id="31955-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="31955-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31955-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31955-114">See also</span></span>

- [<span data-ttu-id="31955-115">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="31955-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
