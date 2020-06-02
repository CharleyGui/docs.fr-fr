---
title: Internationalisation et localisation d’applications .NET
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: 10d07a02a7ff744a87b920fd97df24b076c22cc3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288288"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="d1ec5-102">Internationalisation et localisation d’applications .NET</span><span class="sxs-lookup"><span data-stu-id="d1ec5-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="d1ec5-103">Le développement d’une application mondialisable, notamment une application qui peut être localisée dans une ou plusieurs langues, implique trois étapes : la mondialisation, l’étude de la localisabilité et la localisation.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="d1ec5-104">Globalisation</span><span class="sxs-lookup"><span data-stu-id="d1ec5-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="d1ec5-105">Cette étape implique la conception et le codage d'une application indépendante des cultures et des langues qui prend en charge les interfaces utilisateur localisées et les paramètres régionaux pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="d1ec5-106">Elle implique également de prendre des décisions relatives à la conception et à la programmation qui ne sont pas basées sur des hypothèses spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="d1ec5-107">Même si une application globalisée n'est pas localisée, elle est néanmoins conçue et écrite pour pouvoir être ensuite localisée assez facilement en une ou plusieurs langues.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="d1ec5-108">Révision de l’adaptabilité</span><span class="sxs-lookup"><span data-stu-id="d1ec5-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="d1ec5-109">Cette étape implique d’examiner le code et la conception d’une application pour vérifier qu’elle peut être localisée facilement et identifier les obstacles éventuels à la localisation, et de vérifier que le code exécutable de l’application est bien séparé de ses ressources.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="d1ec5-110">Si la phase de globalisation s'est déroulée correctement, l'examen de la faisabilité de localisation confirmera les choix de conception et de codage effectués pendant la globalisation.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="d1ec5-111">La phase d'examen de la faisabilité de localisation peut également identifier les problèmes restants afin de ne pas avoir à modifier le code source d'une application pendant la phase de localisation.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="d1ec5-112">Localisation</span><span class="sxs-lookup"><span data-stu-id="d1ec5-112">Localization</span></span>](localization.md)

<span data-ttu-id="d1ec5-113">Cette étape implique la personnalisation d'une application pour des cultures ou des régions spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="d1ec5-114">Si les étapes de globalisation et de faisabilité de localisation ont été effectuées correctement, la localisation consiste principalement à traduire l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="d1ec5-115">L'exécution de ces trois étapes offre deux avantages :</span><span class="sxs-lookup"><span data-stu-id="d1ec5-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="d1ec5-116">Vous n'avez plus à adapter a posteriori une application conçue pour prendre en charge une seule culture, telle que l'anglais (États-Unis), pour prendre en charge d'autres cultures.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="d1ec5-117">Il en résulte des applications localisées plus stables qui présentent moins de bogues.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="d1ec5-118">.NET assure une prise en charge complète du développement d’applications internationalisables et localisées.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="d1ec5-119">En particulier, plusieurs membres de type de la bibliothèque de classes .NET facilitent l’internationalisation en retournant des valeurs qui reflètent les conventions de la culture de l’utilisateur actuel ou d’une culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="d1ec5-120">De plus, .NET prend en charge les assemblys satellites, qui simplifient le processus de localisation d’une application.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="d1ec5-121">Pour plus d'informations, consultez la [documentation sur la globalisation](/globalization/).</span><span class="sxs-lookup"><span data-stu-id="d1ec5-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d1ec5-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d1ec5-122">In this section</span></span>

[<span data-ttu-id="d1ec5-123">Globalisation</span><span class="sxs-lookup"><span data-stu-id="d1ec5-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="d1ec5-124">Décrit la première phase de création d'une application mondialisable, qui implique la conception et le codage d'une application indépendante des cultures et des langues.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="d1ec5-125">Globalisation et ICU .NET</span><span class="sxs-lookup"><span data-stu-id="d1ec5-125">.NET globalization and ICU</span></span>](globalization-icu.md)

<span data-ttu-id="d1ec5-126">Décrit comment la globalisation .NET utilise [les composants internationaux pour Unicode (ICU)](http://site.icu-project.org/home).</span><span class="sxs-lookup"><span data-stu-id="d1ec5-126">Describes how .NET globalization uses [International Components for Unicode (ICU)](http://site.icu-project.org/home).</span></span>

[<span data-ttu-id="d1ec5-127">Révision de l’adaptabilité</span><span class="sxs-lookup"><span data-stu-id="d1ec5-127">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="d1ec5-128">Décrit la seconde phase de création d'une application localisée, qui implique l'identification d'obstacles éventuels à la localisation.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-128">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="d1ec5-129">Localisation</span><span class="sxs-lookup"><span data-stu-id="d1ec5-129">Localization</span></span>](localization.md)

<span data-ttu-id="d1ec5-130">Décrit la phase finale de la création d'une application localisée, qui implique la personnalisation de l'interface utilisateur d'une application en fonction de régions ou de cultures spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-130">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="d1ec5-131">Opérations de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="d1ec5-131">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="d1ec5-132">Explique comment utiliser les méthodes et les classes .NET dépendantes de la culture par défaut pour obtenir des résultats indépendants de la culture.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-132">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="d1ec5-133">Bonnes pratiques pour développer des applications internationales</span><span class="sxs-lookup"><span data-stu-id="d1ec5-133">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="d1ec5-134">Décrit les meilleures pratiques en matière de globalisation, de localisation et de développement d'applications ASP.NET mondialisables.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-134">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="d1ec5-135">Référence</span><span class="sxs-lookup"><span data-stu-id="d1ec5-135">Reference</span></span>

- <span data-ttu-id="d1ec5-136">Espace de noms <xref:System.Globalization?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d1ec5-136"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="d1ec5-137">Contient des classes qui définissent des informations liées à la culture, notamment la langue, le pays ou la région, les calendriers utilisés, les formats des dates, des monnaies et des nombres, ainsi que l'ordre de tri à respecter pour les chaînes.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-137">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="d1ec5-138">Espace de noms <xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="d1ec5-138"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="d1ec5-139">Fournit des classes pour créer, manipuler et utiliser des ressources.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-139">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="d1ec5-140">Espace de noms <xref:System.Text></span><span class="sxs-lookup"><span data-stu-id="d1ec5-140"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="d1ec5-141">Contient des classes représentant les encodages de caractères ASCII, ANSI, Unicode et autres.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-141">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="d1ec5-142">Resgen. exe (générateur de fichier de ressources)</span><span class="sxs-lookup"><span data-stu-id="d1ec5-142">Resgen.exe (Resource File Generator)</span></span>](../../framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="d1ec5-143">Explique comment utiliser Resgen.exe pour convertir des fichiers .txt et des fichiers .resx (format de ressource basé sur XML) en fichiers binaires .resources du Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-143">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="d1ec5-144">Winres. exe (Windows Forms éditeur de ressources)</span><span class="sxs-lookup"><span data-stu-id="d1ec5-144">Winres.exe (Windows Forms Resource Editor)</span></span>](../../framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="d1ec5-145">Explique comment utiliser Winres.exe pour localiser des formulaires Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d1ec5-145">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
