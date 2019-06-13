---
title: Éléments obsolètes dans la bibliothèque de classes .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 810f49581d4cb28987ea41237645f75c50388084
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690477"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="9876e-102">Éléments obsolètes dans la bibliothèque de classes .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9876e-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="9876e-103">Le .NET Framework évolue.</span><span class="sxs-lookup"><span data-stu-id="9876e-103">The .NET Framework changes over time.</span></span> <span data-ttu-id="9876e-104">Chaque nouvelle version comporte de nouveaux types et membres de type qui fournissent de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="9876e-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="9876e-105">Les types existants et leurs membres évoluent aussi.</span><span class="sxs-lookup"><span data-stu-id="9876e-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="9876e-106">Par exemple, certains types deviennent moins importants quand la technologie qu'ils prennent en charge est remplacée par une nouvelle, tandis que certaines méthodes sont remplacées par de nouvelles méthodes qui sont soit plus pratiques, soit plus complètes.</span><span class="sxs-lookup"><span data-stu-id="9876e-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are either more convenient or more full-featured.</span></span>

<span data-ttu-id="9876e-107">Le .NET Framework et le Common Language Runtime s'efforcent de prendre en charge une compatibilité descendante (ce qui permet aux applications développées avec une version du .NET Framework de fonctionner sur la version suivante).</span><span class="sxs-lookup"><span data-stu-id="9876e-107">The .NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of the .NET Framework to run on the next version of the .NET Framework).</span></span> <span data-ttu-id="9876e-108">Il est donc difficile de simplement supprimer un type ou un membre de type.</span><span class="sxs-lookup"><span data-stu-id="9876e-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="9876e-109">C'est pourquoi le .NET Framework indique plutôt qu'un type ou un membre de type ne doit plus être utilisé en le marquant comme obsolète ou déprécié.</span><span class="sxs-lookup"><span data-stu-id="9876e-109">Instead, the .NET Framework indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="9876e-110">Le fait de déprécier un type ou un membre implique de le marquer afin que les développeurs soient informés de sa future suppression et qu'ils aient le temps de réagir.</span><span class="sxs-lookup"><span data-stu-id="9876e-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="9876e-111">Toutefois, le code existant qui utilise le type ou le membre en question continue à fonctionner dans la nouvelle version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9876e-111">However, existing code that uses the type or member continues to run in the new version of the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="9876e-112">Les termes *obsolète* et *déprécié* ont la même signification quand ils sont appliqués aux types et aux membres du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9876e-112">The terms *obsolete* and *deprecated* have the same meaning when applied to the types and members of the .NET Framework.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="9876e-113">Attribut ObsoleteAttribute</span><span class="sxs-lookup"><span data-stu-id="9876e-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="9876e-114">Le .NET Framework indique qu'un type ou membre de type est obsolète en le marquant avec l'attribut <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9876e-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="9876e-115">L'application de cet attribut à un type ou membre indique que ce type ou membre sera supprimé dans une version ultérieure du .NET Framework sans casser le code compilé qui utilise ce membre.</span><span class="sxs-lookup"><span data-stu-id="9876e-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="9876e-116">En plus d'indiquer qu'un type ou un membre de type est obsolète, <xref:System.ObsoleteAttribute> définit comment le compilateur gère le code source qui inclut ce type ou membre.</span><span class="sxs-lookup"><span data-stu-id="9876e-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="9876e-117">Le compilateur peut compiler le code en émettant un message d'avertissement, ou il peut traiter l'utilisation du type ou du membre comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="9876e-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="9876e-118">Dans le premier cas, le code peut être compilé avec succès, mais un message d'avertissement indique que le type ou le membre est obsolète.</span><span class="sxs-lookup"><span data-stu-id="9876e-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="9876e-119">Dans le deuxième cas, la compilation échoue.</span><span class="sxs-lookup"><span data-stu-id="9876e-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="9876e-120">Même si la compilation produit une erreur au lieu d'un message d'avertissement, <xref:System.ObsoleteAttribute> n'affecte pas le comportement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9876e-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="9876e-121">Autrement dit, les applications qui utilisent le type ou le membre et qui ont été compilées avec succès s'exécuteront toujours correctement.</span><span class="sxs-lookup"><span data-stu-id="9876e-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="9876e-122">Seule une tentative de recompilation d'une application qui utilise le type ou le membre échoue.</span><span class="sxs-lookup"><span data-stu-id="9876e-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="9876e-123">Comment gérer des types et membres obsolètes</span><span class="sxs-lookup"><span data-stu-id="9876e-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="9876e-124">Quand vous mettez à niveau et recompilez du code existant, l'utilisation d'un type ou d'un membre obsolète qui génère un avertissement du compilateur dans votre application est parfaitement acceptable.</span><span class="sxs-lookup"><span data-stu-id="9876e-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="9876e-125">Toutefois, vous devez examiner le message d'avertissement du compilateur pour déterminer si vous devez modifier le code de votre application.</span><span class="sxs-lookup"><span data-stu-id="9876e-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="9876e-126">Si le message ne pointe pas vers une alternative appropriée, vous devez faire l'une ou l'autre des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="9876e-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="9876e-127">Modifiez votre code en supprimant l'utilisation du type ou membre, si possible.</span><span class="sxs-lookup"><span data-stu-id="9876e-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="9876e-128">- ou -</span><span class="sxs-lookup"><span data-stu-id="9876e-128">-or-</span></span>

- <span data-ttu-id="9876e-129">Examinez la documentation de ce domaine technologique pour savoir que faire face à des éléments obsolètes.</span><span class="sxs-lookup"><span data-stu-id="9876e-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="9876e-130">Vous pouvez choisir de ne pas recompiler le code existant avec une version ultérieure du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9876e-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="9876e-131">À la place, vous pouvez spécifier la version du .NET Framework sur laquelle votre code compilé existant est exécuté.</span><span class="sxs-lookup"><span data-stu-id="9876e-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="9876e-132">Par exemple, supposons que vous avez une application nommée app1.exe qui a été compilée avec le .NET Framework 3.5, mais que vous souhaitez que l’application s’exécute avec le .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="9876e-132">For example, suppose that you have an application named app1.exe that was compiled against the .NET Framework 3.5, but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="9876e-133">Ce processus implique les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9876e-133">This requires the following steps:</span></span>

1. <span data-ttu-id="9876e-134">Créez un fichier de configuration pour votre fichier exécutable principal et nommez-le *Nom_app*.exe.config, où *Nom_app* est le nom du fichier exécutable de l’application.</span><span class="sxs-lookup"><span data-stu-id="9876e-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="9876e-135">Pour l'application nommée app1.exe de notre exemple, vous devez créer un fichier de configuration intitulé app1.exe.config.</span><span class="sxs-lookup"><span data-stu-id="9876e-135">For the application named app1.exe in our example, you would create a configuration file named app1.exe.config.</span></span>

2. <span data-ttu-id="9876e-136">Ajoutez le code suivant au fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="9876e-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="9876e-137">Le tableau suivant répertorie les valeurs de chaîne que vous pouvez assigner à l’attribut `version` pour cibler une version spécifique du .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="9876e-137">The following table lists the string values that you can assign to the `version` attribute to target a specific version of the .NET Framework:</span></span>

|<span data-ttu-id="9876e-138">Version du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9876e-138">.NET Framework version</span></span>|<span data-ttu-id="9876e-139">Chaîne `version`</span><span class="sxs-lookup"><span data-stu-id="9876e-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="9876e-140">4.8</span><span class="sxs-lookup"><span data-stu-id="9876e-140">4.8</span></span>|<span data-ttu-id="9876e-141">v4.0</span><span class="sxs-lookup"><span data-stu-id="9876e-141">v4.0</span></span>|
|<span data-ttu-id="9876e-142">4.7 (y compris 4.7.1 et 4.7.2)</span><span class="sxs-lookup"><span data-stu-id="9876e-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="9876e-143">v4.0</span><span class="sxs-lookup"><span data-stu-id="9876e-143">v4.0</span></span>|
|<span data-ttu-id="9876e-144">4.6 (y compris 4.6.1 et 4.6.2)</span><span class="sxs-lookup"><span data-stu-id="9876e-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="9876e-145">v4.0</span><span class="sxs-lookup"><span data-stu-id="9876e-145">v4.0</span></span>|
|<span data-ttu-id="9876e-146">4.5 (y compris 4.5.1 et 4.5.2)</span><span class="sxs-lookup"><span data-stu-id="9876e-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="9876e-147">v4.0</span><span class="sxs-lookup"><span data-stu-id="9876e-147">v4.0</span></span>|
|<span data-ttu-id="9876e-148">4</span><span class="sxs-lookup"><span data-stu-id="9876e-148">4</span></span>|<span data-ttu-id="9876e-149">v4.0</span><span class="sxs-lookup"><span data-stu-id="9876e-149">v4.0</span></span>|
|<span data-ttu-id="9876e-150">3.5</span><span class="sxs-lookup"><span data-stu-id="9876e-150">3.5</span></span>|<span data-ttu-id="9876e-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="9876e-151">v2.0.50727</span></span>|
|<span data-ttu-id="9876e-152">2.0</span><span class="sxs-lookup"><span data-stu-id="9876e-152">2.0</span></span>|<span data-ttu-id="9876e-153">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="9876e-153">v2.0.50727</span></span>|
|<span data-ttu-id="9876e-154">1.1</span><span class="sxs-lookup"><span data-stu-id="9876e-154">1.1</span></span>|<span data-ttu-id="9876e-155">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="9876e-155">v1.1.4322</span></span>|
|<span data-ttu-id="9876e-156">1.0</span><span class="sxs-lookup"><span data-stu-id="9876e-156">1.0</span></span>|<span data-ttu-id="9876e-157">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="9876e-157">v1.0.3705</span></span>|

## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a><span data-ttu-id="9876e-158">Listes des éléments obsolètes pour .NET Framework 4.5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="9876e-158">Obsolete lists for the .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="9876e-159">Types obsolètes</span><span class="sxs-lookup"><span data-stu-id="9876e-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="9876e-160">Membres obsolètes</span><span class="sxs-lookup"><span data-stu-id="9876e-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-lists-for-previous-versions"></a><span data-ttu-id="9876e-161">Listes des éléments obsolètes pour les versions antérieures</span><span class="sxs-lookup"><span data-stu-id="9876e-161">Obsolete lists for previous versions</span></span>

- <span data-ttu-id="9876e-162">[Types obsolètes dans le .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9876e-162">[Obsolete Types in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>

- <span data-ttu-id="9876e-163">[Membres obsolètes dans le .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9876e-163">[Obsolete Members in the .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>

- <span data-ttu-id="9876e-164">[Liste des éléments obsolètes pour le .NET Framework 3.5](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="9876e-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>

- <span data-ttu-id="9876e-165">[Liste des éléments obsolètes pour le .NET Framework 2.0](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="9876e-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="9876e-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9876e-166">See also</span></span>

- [<span data-ttu-id="9876e-167">\<supportedRuntime>, élément</span><span class="sxs-lookup"><span data-stu-id="9876e-167">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
