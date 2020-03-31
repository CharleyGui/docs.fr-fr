---
title: Quoi de neuf dans .NET Standard
description: Cet article résume les nouvelles fonctionnalités et améliorations de chaque nouvelle version de .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438201"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="e90e8-103">Quoi de neuf dans .NET Standard</span><span class="sxs-lookup"><span data-stu-id="e90e8-103">What's new in .NET Standard</span></span>

<span data-ttu-id="e90e8-104">.NET Standard est une spécification formelle qui définit un ensemble versionné d’API qui doivent être disponibles sur les implémentations .NET qui se conforment à cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="e90e8-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="e90e8-105">.NET Standard s’adresse aux développeurs de bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="e90e8-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="e90e8-106">Une bibliothèque qui cible une version .NET Standard peut être utilisée sur n’importe quelle implémentation .NET Framework, .NET Core ou Xamarin prenant en charge cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="e90e8-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="e90e8-107">.NET Standard est inclus avec le .NET Core SDK, ainsi qu’avec Visual Studio lorsque vous sélectionnez la charge de travail .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e90e8-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="e90e8-108">Implémentations de .NET prises en charge</span><span class="sxs-lookup"><span data-stu-id="e90e8-108">Supported .NET implementations</span></span>

<span data-ttu-id="e90e8-109">.NET Standard 2.0 est soutenu par les implémentations suivantes .NET:</span><span class="sxs-lookup"><span data-stu-id="e90e8-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="e90e8-110">.NET Core 2.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="e90e8-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="e90e8-111">.NET Framework 4.6.1 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="e90e8-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="e90e8-112">Mono 5.4 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="e90e8-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="e90e8-113">Xamarin.iOS 10.14 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="e90e8-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="e90e8-114">Xamarin.Mac 3.8 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="e90e8-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="e90e8-115">Xamarin.Android 8.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="e90e8-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="e90e8-116">Plateforme Windows universelle 10.0.16299 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="e90e8-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="e90e8-117">Quoi de neuf dans .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="e90e8-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="e90e8-118">.NET Standard 2.0 comprend les nouvelles fonctionnalités suivantes:</span><span class="sxs-lookup"><span data-stu-id="e90e8-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="e90e8-119">Un ensemble d’API largement étendu</span><span class="sxs-lookup"><span data-stu-id="e90e8-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="e90e8-120">Grâce à la version 1.6, .NET Standard comprenait un sous-ensemble relativement petit d’API.</span><span class="sxs-lookup"><span data-stu-id="e90e8-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="e90e8-121">Ce sous-ensemble excluait de nombreuses API utilisées dans .NET Framework ou Xamarin.</span><span class="sxs-lookup"><span data-stu-id="e90e8-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="e90e8-122">Cela complique le développement en obligeant les développeurs à trouver des remplacements appropriés pour les API courantes lorsqu’ils développent des applications et des bibliothèques ciblant plusieurs implémentations .NET.</span><span class="sxs-lookup"><span data-stu-id="e90e8-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="e90e8-123">.NET Standard 2.0 répond à cette limitation en ajoutant plus de 20.000 API de plus que ce qui était disponible dans .NET Standard 1.6, la version précédente de la norme.</span><span class="sxs-lookup"><span data-stu-id="e90e8-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="e90e8-124">Pour une liste des API qui ont été ajoutées à .NET Standard 2.0, voir [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="e90e8-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="e90e8-125">Voici certains des ajouts à l’espace de noms <xref:System> dans .NET Standard 2.0 :</span><span class="sxs-lookup"><span data-stu-id="e90e8-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="e90e8-126">Prise en charge de la classe <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="e90e8-127">Meilleure prise en charge de l’utilisation de tableaux provenant d’autres membres de la classe <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="e90e8-128">Meilleure prise en charge de l’utilisation d’attributs provenant d’autres membres de la classe <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="e90e8-129">Meilleure prise en charge du calendrier et d’autres options de mise en forme pour les valeurs <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="e90e8-130">Ajout d’une fonctionnalité d’arrondi <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="e90e8-131">Ajout d’une fonctionnalité à la classe <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="e90e8-132">Meilleur contrôle du récupérateur de mémoire via la classe <xref:System.GC>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="e90e8-133">Meilleure prise en charge de la comparaison de chaînes, de l’énumération et de la normalisation dans la classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="e90e8-134">Prise en charge des ajustements à l’heure d’été et des durées de transition dans les classes <xref:System.TimeZoneInfo.AdjustmentRule> et <xref:System.TimeZoneInfo.TransitionTime>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="e90e8-135">Importante amélioration de la fonctionnalité dans la classe <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="e90e8-136">Meilleure prise en charge de la désérialisation des objets d’exception par ajout d’un constructeur d’exception avec les paramètres <xref:System.Runtime.Serialization.SerializationInfo> et <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="e90e8-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="e90e8-137">Prise en charge des bibliothèques .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e90e8-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="e90e8-138">L’écrasante majorité des bibliothèques ciblent .NET Framework plutôt que .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e90e8-138">The overwhelming majority of libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="e90e8-139">Cependant, la plupart des appels dans ces bibliothèques sont à des API qui sont inclus dans .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="e90e8-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="e90e8-140">En commençant par .NET Standard 2.0, vous pouvez accéder à des bibliothèques cadre .NET à partir d’une bibliothèque .NET Standard en utilisant un [cal de compatibilité](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="e90e8-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="e90e8-141">Cette couche de compatibilité est transparente pour les développeurs ; vous n’avez rien à faire pour tirer parti des bibliothèques .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e90e8-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="e90e8-142">L’exigence unique est que les API appelées par la bibliothèque de classe cadre .NET doivent être incluses dans la norme .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="e90e8-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="e90e8-143">Prise en charge de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e90e8-143">Support for Visual Basic</span></span>

<span data-ttu-id="e90e8-144">Vous pouvez désormais développer des bibliothèques .NET Standard dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e90e8-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="e90e8-145">Visual Studio 2019 et Visual Studio 2017 version 15.3 ou plus tard avec la charge de travail .NET Core installé comprennent un modèle .NET Standard Class Library.</span><span class="sxs-lookup"><span data-stu-id="e90e8-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="e90e8-146">Pour les développeurs Visual Basic qui utilisent d’autres outils de développement et environnements, vous pouvez utiliser la commande [dotnet new](../../core/tools/dotnet-new.md) pour créer un projet de bibliothèque .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e90e8-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="e90e8-147">Pour plus d’informations, consultez [Prise en charge des outils pour les bibliothèques .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="e90e8-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="e90e8-148">Prise en charge des outils pour les bibliothèques .NET Standard</span><span class="sxs-lookup"><span data-stu-id="e90e8-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="e90e8-149">Avec la sortie de .NET Core 2.0 et .NET Standard 2.0, Visual Studio 2017 et le [.NET Core CLI](../../core/tools/index.md) incluent le support d’outillage pour la création de bibliothèques .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e90e8-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="e90e8-150">Si vous installez Visual Studio avec la charge de travail **de développement multiplateforme .NET Core,** vous pouvez créer un projet de bibliothèque .NET Standard 2.0 en utilisant un modèle de projet, comme le montre le chiffre suivant :</span><span class="sxs-lookup"><span data-stu-id="e90e8-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="e90e8-151">C#</span><span class="sxs-lookup"><span data-stu-id="e90e8-151">C#</span></span>](#tab/csharp)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="e90e8-153">Si vous utilisez le CLI .NET Core, la nouvelle commande [dotnet](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classe qui cible .NET Standard 2.0 :</span><span class="sxs-lookup"><span data-stu-id="e90e8-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="e90e8-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e90e8-154">Visual Basic</span></span>](#tab/vb)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="e90e8-156">Si vous utilisez le CLI .NET Core, la nouvelle commande [dotnet](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classe qui cible .NET Standard 2.0 :</span><span class="sxs-lookup"><span data-stu-id="e90e8-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="e90e8-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e90e8-157">See also</span></span>

- [<span data-ttu-id="e90e8-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e90e8-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="e90e8-159">Présentation de .NET Standard</span><span class="sxs-lookup"><span data-stu-id="e90e8-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
