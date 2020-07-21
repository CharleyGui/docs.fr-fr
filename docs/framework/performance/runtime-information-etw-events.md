---
title: Événements ETW d'information du runtime
description: Consultez événements ETW relatifs aux informations d’exécution, qui enregistrent la référence (SKU), le numéro de version, la façon dont le runtime a été activé (y compris les paramètres de ligne de commande), le GUID et bien plus encore.
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
ms.openlocfilehash: 385519229bdb76841cdf592d95e96d2288ec5e1a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474226"
---
# <a name="runtime-information-etw-events"></a>Événements ETW d'information du runtime
Ces événements ETW journalise des informations sur l’exécution, notamment la référence SKU, le numéro de version, le mode d’activation du runtime, les paramètres de ligne de commande avec lesquels il a été démarré, le GUID (le cas échéant) et d’autres informations pertinentes. Si plusieurs runtimes sont exécutés dans un processus, les informations fournies par ces événements (le ClrInstanceID) permettent de lever l’ambiguïté sur les runtimes.  
  
 Le tableau ci-dessous montre les deux événements d’informations liés au runtime. Les événements peuvent être déclenchés sous n’importe quel mot clé ou masque. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Événement|ID de l’événement|Fournisseur|Description|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Déclenché lorsqu’un runtime est chargé.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Énumère les runtimes chargés.|  
  
 Le tableau suivant affiche des données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
|Sku|win:UInt16|1 – Desktop CLR.<br /><br /> 2 – CoreCLR.|  
|BclVersion – Version principale|win:UInt16|Version principale de mscorlib.dll.|  
|BclVersion – Version secondaire|win:UInt16|Numéro de la version secondaire de mscorlib.dll.|  
|BclVersion – Numéro de build|win:UInt16|Numéro de build de mscorlib.dll.|  
|BclVersion – Correctif QFE|win:UInt16|Numéro de version du correctif logiciel de mscorlib.dll.|  
|VMVersion – Version principale|win:UInt16|Version de clr.dll ou de coreclr.dll, selon la référence SKU.|  
|VMVersion – Version secondaire|win:UInt16|Version secondaire de clr.dll ou de coreclr.dll, selon la référence SKU.|  
|VMVersion – Numéro de build|win:UInt16|Numéro de build de clr.dll ou de coreclr.dll.|  
|VMVersion – Correctif QFE|win:UInt16|Numéro du correctif logiciel de clr.dll ou de coreclr.dll.|  
|StartupFlags|win:UInt32|Indicateurs de démarrage définis dans mscoree.h.|  
|StartupMode|win:UInt8|0x01 - Fichier exécutable managé.<br /><br /> 0x02 - CLR hébergé.<br /><br /> 0x04 - Code Interop managé C++.<br /><br /> 0x08 - Activé pour COM.<br /><br /> 0x10 - Autre.|  
|CommandLine|win:UnicodeString|Non null seulement si StartupMode=0x01.|  
|ComObjectGUID|win:GUID|Non null seulement si StartupMode=0x08.|  
|RuntimeDLLPath|win:UnicodeString|Chemin du fichier .dll du CLR qui a été chargé dans le processus.|  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
