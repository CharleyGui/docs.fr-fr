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
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615122"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod, interface
Représente une méthode dans le magasin de symboles. Cette interface fournit l’accès uniquement aux attributs liés aux symboles d’une méthode, plutôt qu’aux attributs liés au type.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetNamespace, méthode](isymunmanagedmethod-getnamespace-method.md)|Obtient l’espace de noms dans lequel cette méthode est définie.|  
|[GetOffset, méthode](isymunmanagedmethod-getoffset-method.md)|Retourne l’offset dans cette méthode qui correspond à une position donnée dans un document.|  
|[GetParameters, méthode](isymunmanagedmethod-getparameters-method.md)|Obtient les paramètres de cette méthode.|  
|[GetRanges, méthode](isymunmanagedmethod-getranges-method.md)|À partir d’une position dans un document, retourne un tableau de paires d’offsets de début et de fin qui correspondent aux plages de langage MSIL (Microsoft Intermediate Language) couvertes par la position dans cette méthode.|  
|[GetRootScope, méthode](isymunmanagedmethod-getrootscope-method.md)|Obtient la portée lexicale racine dans cette méthode. Cette portée englobe la totalité de la méthode.|  
|[GetScopeFromOffset, méthode](isymunmanagedmethod-getscopefromoffset-method.md)|Obtient la portée lexicale la plus englobante dans cette méthode qui englobe l’offset donné.|  
|[GetSequencePointCount, méthode](isymunmanagedmethod-getsequencepointcount-method.md)|Obtient le nombre de points de séquence dans cette méthode.|  
|[GetSequencePoints, méthode](isymunmanagedmethod-getsequencepoints-method.md)|Obtient tous les points de séquence de cette méthode.|  
|[GetSourceStartEnd, méthode](isymunmanagedmethod-getsourcestartend-method.md)|Obtient les positions de début et de fin du document pour la source de cette méthode.|  
|[GetToken, méthode](isymunmanagedmethod-gettoken-method.md)|Retourne le jeton de métadonnées de cette méthode.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
