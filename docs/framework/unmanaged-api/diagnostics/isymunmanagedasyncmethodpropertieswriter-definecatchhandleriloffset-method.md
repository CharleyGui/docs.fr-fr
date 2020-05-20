---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: 58dde2fcce3f4bf578907171e5b575c30c678cfc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441771"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a><span data-ttu-id="0513d-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="0513d-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset Method</span></span>
<span data-ttu-id="0513d-103">Définit l’offset IL pour le gestionnaire catch généré par le compilateur qui encapsule une méthode Async.</span><span class="sxs-lookup"><span data-stu-id="0513d-103">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span>  
  
 <span data-ttu-id="0513d-104">Le décalage IL de l’interception générée est utilisé par le débogueur pour gérer le catch comme s’il s’agissait de code non-utilisateur, même s’il peut se produire dans une méthode de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0513d-104">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code even though it might occur in a user code method.</span></span> <span data-ttu-id="0513d-105">En particulier, elle est utilisée en réponse à un événement d’exception **CatchHandlerFound** .</span><span class="sxs-lookup"><span data-stu-id="0513d-105">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0513d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0513d-106">Syntax</span></span>  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0513d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0513d-107">Parameters</span></span>  
  
|<span data-ttu-id="0513d-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="0513d-108">Parameter</span></span>|<span data-ttu-id="0513d-109">Description</span><span class="sxs-lookup"><span data-stu-id="0513d-109">Description</span></span>|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a><span data-ttu-id="0513d-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0513d-110">Return Value</span></span>  
 <span data-ttu-id="0513d-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="0513d-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0513d-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="0513d-112">Requirements</span></span>  
 <span data-ttu-id="0513d-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0513d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0513d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0513d-114">See also</span></span>

- [<span data-ttu-id="0513d-115">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="0513d-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
