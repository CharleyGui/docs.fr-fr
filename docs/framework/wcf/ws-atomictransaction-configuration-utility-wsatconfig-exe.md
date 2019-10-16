---
title: Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 5333c9c5caad502ce925fe4a45a039c553812ba6
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320199"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe)
L'utilitaire de configuration WS-AtomicTransaction permet de configurer les paramètres de prise en charge WS-AtomicTransaction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Notes  
 Cet outil de ligne de commande peut être utilisé pour configurer les paramètres WS-AT de base sur un ordinateur local uniquement. Si vous devez configurer des paramètres sur des ordinateurs locaux et distants, vous devez utiliser le composant logiciel enfichable MMC, comme décrit dans Configuration de la [prise en charge des transactions WS-Atomic](./feature-details/configuring-ws-atomic-transaction-support.md).  
  
 L'outil de ligne de commande se trouve généralement dans le répertoire d'installation du Kit de développement logiciel Windows.  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\wsatConfig.exe  
  
 Si vous utilisez [!INCLUDE[wxp](../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], vous devez télécharger une mise à jour avant d'exécuter WsatConfig.exe. Pour plus d’informations sur cette mise à jour, consultez [mise à jour pour Commerce Server 2007 (KB912817)](https://go.microsoft.com/fwlink/?LinkId=95340) et [disponibilité de Windows XP com+ correctif cumulatif package 13](https://go.microsoft.com/fwlink/?LinkId=95341).  
  
 Le tableau suivant affiche les options qui peuvent être utilisées avec l'utilitaire de configuration WS-AtomicTransaction (wsatConfig.exe).  
  
> [!NOTE]
> Lorsque vous définissez un certificat SSL pour un port sélectionné, vous remplacez le certificat SSL d’origine associé à ce port, le cas échéant.  
  
|Options|Description|  
|-------------|-----------------|  
|-Accounts : \<account, >|Spécifie la liste des comptes, séparés par une virgule, qui peuvent participer à WS-AtomicTransaction. La validation de ces comptes n'est pas vérifiée.|  
|-accountsCerts : \<thumb >&#124;« Issuer\SubjectName », >|Spécifie la liste des certificats, séparés par une virgule, qui peuvent participer à WS-AtomicTransaction. Les certificats sont indiqués par empreinte numérique ou par la paire Issuer\SubjectName. Utilisez{EMPTY} pour le nom de sujet, s'il est vide.|  
|-endpointCert : < ordinateur&#124;\<thumb >&#124;« Issuer\SubjectName » >|Utilise le certificat d'ordinateur ou un autre certificat de point de terminaison local spécifié par l'empreinte numérique ou par la paire Issuer\SubjectName. Utilise {EMPTY} pour le nom de sujet, s'il est vide.|  
|-maxTimeout : \<sec >|Spécifie le délai d'attente maximal, exprimé en secondes. Les valeurs valides sont comprises entre 0 et 3600.|  
|-Network : \<enable&#124;Disable >|Active ou désactive la gestion réseau WS-AtomicTransaction.|  
|-Port : \<portNum >|Définit le port HTTPS pour WS-AtomicTransaction.<br /><br /> Si vous avez déjà activé le pare-feu avant d'exécuter cet outil, le port est enregistré automatiquement dans la liste d'exceptions. Si le pare-feu est désactivé avant l'exécution de cet outil, aucun élément supplémentaire n'est configuré concernant le pare-feu.<br /><br /> Si vous activez le pare-feu après avoir configuré WS-AT, vous devez exécuter de nouveau cet outil et fournir le numéro de port à l'aide de ce paramètre. Si vous désactivez le pare-feu après la configuration, WS-AT continue à fonctionner sans entrée supplémentaire.|  
|-Timeout : \<sec >|Spécifie le délai d'attente par défaut, exprimé en secondes. Les valeurs valides sont comprises entre 1et 3 600.|  
|-traceActivity : \<enable&#124;Disable >|Active ou désactive le suivi d'événements d'activité.|  
|-traceLevel : @no__t-erreur&#124;&#124;0Off-&#124;informations&#124;critiques&#124; sur&#124;les avertissements pour tout >}|Spécifie le niveau de suivi.|  
|-tracePII : \<enable&#124;Disable >|Active ou désactive le suivi des informations d'identification personnelle.|  
|-traceProp : \<enable&#124;Disable >|Active ou désactive le suivi d'événements de propagation.|  
|-restart|Redémarre MSDTC pour activer immédiatement les modifications apportées. Si cette option n'est pas spécifiée, les modifications entrent en vigueur lorsque MSDTC est redémarré.|  
|-show|Affiche les paramètres actuels du protocole WS-AtomicTransaction.|  
|\<virtualServer >|Spécifie le nom du cluster de ressource DTC.|  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de WS-AtomicTransaction](./feature-details/using-ws-atomictransaction.md)
- [Configuration de la prise en charge WS-Atomic Transaction](./feature-details/configuring-ws-atomic-transaction-support.md)
