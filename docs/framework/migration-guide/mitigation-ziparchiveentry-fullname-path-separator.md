---
title: 'Atténuation : séparateur de chemin ZipArchiveEntry.FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b97436ca2f81fea139689c7c2c2348718827b90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778864"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Atténuation : séparateur de chemin ZipArchiveEntry.FullName
À compter des applications qui ciblent .NET Framework 4.6.1, le séparateur de chemin utilisé dans la propriété <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> a été changé. Il ne s’agit plus de la barre oblique inverse (« \\ ») utilisée dans les versions antérieures du .NET Framework, mais de la barre oblique (« / »).   Les objets <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> sont créés en appelant l’une des surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.  
  
## <a name="impact"></a>Impact  
 L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.  
  
 Décompresser un fichier zip créé par une application qui cible une version antérieure de .NET Framework sur les systèmes d’exploitation non Windows tels que les ordinateurs Macintosh ne permet pas de conserver la structure de répertoire. Par exemple, pour les ordinateurs Macintosh, cela crée un ensemble de fichiers dont le nom concatène le chemin d’accès, ainsi que toute barre oblique inverse (« \\ ») et le nom de fichier. Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.  
  
 L’impact de ce changement sur les fichiers .ZIP qui sont décompressés sur le système d’exploitation Windows par les API dans l’espace de noms <xref:System.IO> du .NET Framework doit être minimal, étant donné que ces API peuvent gérer sans problème aussi bien une barre oblique (« / ») qu’une barre oblique inverse (« \\ ») comme séparateur de chemin.  
  
## <a name="mitigation"></a>Atténuation  
 Si ce comportement n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant un paramètre de configuration pour la section [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de votre application. L’exemple suivant montre la section `<runtime>` et l’option d’annulation.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 De plus, les applications qui ciblent des versions antérieures du .NET Framework mais qui s’exécutent sur .NET Framework 4.6.1 ou les versions ultérieures peuvent accepter ce comportement en ajoutant un paramètre de configuration à la section [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application. L’exemple suivant montre la section `<runtime>` et l’option d’activation.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Modifications de reciblage](retargeting-changes-in-the-net-framework-4-6-1.md)
- [Compatibilité des applications dans la version 4.6.1](application-compatibility-in-the-net-framework-4-6-1.md)
