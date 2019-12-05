---
title: Paramètres de configuration de la globalisation
description: En savoir plus sur les paramètres d’exécution qui configurent les aspects de la globalisation d’une application .NET Core, par exemple la façon dont elle analyse les dates japonaises.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0571c64eff5b38aafa37026fb2ba7f4aef778beb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802777"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="c4913-103">Options de configuration au moment de l’exécution pour la globalisation</span><span class="sxs-lookup"><span data-stu-id="c4913-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="c4913-104">Mode indifférent</span><span class="sxs-lookup"><span data-stu-id="c4913-104">Invariant mode</span></span>

- <span data-ttu-id="c4913-105">Détermine si une application .NET Core s’exécute en mode de globalisation indifférente sans accéder aux données et au comportement spécifiques à la culture, ou si elle a accès aux données culturelles.</span><span class="sxs-lookup"><span data-stu-id="c4913-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="c4913-106">Par défaut : exécutez l’application avec accès aux données culturelles (`false`).</span><span class="sxs-lookup"><span data-stu-id="c4913-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="c4913-107">Pour plus d’informations, consultez [mode d’invariant de la globalisation .net Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="c4913-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="c4913-108">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c4913-108">Setting name</span></span> | <span data-ttu-id="c4913-109">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c4913-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c4913-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c4913-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="c4913-111">`false`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="c4913-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="c4913-112">`true`-s’exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="c4913-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="c4913-113">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="c4913-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="c4913-114">`0`-accès aux données culturelles</span><span class="sxs-lookup"><span data-stu-id="c4913-114">`0` - access to cultural data</span></span><br/><span data-ttu-id="c4913-115">`1`-s’exécuter en mode invariant</span><span class="sxs-lookup"><span data-stu-id="c4913-115">`1` - run in invariant mode</span></span> |

## <a name="era-year-ranges"></a><span data-ttu-id="c4913-116">Plages d’années d’ère</span><span class="sxs-lookup"><span data-stu-id="c4913-116">Era year ranges</span></span>

- <span data-ttu-id="c4913-117">Détermine si les vérifications de plage pour les calendriers qui prennent en charge plusieurs ères sont assouplies ou si les dates qui dépassent la plage de dates d’une ère lèvent une <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="c4913-117">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="c4913-118">Valeur par défaut : les contrôles de plage sont assouplis (`false`).</span><span class="sxs-lookup"><span data-stu-id="c4913-118">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="c4913-119">Pour plus d’informations, consultez [calendriers, ères et plages de dates : contrôles de plage souple](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="c4913-119">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="c4913-120">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c4913-120">Setting name</span></span> | <span data-ttu-id="c4913-121">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c4913-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c4913-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c4913-122">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="c4913-123">`false`-contrôles de plage souples</span><span class="sxs-lookup"><span data-stu-id="c4913-123">`false` - relaxed range checks</span></span><br/><span data-ttu-id="c4913-124">les dépassements de `true` provoquent une exception</span><span class="sxs-lookup"><span data-stu-id="c4913-124">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="c4913-125">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="c4913-125">**Environment variable**</span></span> | <span data-ttu-id="c4913-126">Non applicable</span><span class="sxs-lookup"><span data-stu-id="c4913-126">N/A</span></span> | <span data-ttu-id="c4913-127">Non applicable</span><span class="sxs-lookup"><span data-stu-id="c4913-127">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="c4913-128">Analyse de date japonaise</span><span class="sxs-lookup"><span data-stu-id="c4913-128">Japanese date parsing</span></span>

- <span data-ttu-id="c4913-129">Détermine si une chaîne qui contient « 1 » ou « gannen » comme année est analysée avec succès ou si seul « 1 » est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c4913-129">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="c4913-130">Valeur par défaut : analyser les chaînes qui contiennent soit « 1 » soit « gannen » comme année (`false`).</span><span class="sxs-lookup"><span data-stu-id="c4913-130">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="c4913-131">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="c4913-131">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="c4913-132">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c4913-132">Setting name</span></span> | <span data-ttu-id="c4913-133">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c4913-133">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c4913-134">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c4913-134">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="c4913-135">`false`-« gannen » ou « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="c4913-135">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="c4913-136">`true` seule « 1 » est pris en charge</span><span class="sxs-lookup"><span data-stu-id="c4913-136">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="c4913-137">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="c4913-137">**Environment variable**</span></span> | <span data-ttu-id="c4913-138">Non applicable</span><span class="sxs-lookup"><span data-stu-id="c4913-138">N/A</span></span> | <span data-ttu-id="c4913-139">Non applicable</span><span class="sxs-lookup"><span data-stu-id="c4913-139">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="c4913-140">Format d’année japonaise</span><span class="sxs-lookup"><span data-stu-id="c4913-140">Japanese year format</span></span>

- <span data-ttu-id="c4913-141">Détermine si la première année d’une ère du calendrier japonais est au format « gannen » ou en tant que nombre.</span><span class="sxs-lookup"><span data-stu-id="c4913-141">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="c4913-142">Valeur par défaut : mettez en forme la première année sous la forme « gannen » (`false`).</span><span class="sxs-lookup"><span data-stu-id="c4913-142">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="c4913-143">Pour plus d’informations, consultez [représenter des dates dans des calendriers avec plusieurs ères](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="c4913-143">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="c4913-144">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="c4913-144">Setting name</span></span> | <span data-ttu-id="c4913-145">Valeurs</span><span class="sxs-lookup"><span data-stu-id="c4913-145">Values</span></span> |
| - | - | - |
| <span data-ttu-id="c4913-146">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="c4913-146">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="c4913-147">format d' `false` en tant que « gannen »</span><span class="sxs-lookup"><span data-stu-id="c4913-147">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="c4913-148">`true` sous forme de nombre</span><span class="sxs-lookup"><span data-stu-id="c4913-148">`true` - format as number</span></span> |
| <span data-ttu-id="c4913-149">**Variable d'environnement**</span><span class="sxs-lookup"><span data-stu-id="c4913-149">**Environment variable**</span></span> | <span data-ttu-id="c4913-150">Non applicable</span><span class="sxs-lookup"><span data-stu-id="c4913-150">N/A</span></span> | <span data-ttu-id="c4913-151">Non applicable</span><span class="sxs-lookup"><span data-stu-id="c4913-151">N/A</span></span> |
