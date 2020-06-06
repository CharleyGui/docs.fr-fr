---
title: 'Procédure : Localiser des assemblys à l’aide de DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69913000"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a>Procédure : Localiser des assemblys à l’aide de DEVPATH
Les développeurs peuvent souhaiter s’assurer qu’un assembly partagé qu’ils génèrent fonctionne correctement avec plusieurs applications. Au lieu de placer continuellement l’assembly dans le Global Assembly Cache pendant le cycle de développement, le développeur peut créer une variable d’environnement DEVPATH qui pointe vers le répertoire de sortie de génération de l’assembly.  
  
 Par exemple, supposons que vous génériez un assembly partagé appelé MySharedAssembly et que le répertoire de sortie soit C:\MySharedAssembly\Debug. Vous pouvez placer C:\MySharedAssembly\Debug dans la variable DEVPATH. Vous devez ensuite spécifier l' [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) élément dans le fichier de configuration de l’ordinateur. Cet élément indique à l’common language runtime d’utiliser DEVPATH pour localiser les assemblys.  
  
 L’assembly partagé doit être détectable par le Runtime.  Pour spécifier un répertoire privé pour la résolution des références d’assembly, utilisez l' [ \<codeBase> élément](./file-schema/runtime/codebase-element.md) ou l' [ \<probing> élément](./file-schema/runtime/probing-element.md) dans un fichier de configuration, comme décrit dans spécification de l' [emplacement d’un assembly](specify-assembly-location.md).  Vous pouvez également placer l’assembly dans un sous-répertoire du répertoire de l’application. Pour plus d’informations, consultez [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md).  
  
> [!NOTE]
> Il s’agit d’une fonctionnalité avancée, conçue uniquement pour le développement.  
  
 L’exemple suivant montre comment faire en sorte que le runtime recherche les assemblys dans les répertoires spécifiés par la variable d’environnement DEVPATH.  
  
## <a name="example"></a>Exemple  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 La valeur par défaut de ce paramètre est false.  
  
> [!NOTE]
> Utilisez ce paramètre uniquement au moment du développement. Le runtime ne vérifie pas les versions des assemblys avec nom fort qui se trouvent dans DEVPATH. Il utilise simplement le premier assembly qu’il trouve.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des applications à l'aide de fichiers de configuration](index.md)
