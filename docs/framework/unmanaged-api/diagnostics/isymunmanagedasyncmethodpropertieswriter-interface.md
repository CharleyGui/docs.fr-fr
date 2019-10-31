---
title: ISymUnmanagedAsyncMethodPropertiesWriter, interface
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: db065357e22ac576600a3ca61dda0882b9206a86
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129161"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="e4275-102">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="e4275-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="e4275-103">Vous permet de définir des informations de méthode Async facultatives pour chaque symbole de méthode.</span><span class="sxs-lookup"><span data-stu-id="e4275-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="e4275-104">Utilisez toujours avec une méthode ouverte ; autrement dit, entre les appels à la [méthode OpenMethod,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) et à la [méthode CloseMethod,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4275-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4275-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4275-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="e4275-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e4275-106">Methods</span></span>  
 <span data-ttu-id="e4275-107">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e4275-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="e4275-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="e4275-108">Method</span></span>|<span data-ttu-id="e4275-109">Description</span><span class="sxs-lookup"><span data-stu-id="e4275-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4275-110">DefineAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="e4275-110">DefineAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="e4275-111">Définissez un groupe d’opérations await Async dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="e4275-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="e4275-112">Chaque décalage de rendement correspond à l’instruction de retour d’une instruction await, identifiant un rendement potentiel.</span><span class="sxs-lookup"><span data-stu-id="e4275-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="e4275-113">Chaque `breakpointMethod`/paire d' `breakpointOffset` identifie l’emplacement de reprise de l’opération asynchrone ; Il peut s’agir d’une méthode différente.</span><span class="sxs-lookup"><span data-stu-id="e4275-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="e4275-114">DefineCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="e4275-114">DefineCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="e4275-115">Définit l’offset IL pour le gestionnaire catch généré par le compilateur qui encapsule une méthode Async.</span><span class="sxs-lookup"><span data-stu-id="e4275-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="e4275-116">Le décalage IL de l’interception générée est utilisé par le débogueur pour gérer le catch comme s’il s’agissait de code non-utilisateur, même s’il peut se produire dans une méthode de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e4275-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="e4275-117">En particulier, elle est utilisée en réponse à un événement d’exception **CatchHandlerFound** .</span><span class="sxs-lookup"><span data-stu-id="e4275-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="e4275-118">DefineKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="e4275-118">DefineKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="e4275-119">Définit la méthode de démarrage qui lance l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="e4275-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4275-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="e4275-120">Requirements</span></span>  
 <span data-ttu-id="e4275-121">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e4275-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4275-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4275-122">See also</span></span>

- [<span data-ttu-id="e4275-123">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="e4275-123">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
