---
title: Schéma des fichiers de configuration pour le .NET Framework
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: ab6f12be01899f5b7e54a7ec2d9675d502d88bc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555131"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="79f18-102">Schéma des fichiers de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="79f18-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="79f18-103">Les fichiers de configuration sont des fichiers XML standard que vous pouvez utiliser pour modifier les paramètres et définir des stratégies pour vos applications.</span><span class="sxs-lookup"><span data-stu-id="79f18-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="79f18-104">Le schéma de configuration .NET Framework se compose d'éléments que vous pouvez utiliser dans les fichiers de configuration pour contrôler le comportement de vos applications.</span><span class="sxs-lookup"><span data-stu-id="79f18-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="79f18-105">La table des matières de cette section reflète la hiérarchie du schéma pour les paramètres de démarrage, de runtime et de réseau, ainsi que pour d'autres types de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="79f18-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="79f18-106">Pour plus d’informations sur les types, le format et l’emplacement des fichiers de configuration, consultez [configurer des applications](../index.md).</span><span class="sxs-lookup"><span data-stu-id="79f18-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="79f18-107">Familiarisez-vous avec le langage XML si vous souhaitez modifier directement les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="79f18-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79f18-108">Les étiquettes et attributs XML des fichiers de configuration respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="79f18-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="79f18-109">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="79f18-109">In this section</span></span>

<span data-ttu-id="79f18-110">[**\<configuration>** Appartient](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="79f18-111">Élément de niveau supérieur pour tous les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="79f18-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="79f18-112">[**\<assemblyBinding>** Appartient](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="79f18-113">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="79f18-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="79f18-114">[**\<linkedConfiguration>** Appartient](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="79f18-115">Spécifie un fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="79f18-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="79f18-116">[Schéma des paramètres de démarrage](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-116">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="79f18-117">Éléments qui spécifient la version du common language runtime à utiliser.</span><span class="sxs-lookup"><span data-stu-id="79f18-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="79f18-118">[Schéma des paramètres d’exécution](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-118">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="79f18-119">Éléments qui configurent la liaison d’assembly et le comportement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="79f18-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="79f18-120">[Schéma des paramètres réseau](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-120">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="79f18-121">Éléments qui spécifient la façon dont le .NET Framework se connecte à Internet.</span><span class="sxs-lookup"><span data-stu-id="79f18-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="79f18-122">[Schéma des paramètres de chiffrement](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-122">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="79f18-123">Éléments qui mappent des noms d’algorithmes conviviaux aux classes qui implémentent des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="79f18-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="79f18-124">[Schéma des sections de configuration](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-124">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="79f18-125">Éléments utilisés pour créer et utiliser des sections de configuration pour les paramètres personnalisés.</span><span class="sxs-lookup"><span data-stu-id="79f18-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="79f18-126">[Schéma des paramètres de trace et de débogage](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-126">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="79f18-127">Éléments qui spécifient des commutateurs de trace et des écouteurs.</span><span class="sxs-lookup"><span data-stu-id="79f18-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="79f18-128">[Schéma des paramètres du fournisseur de langage et du compilateur](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="79f18-129">Éléments qui spécifient la configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="79f18-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="79f18-130">[Schéma des paramètres de l’application](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-130">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="79f18-131">Éléments qui permettent à une application Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="79f18-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="79f18-132">[Schéma des paramètres de l’application](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-132">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="79f18-133">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="79f18-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="79f18-134">[Schéma des paramètres Web](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-134">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="79f18-135">Éléments permettant de configurer la façon dont ASP.NET fonctionne avec une application hôte telle qu’IIS.</span><span class="sxs-lookup"><span data-stu-id="79f18-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="79f18-136">Utilisé dans les fichiers *Aspnet.config*.</span><span class="sxs-lookup"><span data-stu-id="79f18-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="79f18-137">[Schéma de configuration de Windows Forms](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-137">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="79f18-138">Tous les éléments de la section de configuration de l’application Windows Forms, qui comprend des personnalisations telles que la prise en charge de plusieurs moniteurs et de la haute résolution.</span><span class="sxs-lookup"><span data-stu-id="79f18-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="79f18-139">[Schéma de configuration WCF](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-139">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="79f18-140">Tous les éléments qui vous permettent de configurer les applications clientes et de service WCF.</span><span class="sxs-lookup"><span data-stu-id="79f18-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="79f18-141">[Syntaxe de directive WCF](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-141">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="79f18-142">Décrit la `@ServiceHost` directive, qui définit des attributs spécifiques à la page utilisés par le compilateur. svc.</span><span class="sxs-lookup"><span data-stu-id="79f18-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="79f18-143">[Schéma de configuration de WIF](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="79f18-143">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="79f18-144">Tous les éléments du schéma de configuration de Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="79f18-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="79f18-145">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="79f18-145">Related sections</span></span>

<span data-ttu-id="79f18-146">[Schéma des paramètres de communication à distance](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="79f18-146">[Remoting Settings Schema](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="79f18-147">Décrit les éléments qui configurent les applications client-serveur qui implémentent la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="79f18-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="79f18-148">[Schéma des paramètres ASP.NET](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="79f18-148">[ASP.NET Settings Schema](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="79f18-149">Décrit les éléments qui contrôlent le comportement d'applications web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="79f18-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="79f18-150">[Schéma des paramètres des services Web](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="79f18-150">[Web Services Settings Schema](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="79f18-151">Décrit les éléments qui contrôlent le comportement des services web ASP.NET et de leurs clients.</span><span class="sxs-lookup"><span data-stu-id="79f18-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="79f18-152">[Configuration des applications .NET Framework](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="79f18-152">[Configuring .NET Framework Apps](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="79f18-153">Décrit comment configurer la sécurité, les liaisons d’assembly et la communication à distance dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="79f18-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
