---
title: 'Atténuation : Séparateur de chemin ZipArchiveEntry.FullName'
description: Découvrez comment le séparateur de chemin d’accès de la propriété ZipArchiveEntry. FullName a changé à partir des applications qui ciblent .NET Framework 4.6.1.
ms.date: 03/30/2017
helpviewer_keywords:
- application compatibility
- ',NET Framework application compatibility'
- .NET Framework 4.6.1
- .NET Framework 4.6.1 retargeting changes
- retargeting changes
ms.assetid: 8d575722-4fb6-49a2-8a06-f72d62dc3766
ms.openlocfilehash: 6e2c0908098f8487f7d429274fe7ad797bedfda1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283443"
---
# <a name="mitigation-ziparchiveentryfullname-path-separator"></a>Atténuation : Séparateur de chemin ZipArchiveEntry.FullName

À compter des applications qui ciblent le .NET Framework 4.6.1, le séparateur de chemin d’accès utilisé dans la <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriété a été modifié par rapport à la barre oblique inverse (« \\ ») utilisée dans les versions précédentes de .NET Framework à une barre oblique (« / »). Les objets <xref:System.IO.Compression.ZipArchiveEntry?displayProperty=nameWithType> sont créés en appelant l’une des surcharges de la méthode <xref:System.IO.Compression.ZipFile.CreateFromDirectory%2A?displayProperty=nameWithType>.  
  
## <a name="impact"></a>Impact  

 L’implémentation .NET est ainsi conforme à la section 4.4.17.1 des [Spécifications relatives au format des fichiers ZIP](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) et permet aux archives ZIP d’être décompressées sur des systèmes non Windows.  
  
 La décompression d’un fichier zip créé par une application ciblant une version antérieure de .NET Framework sur des systèmes d’exploitation autres que Windows, comme MacOS, ne permet pas de conserver la structure de répertoires. Par exemple, sur MacOS, il crée un ensemble de fichiers dont le nom de fichier concatène le chemin d’accès au répertoire, les caractères de barre oblique inverse (« \\ ») et le nom de fichier. Par conséquent, la structure de répertoires des fichiers décompressés n’est pas conservée.  
  
 Impact de cette modification sur. Les fichiers ZIP qui sont décompressés sur le système d’exploitation Windows par les API dans .NET Framework <xref:System.IO> espace de noms doivent être minimaux, puisque ces API peuvent gérer en toute transparence une barre oblique (« / ») ou une barre oblique inverse (« \\ ») comme séparateur de chemin.  
  
## <a name="mitigation"></a>Limitation des risques  

 Si ce comportement n’est pas souhaitable, vous pouvez refuser en ajoutant un paramètre de configuration à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier de configuration de l’application. L’exemple suivant montre la section `<runtime>` et l’option d’annulation.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=true" />  
</runtime>  
```  
  
 En outre, les applications qui ciblent des versions antérieures de .NET Framework mais s’exécutent sur .NET Framework 4.6.1 et les versions ultérieures peuvent accepter ce comportement en ajoutant un paramètre de configuration à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application. L’exemple suivant montre la section `<runtime>` et l’option d’activation.  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IO.Compression.ZipFile.UseBackslash=false" />  
</runtime>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
