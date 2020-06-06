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
ms.openlocfilehash: 35ed53fc480e218df595794f80af2458f3ecec38
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039157"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="06a3b-102">Schéma des fichiers de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="06a3b-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="06a3b-103">Les fichiers de configuration sont des fichiers XML standard que vous pouvez utiliser pour modifier les paramètres et définir des stratégies pour vos applications.</span><span class="sxs-lookup"><span data-stu-id="06a3b-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="06a3b-104">Le schéma de configuration .NET Framework se compose d'éléments que vous pouvez utiliser dans les fichiers de configuration pour contrôler le comportement de vos applications.</span><span class="sxs-lookup"><span data-stu-id="06a3b-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="06a3b-105">La table des matières de cette section reflète la hiérarchie du schéma pour les paramètres de démarrage, de runtime et de réseau, ainsi que pour d'autres types de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="06a3b-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="06a3b-106">Pour plus d’informations sur les types, le format et l’emplacement des fichiers de configuration, consultez [configurer des applications](../index.md).</span><span class="sxs-lookup"><span data-stu-id="06a3b-106">For information about the types, format, and location of configuration files, see [Configure apps](../index.md).</span></span> <span data-ttu-id="06a3b-107">Familiarisez-vous avec le langage XML si vous souhaitez modifier directement les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="06a3b-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06a3b-108">Les étiquettes et attributs XML des fichiers de configuration respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="06a3b-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="06a3b-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="06a3b-109">In this section</span></span>

<span data-ttu-id="06a3b-110">[**\<configuration>** Appartient](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-110">[**\<configuration>** Element](configuration-element.md)</span></span>\
<span data-ttu-id="06a3b-111">Élément de niveau supérieur pour tous les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="06a3b-111">The top-level element for all configuration files.</span></span>

<span data-ttu-id="06a3b-112">[**\<assemblyBinding>** Appartient](assemblybinding-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-112">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md)</span></span>\
<span data-ttu-id="06a3b-113">Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="06a3b-113">Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="06a3b-114">[**\<linkedConfiguration>** Appartient](linkedconfiguration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-114">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md)</span></span>\
<span data-ttu-id="06a3b-115">Spécifie un fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="06a3b-115">Specifies a configuration file to include.</span></span>

<span data-ttu-id="06a3b-116">[Schéma des paramètres de démarrage](./startup/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-116">[Startup Settings Schema](./startup/index.md)</span></span>\
<span data-ttu-id="06a3b-117">Éléments qui spécifient la version du common language runtime à utiliser.</span><span class="sxs-lookup"><span data-stu-id="06a3b-117">Elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="06a3b-118">[Schéma des paramètres d’exécution](./runtime/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-118">[Runtime Settings Schema](./runtime/index.md)</span></span>\
<span data-ttu-id="06a3b-119">Éléments qui configurent la liaison d’assembly et le comportement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="06a3b-119">Elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="06a3b-120">[Schéma des paramètres réseau](./network/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-120">[Network Settings Schema](./network/index.md)</span></span>\
<span data-ttu-id="06a3b-121">Éléments qui spécifient la façon dont le .NET Framework se connecte à Internet.</span><span class="sxs-lookup"><span data-stu-id="06a3b-121">Elements that specify how the .NET Framework connects to the internet.</span></span>

<span data-ttu-id="06a3b-122">[Schéma des paramètres de chiffrement](./cryptography/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-122">[Cryptography Settings Schema](./cryptography/index.md)</span></span>\
<span data-ttu-id="06a3b-123">Éléments qui mappent des noms d’algorithmes conviviaux aux classes qui implémentent des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="06a3b-123">Elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="06a3b-124">[Schéma des sections de configuration](configuration-sections-schema.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-124">[Configuration Sections Schema](configuration-sections-schema.md)</span></span>\
<span data-ttu-id="06a3b-125">Éléments utilisés pour créer et utiliser des sections de configuration pour les paramètres personnalisés.</span><span class="sxs-lookup"><span data-stu-id="06a3b-125">Elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="06a3b-126">[Schéma des paramètres de trace et de débogage](./trace-debug/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-126">[Trace and Debug Settings Schema](./trace-debug/index.md)</span></span>\
<span data-ttu-id="06a3b-127">Éléments qui spécifient des commutateurs de trace et des écouteurs.</span><span class="sxs-lookup"><span data-stu-id="06a3b-127">Elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="06a3b-128">[Schéma des paramètres du fournisseur de langage et du compilateur](./compiler/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-128">[Compiler and Language Provider Settings Schema](./compiler/index.md)</span></span>\
<span data-ttu-id="06a3b-129">Éléments qui spécifient la configuration du compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="06a3b-129">Elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="06a3b-130">[Schéma des paramètres de l’application](application-settings-schema.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-130">[Application Settings Schema](application-settings-schema.md)</span></span>\
<span data-ttu-id="06a3b-131">Éléments qui permettent à une application Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="06a3b-131">Elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="06a3b-132">[Schéma des paramètres de l’application](./appsettings/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-132">[App Settings Schema](./appsettings/index.md)</span></span>\
<span data-ttu-id="06a3b-133">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="06a3b-133">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="06a3b-134">[Schéma des paramètres Web](./web/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-134">[Web Settings Schema](./web/index.md)</span></span>\
<span data-ttu-id="06a3b-135">Éléments permettant de configurer la façon dont ASP.NET fonctionne avec une application hôte telle qu’IIS.</span><span class="sxs-lookup"><span data-stu-id="06a3b-135">Elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="06a3b-136">Utilisé dans les fichiers *Aspnet.config*.</span><span class="sxs-lookup"><span data-stu-id="06a3b-136">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="06a3b-137">[Schéma de configuration de Windows Forms](winforms/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-137">[Windows Forms Configuration Schema](winforms/index.md)</span></span>\
<span data-ttu-id="06a3b-138">Tous les éléments de la section de configuration de l’application Windows Forms, qui comprend des personnalisations telles que la prise en charge de plusieurs moniteurs et de la haute résolution.</span><span class="sxs-lookup"><span data-stu-id="06a3b-138">All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high-DPI support.</span></span>

<span data-ttu-id="06a3b-139">[Schéma de configuration WCF](./wcf/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-139">[WCF Configuration Schema](./wcf/index.md)</span></span>\
<span data-ttu-id="06a3b-140">Tous les éléments qui vous permettent de configurer les applications clientes et de service WCF.</span><span class="sxs-lookup"><span data-stu-id="06a3b-140">All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="06a3b-141">[Syntaxe de directive WCF](./wcf-directive/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-141">[WCF Directive Syntax](./wcf-directive/index.md)</span></span>\
<span data-ttu-id="06a3b-142">Décrit la `@ServiceHost` directive, qui définit des attributs spécifiques à la page utilisés par le compilateur. svc.</span><span class="sxs-lookup"><span data-stu-id="06a3b-142">Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="06a3b-143">[Schéma de configuration de WIF](windows-identity-foundation/index.md)</span><span class="sxs-lookup"><span data-stu-id="06a3b-143">[WIF Configuration Schema](windows-identity-foundation/index.md)</span></span>\
<span data-ttu-id="06a3b-144">Tous les éléments du schéma de configuration de Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="06a3b-144">All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="06a3b-145">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="06a3b-145">Related sections</span></span>

<span data-ttu-id="06a3b-146">[Schéma des paramètres de communication à distance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="06a3b-146">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span>\
<span data-ttu-id="06a3b-147">Décrit les éléments qui configurent les applications client-serveur qui implémentent la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="06a3b-147">Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="06a3b-148">[Schéma des paramètres ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="06a3b-148">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span>\
<span data-ttu-id="06a3b-149">Décrit les éléments qui contrôlent le comportement d'applications web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="06a3b-149">Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="06a3b-150">[Schéma des paramètres des services Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="06a3b-150">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span>\
<span data-ttu-id="06a3b-151">Décrit les éléments qui contrôlent le comportement des services web ASP.NET et de leurs clients.</span><span class="sxs-lookup"><span data-stu-id="06a3b-151">Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="06a3b-152">[Configuration des applications .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="06a3b-152">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))</span></span>\
<span data-ttu-id="06a3b-153">Décrit comment configurer la sécurité, les liaisons d’assembly et la communication à distance dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06a3b-153">Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
