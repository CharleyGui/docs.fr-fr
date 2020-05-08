---
title: ICorDebugDataTarget2, interface
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 1c598d23cac77e50cf302e6936b88b5eb6e558c2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976432"
---
# <a name="icordebugdatatarget2-interface"></a>ICorDebugDataTarget2, interface
Étend logiquement l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[CreateVirtualUnwinder, méthode](icordebugdatatarget2-createvirtualunwinder-method.md)|Crée un dérouleur de pile qui commence le déroulement à partir d'un contexte initial (qui n'est pas forcément la feuille d'un thread).|  
|[EnumerateThreadIDs, méthode](icordebugdatatarget2-enumeratethreadids-method.md)|Retourne une liste des ID de threads actifs.|  
|[GetImageFromPointer, méthode](icordebugdatatarget2-getimagefrompointer-method.md)|Retourne l'adresse de base et la taille d'un module à partir d'une adresse présente dans ce module.|  
|[GetImageLocation, méthode](icordebugdatatarget2-getimagelocation-method.md)|Retourne le chemin d’accès d’un module à partir de l’adresse de base du module.|  
|[GetSymbolProviderForImage, méthode](icordebugdatatarget2-getsymbolproviderforimage-method.md)|Retourne le fournisseur de symboles d'un module à partir de l'adresse de base de ce module.|  
  
## <a name="remarks"></a>Notes   
  
> [!NOTE]
> Cette interface est uniquement disponible avec .NET Native. Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
