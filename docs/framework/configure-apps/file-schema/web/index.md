---
title: Schéma des paramètres web
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: 71b9e46a8c2d60c853af63ee78e2ed5dbe6e98f4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699136"
---
# <a name="web-settings-schema"></a>Schéma des paramètres web
Les paramètres web spécifient les paramètres d’UC et d’ASP.NET au niveau de l’exécution qui s’appliquent au comportement à l’échelle des processus géré par la couche d’hébergement ASP.NET. Ces paramètres se distinguent des paramètres de type de domaine d’application spécifiés dans le fichier Web.config d’une application ASP.NET.  
  
Les paramètres web sont contenus dans les fichiers Aspnet.config, qui se trouvent dans les dossiers d’installation du .NET Framework, qui varient en fonction des versions. Par exemple, le fichier Aspnet. config pour .NET Framework 2,0 se trouve dans le dossier suivant :  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Les paramètres web ne sont utilisés dans aucun autre des fichiers de configuration, tels que le fichier machine.config, le fichier racine Web.config ou les fichiers Web.config au niveau de l’application.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4System. Web >** ](system-web-element-web-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<applicationPool >** ](applicationpool-element-web-settings.md)  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|Contient les informations utilisées par la couche d’hébergement ASP.NET.|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|Spécifie les paramètres d’UC et d’ASP.NET au niveau de l’exécution qui s’appliquent au comportement à l’échelle des processus géré par la couche d’hébergement ASP.NET.|  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des fichiers de configuration](../index.md)
