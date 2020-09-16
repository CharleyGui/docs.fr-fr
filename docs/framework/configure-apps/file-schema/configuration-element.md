---
title: <configuration> (élément)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 8f79981a55d0bc9b1cd522e45f5606fda102c72c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544687"
---
# <a name="configuration-element"></a><span data-ttu-id="4ace4-102">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="4ace4-102">\<configuration> element</span></span>

<span data-ttu-id="4ace4-103">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ace4-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="4ace4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ace4-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="4ace4-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="4ace4-105">Attributes</span></span>

<span data-ttu-id="4ace4-106">None</span><span class="sxs-lookup"><span data-stu-id="4ace4-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="4ace4-107">Élément parent</span><span class="sxs-lookup"><span data-stu-id="4ace4-107">Parent element</span></span>

<span data-ttu-id="4ace4-108">None</span><span class="sxs-lookup"><span data-stu-id="4ace4-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="4ace4-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4ace4-109">Child elements</span></span>

|     | <span data-ttu-id="4ace4-110">Description</span><span class="sxs-lookup"><span data-stu-id="4ace4-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="4ace4-111">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="4ace4-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="4ace4-112">**\<startup>** Schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="4ace4-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="4ace4-113">Tous les éléments du schéma des paramètres de démarrage.</span><span class="sxs-lookup"><span data-stu-id="4ace4-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="4ace4-114">**\<runtime>** Schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="4ace4-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="4ace4-115">Tous les éléments du schéma des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4ace4-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="4ace4-116">[**\<system.runtime.remoting>** Schéma des paramètres](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4ace4-116">[**\<system.runtime.remoting>** Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="4ace4-117">Tous les éléments du schéma des paramètres de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="4ace4-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="4ace4-118">**\<system.Net>** Schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="4ace4-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="4ace4-119">Tous les éléments du schéma des paramètres réseau.</span><span class="sxs-lookup"><span data-stu-id="4ace4-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="4ace4-120">**\<cryptographySettings>** Schéma des paramètres</span><span class="sxs-lookup"><span data-stu-id="4ace4-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="4ace4-121">Tous les éléments du schéma des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="4ace4-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="4ace4-122">**\<configuration>** Schéma des sections</span><span class="sxs-lookup"><span data-stu-id="4ace4-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="4ace4-123">Tous les éléments du schéma des paramètres de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="4ace4-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="4ace4-124">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="4ace4-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="4ace4-125">Tous les éléments du schéma des paramètres de trace et de débogage.</span><span class="sxs-lookup"><span data-stu-id="4ace4-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="4ace4-126">[Schéma des paramètres de configuration de ASP.NET](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4ace4-126">[ASP.NET Configuration Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="4ace4-127">Tous les éléments du schéma de configuration ASP.NET, qui incluent des éléments pour la configuration des applications et des sites Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4ace4-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="4ace4-128">Utilisé dans les fichiers de *Web.config* .</span><span class="sxs-lookup"><span data-stu-id="4ace4-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="4ace4-129">[**\<webServices>** Schéma des paramètres](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4ace4-129">[**\<webServices>** Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="4ace4-130">Tous les éléments du schéma des paramètres des services Web.</span><span class="sxs-lookup"><span data-stu-id="4ace4-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="4ace4-131">Schéma des paramètres Web</span><span class="sxs-lookup"><span data-stu-id="4ace4-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="4ace4-132">Tous les éléments du schéma des paramètres Web, qui inclut des éléments pour la configuration d'ASP.NET en vue d'une utilisation avec une application hôte telle qu'IIS.</span><span class="sxs-lookup"><span data-stu-id="4ace4-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="4ace4-133">Utilisé dans les fichiers de *aspnet.config* .</span><span class="sxs-lookup"><span data-stu-id="4ace4-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4ace4-134">Notes</span><span class="sxs-lookup"><span data-stu-id="4ace4-134">Remarks</span></span>

<span data-ttu-id="4ace4-135">Chaque fichier de configuration doit contenir exactement un **\<configuration>** élément.</span><span class="sxs-lookup"><span data-stu-id="4ace4-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ace4-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ace4-136">See also</span></span>

- [<span data-ttu-id="4ace4-137">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ace4-137">Configuration file schema for the .NET Framework</span></span>](index.md)
