---
title: ISymUnmanagedAsyncMethod, interface
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 02b1866f2b9e89cdc8c8795f399ecc0c733c7202
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707163"
---
# <a name="isymunmanagedasyncmethod-interface"></a>ISymUnmanagedAsyncMethod, interface

Cette interface est le complément de lecture de l' [interface ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
## <a name="syntax"></a>Syntax  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a>Méthodes  

 Cette interface contient les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAsyncStepInfo, méthode](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetAsyncStepInfoCount, méthode](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).|  
|[GetCatchHandlerILOffset, méthode](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|Consultez [méthode definecatchhandleriloffset,](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[GetKickoffMethod, méthode](isymunmanagedasyncmethod-getkickoffmethod-method.md)|Consultez [méthode definekickoffmethod,](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).|  
|[HasCatchHandlerILOffset, méthode](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|Consultez [méthode definecatchhandleriloffset,](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).|  
|[IsAsyncMethod, méthode](isymunmanagedasyncmethod-isasyncmethod-method.md)|Vérifie si la méthode contient des informations asynchrones.<br /><br /> Si cette méthode retourne `FALSE` , il n’est pas valide d’appeler d’autres méthodes dans cette interface. Ils seront tous retournés `E_UNEXPECTED` dans ce cas.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
