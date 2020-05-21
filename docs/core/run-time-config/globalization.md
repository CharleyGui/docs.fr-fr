---
title: Paramètres de configuration de la globalisation
description: En savoir plus sur les paramètres d’exécution qui configurent les aspects de la globalisation d’une application .NET Core, par exemple la façon dont elle analyse les dates japonaises.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 56228e9a6cb6dbab6a22bdc00d11212e1019776b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761965"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="221bf-103">Options de configuration au moment de l’exécution pour la globalisation</span><span class="sxs-lookup"><span data-stu-id="221bf-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="221bf-104">Mode indifférent</span><span class="sxs-lookup"><span data-stu-id="221bf-104">Invariant mode</span></span>

- <span data-ttu-id="221bf-105">Détermine si une application .NET Core s’exécute en mode globalisation-invariant sans accéder aux données et au comportement spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="221bf-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="221bf-106">Si vous omettez ce paramètre, l’application s’exécute avec un accès aux données culturelles.</span><span class="sxs-lookup"><span data-stu-id="221bf-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="221bf-107">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="221bf-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="221bf-108">Pour plus d’informations, consultez [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="221bf-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="221bf-109">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="221bf-109">Setting name</span></span> | <span data-ttu-id="221bf-110">Valeurs</span><span class="sxs-lookup"><span data-stu-id="221bf-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="221bf-111">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="221bf-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="221bf-112">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="221bf-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="221bf-113">`true`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="221bf-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="221bf-114">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="221bf-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="221bf-115">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="221bf-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="221bf-116">`true`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="221bf-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="221bf-117">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="221bf-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="221bf-118">`0`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="221bf-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="221bf-119">`1`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="221bf-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="221bf-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="221bf-120">Examples</span></span>

<span data-ttu-id="221bf-121">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="221bf-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="221bf-122">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="221bf-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="221bf-123">Plages d’années d’ère</span><span class="sxs-lookup"><span data-stu-id="221bf-123">Era year ranges</span></span>

- <span data-ttu-id="221bf-124">Détermine si les vérifications de plage pour les calendriers qui prennent en charge plusieurs ères sont assouplies ou si les dates qui dépassent la plage de dates d’une ère lèvent un <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="221bf-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="221bf-125">Si vous omettez ce paramètre, les contrôles de plage sont assouplis.</span><span class="sxs-lookup"><span data-stu-id="221bf-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="221bf-126">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="221bf-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="221bf-127">Pour plus d’informations, consultez [calendriers, ères et plages de dates : contrôles de plage souple](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="221bf-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="221bf-128">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="221bf-128">Setting name</span></span> | <span data-ttu-id="221bf-129">Valeurs</span><span class="sxs-lookup"><span data-stu-id="221bf-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="221bf-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="221bf-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="221bf-131">`false`-vérifications de plage souples</span><span class="sxs-lookup"><span data-stu-id="221bf-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="221bf-132">`true`-les dépassements de capacité provoquent une exception</span><span class="sxs-lookup"><span data-stu-id="221bf-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="221bf-133">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="221bf-133">**Environment variable**</span></span> | <span data-ttu-id="221bf-134">N/A</span><span class="sxs-lookup"><span data-stu-id="221bf-134">N/A</span></span> | <span data-ttu-id="221bf-135">N/A</span><span class="sxs-lookup"><span data-stu-id="221bf-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="221bf-136">Analyse de date japonaise</span><span class="sxs-lookup"><span data-stu-id="221bf-136">Japanese date parsing</span></span>

- <span data-ttu-id="221bf-137">Détermine si une chaîne qui contient « 1 » ou « gannen » comme année est analysée avec succès ou si seul « 1 » est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="221bf-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="221bf-138">Si vous omettez ce paramètre, les chaînes qui contiennent « 1 » ou « gannen » sont analysées avec succès.</span><span class="sxs-lookup"><span data-stu-id="221bf-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="221bf-139">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="221bf-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="221bf-140">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="221bf-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="221bf-141">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="221bf-141">Setting name</span></span> | <span data-ttu-id="221bf-142">Valeurs</span><span class="sxs-lookup"><span data-stu-id="221bf-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="221bf-143">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="221bf-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="221bf-144">`false`-« Gannen » ou « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="221bf-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="221bf-145">`true`seule « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="221bf-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="221bf-146">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="221bf-146">**Environment variable**</span></span> | <span data-ttu-id="221bf-147">N/A</span><span class="sxs-lookup"><span data-stu-id="221bf-147">N/A</span></span> | <span data-ttu-id="221bf-148">N/A</span><span class="sxs-lookup"><span data-stu-id="221bf-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="221bf-149">Format d’année japonaise</span><span class="sxs-lookup"><span data-stu-id="221bf-149">Japanese year format</span></span>

- <span data-ttu-id="221bf-150">Détermine si la première année d’une ère du calendrier japonais est au format « gannen » ou en tant que nombre.</span><span class="sxs-lookup"><span data-stu-id="221bf-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="221bf-151">Si vous omettez ce paramètre, la première année est mise en forme en tant que « gannen ».</span><span class="sxs-lookup"><span data-stu-id="221bf-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="221bf-152">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="221bf-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="221bf-153">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="221bf-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="221bf-154">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="221bf-154">Setting name</span></span> | <span data-ttu-id="221bf-155">Valeurs</span><span class="sxs-lookup"><span data-stu-id="221bf-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="221bf-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="221bf-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="221bf-157">`false`-format comme « gannen »</span><span class="sxs-lookup"><span data-stu-id="221bf-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="221bf-158">`true`-format comme nombre</span><span class="sxs-lookup"><span data-stu-id="221bf-158">`true` - format as number</span></span> |
| <span data-ttu-id="221bf-159">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="221bf-159">**Environment variable**</span></span> | <span data-ttu-id="221bf-160">N/A</span><span class="sxs-lookup"><span data-stu-id="221bf-160">N/A</span></span> | <span data-ttu-id="221bf-161">N/A</span><span class="sxs-lookup"><span data-stu-id="221bf-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="221bf-162">NLS</span><span class="sxs-lookup"><span data-stu-id="221bf-162">NLS</span></span>

- <span data-ttu-id="221bf-163">Détermine si .NET utilise les API de globalisation NLS (National Language Support) ou International Components for Unicode (ICU) pour les applications Windows.</span><span class="sxs-lookup"><span data-stu-id="221bf-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="221bf-164">.NET 5,0 et les versions ultérieures utilisent les API de globalisation ICU par défaut sur Windows 10 mai 2019 Update et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="221bf-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="221bf-165">Si vous omettez ce paramètre, .NET utilise les API de globalisation ICU par défaut.</span><span class="sxs-lookup"><span data-stu-id="221bf-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="221bf-166">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="221bf-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="221bf-167">Pour plus d’informations, consultez [API de globalisation utiliser des bibliothèques ICU sur Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span><span class="sxs-lookup"><span data-stu-id="221bf-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="221bf-168">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="221bf-168">Setting name</span></span> | <span data-ttu-id="221bf-169">Valeurs</span><span class="sxs-lookup"><span data-stu-id="221bf-169">Values</span></span> | <span data-ttu-id="221bf-170">Présent</span><span class="sxs-lookup"><span data-stu-id="221bf-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="221bf-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="221bf-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="221bf-172">`false`-Utiliser les API de globalisation ICU</span><span class="sxs-lookup"><span data-stu-id="221bf-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="221bf-173">`true`-Utiliser les API de globalisation NLS</span><span class="sxs-lookup"><span data-stu-id="221bf-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="221bf-174">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="221bf-174">.NET 5.0</span></span> |
| <span data-ttu-id="221bf-175">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="221bf-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="221bf-176">`false`-Utiliser les API de globalisation ICU</span><span class="sxs-lookup"><span data-stu-id="221bf-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="221bf-177">`true`-Utiliser les API de globalisation NLS</span><span class="sxs-lookup"><span data-stu-id="221bf-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="221bf-178">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="221bf-178">.NET 5.0</span></span> |
