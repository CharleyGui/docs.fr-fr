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
ms.openlocfilehash: d53d3a105203addfacb1c982e0960bd12996f571
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941427"
---
# <a name="web-settings-schema"></a><span data-ttu-id="4a04a-102">Schéma des paramètres web</span><span class="sxs-lookup"><span data-stu-id="4a04a-102">Web Settings Schema</span></span>
<span data-ttu-id="4a04a-103">Les paramètres web spécifient les paramètres d’UC et d’ASP.NET au niveau de l’exécution qui s’appliquent au comportement à l’échelle des processus géré par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4a04a-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="4a04a-104">Ces paramètres se distinguent des paramètres de type de domaine d’application spécifiés dans le fichier Web.config d’une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4a04a-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="4a04a-105">Les paramètres web sont contenus dans les fichiers Aspnet.config, qui se trouvent dans les dossiers d’installation du .NET Framework, qui varient en fonction des versions.</span><span class="sxs-lookup"><span data-stu-id="4a04a-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="4a04a-106">Par exemple, le fichier Aspnet. config pour .NET Framework 2,0 se trouve dans le dossier suivant:</span><span class="sxs-lookup"><span data-stu-id="4a04a-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="4a04a-107">Les paramètres web ne sont utilisés dans aucun autre des fichiers de configuration, tels que le fichier machine.config, le fichier racine Web.config ou les fichiers Web.config au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="4a04a-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="4a04a-108">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="4a04a-108">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="4a04a-109">\<system.web>, élément (paramètres web)</span><span class="sxs-lookup"><span data-stu-id="4a04a-109">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)  
  
 [<span data-ttu-id="4a04a-110">\<applicationPool >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="4a04a-110">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="4a04a-111">Élément</span><span class="sxs-lookup"><span data-stu-id="4a04a-111">Element</span></span>|<span data-ttu-id="4a04a-112">Description</span><span class="sxs-lookup"><span data-stu-id="4a04a-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a04a-113">\<system.web></span><span class="sxs-lookup"><span data-stu-id="4a04a-113">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="4a04a-114">Contient les informations utilisées par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4a04a-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="4a04a-115">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="4a04a-115">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="4a04a-116">Spécifie les paramètres d’UC et d’ASP.NET au niveau de l’exécution qui s’appliquent au comportement à l’échelle des processus géré par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4a04a-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a04a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a04a-117">See also</span></span>

- [<span data-ttu-id="4a04a-118">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="4a04a-118">Configuration File Schema</span></span>](../index.md)
