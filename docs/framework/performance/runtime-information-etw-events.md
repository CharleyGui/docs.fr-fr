---
title: Événements ETW d'information du runtime
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ab3844b293d09cec02236fb9befd836aa4113ea
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046228"
---
# <a name="runtime-information-etw-events"></a>Événements ETW d'information du runtime
Ces événements ETW journalise des informations sur l’exécution, notamment la référence SKU, le numéro de version, le mode d’activation du runtime, les paramètres de ligne de commande avec lesquels il a été démarré, le GUID (le cas échéant) et d’autres informations pertinentes. Si plusieurs runtimes sont exécutés dans un processus, les informations fournies par ces événements (le ClrInstanceID) permettent de lever l’ambiguïté sur les runtimes.  
  
 Le tableau ci-dessous montre les deux événements d’informations liés au runtime. Les événements peuvent être déclenchés sous n’importe quel mot clé ou masque. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Événement|ID d'événement|Fournisseur|Description|  
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
