---
title: Fonctionnalités obsolètes dans .NET 5 +
description: Découvrez les API qui sont marquées comme obsolètes dans .NET 5,0 et versions ultérieures qui génèrent des avertissements du compilateur SYSLIB.
ms.date: 10/20/2020
ms.openlocfilehash: aa5716ba8fe46c7c4ae2faafe7cc963551eecef7
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440762"
---
# <a name="obsolete-features-in-net-5"></a><span data-ttu-id="14953-103">Fonctionnalités obsolètes dans .NET 5</span><span class="sxs-lookup"><span data-stu-id="14953-103">Obsolete features in .NET 5</span></span>

<span data-ttu-id="14953-104">À compter de .NET 5,0, certaines API qui viennent d’être marquées comme obsolètes utilisent deux nouvelles propriétés sur <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="14953-104">Starting in .NET 5.0, some APIs that are newly marked as obsolete make use of two new properties on <xref:System.ObsoleteAttribute>.</span></span>

- <span data-ttu-id="14953-105">La <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> propriété indique au compilateur de générer des avertissements de génération à l’aide d’un ID de diagnostic personnalisé.</span><span class="sxs-lookup"><span data-stu-id="14953-105">The <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> property tells the compiler to generate build warnings using a custom diagnostic ID.</span></span> <span data-ttu-id="14953-106">L’ID personnalisé permet de supprimer l’avertissement obsoletion spécifiquement et séparément les uns des autres.</span><span class="sxs-lookup"><span data-stu-id="14953-106">The custom ID allows for obsoletion warning to be suppressed specifically and separately from one another.</span></span> <span data-ttu-id="14953-107">Dans le cas de .NET 5 + obsoletions, le format de l’ID de diagnostic personnalisé est `SYSLIBxxxx` .</span><span class="sxs-lookup"><span data-stu-id="14953-107">In the case of the .NET 5+ obsoletions, the format for the custom diagnostic ID is `SYSLIBxxxx`.</span></span>

- <span data-ttu-id="14953-108">La <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> propriété indique au compilateur d’inclure un lien d’URL pour en savoir plus sur le obsoletion.</span><span class="sxs-lookup"><span data-stu-id="14953-108">The <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> property tells the compiler to include a URL link to learn more about the obsoletion.</span></span>

<span data-ttu-id="14953-109">Si vous rencontrez des avertissements ou des erreurs de build en raison de l’utilisation d’une API obsolète, suivez les instructions spécifiques fournies pour l’ID de diagnostic figurant dans la section [référence](#reference) .</span><span class="sxs-lookup"><span data-stu-id="14953-109">If you encounter build warnings or errors due to usage of an obsolete API, follow the specific guidance provided for the diagnostic ID listed in the [Reference](#reference) section.</span></span> <span data-ttu-id="14953-110">Les avertissements ou les erreurs pour ces obsoletions *ne peuvent pas* être supprimés à l’aide de l' [ID de diagnostic standard (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) pour les types ou membres obsolètes ; Utilisez les valeurs d’ID de diagnostic personnalisées à la `SYSLIBxxxx` place.</span><span class="sxs-lookup"><span data-stu-id="14953-110">Warnings or errors for these obsoletions *can't* be suppressed using the [standard diagnostic ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID values instead.</span></span> <span data-ttu-id="14953-111">Pour plus d’informations, consultez [supprimer des avertissements](#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="14953-111">For more information, see [Suppress warnings](#suppress-warnings).</span></span>

## <a name="reference"></a><span data-ttu-id="14953-112">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="14953-112">Reference</span></span>

<span data-ttu-id="14953-113">Le tableau suivant fournit un index des `SYSLIBxxxx` obsoletions dans .net 5 +.</span><span class="sxs-lookup"><span data-stu-id="14953-113">The following table provides an index to the `SYSLIBxxxx` obsoletions in .NET 5+.</span></span>

| <span data-ttu-id="14953-114">ID de diagnostic</span><span class="sxs-lookup"><span data-stu-id="14953-114">Diagnostic ID</span></span> | <span data-ttu-id="14953-115">Description</span><span class="sxs-lookup"><span data-stu-id="14953-115">Description</span></span> |
| - | - |
| [<span data-ttu-id="14953-116">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="14953-116">SYSLIB0001</span></span>](syslib0001.md) | <span data-ttu-id="14953-117">L’encodage UTF-7 n’est pas sécurisé et ne doit pas être utilisé.</span><span class="sxs-lookup"><span data-stu-id="14953-117">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="14953-118">Envisagez plutôt d’utiliser UTF-8.</span><span class="sxs-lookup"><span data-stu-id="14953-118">Consider using UTF-8 instead.</span></span> |
| [<span data-ttu-id="14953-119">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="14953-119">SYSLIB0002</span></span>](syslib0002.md) | <span data-ttu-id="14953-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> n’est pas respecté par le runtime et ne doit pas être utilisé.</span><span class="sxs-lookup"><span data-stu-id="14953-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> |
| [<span data-ttu-id="14953-121">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="14953-121">SYSLIB0003</span></span>](syslib0003.md) | <span data-ttu-id="14953-122">La sécurité d’accès du code (CAS) n’est pas prise en charge ou respectée par le Runtime.</span><span class="sxs-lookup"><span data-stu-id="14953-122">Code access security (CAS) is not supported or honored by the runtime.</span></span> |
| [<span data-ttu-id="14953-123">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="14953-123">SYSLIB0004</span></span>](syslib0004.md) | <span data-ttu-id="14953-124">La fonctionnalité de région d’exécution limitée n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="14953-124">The constrained execution region (CER) feature is not supported.</span></span> |
| [<span data-ttu-id="14953-125">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="14953-125">SYSLIB0005</span></span>](syslib0005.md) | <span data-ttu-id="14953-126">Le Global Assembly Cache (GAC) n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="14953-126">The global assembly cache (GAC) is not supported.</span></span> |
| [<span data-ttu-id="14953-127">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="14953-127">SYSLIB0006</span></span>](syslib0006.md) | <span data-ttu-id="14953-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> n’est pas pris en charge et lève une exception <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="14953-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="14953-129">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="14953-129">SYSLIB0007</span></span>](syslib0007.md) | <span data-ttu-id="14953-130">L’implémentation par défaut de cet algorithme de chiffrement n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="14953-130">The default implementation of this cryptography algorithm is not supported.</span></span> |
| [<span data-ttu-id="14953-131">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="14953-131">SYSLIB0008</span></span>](syslib0008.md) | <span data-ttu-id="14953-132">L' <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API n’est pas prise en charge et lève une exception <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="14953-132">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="14953-133">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="14953-133">SYSLIB0009</span></span>](syslib0009.md) | <span data-ttu-id="14953-134">Les <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> méthodes et ne <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> sont pas prises en charge et lèvent <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="14953-134">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="14953-135">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="14953-135">SYSLIB0010</span></span>](syslib0010.md) | <span data-ttu-id="14953-136">Certaines API de communication à distance ne sont pas prises en charge et lèvent <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="14953-136">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="14953-137">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="14953-137">SYSLIB0011</span></span>](syslib0011.md) | <span data-ttu-id="14953-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> la sérialisation est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="14953-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> |
| [<span data-ttu-id="14953-139">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="14953-139">SYSLIB0012</span></span>](syslib0012.md) | <span data-ttu-id="14953-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> et <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> sont uniquement inclus pour la compatibilité .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="14953-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="14953-141">Utilisez <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> à la place.</span><span class="sxs-lookup"><span data-stu-id="14953-141">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> |

## <a name="suppress-warnings"></a><span data-ttu-id="14953-142">Supprimer les avertissements</span><span class="sxs-lookup"><span data-stu-id="14953-142">Suppress warnings</span></span>

<span data-ttu-id="14953-143">Si vous devez utiliser les API obsolètes et `SYSLIBxxxx` que le diagnostic ne se présente pas comme une erreur, vous pouvez supprimer l’avertissement dans le code ou dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="14953-143">If you must use the obsolete APIs and the `SYSLIBxxxx` diagnostic does not surface as an error, you can suppress the warning in code or in your project file.</span></span>

<span data-ttu-id="14953-144">Dans le code :</span><span class="sxs-lookup"><span data-stu-id="14953-144">In code:</span></span>

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

<span data-ttu-id="14953-145">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="14953-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
   <!-- To suppress multiple warnings, you can use multiple NoWarn elements -->
   <NoWarn>$(NoWarn);SYSLIB0002</NoWarn>
   <NoWarn>$(NoWarn);SYSLIB0003</NoWarn>
   <!-- Alternatively, you can suppress multiple warnings by using a semicolon-delimited list -->
   <NoWarn>$(NoWarn);SYSLIB0001;SYSLIB0002;SYSLIB0003</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> <span data-ttu-id="14953-146">La suppression des avertissements de cette façon ne désactive que les avertissements obsoletion que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="14953-146">Suppressing warnings in this way only disables the obsoletion warnings you specify.</span></span> <span data-ttu-id="14953-147">Il ne désactive pas les autres avertissements, y compris les avertissements obsoletion avec différents ID de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="14953-147">It doesn't disable any other warnings, including obsoletion warnings with different diagnostic IDs.</span></span>
