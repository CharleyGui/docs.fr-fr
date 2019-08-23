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
ms.openlocfilehash: c3b5518b4b86c2e6f47825d552f49579c5ac0a6d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921025"
---
# <a name="configuration-file-schema-for-the-net-framework"></a><span data-ttu-id="900a7-102">Schéma des fichiers de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="900a7-102">Configuration file schema for the .NET Framework</span></span>

<span data-ttu-id="900a7-103">Les fichiers de configuration sont des fichiers XML standard que vous pouvez utiliser pour modifier les paramètres et définir des stratégies pour vos applications.</span><span class="sxs-lookup"><span data-stu-id="900a7-103">Configuration files are standard XML files that you can use to change settings and set policies for your apps.</span></span> <span data-ttu-id="900a7-104">Le schéma de configuration .NET Framework se compose d'éléments que vous pouvez utiliser dans les fichiers de configuration pour contrôler le comportement de vos applications.</span><span class="sxs-lookup"><span data-stu-id="900a7-104">The .NET Framework configuration schema consists of elements that you can use in configuration files to control the behavior of your apps.</span></span> <span data-ttu-id="900a7-105">La table des matières de cette section reflète la hiérarchie du schéma pour les paramètres de démarrage, de runtime et de réseau, ainsi que pour d'autres types de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="900a7-105">The table of contents for this section reflects the schema hierarchy for startup, runtime, network, and other types of configuration settings.</span></span>

<span data-ttu-id="900a7-106">Pour plus d’informations sur les types, le format et l’emplacement des fichiers de configuration, consultez l’article [Configuration d’applications](../index.md).</span><span class="sxs-lookup"><span data-stu-id="900a7-106">For information about the types, format, and location of configuration files, see the article [Configuring Apps](../index.md).</span></span> <span data-ttu-id="900a7-107">Familiarisez-vous avec le langage XML si vous souhaitez modifier directement les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="900a7-107">Familiarize yourself with XML if you want to edit the configuration files directly.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="900a7-108">Les étiquettes et attributs XML des fichiers de configuration respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="900a7-108">XML tags and attributes in configuration files are case-sensitive.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="900a7-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="900a7-109">In this section</span></span>

<span data-ttu-id="900a7-110">[ **\<configuration>** , élément](configuration-element.md) Décrit l’élément `<configuration>`, qui constitue l’élément de niveau supérieur de tous les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="900a7-110">[**\<configuration>** Element](configuration-element.md) Describes the `<configuration>` element, which is the top-level element for all configuration files.</span></span>

<span data-ttu-id="900a7-111">[ **\<assemblyBinding>** , élément](assemblybinding-element-for-configuration.md) Spécifie la stratégie de liaison de l’assembly au niveau de la configuration.</span><span class="sxs-lookup"><span data-stu-id="900a7-111">[**\<assemblyBinding>** Element](assemblybinding-element-for-configuration.md) Specifies assembly binding policy at the configuration level.</span></span>

<span data-ttu-id="900a7-112">[ **\<linkedConfiguration>** , élément](linkedconfiguration-element.md) Spécifie un fichier de configuration à inclure.</span><span class="sxs-lookup"><span data-stu-id="900a7-112">[**\<linkedConfiguration>** Element](linkedconfiguration-element.md) Specifies a configuration file to include.</span></span>

<span data-ttu-id="900a7-113">[Schéma des paramètres de démarrage](./startup/index.md) Décrit les éléments qui spécifient la version du common language runtime à utiliser.</span><span class="sxs-lookup"><span data-stu-id="900a7-113">[Startup Settings Schema](./startup/index.md) Describes the elements that specify which version of the common language runtime to use.</span></span>

<span data-ttu-id="900a7-114">[Schéma des paramètres d’exécution](./runtime/index.md) Décrit les éléments qui configurent les liaisons d’assembly et le comportement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="900a7-114">[Runtime Settings Schema](./runtime/index.md) Describes the elements that configure assembly binding and runtime behavior.</span></span>

<span data-ttu-id="900a7-115">[Schéma des paramètres réseau](./network/index.md) Décrit les éléments qui spécifient la manière dont le .NET Framework se connecte à Internet.</span><span class="sxs-lookup"><span data-stu-id="900a7-115">[Network Settings Schema](./network/index.md) Describes the elements that specify how the .NET Framework connects to the Internet.</span></span>

<span data-ttu-id="900a7-116">[Schéma des paramètres de chiffrement](./cryptography/index.md) Décrit des éléments qui mappent des noms d’algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="900a7-116">[Cryptography Settings Schema](./cryptography/index.md) Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>

<span data-ttu-id="900a7-117">[Schéma des sections de configuration](configuration-sections-schema.md) Décrit les éléments qui servent à créer et à utiliser les sections de configuration pour les paramètres personnalisés.</span><span class="sxs-lookup"><span data-stu-id="900a7-117">[Configuration Sections Schema](configuration-sections-schema.md) Describes the elements used to create and use configuration sections for custom settings.</span></span>

<span data-ttu-id="900a7-118">[Schéma des paramètres de traçage et de débogage](./trace-debug/index.md) Décrit les éléments qui spécifient les commutateurs et les écouteurs de traçage.</span><span class="sxs-lookup"><span data-stu-id="900a7-118">[Trace and Debug Settings Schema](./trace-debug/index.md) Describes the elements that specify trace switches and listeners.</span></span>

<span data-ttu-id="900a7-119">[Schéma des paramètres du fournisseur de langage et du compilateur](./compiler/index.md) Décrit les éléments qui spécifient la configuration de compilateur pour les fournisseurs de langages disponibles.</span><span class="sxs-lookup"><span data-stu-id="900a7-119">[Compiler and Language Provider Settings Schema](./compiler/index.md) Describes the elements that specify compiler configuration for available language providers.</span></span>

<span data-ttu-id="900a7-120">[Schéma des paramètres d’application](application-settings-schema.md) Décrit les éléments qui permettent à une application Windows Forms ou ASP.NET de stocker et d’extraire des paramètres de portée application et de portée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="900a7-120">[Application Settings Schema](application-settings-schema.md) Describes the elements that enable a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span>

<span data-ttu-id="900a7-121">[Schéma des paramètres d’application](./appsettings/index.md) Contient des paramètres d’application personnalisés, tels que des chemins de fichier, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="900a7-121">[App Settings Schema](./appsettings/index.md) Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span>

<span data-ttu-id="900a7-122">[Schéma des paramètres web](./web/index.md) Tous les éléments du schéma des paramètres web, qui inclut des éléments pour la configuration d’ASP.NET en vue d’une utilisation avec une application hôte telle qu’IIS.</span><span class="sxs-lookup"><span data-stu-id="900a7-122">[Web Settings Schema](./web/index.md) All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="900a7-123">Utilisé dans les fichiers *Aspnet.config*.</span><span class="sxs-lookup"><span data-stu-id="900a7-123">Used in *Aspnet.config* files.</span></span>

<span data-ttu-id="900a7-124">[Schéma de configuration Windows Forms](winforms/index.md) Tous les éléments de la section de configuration d’application Windows Forms, qui inclut les personnalisations telles que de la prise en charge de plusieurs moniteurs et de la haute résolution.</span><span class="sxs-lookup"><span data-stu-id="900a7-124">[Windows Forms Configuration Schema](winforms/index.md) All elements in the Windows Forms application configuration section, which includes customizations such as multi-monitor and high DPI support.</span></span>

<span data-ttu-id="900a7-125">[Schéma de configuration WCF](./wcf/index.md) Tous les éléments qui vous permettent de configurer les applications clientes et le service WCF.</span><span class="sxs-lookup"><span data-stu-id="900a7-125">[WCF Configuration Schema](./wcf/index.md) All elements that enable you to configure WCF service and client applications.</span></span>

<span data-ttu-id="900a7-126">[Syntaxe de directive WCF](./wcf-directive/index.md) Décrit la directive `@ServiceHost`, qui définit des attributs spécifiques de la page utilisés par le compilateur .svc.</span><span class="sxs-lookup"><span data-stu-id="900a7-126">[WCF Directive Syntax](./wcf-directive/index.md) Describes the `@ServiceHost` directive, which defines page-specific attributes used by the .svc compiler.</span></span>

<span data-ttu-id="900a7-127">[Schéma de configuration WIF](windows-identity-foundation/index.md) Tous les éléments du schéma de configuration Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="900a7-127">[WIF Configuration Schema](windows-identity-foundation/index.md) All elements of the Windows Identity Foundation (WIF) configuration schema.</span></span>

## <a name="related-sections"></a><span data-ttu-id="900a7-128">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="900a7-128">Related sections</span></span>

<span data-ttu-id="900a7-129">[Schéma des paramètres de communication à distance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Décrit les éléments qui configurent les applications clientes et serveur qui implémentent la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="900a7-129">[Remoting Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) Describes the elements that configure client and server applications that implement remoting.</span></span>

<span data-ttu-id="900a7-130">[Schéma de paramètres ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Décrit les éléments qui contrôlent le comportement des applications web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="900a7-130">[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web applications.</span></span>

<span data-ttu-id="900a7-131">[Schéma des paramètres des services Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Décrit les éléments qui contrôlent le comportement des services web ASP.NET et de leurs clients.</span><span class="sxs-lookup"><span data-stu-id="900a7-131">[Web Services Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) Describes the elements that control the behavior of ASP.NET Web services and their clients.</span></span>

<span data-ttu-id="900a7-132">[Configuration d’applications .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Décrit comment configurer la sécurité, les liaisons d’assembly et la communication à distance dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="900a7-132">[Configuring .NET Framework Apps](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) Describes how to configure security, assembly binding, and remoting in the .NET Framework.</span></span>
