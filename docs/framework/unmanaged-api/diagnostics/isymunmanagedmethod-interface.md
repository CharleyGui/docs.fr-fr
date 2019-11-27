---
title: ISymUnmanagedMethod, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 1d3ccb2265f056d5776199d997dc067c8d5513e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448784"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod, interface
Représente une méthode dans le magasin de symboles. Cette interface fournit l’accès uniquement aux attributs liés aux symboles d’une méthode, plutôt qu’aux attributs liés au type.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetNamespace, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Obtient l’espace de noms dans lequel cette méthode est définie.|  
|[GetOffset, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Retourne l’offset dans cette méthode qui correspond à une position donnée dans un document.|  
|[GetParameters, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Obtient les paramètres de cette méthode.|  
|[GetRanges, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|À partir d’une position dans un document, retourne un tableau de paires d’offsets de début et de fin qui correspondent aux plages de langage MSIL (Microsoft Intermediate Language) couvertes par la position dans cette méthode.|  
|[GetRootScope, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Obtient la portée lexicale racine dans cette méthode. Cette portée englobe la totalité de la méthode.|  
|[GetScopeFromOffset, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Obtient la portée lexicale la plus englobante dans cette méthode qui englobe l’offset donné.|  
|[GetSequencePointCount, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Obtient le nombre de points de séquence dans cette méthode.|  
|[GetSequencePoints, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Obtient tous les points de séquence de cette méthode.|  
|[GetSourceStartEnd, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Obtient les positions de début et de fin du document pour la source de cette méthode.|  
|[GetToken, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Retourne le jeton de métadonnées pour cette méthode.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
