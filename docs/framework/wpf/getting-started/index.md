---
title: Prise en main
description: Créer des applications clientes de bureau avec l’infrastructure d’interface utilisateur de Windows Presentation Foundation (WPF), un sous-ensemble des .NET Framework.
ms.date: 01/26/2018
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
ms.openlocfilehash: 2977831bf17ac11a67f71037d26e4f4665131721
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853851"
---
# <a name="get-started-wpf"></a><span data-ttu-id="2e0ef-103">Bien démarrer (WPF)</span><span class="sxs-lookup"><span data-stu-id="2e0ef-103">Get started (WPF)</span></span>

<span data-ttu-id="2e0ef-104">Windows Presentation Foundation (WPF) est une infrastructure d’interface utilisateur qui permet de créer des applications de bureau clientes.</span><span class="sxs-lookup"><span data-stu-id="2e0ef-104">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="2e0ef-105">La plateforme de développement WPF prend en charge un large éventail de fonctionnalités de développement d’applications, notamment un modèle d’application, des ressources, des contrôles, des graphiques, une disposition, la liaison de données, des documents et la sécurité.</span><span class="sxs-lookup"><span data-stu-id="2e0ef-105">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="2e0ef-106">S’agissant d’un sous-ensemble du .NET Framework, si vous avez déjà créé des applications avec le .NET Framework à l’aide d’ASP.NET ou de Windows Forms, l’environnement de programmation doit vous être familier.</span><span class="sxs-lookup"><span data-stu-id="2e0ef-106">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="2e0ef-107">WPF utilise le langage XAML (Extensible Application Markup Language) pour fournir un modèle déclaratif à des fins de programmation d’applications.</span><span class="sxs-lookup"><span data-stu-id="2e0ef-107">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="2e0ef-108">Cette section contient des rubriques de présentation et d’aide à la prise en main de WPF.</span><span class="sxs-lookup"><span data-stu-id="2e0ef-108">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="2e0ef-109">Par où commencer ?</span><span class="sxs-lookup"><span data-stu-id="2e0ef-109">Where should I start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e0ef-110">Je veux rentrer dans le vif du sujet...</span><span class="sxs-lookup"><span data-stu-id="2e0ef-110">I want to jump right in…</span></span>|[<span data-ttu-id="2e0ef-111">Procédure pas à pas : ma première application de bureau WPF</span><span class="sxs-lookup"><span data-stu-id="2e0ef-111">Walkthrough: My first WPF desktop application</span></span>](walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="2e0ef-112">Comment concevoir l’interface utilisateur de l’application ?</span><span class="sxs-lookup"><span data-stu-id="2e0ef-112">How do I design the application UI?</span></span>|[<span data-ttu-id="2e0ef-113">Conception XAML dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2e0ef-113">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="2e0ef-114">Vous débutez avec .NET ?</span><span class="sxs-lookup"><span data-stu-id="2e0ef-114">New to .NET?</span></span>|[<span data-ttu-id="2e0ef-115">Vue d’ensemble de l' .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e0ef-115">Overview of the .NET Framework</span></span>](../../get-started/overview.md)<br /><br /> [<span data-ttu-id="2e0ef-116">Mises en route de Visual Basic et Visual C#</span><span class="sxs-lookup"><span data-stu-id="2e0ef-116">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/quickstart-visual-basic-console)|  
|<span data-ttu-id="2e0ef-117">En savoir plus sur WPF...</span><span class="sxs-lookup"><span data-stu-id="2e0ef-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="2e0ef-118">Présentation de WPF dans Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="2e0ef-118">Introduction to WPF in Visual Studio</span></span>](introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="2e0ef-119">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="2e0ef-119">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)<br /><br /> [<span data-ttu-id="2e0ef-120">Contrôles</span><span class="sxs-lookup"><span data-stu-id="2e0ef-120">Controls</span></span>](../controls/index.md)<br /><br /> [<span data-ttu-id="2e0ef-121">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="2e0ef-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="2e0ef-122">Vous êtes développeur Windows Forms ?</span><span class="sxs-lookup"><span data-stu-id="2e0ef-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="2e0ef-123">Contrôles Windows Forms et contrôles WPF équivalents</span><span class="sxs-lookup"><span data-stu-id="2e0ef-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="2e0ef-124">Interopérabilité WPF et Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2e0ef-124">WPF and Windows Forms Interoperation</span></span>](../advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="2e0ef-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e0ef-125">See also</span></span>

- [<span data-ttu-id="2e0ef-126">Bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="2e0ef-126">Class Library</span></span>](../class-library-wpf.md)
- [<span data-ttu-id="2e0ef-127">Développement d’applications</span><span class="sxs-lookup"><span data-stu-id="2e0ef-127">Application Development</span></span>](../app-development/index.md)
- [<span data-ttu-id="2e0ef-128">Centre de développement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2e0ef-128">.NET Framework Developer Center</span></span>](https://dotnet.microsoft.com)
