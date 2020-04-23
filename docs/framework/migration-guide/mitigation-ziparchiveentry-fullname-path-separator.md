---
title: 'Atténuation : Séparateur de chemin ZipArchiveEntry.FullName'
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 3f6c7f258fd5dbf01db4d79b73b88ddd7484f9b2
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102617"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Atténuation : Séparateur de chemin ZipArchiveEntry.FullName

En commençant par les applications qui ciblent le cadre .NET 4.6.1, le séparateur de chemin utilisé dans la <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriété a changé de la barre oblique inverse ("\\") utilisé dans les versions précédentes de .NET Framework à une barre oblique avant ("/"). Les objets <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> sont créés en appelant l’une des surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.  
  
## <a name="impact"></a>Impact  
 L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.  
  
 Décompresser un fichier zip créé par une application qui cible une version précédente de .NET Framework sur les systèmes d’exploitation non Windows tels que MacOS ne parvient pas à préserver la structure d’annuaire. Par exemple, sur MacOS, il crée un ensemble de fichiers dont le nom de\\fichier concatenates le chemin de l’annuaire, tout backslash (" ") caractères, et le nom de fichier. Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.  
  
 L’impact de ce changement sur . Les fichiers ZIP qui sont décompressés sur le <xref:System.IO> système d’exploitation Windows par les API dans l’espace nom cadre .NET devraient\\être minimes, puisque ces API peuvent gérer de manière transparente soit une barre oblique ("/") ou un backslash (" " ) comme caractère de séparateur de chemin.  
  
## <a name="mitigation"></a>Limitation des risques  
 Si ce comportement n’est pas souhaitable, vous pouvez vous [ \<](../configure-apps/file-schema/runtime/runtime-element.md) désinscrier en ajoutant un paramètre de configuration à la section de configuration>de votre fichier de configuration d’application. L’exemple suivant montre la section `<runtime>` et l’option d’annulation.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 En outre, les applications qui ciblent les versions précédentes de .NET Framework mais sont en cours d’exécution sur .NET [ \<](../configure-apps/file-schema/runtime/runtime-element.md) Framework 4.6.1 et les versions ultérieures peuvent opter pour ce comportement en ajoutant un paramètre de configuration à la section de temps d’exécution>du fichier de configuration d’application. L’exemple suivant montre la section `<runtime>` et l’option d’activation.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
