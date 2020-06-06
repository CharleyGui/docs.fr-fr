---
title: Spécification de l'emplacement d'un assembly
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646031"
---
# <a name="specifying-an-assemblys-location"></a>Spécification de l'emplacement d'un assembly
Il existe deux façons de spécifier l’emplacement d’un assembly :  
  
- À l’aide de l' [\<codeBase>](./file-schema/runtime/codebase-element.md) élément.  
  
- À l’aide de l' [\<probing>](./file-schema/runtime/probing-element.md) élément.  
  
 Vous pouvez également utiliser l' [outil de Configuration .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) pour spécifier des emplacements d’assembly ou spécifier des emplacements pour le Common Language Runtime pour détecter les assemblys.  
  
## <a name="using-the-codebase-element"></a>Utilisation de l' \<codeBase> élément  
 Vous pouvez utiliser l' **\<codeBase>** élément uniquement dans la configuration de l’ordinateur ou dans les fichiers de stratégie de l’éditeur qui redirigent également la version de l’assembly. Lorsque le runtime détermine la version de l’assembly à utiliser, il applique le paramètre de base du code à partir du fichier qui détermine la version. Si aucune base de code n’est indiquée, le runtime détecte l’assembly de manière normale. Pour plus d’informations, consultez [Comment le runtime localise les assemblys](../deployment/how-the-runtime-locates-assemblies.md).  
  
 L’exemple suivant montre comment spécifier l’emplacement d’un assembly.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 L’attribut **version** est requis pour tous les assemblys avec nom fort, mais doit être omis pour les assemblys qui ne portent pas un nom fort. L' **\<codeBase>** élément requiert l’attribut **href** . Vous ne pouvez pas spécifier de plages de versions dans l' **\<codeBase>** élément.  
  
> [!NOTE]
> Si vous fournissez un indicateur de base de code pour un assembly qui n’a pas un nom fort, l’indicateur doit pointer vers la base de l’application ou vers un sous-répertoire du répertoire de base de l’application.  
  
## <a name="using-the-probing-element"></a>Utilisation de l' \<probing> élément  
 Le runtime localise les assemblys qui n’ont pas de base de code en procédant à une détection. Pour plus d’informations sur la détection, voir [Comment le runtime localise les assemblys](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Vous pouvez utiliser l' [\<probing>](./file-schema/runtime/probing-element.md) élément dans le fichier de configuration de l’application pour spécifier les sous-répertoires que le runtime doit rechercher lors de la localisation d’un assembly. L’exemple suivant montre comment spécifier les répertoires dans lesquels le runtime doit effectuer des recherches.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 L’attribut **privatePath** contient les répertoires dans lesquels le runtime doit rechercher des assemblys. Si l’application se trouve dans C:\Program Files\MyApp, le runtime recherche les assemblys qui ne spécifient pas de base de code dans C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin et C:\Program Files\MyApp\Bin3. Les répertoires spécifiés dans **privatePath** doivent être des sous-répertoires du répertoire de base de l’application.  
  
## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](../../standard/assembly/index.md)
- [Programmation à l’aide d’assemblys](../../standard/assembly/index.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Configuration des applications à l'aide de fichiers de configuration](index.md)
