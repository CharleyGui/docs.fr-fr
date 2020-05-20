---
title: Paramètres de configuration de la globalisation
description: En savoir plus sur les paramètres d’exécution qui configurent les aspects de la globalisation d’une application .NET Core, par exemple la façon dont elle analyse les dates japonaises.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 2561e66e6d18cb4036b0719f7e34ea66540fe095
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703127"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="d0b16-103">Options de configuration au moment de l’exécution pour la globalisation</span><span class="sxs-lookup"><span data-stu-id="d0b16-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="d0b16-104">Mode indifférent</span><span class="sxs-lookup"><span data-stu-id="d0b16-104">Invariant mode</span></span>

- <span data-ttu-id="d0b16-105">Détermine si une application .NET Core s’exécute en mode globalisation-invariant sans accéder aux données et au comportement spécifiques à la culture.</span><span class="sxs-lookup"><span data-stu-id="d0b16-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="d0b16-106">Par défaut : exécutez l’application avec un accès aux données culturelles ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="d0b16-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="d0b16-107">Pour plus d’informations, consultez [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="d0b16-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="d0b16-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="d0b16-108">Setting name</span></span> | <span data-ttu-id="d0b16-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="d0b16-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d0b16-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="d0b16-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="d0b16-111">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="d0b16-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="d0b16-112">`true`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="d0b16-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="d0b16-113">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="d0b16-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="d0b16-114">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="d0b16-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="d0b16-115">`true`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="d0b16-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="d0b16-116">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="d0b16-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="d0b16-117">`0`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="d0b16-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="d0b16-118">`1`-exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="d0b16-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="d0b16-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="d0b16-119">Examples</span></span>

<span data-ttu-id="d0b16-120">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="d0b16-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="d0b16-121">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="d0b16-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="d0b16-122">Plages d’années d’ère</span><span class="sxs-lookup"><span data-stu-id="d0b16-122">Era year ranges</span></span>

- <span data-ttu-id="d0b16-123">Détermine si les vérifications de plage pour les calendriers qui prennent en charge plusieurs ères sont assouplies ou si les dates qui dépassent la plage de dates d’une ère lèvent un <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="d0b16-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="d0b16-124">Valeur par défaut : les contrôles de plage sont assouplis ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="d0b16-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="d0b16-125">Pour plus d’informations, consultez [calendriers, ères et plages de dates : contrôles de plage souple](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="d0b16-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="d0b16-126">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="d0b16-126">Setting name</span></span> | <span data-ttu-id="d0b16-127">Valeurs</span><span class="sxs-lookup"><span data-stu-id="d0b16-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d0b16-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="d0b16-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="d0b16-129">`false`-vérifications de plage souples</span><span class="sxs-lookup"><span data-stu-id="d0b16-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="d0b16-130">`true`-les dépassements de capacité provoquent une exception</span><span class="sxs-lookup"><span data-stu-id="d0b16-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="d0b16-131">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="d0b16-131">**Environment variable**</span></span> | <span data-ttu-id="d0b16-132">N/A</span><span class="sxs-lookup"><span data-stu-id="d0b16-132">N/A</span></span> | <span data-ttu-id="d0b16-133">N/A</span><span class="sxs-lookup"><span data-stu-id="d0b16-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="d0b16-134">Analyse de date japonaise</span><span class="sxs-lookup"><span data-stu-id="d0b16-134">Japanese date parsing</span></span>

- <span data-ttu-id="d0b16-135">Détermine si une chaîne qui contient « 1 » ou « gannen » comme année est analysée avec succès ou si seul « 1 » est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="d0b16-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="d0b16-136">Valeur par défaut : analyser les chaînes qui contiennent soit « 1 » soit « gannen » comme année ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="d0b16-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="d0b16-137">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="d0b16-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="d0b16-138">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="d0b16-138">Setting name</span></span> | <span data-ttu-id="d0b16-139">Valeurs</span><span class="sxs-lookup"><span data-stu-id="d0b16-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d0b16-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="d0b16-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="d0b16-141">`false`-« Gannen » ou « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0b16-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="d0b16-142">`true`seule « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="d0b16-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="d0b16-143">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="d0b16-143">**Environment variable**</span></span> | <span data-ttu-id="d0b16-144">N/A</span><span class="sxs-lookup"><span data-stu-id="d0b16-144">N/A</span></span> | <span data-ttu-id="d0b16-145">N/A</span><span class="sxs-lookup"><span data-stu-id="d0b16-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="d0b16-146">Format d’année japonaise</span><span class="sxs-lookup"><span data-stu-id="d0b16-146">Japanese year format</span></span>

- <span data-ttu-id="d0b16-147">Détermine si la première année d’une ère du calendrier japonais est au format « gannen » ou en tant que nombre.</span><span class="sxs-lookup"><span data-stu-id="d0b16-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="d0b16-148">Valeur par défaut : mettez en forme la première année sous la forme « gannen » ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="d0b16-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="d0b16-149">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="d0b16-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="d0b16-150">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="d0b16-150">Setting name</span></span> | <span data-ttu-id="d0b16-151">Valeurs</span><span class="sxs-lookup"><span data-stu-id="d0b16-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d0b16-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="d0b16-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="d0b16-153">`false`-format comme « gannen »</span><span class="sxs-lookup"><span data-stu-id="d0b16-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="d0b16-154">`true`-format comme nombre</span><span class="sxs-lookup"><span data-stu-id="d0b16-154">`true` - format as number</span></span> |
| <span data-ttu-id="d0b16-155">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="d0b16-155">**Environment variable**</span></span> | <span data-ttu-id="d0b16-156">N/A</span><span class="sxs-lookup"><span data-stu-id="d0b16-156">N/A</span></span> | <span data-ttu-id="d0b16-157">N/A</span><span class="sxs-lookup"><span data-stu-id="d0b16-157">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="d0b16-158">NLS</span><span class="sxs-lookup"><span data-stu-id="d0b16-158">NLS</span></span>

- <span data-ttu-id="d0b16-159">Détermine si .NET utilise les API de globalisation NLS (National Language Support) ou International Components for Unicode (ICU) pour les applications Windows.</span><span class="sxs-lookup"><span data-stu-id="d0b16-159">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="d0b16-160">.NET 5,0 et les versions ultérieures utilisent les API de globalisation ICU par défaut sur Windows 10 mai 2019 Update et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="d0b16-160">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="d0b16-161">Si vous omettez ce paramètre, .NET utilise les API de globalisation ICU par défaut.</span><span class="sxs-lookup"><span data-stu-id="d0b16-161">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="d0b16-162">Cela équivaut à définir la valeur sur `false` .</span><span class="sxs-lookup"><span data-stu-id="d0b16-162">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="d0b16-163">Pour plus d’informations, consultez [API de globalisation utiliser des bibliothèques ICU sur Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span><span class="sxs-lookup"><span data-stu-id="d0b16-163">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="d0b16-164">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="d0b16-164">Setting name</span></span> | <span data-ttu-id="d0b16-165">Valeurs</span><span class="sxs-lookup"><span data-stu-id="d0b16-165">Values</span></span> | <span data-ttu-id="d0b16-166">Présent</span><span class="sxs-lookup"><span data-stu-id="d0b16-166">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="d0b16-167">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="d0b16-167">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="d0b16-168">`false`-Utiliser les API de globalisation ICU</span><span class="sxs-lookup"><span data-stu-id="d0b16-168">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="d0b16-169">`true`-Utiliser les API de globalisation NLS</span><span class="sxs-lookup"><span data-stu-id="d0b16-169">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="d0b16-170">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d0b16-170">.NET 5.0</span></span> |
| <span data-ttu-id="d0b16-171">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="d0b16-171">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="d0b16-172">`false`-Utiliser les API de globalisation ICU</span><span class="sxs-lookup"><span data-stu-id="d0b16-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="d0b16-173">`true`-Utiliser les API de globalisation NLS</span><span class="sxs-lookup"><span data-stu-id="d0b16-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="d0b16-174">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d0b16-174">.NET 5.0</span></span> |
