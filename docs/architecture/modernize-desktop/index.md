---
title: Moderniser des applications de bureau sur Windows 10 avec .NET Core 3,1
description: Découvrez comment moderniser les applications de bureau existantes avec .NET Core 3,1
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423235"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a><span data-ttu-id="8fb85-103">Moderniser des applications de bureau sur Windows 10 avec .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="8fb85-103">Modernizing Desktop Apps on Windows 10 with .NET Core 3.1</span></span>

![Capture d’écran illustrant le livre électronique « Modern Desktop apps ».](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="8fb85-105">PUBLIÉ PAR</span><span class="sxs-lookup"><span data-stu-id="8fb85-105">PUBLISHED BY</span></span>

<span data-ttu-id="8fb85-106">Division Développeurs Microsoft, équipes produit .NET et Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8fb85-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="8fb85-107">Division de Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8fb85-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="8fb85-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="8fb85-108">One Microsoft Way</span></span>

<span data-ttu-id="8fb85-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="8fb85-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="8fb85-110">Copyright © 2020 par Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="8fb85-110">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="8fb85-111">Tous droits réservés.</span><span class="sxs-lookup"><span data-stu-id="8fb85-111">All rights reserved.</span></span> <span data-ttu-id="8fb85-112">Aucune partie du contenu de ce document ne peut être reproduite ou transmise sous quelque forme ou par quelque moyen que ce soit sans l’autorisation écrite de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="8fb85-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="8fb85-113">Ce document est fourni « en l’état » et exprime les points de vue et les opinions de son auteur.</span><span class="sxs-lookup"><span data-stu-id="8fb85-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="8fb85-114">Les points de vue, les opinions et les informations exprimés dans ce document, notamment l’URL et autres références à des sites web Internet, peuvent faire l’objet de modifications sans préavis.</span><span class="sxs-lookup"><span data-stu-id="8fb85-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="8fb85-115"> Certains exemples sont fournis à titre indicatif uniquement et sont fictifs.</span><span class="sxs-lookup"><span data-stu-id="8fb85-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="8fb85-116">Toute association ou lien est purement involontaire ou fortuit.</span><span class="sxs-lookup"><span data-stu-id="8fb85-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="8fb85-117">Microsoft et les marques commerciales mentionnées dans la page web « Marques » sur <https://www.microsoft.com> sont des marques du groupe Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8fb85-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="8fb85-118">Mac et macOS sont des marques commerciales d’Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="8fb85-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="8fb85-119">Toutes les autres marques et tous les autres logos sont la propriété de leurs propriétaires respectifs.</span><span class="sxs-lookup"><span data-stu-id="8fb85-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="8fb85-120">Coauteurs :</span><span class="sxs-lookup"><span data-stu-id="8fb85-120">Co-Authors:</span></span>

> <span data-ttu-id="8fb85-121">**Olia Gavrysh**, responsable de programme, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-121">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="8fb85-122">**Miguel Angel Castejón Dominguez**, architecte d’innovation, Kabel</span><span class="sxs-lookup"><span data-stu-id="8fb85-122">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="8fb85-123">Participants et réviseurs :</span><span class="sxs-lookup"><span data-stu-id="8fb85-123">Participants and reviewers:</span></span>

> <span data-ttu-id="8fb85-124">**Maira Wenzel**, responsable de programme senior, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-124">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="8fb85-125">**Andy gorge**, développeur de contenu senior, équipe .net docs, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-125">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="8fb85-126">**Miguel Ramos**, responsable de programme senior, équipe Windows Developer Platform, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-126">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="8fb85-127">**Adam Braden**, responsable de programme principal, équipe de plateforme de développement Windows, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-127">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="8fb85-128">**Ricardo Minguez Pablos**, responsable de programme senior, équipe Azure IOT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-128">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="8fb85-129">**Nish Anile**, responsable de programme senior, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-129">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="8fb85-130">**Beth Massei**, responsable marketing produit senior, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-130">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="8fb85-131">**Scott Hunter**, responsable partenaire directeur de programme, équipe .net, Microsoft</span><span class="sxs-lookup"><span data-stu-id="8fb85-131">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="8fb85-132">**Marta Fuentes Lara**, Kabel</span><span class="sxs-lookup"><span data-stu-id="8fb85-132">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="8fb85-133">**Raúl Fernández de nicaraguayen**, Kabel</span><span class="sxs-lookup"><span data-stu-id="8fb85-133">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="8fb85-134">**Antonio Manuel Fernández Cantos**, Kabel</span><span class="sxs-lookup"><span data-stu-id="8fb85-134">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="8fb85-135">Introduction</span><span class="sxs-lookup"><span data-stu-id="8fb85-135">Introduction</span></span>

<span data-ttu-id="8fb85-136">Ce livre concerne les stratégies que vous pouvez adopter pour déplacer vos applications de bureau existantes à travers le chemin de modernisation et intégrer les dernières fonctionnalités de Runtime, de langage et de plateforme.</span><span class="sxs-lookup"><span data-stu-id="8fb85-136">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="8fb85-137">Vous découvrirez qu’il n’existe pas de recette unique dans la mesure où chaque application est différente, et donc vos exigences et vos préférences.</span><span class="sxs-lookup"><span data-stu-id="8fb85-137">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="8fb85-138">La bonne nouvelle, c’est qu’il existe des approches courantes que vous pouvez appliquer pour ajouter de nouvelles fonctionnalités à vos applications.</span><span class="sxs-lookup"><span data-stu-id="8fb85-138">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="8fb85-139">Certaines d’entre elles ne nécessitent même pas de modifications majeures de votre code.</span><span class="sxs-lookup"><span data-stu-id="8fb85-139">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="8fb85-140">Dans cet ouvrage, nous allons vous montrer comment toutes ces fonctionnalités fonctionnent en arrière-plan et expliquent les mécanismes de leurs implémentations.</span><span class="sxs-lookup"><span data-stu-id="8fb85-140">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="8fb85-141">En outre, vous trouverez des scénarios courants pour la modernisation des applications de bureau existantes en détail, ce qui vous permet de trouver de l’inspiration pour l’évolution de vos projets.</span><span class="sxs-lookup"><span data-stu-id="8fb85-141">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="8fb85-142">L’approche de Microsoft pour la modernisation des applications existantes est de vous offrir la possibilité de créer votre propre chemin personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8fb85-142">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="8fb85-143">Toutes les stratégies de modernisation décrites dans cet ouvrage sont principalement indépendantes.</span><span class="sxs-lookup"><span data-stu-id="8fb85-143">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="8fb85-144">Vous pouvez choisir ceux qui sont pertinents pour votre application et ignorer d’autres qui ne sont pas importants pour vous.</span><span class="sxs-lookup"><span data-stu-id="8fb85-144">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="8fb85-145">En d’autres termes, vous pouvez mélanger et faire correspondre les stratégies pour répondre au mieux aux besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="8fb85-145">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="8fb85-146">Qui doit utiliser le livre</span><span class="sxs-lookup"><span data-stu-id="8fb85-146">Who should use the book</span></span>

<span data-ttu-id="8fb85-147">Nous avons rédigé cet ouvrage pour les développeurs et les architectes de solutions qui veulent moderniser les applications de bureau Windows Forms et WPF existantes pour tirer parti des avantages de .NET Core et de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="8fb85-147">We wrote this book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET Core and Windows 10.</span></span>

<span data-ttu-id="8fb85-148">Ce livre peut également être utile si vous êtes un décideur technique, tel qu’un architecte d’entreprise ou un responsable ou directeur de développement qui souhaite une vue d’ensemble des avantages de la mise à jour des applications de bureau existantes.</span><span class="sxs-lookup"><span data-stu-id="8fb85-148">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="8fb85-149">Comment utiliser le livre</span><span class="sxs-lookup"><span data-stu-id="8fb85-149">How to use the book</span></span>

<span data-ttu-id="8fb85-150">Ce livre aborde le « pourquoi », pour vous aider à moderniser vos applications existantes et les avantages spécifiques que vous pouvez vous procurer à l’aide de NET Core 3,1 et MSIX pour moderniser vos applications de bureau.</span><span class="sxs-lookup"><span data-stu-id="8fb85-150">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET Core 3.1 and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="8fb85-151">Le contenu du livre est conçu pour les architectes et les décideurs techniques qui souhaitent une vue d’ensemble, mais qui n’ont pas besoin de se concentrer sur la mise en œuvre et les détails techniques, pas à pas.</span><span class="sxs-lookup"><span data-stu-id="8fb85-151">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="8fb85-152">Dans les différents chapitres, des exemples d’extraits de code d’implémentation et des captures d’écran sont fournis, le chapitre 5 étant destiné à présenter un processus de migration complet pour les exemples d’applications.</span><span class="sxs-lookup"><span data-stu-id="8fb85-152">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="8fb85-153">Ce que ce livre ne couvre pas</span><span class="sxs-lookup"><span data-stu-id="8fb85-153">What this book doesn't cover</span></span>

<span data-ttu-id="8fb85-154">Ce livre couvre un sous-ensemble spécifique de scénarios qui se concentrent sur les scénarios d’élévation et de déplacement, en soulignant la façon d’obtenir les avantages de la modernisation sans l’effort de réécriture du code.</span><span class="sxs-lookup"><span data-stu-id="8fb85-154">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="8fb85-155">Ce livre ne s’intéresse pas au développement d’applications modernes avec .NET Core à partir de zéro ou à la prise en main de Windows Forms et de WPF.</span><span class="sxs-lookup"><span data-stu-id="8fb85-155">This book isn't about developing modern applications with .NET Core from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="8fb85-156">Il se concentre sur la façon dont vous pouvez mettre à jour les applications de bureau existantes avec les dernières technologies pour le développement de postes de travail.</span><span class="sxs-lookup"><span data-stu-id="8fb85-156">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="8fb85-157">Exemples utilisés dans ce livre</span><span class="sxs-lookup"><span data-stu-id="8fb85-157">Samples used in this book</span></span>

<span data-ttu-id="8fb85-158">Pour mettre en évidence les étapes nécessaires pour effectuer une modernisation, nous allons utiliser un exemple d’application appelé `eShopModernizing` .</span><span class="sxs-lookup"><span data-stu-id="8fb85-158">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="8fb85-159">Cette application a deux versions, Windows Forms et WPF, et nous vous présenterons un processus pas à pas sur la façon d’effectuer la modernisation des deux à la fois sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8fb85-159">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET Core.</span></span>

<span data-ttu-id="8fb85-160">En outre, sur le référentiel GitHub pour ce livre, vous trouverez les résultats du processus, que vous pouvez consulter si vous décidez de suivre le didacticiel pas à pas.</span><span class="sxs-lookup"><span data-stu-id="8fb85-160">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="8fb85-161">Envoyez votre feedback</span><span class="sxs-lookup"><span data-stu-id="8fb85-161">Send your feedback</span></span>

<span data-ttu-id="8fb85-162">Ce livre et les exemples associés sont en constante évolution. vos commentaires sont donc accueillis !</span><span class="sxs-lookup"><span data-stu-id="8fb85-162">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="8fb85-163">Si vous avez des commentaires sur la façon dont ce livre peut être amélioré, utilisez la section commentaires au bas de toute page reposant sur les [problèmes GitHub](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="8fb85-163">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="8fb85-164">Suivant</span><span class="sxs-lookup"><span data-stu-id="8fb85-164">Next</span></span>](why-modern-applications.md)
