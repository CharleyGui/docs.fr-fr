---
title: 'Atténuation : Normalisation des chemins d’accès'
description: Découvrez comment la normalisation des chemins d’accès dans .NET Framework a changé à partir des applications qui ciblent .NET Framework 4.6.2.
ms.date: 03/30/2017
ms.assetid: 158d47b1-ba6d-4fa6-8963-a012666bdc31
ms.openlocfilehash: 6f7e07690ab06fc7ef03344556c045405a63c374
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253594"
---
# <a name="mitigation-path-normalization"></a>Atténuation : Normalisation des chemins d’accès

À compter des applications qui ciblent .NET Framework 4.6.2, la normalisation des chemins d’accès dans le .NET Framework a changé.  
  
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

 Les applications qui ciblent le .NET Framework 4.6.2 ou version ultérieure peuvent refuser ce changement et utiliser la normalisation héritée en ajoutant le code suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>  
```  
  
Les applications qui ciblent le .NET Framework 4.6.1 ou version antérieure, mais qui s’exécutent sur le .NET Framework 4.6.2 ou version ultérieure, peuvent activer les modifications de la normalisation des chemins d’accès en ajoutant la ligne suivante à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier application. Configuration :  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
