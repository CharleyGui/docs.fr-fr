---
title: Paramètres de configuration de la globalisation
description: En savoir plus sur les paramètres d’exécution qui configurent les aspects de la globalisation d’une application .NET Core, par exemple la façon dont elle analyse les dates japonaises.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733454"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="cb7b1-103">Options de configuration au moment de l’exécution pour la globalisation</span><span class="sxs-lookup"><span data-stu-id="cb7b1-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="cb7b1-104">Mode indifférent</span><span class="sxs-lookup"><span data-stu-id="cb7b1-104">Invariant mode</span></span>

- <span data-ttu-id="cb7b1-105">Détermine si une application .NET Core s’exécute en mode de globalisation indifférente sans accéder aux données et au comportement spécifiques à la culture, ou si elle a accès aux données culturelles.</span><span class="sxs-lookup"><span data-stu-id="cb7b1-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="cb7b1-106">Par défaut : exécutez l’application avec accès aux données culturelles (`false`).</span><span class="sxs-lookup"><span data-stu-id="cb7b1-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="cb7b1-107">Pour plus d’informations, consultez [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="cb7b1-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="cb7b1-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="cb7b1-108">Setting name</span></span> | <span data-ttu-id="cb7b1-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="cb7b1-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="cb7b1-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="cb7b1-111">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="cb7b1-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="cb7b1-112">`true`-s’exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="cb7b1-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="cb7b1-113">**MSBuild, propriété**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="cb7b1-114">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="cb7b1-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="cb7b1-115">`true`-s’exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="cb7b1-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="cb7b1-116">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="cb7b1-117">`0`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="cb7b1-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="cb7b1-118">`1`-s’exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="cb7b1-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="cb7b1-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="cb7b1-119">Examples</span></span>

<span data-ttu-id="cb7b1-120">fichier *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="cb7b1-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="cb7b1-121">Fichier projet :</span><span class="sxs-lookup"><span data-stu-id="cb7b1-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="cb7b1-122">Plages d’années d’ère</span><span class="sxs-lookup"><span data-stu-id="cb7b1-122">Era year ranges</span></span>

- <span data-ttu-id="cb7b1-123">Détermine si les vérifications de plage pour les calendriers qui prennent en charge plusieurs ères sont assouplies ou si les dates qui dépassent la plage de dates d’une ère lèvent une <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="cb7b1-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="cb7b1-124">Valeur par défaut : les contrôles de plage sont assouplis (`false`).</span><span class="sxs-lookup"><span data-stu-id="cb7b1-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="cb7b1-125">Pour plus d’informations, consultez [calendriers, ères et plages de dates : contrôles de plage souple](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="cb7b1-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="cb7b1-126">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="cb7b1-126">Setting name</span></span> | <span data-ttu-id="cb7b1-127">Valeurs</span><span class="sxs-lookup"><span data-stu-id="cb7b1-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="cb7b1-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="cb7b1-129">`false`-contrôles de plage souples</span><span class="sxs-lookup"><span data-stu-id="cb7b1-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="cb7b1-130">les dépassements de `true` provoquent une exception</span><span class="sxs-lookup"><span data-stu-id="cb7b1-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="cb7b1-131">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-131">**Environment variable**</span></span> | <span data-ttu-id="cb7b1-132">Non applicable</span><span class="sxs-lookup"><span data-stu-id="cb7b1-132">N/A</span></span> | <span data-ttu-id="cb7b1-133">Non applicable</span><span class="sxs-lookup"><span data-stu-id="cb7b1-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="cb7b1-134">Analyse de date japonaise</span><span class="sxs-lookup"><span data-stu-id="cb7b1-134">Japanese date parsing</span></span>

- <span data-ttu-id="cb7b1-135">Détermine si une chaîne qui contient « 1 » ou « gannen » comme année est analysée avec succès ou si seul « 1 » est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cb7b1-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="cb7b1-136">Valeur par défaut : analyser les chaînes qui contiennent soit « 1 » soit « gannen » comme année (`false`).</span><span class="sxs-lookup"><span data-stu-id="cb7b1-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="cb7b1-137">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="cb7b1-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="cb7b1-138">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="cb7b1-138">Setting name</span></span> | <span data-ttu-id="cb7b1-139">Valeurs</span><span class="sxs-lookup"><span data-stu-id="cb7b1-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="cb7b1-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="cb7b1-141">`false`-« gannen » ou « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="cb7b1-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="cb7b1-142">`true` seule « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="cb7b1-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="cb7b1-143">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-143">**Environment variable**</span></span> | <span data-ttu-id="cb7b1-144">Non applicable</span><span class="sxs-lookup"><span data-stu-id="cb7b1-144">N/A</span></span> | <span data-ttu-id="cb7b1-145">Non applicable</span><span class="sxs-lookup"><span data-stu-id="cb7b1-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="cb7b1-146">Format d’année japonaise</span><span class="sxs-lookup"><span data-stu-id="cb7b1-146">Japanese year format</span></span>

- <span data-ttu-id="cb7b1-147">Détermine si la première année d’une ère du calendrier japonais est au format « gannen » ou en tant que nombre.</span><span class="sxs-lookup"><span data-stu-id="cb7b1-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="cb7b1-148">Valeur par défaut : mettez en forme la première année sous la forme « gannen » (`false`).</span><span class="sxs-lookup"><span data-stu-id="cb7b1-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="cb7b1-149">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="cb7b1-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="cb7b1-150">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="cb7b1-150">Setting name</span></span> | <span data-ttu-id="cb7b1-151">Valeurs</span><span class="sxs-lookup"><span data-stu-id="cb7b1-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="cb7b1-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="cb7b1-153">format d' `false` en tant que « gannen »</span><span class="sxs-lookup"><span data-stu-id="cb7b1-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="cb7b1-154">`true` sous forme de nombre</span><span class="sxs-lookup"><span data-stu-id="cb7b1-154">`true` - format as number</span></span> |
| <span data-ttu-id="cb7b1-155">**Variable d’environnement**</span><span class="sxs-lookup"><span data-stu-id="cb7b1-155">**Environment variable**</span></span> | <span data-ttu-id="cb7b1-156">Non applicable</span><span class="sxs-lookup"><span data-stu-id="cb7b1-156">N/A</span></span> | <span data-ttu-id="cb7b1-157">Non applicable</span><span class="sxs-lookup"><span data-stu-id="cb7b1-157">N/A</span></span> |
