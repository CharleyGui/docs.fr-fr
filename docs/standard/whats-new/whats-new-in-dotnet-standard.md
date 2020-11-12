---
title: Nouveautés de .NET Standard
description: Cet article résume les nouvelles fonctionnalités et améliorations de chaque nouvelle version de .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 36bd1f9a0dad06d11110b35e9a66f22140cee5ca
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557270"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="dce5f-103">Nouveautés de .NET Standard</span><span class="sxs-lookup"><span data-stu-id="dce5f-103">What's new in .NET Standard</span></span>

<span data-ttu-id="dce5f-104">.NET Standard est une spécification formelle qui définit un ensemble de versions d’API qui doivent être disponibles sur les implémentations de .NET conformes à cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="dce5f-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="dce5f-105">.NET Standard est destiné aux développeurs de bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="dce5f-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="dce5f-106">Une bibliothèque qui cible une version .NET Standard peut être utilisée sur n’importe quelle implémentation .NET Framework, .NET Core ou Xamarin prenant en charge cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="dce5f-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="dce5f-107">.NET Standard est inclus dans le kit SDK .NET Core, ainsi que dans Visual Studio lorsque vous sélectionnez la charge de travail .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dce5f-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="dce5f-108">Implémentations de .NET prises en charge</span><span class="sxs-lookup"><span data-stu-id="dce5f-108">Supported .NET implementations</span></span>

<span data-ttu-id="dce5f-109">.NET Standard 2,0 est pris en charge par les implémentations .NET suivantes :</span><span class="sxs-lookup"><span data-stu-id="dce5f-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="dce5f-110">.NET Core 2.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="dce5f-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="dce5f-111">.NET Framework 4.6.1 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="dce5f-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="dce5f-112">Mono 5.4 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="dce5f-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="dce5f-113">Xamarin.iOS 10.14 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="dce5f-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="dce5f-114">Xamarin.Mac 3.8 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="dce5f-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="dce5f-115">Xamarin.Android 8.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="dce5f-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="dce5f-116">Plateforme Windows universelle 10.0.16299 ou ultérieure</span><span class="sxs-lookup"><span data-stu-id="dce5f-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="dce5f-117">Nouveautés de .NET Standard 2,0</span><span class="sxs-lookup"><span data-stu-id="dce5f-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="dce5f-118">.NET Standard 2,0 comprend les nouvelles fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="dce5f-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="dce5f-119">Un ensemble d’API largement étendu</span><span class="sxs-lookup"><span data-stu-id="dce5f-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="dce5f-120">Jusqu’à la version 1,6, .NET Standard incluait un petit sous-ensemble comparatif d’API.</span><span class="sxs-lookup"><span data-stu-id="dce5f-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="dce5f-121">Parmi ceux exclus, citons de nombreuses API qui étaient couramment utilisées dans .NET Framework ou Xamarin.</span><span class="sxs-lookup"><span data-stu-id="dce5f-121">Among those excluded were many APIs that were commonly used in .NET Framework or Xamarin.</span></span> <span data-ttu-id="dce5f-122">Cela complique le développement en obligeant les développeurs à trouver des remplacements appropriés pour les API courantes lorsqu’ils développent des applications et des bibliothèques ciblant plusieurs implémentations .NET.</span><span class="sxs-lookup"><span data-stu-id="dce5f-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="dce5f-123">.NET Standard 2,0 résout cette limitation en ajoutant plus de 20 000 API que celles disponibles dans .NET Standard 1,6, la version précédente du standard.</span><span class="sxs-lookup"><span data-stu-id="dce5f-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="dce5f-124">Pour obtenir la liste des API qui ont été ajoutées à .NET Standard 2,0, consultez [.NET Standard 2,0 ou 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="dce5f-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="dce5f-125">Voici certains des ajouts à l’espace de noms <xref:System> dans .NET Standard 2.0 :</span><span class="sxs-lookup"><span data-stu-id="dce5f-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="dce5f-126">Prise en charge de la classe <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="dce5f-127">Meilleure prise en charge de l’utilisation de tableaux provenant d’autres membres de la classe <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="dce5f-128">Meilleure prise en charge de l’utilisation d’attributs provenant d’autres membres de la classe <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="dce5f-129">Meilleure prise en charge du calendrier et d’autres options de mise en forme pour les valeurs <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="dce5f-130">Ajout d’une fonctionnalité d’arrondi <xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="dce5f-131">Ajout d’une fonctionnalité à la classe <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="dce5f-132">Meilleur contrôle du récupérateur de mémoire via la classe <xref:System.GC>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="dce5f-133">Meilleure prise en charge de la comparaison de chaînes, de l’énumération et de la normalisation dans la classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="dce5f-134">Prise en charge des ajustements à l’heure d’été et des durées de transition dans les classes <xref:System.TimeZoneInfo.AdjustmentRule> et <xref:System.TimeZoneInfo.TransitionTime>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="dce5f-135">Importante amélioration de la fonctionnalité dans la classe <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="dce5f-136">Meilleure prise en charge de la désérialisation des objets d’exception par ajout d’un constructeur d’exception avec les paramètres <xref:System.Runtime.Serialization.SerializationInfo> et <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="dce5f-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="dce5f-137">Prise en charge des bibliothèques .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dce5f-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="dce5f-138">De nombreuses bibliothèques ciblent .NET Framework plutôt que .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dce5f-138">Many libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="dce5f-139">Toutefois, la plupart des appels dans ces bibliothèques sont des API qui sont incluses dans .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="dce5f-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="dce5f-140">À compter de .NET Standard 2,0, vous pouvez accéder aux bibliothèques de .NET Framework à partir d’une bibliothèque de .NET Standard à l’aide d’un [shim de compatibilité](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="dce5f-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="dce5f-141">Cette couche de compatibilité est transparente pour les développeurs ; vous n’avez rien à faire pour tirer parti des bibliothèques .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dce5f-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="dce5f-142">La seule exigence est que les API appelées par la bibliothèque de classes .NET Framework doivent être incluses dans .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="dce5f-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="dce5f-143">Prise en charge de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dce5f-143">Support for Visual Basic</span></span>

<span data-ttu-id="dce5f-144">Vous pouvez désormais développer des bibliothèques .NET Standard dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dce5f-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="dce5f-145">Visual Studio 2019 et Visual Studio 2017 version 15,3 ou ultérieure avec la charge de travail .NET Core installée incluent un modèle de bibliothèque de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dce5f-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="dce5f-146">Pour les développeurs Visual Basic qui utilisent d’autres outils de développement et environnements, vous pouvez utiliser la commande [dotnet new](../../core/tools/dotnet-new.md) pour créer un projet de bibliothèque .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="dce5f-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="dce5f-147">Pour plus d’informations, consultez [Prise en charge des outils pour les bibliothèques .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="dce5f-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="dce5f-148">Prise en charge des outils pour les bibliothèques .NET Standard</span><span class="sxs-lookup"><span data-stu-id="dce5f-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="dce5f-149">Avec la sortie de .NET Core 2,0 et .NET Standard 2,0, Visual Studio 2017 et le [CLI .net Core](../../core/tools/index.md) incluent la prise en charge des outils pour la création de bibliothèques de .NET standard.</span><span class="sxs-lookup"><span data-stu-id="dce5f-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="dce5f-150">Si vous installez Visual Studio avec la charge de travail **développement multiplateforme .net Core** , vous pouvez créer un projet de bibliothèque .NET standard 2,0 à l’aide d’un modèle de projet, comme le montre l’illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="dce5f-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="dce5f-151">C#</span><span class="sxs-lookup"><span data-stu-id="dce5f-151">C#</span></span>](#tab/csharp)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="dce5f-153">Si vous utilisez le CLI .NET Core, la commande [dotnet New](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classes qui cible .NET standard 2,0 :</span><span class="sxs-lookup"><span data-stu-id="dce5f-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="dce5f-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dce5f-154">Visual Basic</span></span>](#tab/vb)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="dce5f-156">Si vous utilisez le CLI .NET Core, la commande [dotnet New](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classes qui cible .NET standard 2,0 :</span><span class="sxs-lookup"><span data-stu-id="dce5f-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="dce5f-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dce5f-157">See also</span></span>

- [<span data-ttu-id="dce5f-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="dce5f-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="dce5f-159">Présentation de .NET Standard</span><span class="sxs-lookup"><span data-stu-id="dce5f-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
- [<span data-ttu-id="dce5f-160">Télécharger le Kit de développement logiciel (SDK) .NET</span><span class="sxs-lookup"><span data-stu-id="dce5f-160">Download the .NET SDK</span></span>](https://dotnet.microsoft.com/download)
