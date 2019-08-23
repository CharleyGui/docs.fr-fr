---
title: <configuration>, élément
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921244"
---
# <a name="configuration-element"></a><span data-ttu-id="385c5-102">\<élément de > de configuration</span><span class="sxs-lookup"><span data-stu-id="385c5-102">\<configuration> element</span></span>

<span data-ttu-id="385c5-103">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="385c5-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="385c5-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="385c5-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="385c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="385c5-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="385c5-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="385c5-106">Attributes</span></span>

<span data-ttu-id="385c5-107">Aucun</span><span class="sxs-lookup"><span data-stu-id="385c5-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="385c5-108">Élément parent</span><span class="sxs-lookup"><span data-stu-id="385c5-108">Parent element</span></span>

<span data-ttu-id="385c5-109">Aucun</span><span class="sxs-lookup"><span data-stu-id="385c5-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="385c5-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="385c5-110">Child elements</span></span>

|     | <span data-ttu-id="385c5-111">Description</span><span class="sxs-lookup"><span data-stu-id="385c5-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="385c5-112"> **\<assemblyBinding>** </span><span class="sxs-lookup"><span data-stu-id="385c5-112">**\<assemblyBinding>**</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="385c5-113">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="385c5-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="385c5-114">schéma des paramètres de démarrage >  **\<** </span><span class="sxs-lookup"><span data-stu-id="385c5-114">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="385c5-115">Tous les éléments du schéma des paramètres de démarrage.</span><span class="sxs-lookup"><span data-stu-id="385c5-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="385c5-116">schéma des paramètres de > du runtime  **\<** </span><span class="sxs-lookup"><span data-stu-id="385c5-116">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="385c5-117">Tous les éléments du schéma des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="385c5-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="385c5-118">[schéma des paramètres de **> System. Runtime. Remoting \<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="385c5-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="385c5-119">Tous les éléments du schéma des paramètres de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="385c5-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="385c5-120">schéma des paramètres **System .net > \<** </span><span class="sxs-lookup"><span data-stu-id="385c5-120">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="385c5-121">Tous les éléments du schéma des paramètres réseau.</span><span class="sxs-lookup"><span data-stu-id="385c5-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="385c5-122">schéma des paramètres de > cryptographySettings  **\<** </span><span class="sxs-lookup"><span data-stu-id="385c5-122">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="385c5-123">Tous les éléments du schéma des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="385c5-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="385c5-124">schéma des sections de > de configuration  **\<** </span><span class="sxs-lookup"><span data-stu-id="385c5-124">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="385c5-125">Tous les éléments du schéma des paramètres de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="385c5-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="385c5-126">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="385c5-126">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="385c5-127">Tous les éléments du schéma des paramètres de trace et de débogage.</span><span class="sxs-lookup"><span data-stu-id="385c5-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="385c5-128">[Schéma des paramètres de configuration de ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="385c5-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="385c5-129">Tous les éléments du schéma de configuration ASP.NET, qui incluent des éléments pour la configuration des applications et des sites Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="385c5-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="385c5-130">Utilisé dans les fichiers *Web. config* .</span><span class="sxs-lookup"><span data-stu-id="385c5-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="385c5-131">[schéma des paramètres WebServices >  **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="385c5-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="385c5-132">Tous les éléments du schéma des paramètres des services Web.</span><span class="sxs-lookup"><span data-stu-id="385c5-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="385c5-133">Schéma des paramètres web</span><span class="sxs-lookup"><span data-stu-id="385c5-133">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="385c5-134">Tous les éléments du schéma des paramètres Web, qui inclut des éléments pour la configuration d'ASP.NET en vue d'une utilisation avec une application hôte telle qu'IIS.</span><span class="sxs-lookup"><span data-stu-id="385c5-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="385c5-135">Utilisé dans les fichiers *Aspnet. config* .</span><span class="sxs-lookup"><span data-stu-id="385c5-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="385c5-136">Notes</span><span class="sxs-lookup"><span data-stu-id="385c5-136">Remarks</span></span>

<span data-ttu-id="385c5-137">Chaque fichier de configuration doit contenir exactement  **\<** un élément de configuration >.</span><span class="sxs-lookup"><span data-stu-id="385c5-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="385c5-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="385c5-138">See also</span></span>

- [<span data-ttu-id="385c5-139">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="385c5-139">Configuration file schema for the .NET Framework</span></span>](index.md)
