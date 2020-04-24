---
title: Spécification de l'emplacement d'un assembly
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646031"
---
# <a name="specifying-an-assemblys-location"></a>Spécification de l'emplacement d'un assembly
Il y a deux façons de spécifier l’emplacement d’une assemblée :  
  
- Utilisation du [ \<codeBase>](./file-schema/runtime/codebase-element.md) élément.  
  
- Utilisation de [ \<l’élément de sondage>.](./file-schema/runtime/probing-element.md)  
  
 Vous pouvez également utiliser [l’outil de configuration cadre .NET (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) pour spécifier les emplacements d’assemblage ou spécifier les emplacements de l’heure d’exécution de langue commune pour sonder les assemblages.  
  
## <a name="using-the-codebase-element"></a>Utilisation \<du codeBase> Element  
 Vous pouvez utiliser le ** \<codeBase>** élément uniquement dans la configuration de la machine ou les fichiers de stratégie de l’éditeur qui rediriger également la version d’assemblage. Lorsque le temps d’exécution détermine la version d’assemblage à utiliser, il applique le paramètre de base de code du fichier qui détermine la version. Si aucune base de code n’est indiquée, les sondes de temps d’exécution pour l’assemblage de la manière normale. Pour plus de détails, voir [Comment les assemblages De localisation de Runtime](../deployment/how-the-runtime-locates-assemblies.md).  
  
 L’exemple suivant montre comment spécifier l’emplacement d’une assemblée.  
  
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
  
 **L’attribut de version** est exigé pour toutes les assemblées nommées fort, mais doit être omise pour les assemblées qui ne sont pas nommées fort. Le ** \<codeBase>** élément nécessite l’attribut **href.** Vous ne pouvez pas spécifier les plages de version dans l’élément ** \<codeBase>.**  
  
> [!NOTE]
> Si vous fournissez un indice de base de code pour une assemblée qui n’est pas solidement nommée, l’indice doit indiquer la base d’application ou une sous-direction de l’annuaire de base d’application.  
  
## <a name="using-the-probing-element"></a>Utilisation \<de l’élément> de sondage  
 Le temps d’exécution localise les assemblages qui n’ont pas de base de code en sondant. Pour plus d’informations sur l’enquête, voir [Comment les assemblages Runtime Locates](../deployment/how-the-runtime-locates-assemblies.md).  
  
 Vous pouvez [ \<](./file-schema/runtime/probing-element.md) utiliser l’élément de sondage>dans le fichier de configuration d’application pour spécifier les sous-directions que l’heure d’exécution doit rechercher lors de la localisation d’un assemblage. L’exemple suivant montre comment spécifier les répertoires que l’heure d’exécution doit rechercher.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 **L’attribut PrivatePath** contient les répertoires que le temps d’exécution doit rechercher des assemblages. Si l’application est située à C : Fichiers de programme MyApp, l’exécution recherchera des assemblages qui ne spécifient pas une base de code dans C : Fichiers de programme- MyApp’Bin, C : Fichiers de programme -MyApp’Bin2-Subbin, et C : Fichiers de programme-MyApp-Bin3. Les répertoires spécifiés dans **privatePath** doivent être des sous-directeurs de l’annuaire de base d’application.  
  
## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](../../standard/assembly/index.md)
- [Programmation à l’aide d’assemblys](../../standard/assembly/index.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Configuration des applications à l'aide de fichiers de configuration](index.md)
