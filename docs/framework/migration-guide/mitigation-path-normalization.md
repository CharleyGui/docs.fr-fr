---
title: 'Atténuation : Normalisation des chemins d’accès'
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 61c8eec2043aa2fb9309ee6052e27fc2c91c6c6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181237"
---
# <a name="mitigation-path-normalization"></a>Atténuation : Normalisation des chemins d’accès
À compter des applications qui ciblent .NET Framework 4.6.2, la normalisation des chemins d’accès dans le .NET Framework a été modifiée.  
  
## <a name="what-is-path-normalization"></a>Qu’est-ce que la normalisation des chemins d’accès ?  
 La normalisation d’un chemin d’accès implique la modification de la chaîne qui identifie un fichier ou un chemin d’accès afin qu’il soit conforme à un chemin d’accès valide sur le système d’exploitation cible. La normalisation implique généralement :  
  
- La mise en forme canonique des composants et séparateurs de répertoires.  
  
- L’application du répertoire actuel à un chemin d’accès relatif.  
  
- L’évaluation du répertoire relatif (`.`) ou du répertoire parent (`..`) dans un chemin d’accès.  
  
- La suppression des caractères spécifiés.  
  
## <a name="the-changes"></a>Les changements  
 À compter des applications qui ciblent .NET Framework 4.6.2, la normalisation des chemins a été modifiée des façons suivantes :  
  
- Le runtime défère à la fonction [GetFullPathName](/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) du système d’exploitation pour normaliser les chemins d’accès.  
  
- La normalisation n’implique plus la suppression de la fin des segments de répertoire (comme un espace à la fin d’un nom de répertoire).  
  
- Prise en charge pour la syntaxe de chemin d’accès de périphérique avec une confiance totale, y compris `\\.\` et, pour les API d’E/S de fichiers, dans mscorlib.dll, `\\?\`.  
  
- Le runtime ne valide pas les chemins d’accès de syntaxe de périphérique.  
  
- L’utilisation de la syntaxe de périphérique pour accéder aux autres flux de données est prise en charge.  
  
## <a name="impact"></a>Impact  

Pour les applications qui ciblent .NET Framework 4.6.2 ou ultérieur, ces modifications sont activées par défaut. Elles améliorent les performances tout en activant des méthodes d’accès à des chemins précédemment inaccessibles.  
  
Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures, mais s’exécutent sur .NET Framework 4.6.2 ou une version ultérieure ne sont pas concernées par ce changement.  
  
## <a name="mitigation"></a>Limitation des risques  
 Les applications qui ciblent le cadre .NET 4.6.2 ou plus tard peuvent se [ \<](../configure-apps/file-schema/runtime/runtime-element.md) retirer de cette modification et utiliser la normalisation héritée en ajoutant ce qui suit à la section>de temps d’exécution du fichier de configuration d’application :  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
Les applications qui ciblent le cadre .NET 4.6.1 ou plus tôt mais sont en cours d’exécution sur le cadre .NET 4.6.2 ou plus tard peuvent permettre les changements à la normalisation de la trajectoire en ajoutant la ligne suivante à [ \<l’heure d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier .configuration d’application :  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
