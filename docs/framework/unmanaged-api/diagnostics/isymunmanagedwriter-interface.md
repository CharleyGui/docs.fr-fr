---
title: ISymUnmanagedWriter, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
ms.openlocfilehash: fc19ee25e903046daef376e4297c8feb3d01ad47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427936"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter, interface
Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Abort, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Ferme le writer de symbole sans valider les symboles dans le magasin de symboles.|  
|[Close, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Ferme le writer de symbole après avoir validé les symboles dans le magasin de symboles.|  
|[CloseMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Ferme la méthode actuelle. Une fois qu’une méthode est fermée, aucun autre symbole ne peut être défini à l’intérieur de celle-ci.|  
|[CloseNamespace, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Ferme l’espace de noms le plus récemment ouvert.|  
|[CloseScope, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Ferme la portée lexicale actuelle.|  
|[DefineConstant, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Définit un nom pour une valeur de constante.|  
|[DefineDocument, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Définit un document source.|  
|[DefineField, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Définit une variable unique qui ne se trouve pas dans une méthode.|  
|[DefineGlobalVariable, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Définit une variable globale unique.|  
|[DefineLocalVariable, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|Définit une variable unique dans la portée lexicale actuelle.|  
|[DefineParameter, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Définit un paramètre unique dans la méthode actuelle.|  
|[DefineSequencePoints, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Définit un groupe de points de séquence dans la méthode actuelle.|  
|[GetDebugInfo, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Retourne les informations nécessaires à un compilateur pour écrire l’entrée de répertoire de débogage dans l’en-tête de fichier exécutable portable (PE).|  
|[Initialize, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Définit l’interface d’émetteur de métadonnées à laquelle ce writer sera associé et définit le nom du fichier de sortie dans lequel les symboles de débogage seront écrits.|  
|[Initialize2, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Définit l’interface d’émetteur de métadonnées à laquelle ce writer sera associé, définit le nom du fichier de sortie dans lequel les symboles de débogage seront écrits et définit l’emplacement final du fichier de base de données du programme (PDB).|  
|[OpenMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Ouvre une méthode dans laquelle les informations de symboles sont émises.|  
|[OpenNamespace, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Ouvre un nouvel espace de noms.|  
|[OpenScope, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Ouvre une nouvelle portée lexicale dans la méthode actuelle.|  
|[RemapToken, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Notifie le writer de symbole qu’un jeton de métadonnées a été remappé à la sortie des métadonnées.|  
|[SetMethodSourceRange, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Spécifie le début et la fin d’une méthode dans un fichier source.|  
|[SetScopeRange, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Définit la plage d'offsets pour la portée lexicale spécifiée.|  
|[SetSymAttribute, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Définit un attribut personnalisé en fonction de son nom.|  
|[SetUserEntryPoint, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Spécifie la méthode définie par l’utilisateur qui est le point d’entrée de ce module.|  
|[UsingNamespace, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Spécifie que le nom d’espace de noms complet donné est utilisé dans la portée lexicale actuellement ouverte.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
