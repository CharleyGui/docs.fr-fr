---
title: Nouveautés de .NET Standard
description: Cet article résume les nouvelles fonctionnalités et améliorations de chaque nouvelle version de .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: a90df0360211c3b02f4f2d8697890180099c5807
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921055"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="06b27-103">Nouveautés de .NET Standard</span><span class="sxs-lookup"><span data-stu-id="06b27-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="06b27-104">.NET Standard est une spécification formelle qui définit un ensemble d’API avec gestion des versions, qui doit être disponible sur les implémentations de .NET conformes à cette version du standard.</span><span class="sxs-lookup"><span data-stu-id="06b27-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="06b27-105">.NET Standard est destiné aux développeurs de bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="06b27-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="06b27-106">Une bibliothèque qui cible une version .NET Standard peut être utilisée sur n’importe quelle implémentation .NET Framework, .NET Core ou Xamarin prenant en charge cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="06b27-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="06b27-107">La version la plus récente de .NET Standard est 2.0.</span><span class="sxs-lookup"><span data-stu-id="06b27-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="06b27-108">Il est inclus avec le .NET Core 2.0 SDK, ainsi qu’avec Visual Studio 2017 version 15.3 avec la charge de travail .NET Core installé.</span><span class="sxs-lookup"><span data-stu-id="06b27-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="06b27-109">Implémentations de .NET prises en charge</span><span class="sxs-lookup"><span data-stu-id="06b27-109">Supported .NET implementations</span></span>

<span data-ttu-id="06b27-110">Les implémentations .NET suivantes prennent en charge la norme .NET Standard 2.0 :</span><span class="sxs-lookup"><span data-stu-id="06b27-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="06b27-111">.NET Core 2.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="06b27-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="06b27-112">.NET Framework 4.6.1 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="06b27-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="06b27-113">Mono 5.4 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="06b27-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="06b27-114">Xamarin.iOS 10.14 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="06b27-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="06b27-115">Xamarin.Mac 3.8 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="06b27-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="06b27-116">Xamarin.Android 8.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="06b27-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="06b27-117">Plateforme Windows universelle 10.0.16299 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="06b27-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="06b27-118">Nouveautés de .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="06b27-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="06b27-119">.NET Standard 2.0 inclut les nouvelles fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="06b27-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="06b27-120">Un ensemble d’API largement étendu</span><span class="sxs-lookup"><span data-stu-id="06b27-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="06b27-121">Jusqu'à la version 1.6, .NET Standard incluait un sous-ensemble d’API relativement limité.</span><span class="sxs-lookup"><span data-stu-id="06b27-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="06b27-122">Ce sous-ensemble excluait de nombreuses API utilisées dans .NET Framework ou Xamarin.</span><span class="sxs-lookup"><span data-stu-id="06b27-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="06b27-123">Cela complique le développement en obligeant les développeurs à trouver des remplacements appropriés pour les API courantes lorsqu’ils développent des applications et des bibliothèques ciblant plusieurs implémentations .NET.</span><span class="sxs-lookup"><span data-stu-id="06b27-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="06b27-124">.NET Standard 2.0 lève cette limitation en ajoutant plus de 20 000 API supplémentaires par rapport à .NET Standard 1.6, la version précédente de la norme.</span><span class="sxs-lookup"><span data-stu-id="06b27-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="06b27-125">Pour obtenir la liste des API ajoutées à .NET Standard 2.0, voir [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="06b27-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="06b27-126">Voici certains des ajouts à l’espace de noms <xref:System> dans .NET Standard 2.0 :</span><span class="sxs-lookup"><span data-stu-id="06b27-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="06b27-127">Prise en charge de la classe <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="06b27-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="06b27-128">Meilleure prise en charge de l’utilisation de tableaux provenant d’autres membres de la classe <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="06b27-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="06b27-129">Meilleure prise en charge de l’utilisation d’attributs provenant d’autres membres de la classe <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="06b27-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="06b27-130">Meilleure prise en charge du calendrier et d’autres options de mise en forme pour les valeurs <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="06b27-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="06b27-131">Ajout d’une fonctionnalité d’arrondi <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="06b27-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="06b27-132">Ajout d’une fonctionnalité à la classe <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="06b27-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="06b27-133">Meilleur contrôle du récupérateur de mémoire via la classe <xref:System.GC>.</span><span class="sxs-lookup"><span data-stu-id="06b27-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="06b27-134">Meilleure prise en charge de la comparaison de chaînes, de l’énumération et de la normalisation dans la classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="06b27-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="06b27-135">Prise en charge des ajustements à l’heure d’été et des durées de transition dans les classes <xref:System.TimeZoneInfo.AdjustmentRule> et <xref:System.TimeZoneInfo.TransitionTime>.</span><span class="sxs-lookup"><span data-stu-id="06b27-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="06b27-136">Importante amélioration de la fonctionnalité dans la classe <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="06b27-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="06b27-137">Meilleure prise en charge de la désérialisation des objets d’exception par ajout d’un constructeur d’exception avec les paramètres <xref:System.Runtime.Serialization.SerializationInfo> et <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="06b27-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="06b27-138">Prise en charge des bibliothèques .NET Framework</span><span class="sxs-lookup"><span data-stu-id="06b27-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="06b27-139">La très grande majorité des bibliothèques ciblent .NET Framework plutôt que .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="06b27-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="06b27-140">Toutefois, la plupart des appels dans ces bibliothèques sont dirigés vers les API incluses dans .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="06b27-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="06b27-141">À partir de .NET Standard 2.0, vous pouvez accéder aux bibliothèques .NET Framework depuis une bibliothèque .NET Standard en utilisant un [correctif de compatibilité](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="06b27-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="06b27-142">Cette couche de compatibilité est transparente pour les développeurs ; vous n’avez rien à faire pour tirer parti des bibliothèques .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06b27-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="06b27-143">La seule condition est que les API appelées par la bibliothèque de classes .NET Framework doivent être incluses dans .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="06b27-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="06b27-144">Prise en charge de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06b27-144">Support for Visual Basic</span></span>

<span data-ttu-id="06b27-145">Vous pouvez désormais développer des bibliothèques .NET Standard dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="06b27-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="06b27-146">Pour les développeurs Visual Basic utilisant Visual Studio 2017 version 15.3 ou plus tard avec la charge de travail .NET Core installé, Visual Studio comprend maintenant un modèle .NET Standard Class Library.</span><span class="sxs-lookup"><span data-stu-id="06b27-146">For Visual Basic developers using Visual Studio 2017 version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="06b27-147">Pour les développeurs Visual Basic qui utilisent d’autres outils de développement et environnements, vous pouvez utiliser la commande [dotnet new](../../core/tools/dotnet-new.md) pour créer un projet de bibliothèque .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="06b27-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="06b27-148">Pour plus d’informations, consultez [Prise en charge des outils pour les bibliothèques .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="06b27-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="06b27-149">Prise en charge des outils pour les bibliothèques .NET Standard</span><span class="sxs-lookup"><span data-stu-id="06b27-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="06b27-150">Avec la sortie de .NET Core 2.0 et .NET Standard 2.0, Visual Studio 2017 et le [.NET Core CLI](../../core/tools/index.md) incluent le support d’outillage pour la création de bibliothèques .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="06b27-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="06b27-151">Si vous installez Visual Studio avec la charge de travail **de développement multiplateforme .NET Core,** vous pouvez créer un projet de bibliothèque .NET Standard 2.0 en utilisant un modèle de projet, comme le montre le chiffre suivant :</span><span class="sxs-lookup"><span data-stu-id="06b27-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="06b27-152">C #</span><span class="sxs-lookup"><span data-stu-id="06b27-152">C#</span></span>](#tab/csharp)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="06b27-154">Si vous utilisez l’interface CLI .NET Core, la commande [dotnet new](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classes qui cible .NET Standard 2.0 :</span><span class="sxs-lookup"><span data-stu-id="06b27-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="06b27-155">Base visuelle</span><span class="sxs-lookup"><span data-stu-id="06b27-155">Visual Basic</span></span>](#tab/vb)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="06b27-157">Si vous utilisez l’interface CLI .NET Core, la commande [dotnet new](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classes qui cible .NET Standard 2.0 :</span><span class="sxs-lookup"><span data-stu-id="06b27-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="06b27-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06b27-158">See also</span></span>

- [<span data-ttu-id="06b27-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="06b27-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="06b27-160">Présentation de .NET Standard</span><span class="sxs-lookup"><span data-stu-id="06b27-160">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
