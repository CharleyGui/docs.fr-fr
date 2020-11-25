---
title: ISymUnmanagedAsyncMethodPropertiesWriter, interface
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
ms.openlocfilehash: 779b737da43f61d1023a0a640dce936e11c4704c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707033"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter, interface

Vous permet de définir des informations de méthode Async facultatives pour chaque symbole de méthode. Utilisez toujours avec une méthode ouverte ; autrement dit, entre les appels à la [méthode OpenMethod,](isymunmanagedwriter-openmethod-method.md) et à la [méthode CloseMethod,](isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Syntax  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Méthodes  

 Cette interface contient les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineAsyncStepInfo, méthode](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Définissez un groupe d’opérations await Async dans la méthode actuelle.<br /><br /> Chaque décalage de rendement correspond à l’instruction de retour d’une instruction await, identifiant un rendement potentiel. Chaque `breakpointMethod` / `breakpointOffset` paire identifie l’emplacement où l’opération asynchrone reprendra ; elle peut être dans une autre méthode.|  
|[DefineCatchHandlerILOffset, méthode](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Définit l’offset IL pour le gestionnaire catch généré par le compilateur qui encapsule une méthode Async.<br /><br /> Le décalage IL de l’interception générée est utilisé par le débogueur pour gérer le catch comme s’il s’agissait de code non-utilisateur, même s’il peut se produire dans une méthode de code utilisateur. En particulier, elle est utilisée en réponse à un événement d’exception **CatchHandlerFound** .|  
|[DefineKickoffMethod, méthode](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Définit la méthode de démarrage qui lance l’opération asynchrone.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
