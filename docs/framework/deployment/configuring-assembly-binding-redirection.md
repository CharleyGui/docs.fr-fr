---
title: Configuration de la liaison d’assembly
description: Consultez Comment configurer la redirection de liaison d’assembly dans .NET à l’aide de l’attribut appliesTo dans l’élément assemblyBinding d’un fichier de configuration d’application.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
ms.openlocfilehash: 8f3e2270d92e11ea467d6cefc2b19b4faff563b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621728"
---
# <a name="configuring-assembly-binding-redirection"></a>Configuration de la liaison d’assembly
Par défaut, les applications utilisent le jeu d'assemblys .NET Framework qui est fourni avec la version du runtime utilisée pour compiler l'application. Vous pouvez utiliser l’attribut **appliesTo** sur l' [\<assemblyBinding>](../configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) élément dans un fichier de configuration de l’application pour rediriger les références de liaison d’assembly vers une version spécifique des assemblys .NET Framework. Cet attribut facultatif utilise un numéro de version .NET Framework pour indiquer la version à laquelle il s'applique. Si aucun attribut **appliesTo** n’est spécifié, l' **\<assemblyBinding>** élément s’applique à toutes les versions du .NET Framework.  
  
 L’attribut **appliesTo** a été introduit dans le .NET Framework 1.1. Il est ignoré dans le .NET Framework 1.0. Cela signifie que tous les **\<assemblyBinding>** éléments sont appliqués lors de l’utilisation de la version 1,0 de .NET Framework, même si un attribut **appliesTo** est spécifié.  
  
> [!NOTE]
> Utilisez l’attribut **appliesTo** pour limiter la redirection de liaison d’assembly vers une version spécifique du runtime.  
  
 Par exemple, pour rediriger la liaison d’assembly pour un assembly du .NET Framework 1.0, vous devez inclure le code XML suivant dans votre fichier de configuration de l’application.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 Les **\<assemblyBinding>** éléments sont sensibles à l’ordre. Ainsi, vous devez d’abord entrer les informations de redirection des liaisons des assemblys du .NET Framework 1.0, puis celles des assemblys du .NET Framework 1.1. Enfin, vous devez entrer les informations de redirection des liaisons d'assembly pour toutes les redirections d'assembly du .NET Framework qui n'utilisent pas d'attribut **appliesTo** et qui s'appliquent donc à toutes les versions du .NET Framework. En cas de conflit de redirection, la première instruction de redirection correspondante dans le fichier de configuration est utilisée.  
  
 Par exemple, pour rediriger une référence à un assembly du .NET Framework 1.0 et une autre à un assembly du .NET Framework 1.1, utilisez le modèle indiqué dans le pseudo-code suivant.  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">
  <!-- .NET Framework version 1.0 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">
  <!-- .NET Framework version 1.1 redirects here. -->
</assemblyBinding>
  
<assemblyBinding xmlns="...">
  <!-- Redirects meant for all versions of the .NET Framework. -->
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a>Débogage des erreurs de fichier de configuration  
 Le runtime analyse les fichiers de configuration au moment de la création d'un domaine d'application, puis il charge le code dans ce domaine d'application. Le common language runtime gère les erreurs dans un fichier de configuration en ignorant l'entrée. Le runtime ignore tout le fichier de configuration si celui-ci contient du code XML incorrectement formé. En présence de code XML non valide, seules les sections non valides sont ignorées.  
  
 Vous pouvez déterminer si un fichier de configuration est actuellement utilisé en vérifiant si des redirections de liaison d’assembly ont lieu. Utilisez la [Visionneuse du journal de liaison d’assembly (Fuslogvw.exe)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) pour voir quels assemblys sont chargés. Pour voir toutes les liaisons d’assembly, vous devez ajouter une entrée pour **ForceLog** dans le Registre.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : Activer et désactiver la redirection de liaison automatique](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
