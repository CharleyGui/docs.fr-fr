---
title: Développement des applications de service Windows
description: Consultez des liens vers des articles qui expliquent comment développer des applications de service Windows à l’aide de Visual Studio ou du kit de développement logiciel (SDK) .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- ServiceInstaller class, Windows Service applications
- Service class, Windows Service applications
- Windows Service applications
- Windows NT services
- ServiceProcessInstaller class, Windows Service applications
- services
- .NET applications, Windows applications
ms.assetid: ba72d648-9553-4849-b829-069ad5ea014b
author: ghogen
ms.openlocfilehash: ed02d523c21c51df2ed886843fdb71c075c93c30
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925694"
---
# <a name="develop-windows-service-apps"></a><span data-ttu-id="47b2a-103">Développer des applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="47b2a-103">Develop Windows service apps</span></span>

<span data-ttu-id="47b2a-104">Utilisez Visual Studio ou le SDK .NET Framework pour créer facilement des services. En fait, vous créez une application qui est installée comme service.</span><span class="sxs-lookup"><span data-stu-id="47b2a-104">Using Visual Studio or the .NET Framework SDK, you can easily create services by creating an application that is installed as a service.</span></span> <span data-ttu-id="47b2a-105">Ce type d’application est appelé un service Windows.</span><span class="sxs-lookup"><span data-stu-id="47b2a-105">This type of application is called a Windows service.</span></span> <span data-ttu-id="47b2a-106">Grâce aux fonctionnalités du framework, vous pouvez non seulement créer des services, les installer, les démarrer et les arrêter, mais aussi contrôler leur comportement.</span><span class="sxs-lookup"><span data-stu-id="47b2a-106">With framework features, you can create services, install them, and start, stop, and otherwise control their behavior.</span></span>

> [!NOTE]
> <span data-ttu-id="47b2a-107">Dans Visual Studio, vous pouvez créer un service dans le code managé en Visual C# ou Visual Basic, qui peut interagir avec le code C++ existant, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="47b2a-107">In Visual Studio you can create a service in managed code in Visual C# or Visual Basic, which can interoperate with existing C++ code if required.</span></span> <span data-ttu-id="47b2a-108">Ou, vous pouvez créer un service Windows en C++ natif à l’aide de [l’Assistant Projet ATL](/cpp/atl/reference/atl-project-wizard).</span><span class="sxs-lookup"><span data-stu-id="47b2a-108">Or, you can create a Windows service in native C++ by using the [ATL Project Wizard](/cpp/atl/reference/atl-project-wizard).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="47b2a-109">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="47b2a-109">In this section</span></span>

[<span data-ttu-id="47b2a-110">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="47b2a-110">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)

<span data-ttu-id="47b2a-111">Fournit une vue d’ensemble des applications de service Windows, de la durée de vie d’un service, et des différences entre les applications de service et les autres types de projets courants.</span><span class="sxs-lookup"><span data-stu-id="47b2a-111">Provides an overview of Windows service applications, the lifetime of a service, and how service applications differ from other common project types.</span></span>

[<span data-ttu-id="47b2a-112">Procédure pas à pas : création d’une application de service Windows dans le Concepteur de composants</span><span class="sxs-lookup"><span data-stu-id="47b2a-112">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)

<span data-ttu-id="47b2a-113">Fournit un exemple de création d’un service en Visual Basic et Visual C#.</span><span class="sxs-lookup"><span data-stu-id="47b2a-113">Provides an example of creating a service in Visual Basic and Visual C#.</span></span>

[<span data-ttu-id="47b2a-114">Architecture de programmation d'une application de service</span><span class="sxs-lookup"><span data-stu-id="47b2a-114">Service Application Programming Architecture</span></span>](service-application-programming-architecture.md)

<span data-ttu-id="47b2a-115">Explique les éléments de langage utilisés dans la programmation d’un service.</span><span class="sxs-lookup"><span data-stu-id="47b2a-115">Explains the language elements used in service programming.</span></span>

[<span data-ttu-id="47b2a-116">Procédure : créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="47b2a-116">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)

<span data-ttu-id="47b2a-117">Décrit le processus de création et de configuration de services Windows à l’aide du modèle de projet de service Windows.</span><span class="sxs-lookup"><span data-stu-id="47b2a-117">Describes the process of creating and configuring Windows services using the Windows service project template.</span></span>

## <a name="related-sections"></a><span data-ttu-id="47b2a-118">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="47b2a-118">Related sections</span></span>

<span data-ttu-id="47b2a-119"><xref:System.ServiceProcess.ServiceBase> - Décrit les principales fonctionnalités de la classe <xref:System.ServiceProcess.ServiceBase> qui est utilisée pour créer des services.</span><span class="sxs-lookup"><span data-stu-id="47b2a-119"><xref:System.ServiceProcess.ServiceBase> - Describes the major features of the <xref:System.ServiceProcess.ServiceBase> class, which is used to create services.</span></span>

<span data-ttu-id="47b2a-120"><xref:System.ServiceProcess.ServiceProcessInstaller> - Décrit les fonctionnalités de la classe <xref:System.ServiceProcess.ServiceProcessInstaller>. Celle-ci, utilisée avec la classe <xref:System.ServiceProcess.ServiceInstaller>, permet d’installer et de désinstaller vos services.</span><span class="sxs-lookup"><span data-stu-id="47b2a-120"><xref:System.ServiceProcess.ServiceProcessInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceProcessInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceInstaller> class to install and uninstall your services.</span></span>

<span data-ttu-id="47b2a-121"><xref:System.ServiceProcess.ServiceInstaller> - Décrit les fonctionnalités de la classe <xref:System.ServiceProcess.ServiceInstaller>. Celle-ci, utilisée avec la classe <xref:System.ServiceProcess.ServiceProcessInstaller>, permet d’installer et de désinstaller votre service.</span><span class="sxs-lookup"><span data-stu-id="47b2a-121"><xref:System.ServiceProcess.ServiceInstaller> - Describes the features of the <xref:System.ServiceProcess.ServiceInstaller> class, which is used along with the <xref:System.ServiceProcess.ServiceProcessInstaller> class to install and uninstall your service.</span></span>

<span data-ttu-id="47b2a-122">[Créer des projets à partir de modèles](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) - Décrit les types de projets utilisés dans ce chapitre et comment faire votre choix.</span><span class="sxs-lookup"><span data-stu-id="47b2a-122">[Create Projects from Templates](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0fyc0azh(v=vs.120)) -  Describes the projects types used in this chapter and how to choose between them.</span></span>
