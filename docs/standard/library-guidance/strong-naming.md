---
title: Affectation de noms forts et bibliothèques .NET
description: Meilleures pratiques recommandées pour l’affectation de noms forts aux bibliothèques .NET.
ms.date: 10/16/2018
ms.openlocfilehash: db268093b07a2ece7cdb8329fd789b52da9c5c32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744537"
---
# <a name="strong-naming"></a><span data-ttu-id="9ee2a-103">Affectation de noms forts</span><span class="sxs-lookup"><span data-stu-id="9ee2a-103">Strong naming</span></span>

<span data-ttu-id="9ee2a-104">L’affectation de noms forts fait référence à la signature d’un assembly avec une clé, produisant un [assembly avec un nom fort](../assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="9ee2a-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../assembly/strong-named.md).</span></span> <span data-ttu-id="9ee2a-105">Lorsqu’un assembly a un nom fort, cela crée une identité unique basée sur le nom et le numéro de version de l’assembly, et cela peut aider à éviter les conflits de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="9ee2a-106">L’inconvénient de l’utilisation de noms forts est que le .NET Framework sur Windows permet le chargement strict des assemblys une fois qu’un assembly possède un nom fort.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="9ee2a-107">Une référence d’assembly avec un nom fort doit correspondre exactement à la version référencée par un assembly, ce qui force les développeurs à [configurer des redirections de liaison](../../framework/configure-apps/redirect-assembly-versions.md) lors de l’utilisation de l’assembly :</span><span class="sxs-lookup"><span data-stu-id="9ee2a-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="9ee2a-108">Lorsque les développeurs .NET se plaignent de l’affectation de noms forts, ils se plaignent généralement d’un chargement d’assembly strict.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="9ee2a-109">Heureusement, ce problème est limité au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="9ee2a-110">.NET Core, Xamarin, UWP et la plupart des autres implémentations .NET n’ont pas le chargement d’assembly strict, ce qui élimine le principal inconvénient lié à l’affectation de noms forts.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="9ee2a-111">Un aspect important de l’affectation de noms forts est qu’elle est virale : un assembly avec un nom fort ne peut référencer que d’autres assemblys avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="9ee2a-112">Si votre bibliothèque n’a pas un nom fort, vous empêchez alors les développeurs qui créent une application ou une bibliothèque ayant besoin de l’affectation de noms fortsr de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="9ee2a-113">Les avantages de l’affectation de noms forts sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="9ee2a-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="9ee2a-114">L’assembly peut être référencé et utilisé par d’autres assemblys avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="9ee2a-115">L'assembly peut être stocké dans le Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="9ee2a-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="9ee2a-116">L’assembly peut être chargé côte à côte avec d’autres versions de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="9ee2a-117">Le chargement des assemblys côte à côte est généralement requis par les applications avec des architectures de plug-in.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="9ee2a-118">Créer des bibliothèques .NET à nom fort</span><span class="sxs-lookup"><span data-stu-id="9ee2a-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="9ee2a-119">Vous devez donner à vos bibliothèques .NET open source des noms forts.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="9ee2a-120">L’affectation d’un nom fort à un assembly garantit que la plupart des personnes peuvent l’utiliser, et le chargement d’assembly strict affecte uniquement le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="9ee2a-121">Ce guide est spécifique aux bibliothèques .NET publiquement distribuées, telles que les bibliothèques .NET publiées sur NuGet.org. L’attribution d’un nom fort n’est pas requise par la plupart des applications .NET et ne doit pas être effectuée par défaut.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="9ee2a-122">✔️ envisagez d’utiliser un nom fort pour les assemblys de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-122">✔️ CONSIDER strong naming your library's assemblies.</span></span>

<span data-ttu-id="9ee2a-123">✔️ envisagez d’ajouter la clé de nom fort à votre système de contrôle de code source.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-123">✔️ CONSIDER adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="9ee2a-124">Une clé disponible publiquement permet aux développeurs de modifier et de recompiler le code source de votre bibliothèque avec la même clé.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
>
> <span data-ttu-id="9ee2a-125">Vous ne devez pas rendre la clé d’affectation de noms forts publique si elle a été utilisé dans le passé pour accorder des autorisations spéciales dans des [scénarios de confiance partielle](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span><span class="sxs-lookup"><span data-stu-id="9ee2a-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](../../framework/misc/using-libraries-from-partially-trusted-code.md).</span></span> <span data-ttu-id="9ee2a-126">Sinon, vous pourriez compromettre les environnements existants.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ee2a-127">Lorsque l’identité de l’éditeur du code est requise, [Authenticode](/windows-hardware/drivers/install/authenticode) et [Signature du package NuGet](/nuget/create-packages/sign-a-package) sont recommandés.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="9ee2a-128">La sécurité d’accès du code (CAS) ne doit pas être utilisée comme atténuation des risques de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="9ee2a-129">✔️ envisagez d’incrémenter la version de l’assembly uniquement sur les modifications de version majeures pour aider les utilisateurs à réduire les redirections de liaison et la fréquence à laquelle elles sont mises à jour.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-129">✔️ CONSIDER incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="9ee2a-130">En savoir plus sur [le contrôle de version et la version de l’assembly](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="9ee2a-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="9ee2a-131">❌ n’ajoutez pas, ne supprimez pas ou ne modifiez pas la clé de nom fort.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-131">❌ DO NOT add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="9ee2a-132">La modification de la clé d’affectation de noms forts d’un assembly modifie l’identité de l’assembly et altère le code compilé qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="9ee2a-133">Pour plus d'informations, consultez [Modifications importantes binaires](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="9ee2a-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="9ee2a-134">❌ ne publiez pas de versions avec nom fort et non avec nom fort de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-134">❌ DO NOT publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="9ee2a-135">Par exemple : `Contoso.Api` et `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="9ee2a-136">La publication deux packages duplique (fork) votre écosystème de développeur.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="9ee2a-137">En outre, si une application dépend des deux packages, le développeur peut rencontrer des conflits de noms de type.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="9ee2a-138">En ce qui concerne .NET, il existe des types différents dans des assemblys différents.</span><span class="sxs-lookup"><span data-stu-id="9ee2a-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9ee2a-139">[Précédent](cross-platform-targeting.md)
>[Suivant](nuget.md)</span><span class="sxs-lookup"><span data-stu-id="9ee2a-139">[Previous](cross-platform-targeting.md)
[Next](nuget.md)</span></span>
