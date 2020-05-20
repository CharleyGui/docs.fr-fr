---
title: ISymUnmanagedAsyncMethodPropertiesWriter, interface
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 360d1150b0accd6a070fa36531e570d222787cee
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441758"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a><span data-ttu-id="f3155-102">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="f3155-102">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>
<span data-ttu-id="f3155-103">Vous permet de définir des informations de méthode Async facultatives pour chaque symbole de méthode.</span><span class="sxs-lookup"><span data-stu-id="f3155-103">Allows you to define optional async method information for each method symbol.</span></span> <span data-ttu-id="f3155-104">Utilisez toujours avec une méthode ouverte ; autrement dit, entre les appels à la [méthode OpenMethod,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) et à la [méthode CloseMethod,](isymunmanagedwriter-closemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="f3155-104">Always use with an opened method; that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3155-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3155-105">Syntax</span></span>  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="f3155-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f3155-106">Methods</span></span>  
 <span data-ttu-id="f3155-107">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f3155-107">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="f3155-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="f3155-108">Method</span></span>|<span data-ttu-id="f3155-109">Description</span><span class="sxs-lookup"><span data-stu-id="f3155-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3155-110">DefineAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="f3155-110">DefineAsyncStepInfo Method</span></span>](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|<span data-ttu-id="f3155-111">Définissez un groupe d’opérations await Async dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="f3155-111">Define a group of async await operations in the current method.</span></span><br /><br /> <span data-ttu-id="f3155-112">Chaque décalage de rendement correspond à l’instruction de retour d’une instruction await, identifiant un rendement potentiel.</span><span class="sxs-lookup"><span data-stu-id="f3155-112">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="f3155-113">Chaque `breakpointMethod` / `breakpointOffset` paire identifie l’emplacement où l’opération asynchrone reprendra ; elle peut être dans une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="f3155-113">Each `breakpointMethod`/`breakpointOffset` pair identifies where the asynchronous operation will resume; it may be in a different method.</span></span>|  
|[<span data-ttu-id="f3155-114">DefineCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="f3155-114">DefineCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|<span data-ttu-id="f3155-115">Définit l’offset IL pour le gestionnaire catch généré par le compilateur qui encapsule une méthode Async.</span><span class="sxs-lookup"><span data-stu-id="f3155-115">Sets the IL offset for the compiler-generated catch handler that wraps an async method.</span></span><br /><br /> <span data-ttu-id="f3155-116">Le décalage IL de l’interception générée est utilisé par le débogueur pour gérer le catch comme s’il s’agissait de code non-utilisateur, même s’il peut se produire dans une méthode de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f3155-116">The IL offset of the generated catch is used by the debugger to handle the catch as if it were non-user code, even though it may occur in a user code method.</span></span> <span data-ttu-id="f3155-117">En particulier, elle est utilisée en réponse à un événement d’exception **CatchHandlerFound** .</span><span class="sxs-lookup"><span data-stu-id="f3155-117">In particular, it is used in response to a **CatchHandlerFound** exception event.</span></span>|  
|[<span data-ttu-id="f3155-118">DefineKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="f3155-118">DefineKickoffMethod Method</span></span>](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|<span data-ttu-id="f3155-119">Définit la méthode de démarrage qui lance l’opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="f3155-119">Sets the starting method that initiates the async operation.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3155-120">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="f3155-120">Requirements</span></span>  
 <span data-ttu-id="f3155-121">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f3155-121">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3155-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3155-122">See also</span></span>

- [<span data-ttu-id="f3155-123">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="f3155-123">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
