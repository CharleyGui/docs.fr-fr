---
title: Interfaces du magasin de symboles de diagnostics
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 044ed5e08a85442c5a73c123cf51529d2fd3f1fc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442174"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Interfaces du magasin de symboles de diagnostics
Cette rubrique décrit les interfaces non managées qui permettent à un compilateur de générer des informations de symbole pour une utilisation par un débogueur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IBindingDisplay, interface](ibindingdisplay-interface.md)  
 Fournit des méthodes qui affichent les informations de liaison actuelles sur l’application en cours d’exécution.  
  
 [IDebugAutoAttach, interface](idebugautoattach-interface.md)  
 Définit l’interface pour un attachement automatique du débogueur appelé par le serveur.  
  
 [INotifyConnection2, interface](inotifyconnection2-interface.md)  
 Déclare des méthodes pour l’inscription et l’annulation de l’inscription d’une source de notification de connexion.  
  
 [INotifySink2, interface](inotifysink2-interface.md)  
 Déclare des méthodes pour la notification du récepteur.  
  
 [INotifySource2, interface](inotifysource2-interface.md)  
 Déclare une méthode pour définir des filtres de notification.  
  
 [ISymENCUnmanagedMethod, interface](isymencunmanagedmethod-interface.md)  
 Fournit des informations pour la fonctionnalité modifier et continuer.  
  
 [ISymUnmanagedAsyncMethod, interface](isymunmanagedasyncmethod-interface.md)  
 Cette interface est le complément de lecture de l' [interface ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter, interface](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Autorise la définition d’informations de méthode Async facultatives par symbole de méthode. Doit utiliser avec une méthode ouverte (c’est-à-dire entre les appels à la [méthode OpenMethod,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)et la [méthode CloseMethod,](isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder, interface](isymunmanagedbinder-interface.md)  
 Représente un Binder de symboles pour du code non managé.  
  
 [ISymUnmanagedBinder2, interface](isymunmanagedbinder2-interface.md)  
 Représente un Binder de symboles pour du code non managé et étend l' `ISymUnmanagedBinder` interface.  
  
 [ISymUnmanagedBinder3, interface](isymunmanagedbinder3-interface.md)  
 Représente un Binder de symboles pour du code non managé et étend l' `ISymUnmanagedBinder` interface.  
  
 [ISymUnmanagedConstant, interface](isymunmanagedconstant-interface.md)  
 Fournit l’accès aux constantes non managées.  
  
 [ISymUnmanagedDispose, interface](isymunmanageddispose-interface.md)  
 Supprime les ressources non managées.  
  
 [ISymUnmanagedDocument, interface](isymunmanageddocument-interface.md)  
 Représente un document référencé par un magasin de symboles.  
  
 [ISymUnmanagedDocumentWriter, interface](isymunmanageddocumentwriter-interface.md)  
 Fournit des méthodes d'écriture dans un document référencé par un magasin de symboles.  
  
 [ISymUnmanagedENCUpdate, interface](isymunmanagedencupdate-interface.md)  
 Fournit des méthodes pour la fonctionnalité modifier et continuer.  
  
 [ISymUnmanagedMethod, interface](isymunmanagedmethod-interface.md)  
 Représente une méthode dans le magasin de symboles.  
  
 [ISymUnmanagedNamespace, interface](isymunmanagednamespace-interface.md)  
 Représente un espace de noms.  
  
 [ISymUnmanagedReader, interface](isymunmanagedreader-interface.md)  
 Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables dans un magasin de symboles.  
  
 [ISymUnmanagedReader2, interface](isymunmanagedreader2-interface.md)  
 Obtient une méthode de lecteur de symboles en fonction d’un jeton de méthode et d’un numéro de version de modification et de copie.  
  
 [ISymUnmanagedReaderSymbolSearchInfo, interface](isymunmanagedreadersymbolsearchinfo-interface.md)  
 Fournit des méthodes qui obtiennent des informations de recherche de symboles.  
  
 [ISymUnmanagedScope, interface](isymunmanagedscope-interface.md)  
 Représente une portée lexicale dans une méthode.  
  
 [ISymUnmanagedScope2, interface](isymunmanagedscope2-interface.md)  
 Représente une portée lexicale dans une méthode et étend l' `ISymUnmanagedScope` interface avec des méthodes qui obtiennent des informations sur les constantes définies dans la portée.  
  
 [ISymUnmanagedSourceServerModule, interface](isymunmanagedsourceservermodule-interface.md)  
 Fournit les données du serveur source pour un module.  
  
 [ISymUnmanagedSymbolSearchInfo, interface](isymunmanagedsymbolsearchinfo-interface.md)  
 Fournit des méthodes qui obtiennent des informations sur le chemin de recherche.  
  
 [ISymUnmanagedVariable, interface](isymunmanagedvariable-interface.md)  
 Représente une variable, telle qu’un paramètre, une variable locale ou un champ.  
  
 [ISymUnmanagedWriter, interface](isymunmanagedwriter-interface.md)  
 Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.  
  
 [ISymUnmanagedWriter2, interface](isymunmanagedwriter2-interface.md)  
 Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables. Étend l' `ISymUnmanagedWriter` interface.  
  
 [ISymUnmanagedWriter3, interface](isymunmanagedwriter3-interface.md)  
 Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables. Étend l' `ISymUnmanagedWriter` interface.  
  
 [ISymUnmanagedWriter4, interface](isymunmanagedwriter4-interface.md)  
 Interface Isymunmanagedwriter4,.  
  
 [ISymUnmanagedWriter5, interface](isymunmanagedwriter5-interface.md)  
 Interface ISymUnmanagedWriter5.  
  
## <a name="related-sections"></a>Sections connexes  
 [Énumérations du magasin de symboles de diagnostics](diagnostics-symbol-store-enumerations.md)  
  
 [Structures du magasin de symboles de diagnostics](diagnostics-symbol-store-structures.md)  
  
 [Débogage](../debugging/index.md)
