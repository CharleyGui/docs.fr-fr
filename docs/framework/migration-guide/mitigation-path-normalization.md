---
title: 'Atténuation : normalisation des chemins d’accès'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51291fbc9ad2927bc3b9649074a6dbf374aaf7f1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648441"
---
# <a name="mitigation-path-normalization"></a>Atténuation : normalisation des chemins d’accès
À compter des applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la normalisation des chemins d’accès dans .NET Framework a été modifiée.  
  
## <a name="what-is-path-normalization"></a>Qu’est-ce que la normalisation des chemins d’accès ?  
 La normalisation d’un chemin d’accès implique la modification de la chaîne qui identifie un fichier ou un chemin d’accès afin qu’il soit conforme à un chemin d’accès valide sur le système d’exploitation cible. La normalisation implique généralement :  
  
- La mise en forme canonique des composants et séparateurs de répertoires.  
  
- L’application du répertoire actuel à un chemin d’accès relatif.  
  
- L’évaluation du répertoire relatif (`.`) ou du répertoire parent (`..`) dans un chemin d’accès.  
  
- La suppression des caractères spécifiés.  
  
## <a name="the-changes"></a>Les changements  
 À compter des applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la normalisation des chemins d’accès a changé des façons suivantes :  
  
- Le runtime défère à la fonction [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) du système d’exploitation pour normaliser les chemins d’accès.  
  
- La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).  
  
- Prise en charge pour la syntaxe de chemin d’accès de périphérique avec une confiance totale, y compris `\\.\` et, pour les API d’E/S de fichiers, dans mscorlib.dll, `\\?\`.  
  
- Le runtime ne valide pas les chemins d’accès de syntaxe de périphérique.  
  
- L’utilisation de la syntaxe de périphérique pour accéder aux autres flux de données est prise en charge.  
  
## <a name="impact"></a>Impact  
 Pour les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou versions ultérieures, ces modifications sont activées par défaut. Elles améliorent les performances tout en activant des méthodes d’accès à des chemins précédemment inaccessibles.  
  
 Les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et versions antérieures, mais sont en cours d’exécution sous [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou ultérieure ne sont pas affectées par cette modification.  
  
## <a name="mitigation"></a>Atténuation  
 Les applications qui ciblent [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou versions ultérieures peuvent annuler cette modification et utiliser la normalisation héritée en ajoutant le code suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration d’application :  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
</runtime>  
```  
  
 Les applications qui ciblent [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ou versions antérieures mais sont en cours d’exécution sous [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ou versions ultérieures peuvent activer les modifications apportées à la normalisation des chemins d’accès en ajoutant la ligne suivante à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier .configuration de l’application :  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />    
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
