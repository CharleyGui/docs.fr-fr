---
title: Fonctions statiques globales de la fusion
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a8f15bc862c0486311960f7567c49424859846e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795317"
---
# <a name="fusion-global-static-functions"></a>Fonctions statiques globales de la fusion
Cette section décrit les fonctions statiques globales non managées utilisées par l’API de fusion.  
  
## <a name="in-this-section"></a>Dans cette section  
 [ClearDownloadCache, fonction](cleardownloadcache-function.md)  
 Efface le Global Assembly Cache d’assemblys téléchargés.  
  
 [CompareAssemblyIdentity, fonction](compareassemblyidentity-function.md)  
 Compare deux identités d’assembly pour déterminer si elles sont équivalentes.  
  
 [CreateApplicationContext, fonction](createapplicationcontext-function.md)  
 Interne uniquement. (Cette fonction prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement à partir de votre code.)  
  
 [CreateAssemblyCache, fonction](createassemblycache-function.md)  
 Obtient un pointeur vers une nouvelle instance [IAssemblyCache](iassemblycache-interface.md) qui représente le global assembly cache.  
  
 [CreateAssemblyEnum, fonction](createassemblyenum-function.md)  
 Obtient un pointeur vers une instance de [IAssemblyEnum](iassemblyenum-interface.md) qui représente une liste d’objets qui existent dans l’assembly spécifié.  
  
 [CreateAssemblyNameObject, fonction](createassemblynameobject-function.md)  
 Obtient un pointeur vers une instance de [IAssemblyName](iassemblyname-interface.md) qui représente l’identité unique de l’assembly avec le nom spécifié.  
  
 [CreateHistoryReader, fonction](createhistoryreader-function.md)  
 Crée un lecteur d’historique pour le fichier spécifié.  
  
 [CreateInstallReferenceEnum, fonction](createinstallreferenceenum-function.md)  
 Obtient un pointeur vers une instance [IInstallReferenceEnum](iinstallreferenceenum-interface.md) qui représente une liste des références d’une application à l’assembly spécifié.  
  
 [GetAppIdAuthority, fonction](getappidauthority-function.md)  
 Obtient un pointeur vers une instance [IAppIdAuthority](iappidauthority-interface.md) qui gère les clés pour les identités et les références de l’application.  
  
 [GetAssemblyIdentityFromFile, fonction](getassemblyidentityfromfile-function.md)  
 Obtient un pointeur vers un `IUnknown` objet avec le spécifié `IID` dans l’assembly dans le chemin d’accès au fichier spécifié.  
  
 [GetCachePath, fonction](getcachepath-function.md)  
 Obtient le chemin d’accès à l’assembly mis en cache, à l’aide des indicateurs spécifiés.  
  
 [GetHistoryFileDirectory, fonction](gethistoryfiledirectory-function.md)  
 Récupère le chemin d’accès du répertoire de l’historique de l’application.  
  
 [GetIdentityAuthority, fonction](getidentityauthority-function.md)  
 Obtient un pointeur vers une instance [IIdentityAuthority](iidentityauthority-interface.md) qui gère les clés pour les objets de code.  
  
 [IsFrameworkAssembly, fonction](isframeworkassembly-function.md)  
 Obtient une valeur qui indique si l’assembly spécifié est managé.  
  
 [NukeDownloadedCache, fonction](nukedownloadedcache-function.md)  
 Supprime le cache de téléchargement common language runtime.  
  
 [PreBindAssemblyEx, fonction](prebindassemblyex-function.md)  
 Obtient le nom complet de la stratégie d’un assembly.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Interfaces de fusion](fusion-interfaces.md)  
  
 [Énumérations de fusion](fusion-enumerations.md)  
  
 [Structures de fusion](fusion-structures.md)  
  
 [Global Assembly Cache](../../app-domains/gac.md)
