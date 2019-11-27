---
title: ISymUnmanagedVariable, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: ee57ba14f048032e2cd9d0129089743c0f0304bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445976"
---
# <a name="isymunmanagedvariable-interface"></a>ISymUnmanagedVariable, interface
Représente une variable, telle qu’un paramètre, une variable locale ou un champ.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAddressField1, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|Obtient le premier champ d’adresse pour cette variable. Sa signification dépend du type d’adresse.|  
|[GetAddressField2, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|Obtient le deuxième champ d’adresse pour cette variable. Sa signification dépend du type d’adresse.|  
|[GetAddressField3, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|Obtient le troisième champ d’adresse pour cette variable. Sa signification dépend du type d’adresse.|  
|[GetAddressKind, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|Obtient le type d’adresse de cette variable.|  
|[GetAttributes, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|Obtient les indicateurs d’attribut pour cette variable.|  
|[GetEndOffset, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|Obtient le décalage de fin de cette variable dans son parent.|  
|[GetName, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|Obtient le nom de cette variable.|  
|[GetSignature, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|Obtient la signature de cette variable.|  
|[GetStartOffset, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|Obtient le décalage de début de cette variable dans son parent.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
