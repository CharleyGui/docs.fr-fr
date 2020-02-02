---
title: Outil WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 5e7d39062a8ad016eebf949daa625a5ba7848328
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921231"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Outil WorkFlow Service Registration (WFServicesReg.exe)
Workflow Services Registration (WFServicesReg.exe) est un outil autonome qui peut être utilisé pour ajouter, supprimer ou réparer les éléments de configuration correspondant aux services Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Notes  
 L’outil se trouve à l’emplacement d’installation .NET Framework 3,5, en particulier%windir%\Microsoft.NET\Framework\v3.5 ou sur%windir%\Microsoft.NET\Framework64\v3.5 sur les ordinateurs 64 bits.  
  
 Les tableaux suivants décrivent les options pouvant être utilisées avec l'outil Workflow Services Registration (WFServicesReg.exe).  
  
|Option|Description|  
|------------|-----------------|  
|`/c`|Configure les services de workflow Windows. Utilisé dans les scénarios d'installation et de réparation.|  
|`/r`|Supprime la configuration des services de workflow Windows.|  
|`/v`|Imprimez des informations détaillées (pour la configuration ou la suppression).|  
|`/m`|Active le format d'enregistrement MSI.|  
|`/i`|Réduit la fenêtre lorsque l'application est exécutée.|  
  
## <a name="registration"></a>Inscription  
 L'outil vérifie le fichier Web.config et enregistre les éléments suivants :  
  
- .NET Framework des assemblys de référence 3,5.  
  
- Fournisseur de version pour fichiers .xoml.  
  
- Gestionnaires HTTP pour fichiers .xoml et .rules.  
  
 L'outil vérifie le fichier Machine.config et enregistre les extensions suivantes :  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 L'outil enregistre également les importateurs de métadonnées clients suivants :  
  
- policyImporters  
  
- wsdlImporters  
  
 L'outil enregistre également des mappages de scripts .xoml et .rules ainsi que des gestionnaires dans la métabase IIS.  
  
 Sur les ordinateurs Windows Server 2003 et Windows XP (IIS 5,1 et IIS 6,0), un ensemble de scriptmaps. xoml et. Rules est inscrit.  
  
 Sur les ordinateurs 64 bits, l'outil enregistre les mappages de scripts en mode WOW si le commutateur `Enable32BitAppOnWin64` est activé, ou les mappages de scripts 64 bits natifs si le commutateur `Enable32BitAppOnWin64` est désactivé.  
  
 Sur les ordinateurs Windows Vista et Windows Server 2008 (IIS 7,0 et versions ultérieures), deux ensembles de gestionnaires. xoml et. Rules sont inscrits : un pour le mode intégré et un pour le mode classique.  
  
 Sur les ordinateurs 64 bits, trois jeux de gestionnaires sont enregistrés (indépendamment de l'état du commutateur `Enable32BitAppOnWin64`) : un pour le mode intégré, un pour le mode classique WOW et le dernier pour le mode classique 64 bits natif.  
  
> [!NOTE]
> Contrairement à ServiceModelReg.exe, WFServicesReg.exe n'autorise pas l'ajout, la suppression ou la réparation des mappages de scripts ou des gestionnaires correspondant à un site Web particulier. Pour contourner ce problème, consultez la section « Réparation des mappages de scripts ».  
  
## <a name="usage-scenarios"></a>Scénarios d'utilisation  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Installation des services IIS après l'installation de .NET Framework 3.5  
 Sur un ordinateur Windows Server 2003, .NET Framework 3,5 est installé avant l’installation d’IIS. En raison de l’indisponibilité de la métabase IIS, l’installation de .NET Framework 3,5 s’effectue correctement sans installer les scriptmaps. xoml et. Rules.  
  
 Après avoir installé les services IIS, vous pouvez utiliser l'outil WFServicesReg.exe avec le commutateur `/c` pour installer ces mappages de scripts spécifiques.  
  
### <a name="repairing-the-scriptmaps"></a>Réparation des mappages de scripts  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Mappage de scripts supprimé sous le nœud Sites Web  
 Sur un ordinateur Windows Server 2003, les règles. xoml ou. Rules sont accidentellement supprimées du nœud sites Web. Ce problème peut être résolu en exécutant l'outil WFServicesReg.exe avec le commutateur `/c`.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mappage de scripts supprimé sous un site web particulier  
 Sur un ordinateur Windows Server 2003, les règles. xoml ou. Rules sont accidentellement supprimées d’un site Web particulier (par exemple, le site Web par défaut) plutôt que du nœud sites Web.  
  
 Pour réparer des gestionnaires supprimés pour un site Web particulier, exécutez « WFServicesReg. exe/r » pour supprimer les gestionnaires de tous les sites Web, puis exécutez « WFServicesReg. exe/c » pour créer les gestionnaires appropriés pour tous les sites Web.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Configuration de gestionnaires après activation du mode IIS  
 Quand IIS est en mode de configuration partagée et .NET Framework 3,5 est installé, la métabase IIS est configurée sous un emplacement partagé. Si vous basculez IIS en mode de configuration non partagé, la métabase locale ne contiendra pas les gestionnaires requis. Pour configurer correctement la métabase locale, vous pouvez soit importer la métabase partagée vers la métabase locale, soit exécuter « WFServicesReg. exe/c », ce qui configure la métabase locale.
