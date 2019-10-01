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
# <a name="web-settings-schema"></a><span data-ttu-id="fc9f0-102">Schéma des paramètres web</span><span class="sxs-lookup"><span data-stu-id="fc9f0-102">Web Settings Schema</span></span>
<span data-ttu-id="fc9f0-103">Les paramètres web spécifient les paramètres d’UC et d’ASP.NET au niveau de l’exécution qui s’appliquent au comportement à l’échelle des processus géré par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc9f0-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="fc9f0-104">Ces paramètres se distinguent des paramètres de type de domaine d’application spécifiés dans le fichier Web.config d’une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc9f0-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="fc9f0-105">Les paramètres web sont contenus dans les fichiers Aspnet.config, qui se trouvent dans les dossiers d’installation du .NET Framework, qui varient en fonction des versions.</span><span class="sxs-lookup"><span data-stu-id="fc9f0-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="fc9f0-106">Par exemple, le fichier Aspnet. config pour .NET Framework 2,0 se trouve dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="fc9f0-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="fc9f0-107">Les paramètres web ne sont utilisés dans aucun autre des fichiers de configuration, tels que le fichier machine.config, le fichier racine Web.config ou les fichiers Web.config au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="fc9f0-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
[<span data-ttu-id="fc9f0-108"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="fc9f0-108">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="fc9f0-109">&nbsp; @ no__t-1[ **@no__t -4System. Web >** ](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fc9f0-109">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>  
<span data-ttu-id="fc9f0-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<applicationPool >** ](applicationpool-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="fc9f0-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)</span></span>  
  
|<span data-ttu-id="fc9f0-111">Élément</span><span class="sxs-lookup"><span data-stu-id="fc9f0-111">Element</span></span>|<span data-ttu-id="fc9f0-112">Description</span><span class="sxs-lookup"><span data-stu-id="fc9f0-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc9f0-113">\<system.web></span><span class="sxs-lookup"><span data-stu-id="fc9f0-113">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="fc9f0-114">Contient les informations utilisées par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc9f0-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="fc9f0-115">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="fc9f0-115">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="fc9f0-116">Spécifie les paramètres d’UC et d’ASP.NET au niveau de l’exécution qui s’appliquent au comportement à l’échelle des processus géré par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fc9f0-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc9f0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc9f0-117">See also</span></span>

- [<span data-ttu-id="fc9f0-118">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="fc9f0-118">Configuration File Schema</span></span>](../index.md)
